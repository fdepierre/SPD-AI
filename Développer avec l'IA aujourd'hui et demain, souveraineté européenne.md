# Développer avec l'IA : aujourd'hui et demain, avec un objectif de souveraineté européenne

Version de travail du 21 octobre 2026. Révision de cohérence avec SPD-AI, version 1.0 d'octobre 2026 ; dernière révision visible du dépôt : a261f2e. Les références commerciales et chiffrages hérités du 19 octobre ne sont pas tous revérifiés à leur source primaire dans cette révision.

## 1. Objet et périmètre

Ce document décrit comment organiser le développement logiciel assisté par IA (assistants de code, agents, revue, tests, documentation) avec un objectif à moyen terme : utiliser principalement des services européens et des modèles open weight, afin de ne pas dépendre d'entreprises soumises au droit américain, en particulier au CLOUD Act et à la section 702 du FISA.

Il distingue :
- les faits vérifiables (sources citées) ;
- les hypothèses ;
- les recommandations, avec leurs limites.

Il ne remplace pas un avis juridique. Les points contractuels (actionnariat du fournisseur, sous-traitants, clauses de réquisition) doivent être vérifiés fournisseur par fournisseur.

### Articulation avec SPD-AI et convention de lecture

Ce guide est le complément opérationnel de [« Le futur du Product Management à l'ère des agents IA », publié dans SPD-AI](https://github.com/fdepierre/SPD-AI/blob/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md). SPD-AI traite principalement de la valeur, des décisions, de la transmission, des permissions et des preuves ; ce guide décline ces questions pour une chaîne de développement à maîtrise européenne, son hébergement, ses coûts et ses contrôles.

La lecture distingue cinq statuts : fait documenté, déclaration d'un acteur, hypothèse, recommandation et question ouverte, conformément à la méthode présentée dans [SPD-AI, sections 1.2 et 1.3](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md). Une citation ne signifie pas qu'un résultat a été validé indépendamment ; un chiffrage de sensibilité n'est pas une prévision.

Les tableaux d'architecture et de gouvernance sont des recommandations, sauf mention contraire. Les prix, licences et calendriers hérités sont des informations à revalider avant contractualisation ; l'annexe « Réserves et vérifications avant publication » identifie les points qui ne doivent pas être présentés comme établis.

Deux distinctions organisent désormais le guide : développer avec l'IA n'est pas développer un produit contenant de l'IA ; maîtriser l'hébergement n'est pas démontrer la correction du logiciel. Elles prolongent les distinctions de [SPD-AI, sections 1.1, 5.1 et 7.3](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md).

## 2. Le problème juridique en une page

### Ce que dit le CLOUD Act

Le CLOUD Act de 2018 permet aux autorités américaines d'exiger d'un fournisseur soumis à leur juridiction les données qu'il « possède, détient ou contrôle », même si elles sont stockées hors des États-Unis. Le critère est le rattachement du fournisseur, pas l'emplacement de la donnée ([donneespersonnelles.fr](https://www.donneespersonnelles.fr/cloud-souverain)).

Conséquence directe : un hébergement « en région Europe » chez un fournisseur américain, ou chez une filiale européenne d'un groupe américain, ne supprime pas le risque.

### Ce que cela signifie pour le code

Pour un assistant de code, les données exposées ne sont pas seulement les dépôts. Elles comprennent :
- les extraits de code envoyés dans chaque requête (prompts, contexte, fichiers ouverts) ;
- les journaux d'exécution des agents, sorties de compilation et de tests ;
- les secrets accidentellement présents dans le contexte (clés, chaînes de connexion) ;
- la télémétrie des IDE et des extensions ;
- les index sémantiques (embeddings) du code, souvent stockés chez l'éditeur de l'outil.

Un modèle hébergé en Europe ne suffit donc pas si l'IDE, l'agent ou l'indexation passent par un service américain.

### SecNumCloud comme référence la plus exigeante

Les analyses citées présentent SecNumCloud comme un référentiel particulièrement exigeant sur l'exposition aux lois extraterritoriales, notamment par des conditions d'établissement et de contrôle capitalistique ([donneespersonnelles.fr](https://www.donneespersonnelles.fr/cloud-souverain)). Les seuils de 24 % individuellement et 39 % collectivement pour les participations non européennes sont rapportés par une source secondaire ; les conditions exactes et leur application au fournisseur choisi doivent être vérifiées sur le référentiel officiel avant contractualisation ([Oodrive](https://www.oodrive.com/fr/blog/secnumcloud/infrastructure/5-raisons-choisir-environnement-qualifie-secnumcloud/)).

Deux limites à garder en tête :
- ces critères réduisent fortement l'exposition au CLOUD Act et au FISA 702, sans garantie absolue ([Cyber Networks](https://cyber-networks.fr/cybersecurite/secnumcloud-qualification-anssi-guide/)) ;
- une offre reposant sur une pile logicielle américaine soulève des questions spécifiques, citées notamment pour Bleu et S3NS ([Nexthop](https://www.nexthop.fr/secnumcloud/)).

Recommandation : réserver l'exigence SecNumCloud aux projets sensibles (OT, défense, données clients critiques), et accepter un hébergeur européen non qualifié pour le reste, avec une vérification contractuelle.

## 3. Open weight ne veut pas dire souverain

C'est le point le plus souvent mal compris.

| Question | Ce qui protège | Ce qui ne protège pas |
|---|---|---|
| Qui peut accéder à mes données ? | L'opérateur de l'inférence (vous ou un hébergeur européen) | La nationalité du créateur du modèle |
| Le modèle peut-il être retiré ? | Avoir les poids en local, avec une licence permissive | Une API, même européenne |
| Puis-je l'utiliser commercialement ? | Apache 2.0, MIT | Licences « modifiées » à seuils |
| Le modèle est-il fiable ? | Vos propres tests | Le pays d'origine, les classements publics |

### Modèle chinois auto-hébergé ou API chinoise

Exécuter les poids d'un modèle Qwen, GLM ou DeepSeek sur une infrastructure maîtrisée ne nécessite pas, en soi, d'envoyer les requêtes au laboratoire d'origine ; le contrôle dépend aussi du moteur d'inférence, des bibliothèques, de la télémétrie et des accès réseau, pas seulement de l'origine des poids, selon l'analyse de la chaîne proposée dans [SPD-AI, section 7.3.1](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md). Recommandation : vérifier ces flux dans le déploiement réel, plutôt que promettre une absence automatique de transmission.

Risques résiduels d'un modèle open weight, quelle que soit son origine :
- biais ou comportements indésirables liés à l'entraînement (hypothèse à tester, pas un fait démontré pour un modèle donné) ;
- dépendance au rythme de publication d'un laboratoire étranger ;
- licence pouvant changer pour les versions futures (les versions déjà publiées restent sous leur licence d'origine).

### Licences : à vérifier modèle par modèle

Exemple concret : la licence « MIT modifiée » de Mistral pour Mistral Medium 3.5 128B et Devstral 2 123B n'accorde aucun droit si le chiffre d'affaires mensuel consolidé de l'entreprise dépasse 20 millions de dollars ; il faut alors une licence commerciale ou passer par les services hébergés de Mistral ([Developers Digest](https://www.developersdigest.tech/local-models/licenses)). D'autres modèles Mistral, comme Devstral Small 2 24B, Mistral Small 4 et Mistral Large 3, figurent parmi les modèles sous licence permissive standard selon la même source.

Autre point : Scaleway indique que certaines licences restrictives (par exemple non commerciales) ne s'appliquent pas à l'usage via ses produits, grâce à des partenariats ([Scaleway](https://www.scaleway.com/en/docs/generative-apis/reference-content/supported-models/)). C'est utile, mais cela crée une dépendance à l'hébergeur : le même modèle auto-hébergé n'aurait pas les mêmes droits.

## 4. La situation aujourd'hui (octobre 2026)

### Les briques d'une chaîne de développement assisté par IA

| Brique | Rôle | Point de vigilance souveraineté |
|---|---|---|
| Modèle | Génère et modifie le code | Opérateur de l'inférence, licence |
| Inférence | Exécute le modèle (API ou serveur) | Juridiction de l'hébergeur |
| Agent / IDE | Lit les fichiers, appelle les outils, lance les tests | Télémétrie, indexation, relais cloud |
| Forge Git | Dépôts, revues, CI | Hébergement du code source lui-même |
| CI / exécution | Compilation, tests, sandbox de l'agent | Accès aux secrets, réseau sortant |
| Sécurité | Scanners, revue, SBOM | Ne pas confier la validation au même modèle que la génération |

### Offres européennes d'inférence disponibles

Scaleway Generative APIs :
- hébergement à Paris, API compatible OpenAI ([DeepWiki, documentation Scaleway](https://deepwiki.com/scaleway/docs-content/5.1-generative-apis)) ;
- catalogue incluant GLM-5.3 (contexte 256k), Devstral 2 123B, DeepSeek-V4-Flash et Qwen3.8 27B ([Scaleway, modèles supportés](https://www.scaleway.com/en/docs/generative-apis/reference-content/supported-models/), [Scaleway, documentation](https://www.scaleway.com/en/docs/generative-apis/)) ;
- Scaleway affirme que Qwen3.8 27B est le modèle open weight le plus performant de sa taille sur la plupart des benchmarks en août 2026 et qu'il peut être branché dans des outils agentiques ou IDE ([Scaleway](https://www.scaleway.com/en/docs/generative-apis/)). C'est une affirmation du fournisseur, à vérifier sur vos tâches ;
- tarif public affiché par exemple pour mistral-medium-3.5-128b : 1,50 € par million de tokens en entrée, 7,50 € en sortie ([Scaleway](https://www.scaleway.com/en/generative-apis/)) ;
- déploiements dédiés possibles, y compris de vos propres modèles ([Scaleway FAQ](https://www.scaleway.com/en/docs/generative-apis/faq/)).

OVHcloud AI Endpoints :
- plus de 20 modèles open weight, hébergés et exploités dans l'UE, données non utilisées pour l'entraînement ([OVHcloud](https://www.ovhcloud.com/en/public-cloud/ai-endpoints/)) ;
- API compatible OpenAI, intégration annoncée avec OpenCode, Continue et Hugging Face ([OVHcloud](https://www.ovhcloud.com/en/public-cloud/ai-endpoints/)) ;
- limite de 400 requêtes par minute par projet et par modèle avec clé d'API ([OVHcloud docs](https://docs.ovhcloud.com/en/guides/public-cloud/ai-machine-learning/ai-endpoints-capabilities.md)) ;
- cycle de vie : certains modèles sont retirés après environ trois mois d'annonce, par exemple Mistral-Small-3.2-24B, retrait prévu le 4 novembre 2026 ([OVHcloud docs](https://docs.ovhcloud.com/en/guides/public-cloud/ai-machine-learning/ai-endpoints-billing)).

À compléter selon vos besoins : Mistral AI (API et offres entreprise), IONOS, OUTSCALE, Cloud Temple et autres hébergeurs qualifiés SecNumCloud. [à vérifier : catalogue IA et qualification réelle de chaque offre]

Point important : le cycle de vie des modèles chez un hébergeur est une contrainte d'exploitation. Scaleway documente des dates de dépréciation et de fin de vie, avec redirection automatique vers un autre modèle ([Scaleway](https://www.scaleway.com/en/docs/generative-apis/reference-content/supported-models/)). Une redirection silencieuse peut changer le comportement d'un agent : il faut fixer les versions et suivre ces annonces.

### Le maillon faible actuel : les outils

Les modèles et l'inférence européens existent. Le vrai écart se situe dans les outils : les assistants les plus utilisés (Cursor, GitHub Copilot, Claude Code, Codex, Windsurf, etc.) sont édités par des entreprises américaines et s'appuient souvent sur leurs propres services cloud, même quand on configure un modèle externe.

Alternatives réalistes aujourd'hui :
- agents open source configurables avec un point d'accès compatible OpenAI : OpenCode, Continue, Aider, Cline et équivalents ;
- IDE sans télémétrie obligatoire : VSCodium, JetBrains (éditeur d'origine européenne, mais vérifier où passent les fonctions IA), Neovim, Zed ;
- forge auto-hébergée : GitLab self-managed, Forgejo/Gitea, ou un hébergement européen.

Hypothèse de travail : ces outils open source offrent aujourd'hui une expérience un peu moins intégrée que les meilleurs outils commerciaux, mais l'écart dépend surtout de la qualité du modèle et du contexte fourni. À mesurer dans le pilote.

### Cadre réglementaire européen

Les obligations des fournisseurs de modèles d'IA à usage général (GPAI) s'appliquent depuis le 2 août 2025, et les pouvoirs d'exécution de la Commission depuis le 2 août 2026 ([AI Act Service Desk](https://ai-act-service-desk.ec.europa.eu/fr/faq?combine=)). Les fournisseurs de modèles sous licence libre et open source n'ont, sauf risque systémique, que les obligations liées au droit d'auteur et au résumé des données d'entraînement ([artificialintelligenceact.eu](https://artificialintelligenceact.eu/fr/high-level-summary/)).

Pour une équipe qui utilise un assistant de code en interne, l'AI Act pèse surtout indirectement : documentation fournie par les fournisseurs, littératie IA des équipes, et vigilance si le logiciel produit est lui-même un système IA à haut risque. Les obligations de l'annexe III ont été reportées au 2 décembre 2027 selon [Cabinet Persée](https://cabinetpersee.com/blog/posts/ai-act-ce-qui-change-2026/).

Pour vos sujets industriels, le Cyber Resilience Act et l'IEC 62443 comptent davantage : le code généré par IA reste sous votre responsabilité de fabricant (gestion des vulnérabilités, SBOM, traçabilité).

### Autres référentiels « à la SecNumCloud » à considérer

SecNumCloud n'est pas seul. Plusieurs dispositifs européens se recoupent, se complètent ou se concurrencent. Le point important : la plupart s'appliquent à l'hébergement et aux services, pas à votre logiciel lui-même. Pour un éditeur de logiciel souverain, ils comptent à deux titres : pour choisir où faire tourner votre SaaS, et comme exigences d'accès à certains marchés publics.

| Dispositif | Pays ou niveau | Statut au 19 octobre 2026 | Ce qu'il couvre | Quand il vous concerne |
|---|---|---|---|---|
| EUCS | UE | non adopté : en négociation depuis 2020, les critères de souveraineté ont été retirés des projets et l'adoption reste bloquée ([Wikipédia](https://en.wikipedia.org/wiki/EUCS_(cloud_computing)), [Nexthop](https://www.nexthop.fr/en/understand/eucs)) | certification cloud européenne à trois niveaux (base, substantiel, élevé), harmonisant les schémas nationaux | à surveiller : c'est le futur cadre unifié, mais aucun fournisseur ne peut aujourd'hui revendiquer une certification EUCS |
| Cloud and AI Development Act | UE | projet présenté le 3 juin 2026 par la Commission : un cadre de souveraineté à quatre niveaux pour la commande publique, de la localisation européenne jusqu'au contrôle capitalistique ([IT SOCIAL](https://itsocial.fr/cybersecurite/cybersecurite-articles/eucs-et-cada-leurope-abandonne-la-souverainete-dans-son-label-cloud-et-la-reintroduit-dans-la-commande-publique/)) | critères de souveraineté dans les marchés publics cloud | à intégrer dans votre veille si vous visez la commande publique européenne |
| EUCC | UE | adopté (règlement d'exécution (UE) 2024/482), opérationnel depuis février 2025 ([Commission européenne](https://digital-strategy.ec.europa.eu/en/factpages/european-cybersecurity-certification-framework), [ENISA](https://certification.enisa.europa.eu/browse-topic/eucc_en?prefLang=ro)) | certification de produits ICT (matériel, logiciel, composants), basée sur Common Criteria, certificats valides jusqu'à 5 ans | si votre logiciel est un produit ICT à exigence de sécurité : c'est le premier schéma européen réellement délivrable |
| C5 | Allemagne | version C5:2026 publiée en avril 2026, 168 critères sur 17 domaines, opposable aux audits à partir de juin 2027 ; le BSI prépare en complément des critères de souveraineté pour le cloud ([BSI](https://www.bsi.bund.de/DE/Service-Navi/Presse/Pressemitteilungen/Presse2026/260407_C5_Cloud_Computing.html), [CloudPick](https://docs.cloudpick.kr/en/eu/national-schemes/)) | attestation (par des auditeurs, pas une certification d'État) de la sécurité des services cloud | si vos clients sont allemands ou publics : l'attestation C5 de votre hébergeur est le standard de facto |
| ENS | Espagne | en vigueur (real decreto 311/2022) ([Ministère de l'Économie espagnol](https://portal.mineco.gob.es/es-es/ministerio/estrategias/Paginas/Esquema_Nacional_de_Seguridad.aspx)) | schéma national de sécurité pour le secteur public espagnol et ses fournisseurs technologiques, avec exigences dédiées au cloud et à la chaîne d'approvisionnement | si vous vendez au secteur public espagnol |
| Qualifications ACN | Italie | en vigueur | cadre de qualification des services cloud pour l'administration italienne ([CloudPick](https://docs.cloudpick.kr/en/eu/national-schemes/)) | si vous vendez au secteur public italien |
| HDS | France | certification obligatoire pour l'hébergement de données de santé, ISO 27001 exigée, hébergement physique limité à l'EEE, exigences de souveraineté au chapitre 7 du référentiel ([Agence du Numérique en Santé](https://esante.gouv.fr/labels-certifications/hebergement-des-donnees-de-sante), [sante.gouv.fr](https://sante.gouv.fr/actualites-presse/presse/communiques-de-presse/article/publication-au-journal-officiel-du-referentiel-de-certification-hds)) | hébergement des données de santé à caractère personnel | si votre logiciel traite des données de santé, même indirectement |

Lecture pratique de ce paysage :

1. Pour votre logiciel lui-même, la conformité produit passe par le CRA (section 10) et, pour un produit ICT à exigence de sécurité, par l'EUCC. Pour vos déploiements OT, l'IEC 62443 reste la référence. Les référentiels cloud ne certifient pas votre code.
2. Les schémas nationaux restent le passeport réel : SecNumCloud en France, C5 en Allemagne, ENS en Espagne, ACN en Italie. Si votre SaaS vise plusieurs marchés publics européens, le plus réaliste aujourd'hui est un hébergeur multi-qualifié ou un déploiement par pays.
3. L'EUCS devait unifier tout cela, mais les critères de souveraineté ont été retirés des projets face aux divisions entre États membres : un service certifié EUCS pourrait reposer sur un fournisseur exposé au CLOUD Act ([IT SOCIAL](https://itsocial.fr/cybersecurite/cybersecurite-articles/eucs-et-cada-leurope-abandonne-la-souverainete-dans-son-label-cloud-et-la-reintroduit-dans-la-commande-publique/)). La Commission semble déplacer la souveraineté vers la commande publique (Cloud and AI Development Act). À suivre de près, sans construire aujourd'hui une architecture qui dépend d'un texte non adopté.
4. Recommandation : construire un système de management de la sécurité cohérent, puis cartographier les exigences propres à chaque référentiel. Ne pas supposer qu'ISO 27001 est partout exigée, qu'elle vaut équivalence ou qu'une qualification en remplace une autre.
5. Recommandation : choisir ensemble les marchés visés, les exigences applicables, l'opérateur, l'hébergement et les accès d'administration. La localisation seule ne suffit ni à établir la souveraineté ni à obtenir la qualification du service fourni.

## 5. Architecture cible recommandée

### Principe : trois niveaux de confidentialité

| Niveau | Exemples | Inférence autorisée | Outils autorisés |
|---|---|---|---|
| N1 – Public | Code open source, docs publiques | Toute API, y compris US si besoin | Tous |
| N2 – Interne | Applications métier, outils internes | Hébergeur européen (Scaleway, OVHcloud, Mistral…) | Agents open source, sans télémétrie |
| N3 – Sensible | Code OT, PLC, sécurité, données clients, défense | Auto-hébergé ou SecNumCloud | Agents open source, réseau sortant filtré |

Ce découpage évite deux erreurs : tout interdire (perte de productivité, usage parallèle non contrôlé) ou tout autoriser (fuite de code sensible).

Ces niveaux sont une politique proposée, pas des catégories réglementaires. Ils s'appliquent au contenu de chaque artefact : dépôt, extrait, spécification, capture, binaire, jeu de tests, index sémantique et journal ; ils ne déterminent pas les permissions de l'agent, conformément à [SPD-AI, section 5.1.5](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md).

Une spécification dérivée de règles sensibles conserve leur classification, sauf revue et déclassement explicites. Ni un logiciel neuf n'est public par défaut, ni un patrimoine ancien sensible par nature ; une classification doit précéder l'accès des agents, comme le souligne [SPD-AI, section 6.1](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md).

### Schéma logique

```
Développeur (IDE sans télémétrie + agent open source)
        |
  Passerelle IA interne (routage, journalisation, filtrage des secrets, quotas)
        |-------------------------|---------------------------|
  N3 : serveur interne        N2 : API européenne        N1 : API au choix
  (vLLM / SGLang,             (Scaleway, OVHcloud,
   modèle compact)             Mistral…)
        |
  Forge Git européenne / auto-hébergée -> CI isolée -> scanners de sécurité -> revue humaine
```

La passerelle interne (par exemple LiteLLM ou équivalent auto-hébergé) est la pièce maîtresse :
- elle rend les modèles interchangeables, sans modifier les postes ;
- elle applique les règles de destination selon la classification du dépôt et de chaque artefact ;
- elle détecte et bloque les secrets identifiables avant envoi, sans garantie d'exhaustivité ;
- elle fournit les mesures de coût et d'usage.

Recommandation : séparer la passerelle d'inférence de la sandbox d'exécution et de l'autorité d'acceptation. La passerelle ne remplace ni le filtrage des autres sorties réseau, ni le contrôle des outils appelés, ni la revue des preuves ; un service construit sur une infrastructure qualifiée ne doit pas être présenté comme lui-même qualifié sans vérification de son périmètre.

### Patrimoine transmissible, plutôt que contexte accumulé

SPD-AI propose une chaîne de connaissance qui dépasse le code : contexte, règles validées, spécifications, décisions, réalisation, preuves et retours d'exploitation ; il distingue également le contexte court destiné aux agents de la mémoire explicative destinée aux personnes ([SPD-AI, section 4.1](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). Nous recommandons de conserver cette chaîne dans la forge maîtrisée, avec les mêmes contrôles de confidentialité que le code.

| Fichier proposé | Contenu minimal | Responsable de la validation |
|---|---|---|
| `contexte.md` | Utilisateurs, objectifs, périmètre et exclusions | Product et métier |
| `regles.md` | Définitions, unités, calculs, exceptions, références et dates de validité | Référent métier ou industriel |
| `decisions.md` | Options retenues ou rejetées, raisons, risques et inconnues | Décideur identifié selon le sujet |
| `verification.md` | Cas de référence, résultats attendus, preuves et limites | Ingénierie, métier et qualité |
| `exploitation.md` | Versions, responsables, accès, incidents, support et reprise | Exploitation et sécurité |
| `marche.md`, si pertinent | Segments, alternatives, intégrations, hypothèses d'achat, sources et dates | Product |

Ce dispositif est une proposition de méthode, pas une norme ni une obligation de créer ces noms de fichiers ; il reprend le dispositif minimal de [SPD-AI, section 4.1.4](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md). Pour chaque règle, tenir séparément son approbation métier, son implémentation et sa couverture de tests, avec provenance, date et validateur.

Recommandation : limiter `AGENTS.md` aux consignes utiles et non standard, puis mesurer leur effet au lieu d'injecter toute la documentation dans chaque requête. Un successeur doit pouvoir retrouver les raisons d'une décision et maintenir le produit, même si l'outil ou le modèle d'origine a disparu.

### Architecture vérifiable et réversible

SPD-AI propose de séparer le moteur métier de ses canaux d'accès et de préserver contrats d'interface, permissions, chaîne de compilation et preuves par plateforme ; Rust, WebAssembly ou WebGPU y sont des options à évaluer, pas des garanties universelles de qualité ([SPD-AI, section 5.3](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). La recommandation pratique est de choisir des composants que l'équipe peut effectivement comprendre, tester, remplacer et exploiter, plutôt qu'une pile supposée idéale pour les agents.

### Choix de modèles pour un pilote

| Rôle | Candidat | Où l'exécuter |
|---|---|---|
| Référence de qualité, tâches difficiles | GLM-5.3 | API européenne (disponible chez [Scaleway](https://www.scaleway.com/en/docs/generative-apis/reference-content/supported-models/)) |
| Modèle de code européen | Devstral 2 123B, Devstral Small 2 24B | API Mistral ou européenne ; vérifier la licence avant auto-hébergement |
| Candidat compact local | Qwen3.8 27B | Serveur interne ou API européenne |
| Référence coût/vitesse | DeepSeek-V4-Flash | Hébergeur européen, pas l'API chinoise |

## 6. Demain : 12 à 36 mois

Ce qui suit relève de l'analyse prospective, pas de faits établis.

### Tendances probables

- Des modèles compacts (20 à 80 milliards de paramètres) suffisants pour la majorité des tâches courantes. C'est la tendance la plus favorable à l'auto-hébergement, car elle ramène le besoin matériel à un ou deux serveurs GPU.
- Des agents plus autonomes, qui travaillent de longues heures sur un ticket. Le coût se déplace alors vers la mémoire de contexte et la sandbox d'exécution, plus que vers les poids du modèle.
- Une offre européenne plus large : catalogues d'inférence plus fournis, offres qualifiées SecNumCloud avec GPU, et probablement des outils de développement européens plus complets. [à vérifier au fil des annonces]
- Des exigences clients et réglementaires plus fortes sur la traçabilité du code généré (CRA, NIS2 chez vos clients, achats publics).

### Trois trajectoires à ne pas confondre avec une prévision

SPD-AI présente trois futurs à égalité : une autonomie accompagnée des métiers, une spécification devenue artefact principal, ou une automatisation beaucoup plus large ; dans les trois cas, transmission, preuves, décisions sur la valeur et responsabilités demeurent nécessaires ([SPD-AI, section 8.1](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). Ce guide ne présume donc ni la disparition de la lecture du code, ni la régénération fiable de tous les produits, ni la supériorité durable d'une taille de modèle.

Recommandation : conserver des spécifications, interfaces, preuves et procédures de reprise portables dans chacune de ces trajectoires. L'option d'un remplacement futur du modèle ou de l'agent doit être vérifiée par un essai de substitution, pas seulement annoncée dans l'architecture.

### Ce qui pourrait remettre en cause la stratégie

| Évènement | Effet | Réponse |
|---|---|---|
| Écart de qualité fort et durable entre modèles fermés US et open weight | Coût d'opportunité de la souveraineté | Garder N1 ouvert aux meilleurs modèles pour le code non sensible |
| Changement de licence des futurs modèles open weight | Moins de choix en auto-hébergement | Conserver les poids et versions validés ; diversifier les familles |
| Hébergeur européen racheté par un groupe non européen | Perte de l'immunité | Clause de changement de contrôle, passerelle permettant de basculer |
| Pénurie ou forte hausse des GPU | Coût de l'auto-hébergement | Location chez un hébergeur européen plutôt qu'achat |
| Restrictions d'export sur les modèles ou puces | Accès aux nouvelles versions | Stock de versions validées, veille |

## 7. Feuille de route proposée

### Phase 1 – 0 à 3 mois : cadrer et mesurer

- Classer les dépôts et leurs artefacts en N1, N2, N3 ; désigner les responsables des déclassements.
- Constituer le patrimoine minimal et distinguer comportement observé, règle approuvée et comportement cible.
- Définir les permissions des agents et l'autorité d'acceptation avant les premiers essais.
- Inventorier les outils IA déjà utilisés (y compris usages personnels non déclarés).
- Mettre en place la passerelle IA et un agent open source sur un groupe pilote.
- Constituer un banc d'essai interne : 30 à 50 tickets réels (Python, JavaScript, Structured Text, modèles d'optimisation), avec critères d'acceptation.
- Comparer 3 à 4 modèles sur ce banc via des API européennes, sans achat matériel.

### Phase 2 – 3 à 9 mois : généraliser N2, préparer N3

- Étendre aux équipes sur le code N2.
- Louer un serveur GPU européen pour tester un modèle compact en N3.
- Mettre en place les règles : revue dimensionnée selon le risque, scanners, SBOM, preuves indépendantes et journalisation des contributions IA.
- Financer le maintien des tests, de la compréhension des équipes et de la capacité de reprise, pas seulement la consommation IA.
- Négocier les contrats : localisation, sous-traitants, absence d'entraînement sur vos données, notification des réquisitions, changement de contrôle.

### Phase 3 – 9 à 24 mois : réduire la dépendance US

- Basculer progressivement les usages N1 vers les services européens si la qualité mesurée le permet.
- Décider achat ou location du matériel N3 selon la charge mesurée.
- Revoir le banc d'essai à chaque génération de modèles majeure.

## 8. Indicateurs à suivre

L'indicateur de gestion proposé est le coût complet par modification acceptée puis maintenue en exploitation, et non le prix du token ou le volume de code ; SPD-AI le décompose en huit activités et rappelle qu'une acceptation trop indulgente peut fausser la mesure ([SPD-AI, section 7.2](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). Nous recommandons une fenêtre d'observation explicite, par exemple 30 jours à adapter au cycle du produit, sans attendre cette échéance pour traiter les incidents graves.

\[
\text{Coût par modification acceptée} = \frac{\text{coûts complets de la période, reprises et défauts inclus}}{\text{modifications acceptées et maintenues sur la fenêtre retenue}}
\]

Compléter par :
- taux de modifications acceptées sans retouche ;
- temps de revue humaine par modification ;
- régressions et vulnérabilités détectées après fusion ;
- part de l'usage IA passant par des services européens ou internes (indicateur de souveraineté) ;
- satisfaction des développeurs (un outil contourné n'apporte aucune protection).

Décomposer le coût en préparation du contexte, génération, évaluations automatiques, revue, corrections, déploiement, surveillance et défauts après acceptation, conformément à [SPD-AI, section 7.2.1](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md). Pour éviter les doubles comptes, répartir la plateforme partagée une seule fois, puis enregistrer les temps humains et consommations propres à chaque activité.

Recommandation : suivre aussi les écarts métier inexpliqués, les retours arrière, le temps de reprise par un autre ingénieur et l'effet sur l'usage réel. Une meilleure note technique ou davantage de tickets fermés ne démontrent pas, seuls, une meilleure valeur produit.

## 9. Règles de sécurité indépendantes du modèle

- Ne jamais donner à l'agent des droits de fusion ou de déploiement.
- Exécuter les agents dans une sandbox, réseau sortant limité à la passerelle.
- Interdire les secrets dans le contexte (détection automatique avant envoi).
- Valider le code généré par des outils indépendants (SAST, analyse des dépendances, tests), pas par le même modèle.
- Vérifier les dépendances proposées par l'IA : paquets inexistants ou malveillants au nom proche.
- Pour le code OT et PLC : revue par un expert du domaine et tests sur simulateur avant tout essai sur équipement.

### Permissions explicites et autorité d'acceptation

Le cadre de permissions de SPD-AI distingue accès, modification, validation, escalade et réversibilité ; il ne les déduit ni de la confidentialité ni de la seule capacité du modèle ([SPD-AI, section 5.1](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). Les valeurs ci-dessous sont recommandées pour un produit partagé ou critique.

| Permission | Règle de départ | Contrôle attendu |
|---|---|---|
| Accès | Seulement les artefacts nécessaires et les destinations autorisées | Identité, périmètre et journal d'accès |
| Modification | Branche de travail ou sandbox ; aucune écriture de production | Droits techniques limités et contrôle des outils |
| Validation | Proposer un dossier, sans auto-accepter le changement | Décision par l'autorité désignée |
| Escalade | Arrêt en cas de règle ambiguë, secret, effet irréversible ou écart inexpliqué | Critères d'arrêt et interlocuteur identifiés |
| Réversibilité | Retour arrière vérifié avant toute action engageante | Sauvegarde, restauration et procédure testées |

SPD-AI sépare trois acceptations : technique, métier, puis produit et exploitation ; il souligne que désigner un signataire sans temps, information ni pouvoir de refus ne constitue pas une supervision effective ([SPD-AI, section 5.2](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). Recommandation : affecter ces décisions aux personnes compétentes, pas automatiquement au Product Manager, et conserver leurs raisons, les réserves et la version des preuves.

Recommandation : protéger les tests d'acceptation et les données de référence contre les modifications non approuvées des agents ; conserver des contrôles indépendants de ceux qui pilotent la génération. Des tests passés, un second modèle favorable ou une sandbox ne suffisent pas à exclure un défaut métier ou une exfiltration.

## 10. Compliance NIS2 et Cyber Resilience Act

Ces deux textes transforment vos choix d'outils IA en enjeu de conformité, pas seulement de productivité. NIS2 vous concerne comme entité potentiellement assujettie (énergie, fabrication), le CRA comme fabricant si vos logiciels sont mis sur le marché européen.

### 10.1 NIS2 : ce qui vous attend

Repères et réserves sur l'état du droit :
- la directive (UE) 2022/2555 couvre 18 secteurs critiques, dont l'énergie, avec deux catégories d'entités (essentielles et importantes) et des mesures minimales de gestion des risques ([Commission européenne](https://digital-strategy.ec.europa.eu/en/policies/nis2-directive)) ;
- l'état juridique exact de la transposition française n'est pas établi par cette révision : SPD-AI le conserve comme point à vérifier, plutôt que d'en déduire une date ou une absence de promulgation ([SPD-AI, sections 7.3.4 et H.3](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)) ;
- SPD-AI relève la disponibilité du Référentiel Cyber France (ReCyF) depuis le 17 mars 2026 comme document de travail ; ce guide recommande de l'utiliser pour la préparation, sans le présenter comme une certification ni une garantie de conformité ([SPD-AI, section 7.3.4](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)) ;
- l'enregistrement des entités se fera sur la plateforme MonEspaceNIS2, en cours de développement ([FAQ MonEspaceNIS2](https://aide.monespacenis2.cyber.gouv.fr/fr/category/obligations-9vpf70/)).

Les mesures minimales de l'article 21 incluent notamment : analyse de risques, gestion d'incidents, continuité d'activité, sécurité de la chaîne d'approvisionnement, sécurité de l'acquisition, du développement et de la maintenance (y compris traitement et divulgation des vulnérabilités), cyberhygiène, cryptographie, contrôle d'accès et authentification multifacteur ([ANSSI, FAQ NIS2](https://aide.monespacenis2.cyber.gouv.fr/fr/article/quelles-sont-les-exigences-en-matiere-de-cybersecurite-auxquelles-les-entites-regulees-a-la-directive-nis-2-devront-se-soumettre-193huwi/)). L'article 20 impose en plus que l'organe de direction approuve ces mesures et en supervise la mise en œuvre, ses membres devant suivre une formation.

### 10.2 NIS2 appliqué à votre chaîne de développement IA

C'est le point de jonction avec ce document : la sécurité de la chaîne d'approvisionnement (article 21(2)(d)) et la sécurité du développement (article 21(2)(e)) englobent vos outils d'IA.

| Exigence NIS2 | Application à la chaîne IA | Lien avec ce document |
|---|---|---|
| Sécurité de la chaîne d'approvisionnement | Vos fournisseurs d'inférence, d'IDE, d'agents et d'hébergement sont des fournisseurs directs : évaluer leurs pratiques de développement sécurisé | Sections 3 et 4 (choix de fournisseurs, contrats) |
| Sécurité du développement et des vulnérabilités | Le code généré par IA entre dans vos produits : processus de détection, correction et divulgation des vulnérabilités | Section 9 (règles de sécurité) |
| Analyse de risques | Cartographier les risques propres à chaque usage d'IA (fuite de code, dépendance, injection) | Passerelle et classification N1/N2/N3 |
| Contrôle d'accès et MFA | Restreindre les droits des agents, journaliser leurs actions | Section 9 (droits des agents) |
| Gouvernance (art. 20) | La direction approuve la politique d'usage de l'IA et les mesures associées | Politique d'usage à formaliser |

Recommandations concrètes :
1. Documenter une politique d'usage de l'IA en développement, approuvée par la direction : c'est une déclinaison proposée de la gouvernance, pas l'affirmation que l'article 20 exige un document portant ce titre.
2. Évaluer formellement chaque fournisseur de la chaîne IA (hébergeur, éditeur d'outil, forge) sur ses pratiques de développement sécurisé : l'article 21(3) impose de tenir compte des vulnérabilités propres à chaque fournisseur direct.
3. Le ReCyF de l'ANSSI donne une base de travail dès maintenant, sans attendre la loi : l'utiliser comme grille d'autodiagnostic.
4. Anticiper la notification d'incidents significatifs : alerte sous 24 h, notification sous 72 h. Un incident lié à un outil IA (fuite de code, compromission d'un agent) peut être un incident NIS2 : la classification N1/N2/N3 aide à qualifier la gravité.

### 10.3 Cyber Resilience Act : ce qui vous attend

Le CRA (règlement (UE) 2024/2847) impose des exigences de cybersécurité aux produits numériques mis sur le marché européen. Calendrier vérifié :
- 11 juin 2026 : application des dispositions sur la notification des organismes d'évaluation de conformité ([entreprises.gouv.fr](https://www.entreprises.gouv.fr/decryptages-de-nos-experts/cyber-resilience-act-cra-ce-qui-change-pour-les-entreprises-et-comment)) ;
- 11 septembre 2026 : obligations de signalement en vigueur. Les fabricants doivent notifier les vulnérabilités activement exploitées et les incidents graves via la plateforme unique de l'ENISA : alerte précoce sous 24 h, notification sous 72 h, rapport final sous 14 jours (vulnérabilités) ou un mois (incidents) ([Commission européenne](https://digital-strategy.ec.europa.eu/en/policies/cra-reporting), [ENISA](https://www.enisa.europa.eu/news/the-cra-single-reporting-platform-is-launched)) ;
- 11 décembre 2027 : application complète, marquage CE et exigences essentielles de l'annexe I ([Commission européenne](https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act)).

L'annexe I se lit en deux parties : les propriétés de sécurité du produit (sécurité par défaut, surface d'attaque réduite, mises à jour de sécurité installables automatiquement par défaut) et les processus exigés du fabricant : SBOM dans un format courant et lisible par machine couvrant au moins les dépendances de premier niveau, politique de divulgation coordonnée, point de contact pour les signalements, tests réguliers et diffusion gratuite des mises à jour de sécurité ([VamiSec](https://vamisec.com/fr/wissen/grc/eu-cyber-resilience-act)).

### 10.4 CRA appliqué à votre développement assisté par IA

Le CRA s'applique au produit, pas à la manière dont il a été écrit. Le code généré par IA n'est ni exonéré ni plus sévèrement traité : ce sont vos processus qui prouvent la conformité.

| Exigence CRA (annexe I) | Conséquence pour le développement assisté par IA |
|---|---|
| Développement sécurisé sur la base des risques | L'agent IA devient un outil du processus : il doit s'exécuter dans un pipeline qui applique vos règles (revue, scanners, tests) |
| SBOM lisible par machine, dépendances de premier niveau | Vérifier automatiquement les dépendances proposées par l'IA (risque de paquets malveillants au nom proche) et générer le SBOM à chaque build |
| Gestion des vulnérabilités et divulgation coordonnée | Toute vulnérabilité introduite par du code IA suit le même processus de gestion ; la trace des contributions IA facilite l'analyse d'impact |
| Mises à jour de sécurité gratuites pendant la période de support | Dimensionner la maintenance des produits dont le code évolue plus vite grâce à l'IA |
| Signalement 24 h / 72 h (depuis le 11 septembre 2026) | Une vulnérabilité activement exploitée dans un produit mis sur le marché déclenche l'obligation, même si le code est d'origine IA |

Points de vigilance :
- la charge de signalement CRA s'applique aussi aux produits déjà mis sur le marché avant le 11 septembre 2026 ([CMS](https://cms.law/en/int/legal-updates/ready-respond-report-the-cyber-resilience-act-s-reporting-regime-is-here)) ;
- les « stewards » de logiciels open source ne sont soumis au signalement qu'à partir du 11 décembre 2027 ([ENISA](https://www.enisa.europa.eu/news/the-cra-single-reporting-platform-is-launched)) ; si vous maintenez des dépôts open source utilisés dans des produits, clarifiez votre statut ;
- si votre logiciel contient de l'IA, l'AI Act se superpose : les obligations GPAI s'appliquent depuis août 2025 et les pouvoirs d'exécution depuis le 2 août 2026 ([AI Act Service Desk](https://ai-act-service-desk.ec.europa.eu/fr/faq?combine=)), avec le report des systèmes à haut risque de l'annexe III au 2 décembre 2027 ([Cabinet Persée](https://cabinetpersee.com/blog/posts/ai-act-ce-qui-change-2026/)).

### 10.5 Ce que cela change concrètement

Ces deux textes renforcent plutôt qu'ils ne contredisent l'architecture proposée :
- la classification N1/N2/N3 et la passerelle fournissent la documentation demandée par NIS2 (analyse de risques, traçabilité) et préparent les processus CRA (vulnérabilités, divulgation) ;
- les règles de sécurité de la section 9 (SBOM, scanners, divulgation coordonnée, point de contact) sont directement alignées sur l'annexe I du CRA ;
- la préférence pour des fournisseurs européens avec contrats vérifiés s'inscrit dans l'exigence NIS2 de sécurité de la chaîne d'approvisionnement ;
- la journalisation des contributions IA dans la forge facilite les rapports de vulnérabilité : savoir quelles modifications sont d'origine IA accélère l'analyse d'impact.

Actions recommandées : une politique d'usage de l'IA formellement approuvée par la direction, un inventaire documenté des fournisseurs et un exercice de notification. Malgré des délais initiaux proches, ne pas fusionner les analyses NIS2 et CRA : instruire séparément l'entité ou le produit concerné, l'événement déclencheur, les destinataires et les conditions du rapport final.

### Relier les preuves aux obligations sans inventer une certification

SPD-AI distingue conformité du produit, obligations de l'organisation et qualification de l'hébergement ; il présente le lien entre autorité d'acceptation et démonstration de conformité comme une hypothèse de mise en œuvre, non comme une prescription européenne nommant ce rôle ([SPD-AI, sections 7.3.2 et 7.3.5](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). Nos dossiers d'acceptation sont donc des pièces de preuve proposées, pas un certificat CRA ou NIS2.

| Niveau à instruire | Question préalable | Pièces recommandées |
|---|---|---|
| Produit | Le produit et son mode de fourniture entrent-ils dans le champ du CRA ou d'autres textes sectoriels ? | Analyse de champ, risques, composants, tests, vulnérabilités et support |
| Organisation | L'entité est-elle assujettie à NIS2, et selon quelle transposition ? | Gouvernance, risques, fournisseurs, continuité et notifications |
| Données | Quels traitements et transferts doivent être examinés au titre du RGPD ? | Inventaire des données, sous-traitants, destinations, conservation et accès |
| Hébergement | Quel service, quelle version et quel périmètre sont effectivement qualifiés ? | Certificat ou décision, périmètre, contrat et responsabilités |
| Usage de l'IA | Utilise-t-on seulement un outil de développement, ou fournit-on aussi un système ou modèle d'IA ? | Analyse des rôles, usages, intégrations et obligations applicables |

Recommandation : ne pas traiter tout SaaS comme automatiquement soumis à toutes les obligations produit du CRA, ni toute entreprise qui utilise un assistant comme fournisseur de modèle GPAI. Faire valider les champs, exemptions, rôles et calendriers avant de transformer cette grille en exigences contractuelles.

## 11. Ordres de grandeur économiques

Objectif de cette section : donner des ordres de grandeur, pas des devis. Les prix évoluent vite et les tarifs publics ne comprennent pas toujours la totalité des postes ; les enveloppes ci-dessous restent celles de la version précédente, sans actualisation tarifaire générale au 21 octobre.

SPD-AI signale explicitement le TCO H100 et plusieurs données commerciales comme non vérifiés à leur source primaire ; l'alignement présent ne transforme pas ces estimations en données établies ([SPD-AI, sections 7.2.7 et H.2-H.3](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). Les configurations ne doivent pas être achetées sur cette seule base : confirmer modèle exact, licence, quantification, contexte, concurrence, moteur et débit par essai ou devis.

### 11.1 Le point de départ : le coût mémoire d'un modèle

Ce qui dimensionne l'infrastructure, c'est la mémoire nécessaire aux poids et au contexte.

| Modèle | Poids en 4 bits (ordre de grandeur) | Matériel minimal | Ordre de grandeur du coût |
|---|---|---|---|
| Qwen3.8 27B | environ 14 Go | une carte 24 Go | entrée de gamme |
| Devstral 2 123B | environ 60 Go | 1 à 2 cartes 96 Go | palier intermédiaire |
| GLM-5.3 753B | environ 380 Go | 8 GPU de 80 Go | palier serveur complet |

Les chiffres de poids sont des calculs (paramètres divisés par deux en 4 bits), avant mémoire de contexte et cache KV, qui peuvent sensiblement augmenter le besoin.

### 11.2 Scénario A : API européennes uniquement

C'est le démarrage le plus simple, sans investissement.

Repère de prix : mistral-medium-3.5-128b chez Scaleway est affiché à 1,50 € par million de tokens en entrée et 7,50 € en sortie ([Scaleway](https://www.scaleway.com/en/generative-apis/)). OVHcloud facture aussi au million de tokens, sans frais fixes ([OVHcloud](https://www.ovhcloud.com/en/public-cloud/ai-endpoints/)).

Exemples de calcul, et non consommation mesurée par développeur : hypothèse de 20 jours d'utilisation par mois, avec les tarifs de référence hérités de 1,50 €/million en entrée et 7,50 €/million en sortie, sans remise ni cache.

| Hypothèse de charge | Entrée par jour | Sortie par jour | Calcul mensuel |
|---|---|---|---|
| Ponctuelle | 0,5 million | 0,05 million | 22,50 € |
| Régulière | 2 millions | 0,2 million | 90 € |
| Agentique soutenue | 5 millions | 0,5 million | 225 € |
| Très soutenue | 20 millions | 2 millions | 900 € |

Ces exemples donneraient 112,50 à 4 500 € par mois pour cinq utilisateurs identiques ; ils corrigent l'ancien tableau qui ne séparait pas entrées et sorties. Le budget pilote de 250 à 3 000 € reste une enveloppe choisie, pas une borne maximale : mesurer les nouvelles tentatives, lectures répétées, sorties longues et appels d'outils.

Ce scénario ne couvre pas le niveau N3 (sensible) tant que le contrat n'a pas été vérifié, mais il suffit pour N1 et N2.

### 11.3 Scénario B : location de GPU dans un cloud européen

Pour déployer vos propres modèles open weight (niveau N3) sans acheter de matériel.

Tarifs publics constatés en octobre 2026 :

| Fournisseur | Offre | Prix constaté | Coût mensuel à plein temps (730 h) |
|---|---|---|---|
| Scaleway | L4 24 Go | 0,79 €/h ([Scaleway](https://www.scaleway.com/en/pricing/gpu/)) | environ 575 € |
| Scaleway | 1x H100 80 Go | environ 2,7 à 3,3 €/h ([Qovery](https://www.qovery.com/blog/gpu-pricing-comparison-method-aws-gcp-azure-scaleway-2026), [GPU Finder](https://gpufinder.dev/providers/scaleway)) | environ 2 000 à 2 400 € |
| OVHcloud | 1x H100 80 Go | 2,80 à 2,99 €/h ([OVHcloud](https://corporate.ovhcloud.com/en/newsroom/news/ai-offer/)) | environ 2 000 à 2 200 € |

Interprétation pratique :
- un modèle compact type Qwen3.8 27B tient sur une L4 ou une carte 48 Go : quelques centaines d'euros par mois ;
- un modèle 123B ou plusieurs sessions d'agents exigent plutôt 1 à 2 H100 : 2 000 à 5 000 € par mois ;
- le GLM-5.3 complet (753B) exige un nœud 8 GPU : environ 28 $/h, soit 15 000 à 20 000 € par mois ([GPU Finder](https://gpufinder.dev/gpu/h100/8x)).

Hypothèse de calcul : 8 heures par jour pendant 20 jours correspondent à 160 heures, soit environ 22 % de 730 heures, et non un tiers du mois. L'économie n'est réalisable que si le fournisseur arrête effectivement la facturation du GPU entre les sessions ; stockage, réservations, redémarrages et minimums contractuels restent à ajouter.

### 11.4 Scénario C : hébergement dans un cloud qualifié SecNumCloud

C'est une option d'hébergement à examiner pour le niveau N3 lorsque la qualification est exigée. La location d'une infrastructure, la colocation d'un matériel acheté et un service d'inférence managé sont trois prestations différentes : demander un devis et un périmètre de responsabilité propres à chacune, sans supposer que le matériel ou l'application hérite d'une qualification.

Repère hérité, à confirmer : une source secondaire indique 6 141,60 €/mois pour un serveur 2x H100 80 Go avec engagement de 24 mois ; la disponibilité et le périmètre de qualification de cette offre précise n'ont pas été revérifiés ici ([Pipook](https://pipook.fr/outil/cloud-temple/)). Le montant OpenShift de 26 954,41 € repris auparavant est exclu du calcul, faute de clarification de l'unité de facturation, des services inclus et de l'engagement ; demander un devis détaillé au fournisseur ([Cloud Temple, tarifs publics](https://www.cloud-temple.com/nos-tarifs-publics/)).

La prime de 30 à 50 % évoquée dans la version précédente est retirée comme conclusion de marché : nous ne disposons pas ici de devis comparables à périmètre, engagement, disponibilité et exploitation identiques. Recommandation : comparer des services complets et leur qualification réelle, pas seulement le prix divisé par le nombre de GPU.

Autres options qualifiées à étudier : S3NS et Bleu, les offres « trusted cloud » avec les hyperscalers, avec la réserve citée plus haut sur les piles logicielles américaines ([Nexthop](https://www.nexthop.fr/secnumcloud/)). OVHcloud et Scaleway proposent aussi des offres avec des niveaux de garantie intermédiaires : à vérifier offre par offre, car la qualification SecNumCloud s'applique à des services précis, pas à tout le catalogue d'un fournisseur.

Ordre de grandeur pour une équipe de 5 à 10 développeurs avec du code sensible : 6 000 à 10 000 € par mois pour un serveur 2x H100 en SecNumCloud, plus les frais de mise en place et l'exploitation.

### 11.5 Scénario D : achat de matériel (on-premise)

Trois paliers d'achat, prix constatés en octobre 2026 :

| Palier | Configuration | Usage | Ordre de grandeur |
|---|---|---|---|
| Compact | 1 carte RTX PRO 6000 Blackwell 96 Go | Qwen3.8 27B en 4/8 bits, sessions courtes | 18 000 à 23 000 € la carte ([Idealo](https://www.idealo.fr/prix/207353877/nvidia-rtx-pro-6000-blackwell-server-edition.html), [Sabre PC](https://www.sabrepc.com/900-2G153-0000-000-NVIDIA-S8845543)) |
| Intermédiaire | Serveur 2 à 4 cartes 96 Go | Devstral 2 123B, plusieurs sessions | 50 000 à 120 000 € (serveur 8 cartes à partir de 165 000 $, [Blackwell Cloud](https://www.blackwellcloud.com/nvidia-rtx-pro-6000-gpu-servers)) |
| Complet | Serveur HGX 8x H100 | GLM-5.3 complet en 4 bits | 250 000 à 320 000 $, environ 285 000 $ en prix intégré ([Mercatus AI](https://www.mercatus-ai.com/blog/h100-server-price), [CloudZero](https://www.cloudzero.com/blog/h100-gpu-cost/)) |

Ne pas oublier le coût complet (TCO) :

| Poste | Ordre de grandeur annuel |
|---|---|
| Électricité, petite config (2 cartes, usage intermittent) | 400 à 1 000 € (30 à 80 € par mois selon usage, [LocalIA](https://getlocalia.com/blog/combien-coute-serveur-ia-pme-2026)) |
| Électricité, nœud 8x H100 (environ 10 kW) | 10 000 à 18 000 € selon le tarif ([AI Intel Report](https://aiintelreport.com/enterprise-ai/on-premise-ai-cost-tco)) |
| Refroidissement | 25 à 40 % de l'électricité en plus selon le PUE ([AI Intel Report](https://aiintelreport.com/enterprise-ai/on-premise-ai-cost-tco)) |
| Colocation si vous n'avez pas de local technique | 12 000 à 24 000 $ ([AI Intel Report](https://aiintelreport.com/enterprise-ai/on-premise-ai-cost-tco)) |
| Exploitation | au moins 0,5 ETP qualifié ([AI Intel Report](https://aiintelreport.com/enterprise-ai/on-premise-ai-cost-tco)) |

Une estimation de praticiens citée dans la version précédente situe le TCO sur trois ans d'un nœud 8x H100 entre 712 000 et 948 000 dollars, mais sa méthode et ses hypothèses n'ont pas été confirmées ; elle ne doit pas être qualifiée de modélisation indépendante validée ([AI Intel Report](https://aiintelreport.com/enterprise-ai/on-premise-ai-cost-tco), [réserve explicite dans SPD-AI, annexe H](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). Ne pas la comparer directement à une location en euros sans harmoniser change, durée, service, disponibilité et coûts humains.

### 11.6 Seuil de rentabilité achat contre location

Un seuil de 12 à 18 mois ne peut pas être retenu sans le coût complet et un service comparable. Le calcul recommandé est :

\[
\text{Délai de retour en mois} =
\frac{\text{investissement initial net}}
{\text{location mensuelle évitée} - \text{coûts mensuels internes supplémentaires}}
\]

Si le dénominateur est nul ou négatif, il n'y a pas de retour financier dans ce modèle. Le calcul doit aussi intégrer le risque d'obsolescence, la disponibilité, le support et la valeur de la flexibilité, même si ces éléments ne tiennent pas tous dans cette formule simplifiée.

Exemple purement illustratif : un investissement complet de 50 000 €, une location comparable évitée de 2 300 €/mois et 800 €/mois de coûts internes supplémentaires donnent environ 33 mois, pas 12 à 18. Si la location peut être limitée à 160 heures par mois, l'équivalent proportionnel de 2 300 € pour 730 heures est environ 504 €/mois ; il devient alors inférieur aux 800 € de charges internes de cet exemple.

Recommandation : mesurer les heures facturées et l'utilisation effective du GPU, mais aussi les files d'attente, le contexte et les pointes. Une machine allumée toute la journée n'est pas nécessairement utilisée efficacement, et la présence de développeurs ne mesure pas la durée de travail des agents.

### 11.7 Récapitulatif des quatre scénarios

Pour une équipe de 5 développeurs, ordres de grandeur par mois :

| Scénario | Investissement initial | Coût mensuel | Couverture N3 | Quand le choisir |
|---|---|---|---|---|
| A. API européennes | quasi nul | 250 à 3 000 € | non (sauf contrat vérifié) | démarrage, mesure, N1/N2 |
| B. GPU loué européen | quasi nul | 500 à 5 000 € | possible après analyse de risque et contrat ; pas de qualification présumée | charge variable, périmètre autorisé |
| C. SecNumCloud | frais de mise en place | 6 000 à 10 000 € | sous réserve du périmètre qualifié et des autres exigences applicables | exigence de qualification justifiée |
| D. Achat on-prem | 25 000 à 300 000 € + TCO | électricité et exploitation | sous réserve des contrôles et de la capacité d'exploitation | charge stable et forte, mesurée |

Lecture : commencer par le scénario autorisé pour les artefacts réellement traités, pas systématiquement par une API. Le scénario B n'est pas autorisé par défaut pour N3 ; C doit correspondre à une exigence justifiée et à un périmètre vérifié ; D exige des mesures et une capacité d'exploitation.

### Financer la preuve, la transmission et la maintenance

SPD-AI recommande de planifier ensemble les capacités humaines et IA, y compris le renforcement des tests, la refactorisation et les compétences ; il distingue le financement d'un produit industrialisé du coût souvent invisible des outils métier ([SPD-AI, sections 7.2.5 et 7.2.6](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). Recommandation : prévoir des lignes budgétaires distinctes pour ces activités et une règle de reprise quand un prototype devient partagé ou critique.

Exemple de sensibilité, sans tarif de marché revendiqué : pour cinq personnes, consacrer deux heures par semaine et par personne à la preuve et à la transmission représente environ 40 heures par mois sur une base de quatre semaines. À un coût interne complet hypothétique de 80 €/h, cela représente 3 200 €/mois, à rendre visible même si les salaires sont déjà budgétés ; ne pas l'ajouter une seconde fois au budget global de l'équipe.

## 12. Deux scénarios dans un cadre souverain

### État de l'art et niveau de preuve

Les essais sur l'assistance au code ne mesurent pas tous les mêmes activités : l'étude sur 4 867 développeurs rapporte environ 26 % de tâches terminées en plus dans ses contextes, tandis que l'essai METR de début 2025 avait mesuré un ralentissement de 19 % chez des développeurs expérimentés ; la mise à jour de février 2026 ne permet pas d'estimer solidement l'effet des outils les plus récents ([SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4945566), [METR](https://metr.org/blog/2026-02-24-uplift-update/)). Ces résultats ne justifient donc ni un multiplicateur global de productivité ni une réduction automatique des effectifs d'un programme de migration.

SPD-AI distingue la spécification pour guider, vérifier et transmettre une solution de la découverte qui sert à choisir quoi construire ; il présente le spec-driven development comme une approche à évaluer, non comme une méthode universelle démontrée supérieure ([SPD-AI, sections 3.2 et 4.2](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). Nous retirons par conséquent l'affirmation d'une convergence générale du secteur et le nombre d'étoiles GitHub utilisé auparavant comme indice de maturité : l'adoption d'un outil ne prouve pas la qualité des produits livrés.

Les fournisseurs décrivent des outils d'analyse, d'extraction de règles, de transformation et de comparaison : AWS pour Transform et Google pour la modernisation mainframe et Dual Run ; ces capacités annoncées ne constituent pas une mesure indépendante de leurs gains sur tout patrimoine ([AWS](https://aws.amazon.com/blogs/migration-and-modernization/tackling-large-mainframe-portfolio-with-agentic-ai-and-aws-transform/), [Google Cloud](https://cloud.google.com/blog/products/infrastructure-modernization/mainframe-migration-and-modernization-with-ai)). Recommandation : les utiliser comme repères fonctionnels pour un banc d'essai, pas comme preuve qu'une chaîne souveraine reproduira leurs performances.

Le cas historique Amadeus fournit un ordre de grandeur de transformation : environ 2 000 personnes-années, plus de 400 ingénieurs au pic et l'arrêt du dernier mainframe fin 2018 selon sa rétrospective ([Amadeus](https://amadeus.com/en/blog/articles/celebrating-one-year-fully-open-systems)). La fourchette de 20 à 40 % d'effort évité avec l'IA est, dans ce guide, une hypothèse de sensibilité issue de notre travail précédent, sans validation empirique pour Amadeus ; SPD-AI la signale également comme non établie dans son annexe H ([SPD-AI, sections 6.1.3 et H.2](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)).

### Créer un logiciel souverain from scratch

Hypothèse de travail : un nouveau produit logiciel (par exemple une plateforme de gestion énergétique), une équipe de 5 développeurs, un horizon de 18 à 24 mois.

Créer sans existant évite certaines contraintes d'héritage, mais n'exclut ni des règles propriétaires, ni des données personnelles, ni des exigences industrielles sensibles ; SPD-AI demande une classification dès le premier jour ([SPD-AI, section 6.1.1](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). Recommandation : commencer par la finalité, les droits sur les données et les critères d'acceptation, pas par l'achat d'un modèle.

| Étape | Pratique recommandée | Lien souveraineté et conformité |
|---|---|---|
| Découverte | Vérifier besoin, usages et solutions alternatives ; un prototype sert à apprendre | Classifier les entretiens et données ; ne pas confondre prototype et produit |
| Spécification | Règles approuvées, décisions versionnées et critères d'acceptation | Contribution au dossier de conformité, pas preuve suffisante à elle seule |
| Génération | Agents configurables, modèles et outils explicitement autorisés | Vérifier tous les flux, la licence et les versions |
| Revue | Acceptations technique, métier, puis produit et exploitation | Scanners, preuves indépendantes et décideurs identifiés |
| Exécution des agents | Sandbox, secrets hors contexte et sorties réseau filtrées | Réduire les risques, sans prétendre les supprimer |
| Exploitation | Support, surveillance, restauration et transfert à un autre mainteneur | Vérifier la continuité, pas seulement la première livraison |

La génération peut accélérer certains lots, mais nous ne retenons plus l'hypothèse d'une part de travail « maximale » automatiquement accélérable : elle dépend du domaine, de la nouveauté et de la vérifiabilité, comme le distingue [SPD-AI, sections 2.2 et 5.2](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md). Recommandation : traiter séparément conformité aux critères, justesse des règles, utilité pour les utilisateurs et capacité de maintenance.

Hypothèse budgétaire : reprendre l'enveloppe API de 250 à 3 000 € par mois pour le pilote, soit 4 500 à 54 000 € sur 18 mois ou 6 000 à 72 000 € sur 24 mois, sans la présenter comme un devis ni comme le budget du produit. Ajouter équipe, contexte, évaluations, plateforme, sécurité et exploitation ; la revue ne doit pas être supposée dominante sans mesure.

Si un artefact est N3 dès le départ, prévoir immédiatement une exécution interne ou une offre autorisée pour ce niveau. La location peut aussi se justifier par le débit, la latence, la disponibilité ou le coût mesuré, pas uniquement par la confidentialité.

Risques à traiter dans le pilote :
- dépendance à un agent ou à un format de spec propriétaire : garder les specs en Markdown simple et portable ;
- surestimation des gains : appliquer le banc d'essai de la section 7 avant de dimensionner l'équipe ;
- compréhension : vérifier qu'une autre personne peut expliquer une règle et faire évoluer le produit ;
- sécurité et conformité : définir les obligations selon le produit, le rôle de l'entreprise et les dates applicables, sans considérer la présence ou l'absence de SDD comme un verdict juridique.

### Migrer un gros logiciel

Hypothèse de travail : un système critique de plusieurs millions de lignes (architecture de type Amadeus), en exploitation continue, avec exigences transactionnelles fortes.

Le patrimoine peut contenir des règles métier sensibles, mais l'ancienneté ne suffit pas à classer tous ses artefacts en N3 ; une spécification cible peut, inversement, révéler autant que le code source, selon [SPD-AI, sections 5.1.5 et 6.1.2](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md). Recommandation : classifier avant analyse le code, les binaires, captures, journaux, extractions et données de comparaison, puis conserver la classification dans les livrables dérivés.

Le cycle recommandé reprend les huit phases de SPD-AI et ajoute, pour chacune, une décision et une preuve attendue ; aucun niveau N1/N2/N3 n'est attribué automatiquement à une phase ([SPD-AI, section 6.1.4](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). Le tableau est une grille de travail à adapter au domaine et aux risques.

| Phase | Contribution de l'IA | Décision humaine | Preuve attendue |
|---|---|---|---|
| Découverte | Cartographie, dépendances et lignée des données | Confirmer le périmètre, les droits et les inconnues | Carte de l'existant et sources inspectées |
| Extraction des règles | Description des comportements implémentés | Distinguer règle voulue, contournement, exception et défaut | Catalogue relié au code et aux observations |
| Comportement cible | Propositions et questions de clarification | Approuver ce qui doit rester ou changer | Spécification cible distincte de l'existant |
| Architecture cible | Options de découpage et d'intégration | Arbitrer transactions, performance et maintenance | Décisions d'architecture motivées |
| Génération | Code, interfaces, adaptateurs et configuration | Accepter des lots limités et traçables | Modifications reliées aux exigences et tests |
| Équivalence | Comparaison et aide à l'analyse des écarts | Fixer les écarts autorisés | Rapport d'écarts classés et risques résiduels |
| Bascule | Scripts et contrôles préparatoires | Décision de bascule ou d'arrêt | Restauration, réconciliation et repli testés |
| Exploitation | Surveillance et propositions de correction | Décider des évolutions et du retrait de l'ancien | Historique d'incidents, support et transfert |

Recommandation : vérifier le support exact des langages, ordonnanceurs, transactions, bases et formats du patrimoine ; ne pas transposer une démonstration COBOL/z/OS à TPF, à des automates ou à un système distribué sans essai représentatif. Les outils américains de modernisation restent des points de comparaison fonctionnels, et non des choix autorisés par défaut dans le cadre souverain.

### Décrire l'existant sans l'ériger en vérité

SPD-AI appelle « boucle inverse du SDD » la démarche qui part d'un logiciel autorisé à l'analyse, reconstruit son comportement et ses inconnues, puis fait valider la cible avant reconstruction ; il s'agit d'une proposition méthodologique, pas d'un standard ([SPD-AI, section 4.2.5](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). Recommandation : conserver deux livrables distincts, la description de l'existant et la spécification cible, reliés à des sources, versions, niveaux de confiance et personnes ayant validé.

L'analyse de binaires, de l'exécution ou d'une interface peut compléter un code incomplet, mais une reconstruction probable ne prouve ni l'intention ni l'équivalence ; SPD-AI insiste sur les limites des démonstrations de rétro-ingénierie agentique et sur les droits d'analyse ([SPD-AI, sections 2.3, 6.1.5 et 7.3.6](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). Recommandation : examiner séparément les droits d'accéder, d'analyser, de réutiliser et de distribuer avant tout essai.

### Trois preuves distinctes avant la bascule

SPD-AI sépare équivalence avec l'ancien, correction métier et aptitude à l'exploitation ; reproduire un défaut ancien peut satisfaire la première et contredire la deuxième ([SPD-AI, section 5.2.3](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). Recommandation : classer chaque différence en changement approuvé, défaut du nouveau, défaut découvert dans l'ancien ou différence inexpliquée ; l'autorité d'acceptation décide sur ces écarts et leur risque, pas seulement sur un pourcentage de tests réussis.

Recommandation : inclure les arrondis, dates de valeur, ordres de tri, formats, délais, erreurs, reprises et garanties transactionnelles dans les scénarios représentatifs. Pour le parallèle ancien/nouveau, utiliser le rejeu ou un mode sans effets réels : une seule chaîne doit pouvoir déclencher un paiement, une écriture comptable ou une commande industrielle.

La coexistence progressive de type strangler fig évite une réécriture en bascule unique, mais crée des coûts supplémentaires de double exploitation et de comparaison ; SPD-AI ne les assimile pas à un doublement automatique du coût total ([SPD-AI, section 6.1.5](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md)). Recommandation : budgéter explicitement les adaptateurs, synchronisations, réconciliations et fenêtres de coexistence.

### Effort, coûts et trajectoire de décision

Le calcul illustratif sur une base de 2 000 personnes-années donne 1 600 après une réduction hypothétique de 20 %, 1 400 après 30 % et 1 200 après 40 %. Ajouter un scénario sans gain net et un scénario de surcoût de 10 %, soit 2 200 personnes-années ; aucun de ces résultats n'est une estimation actuelle d'Amadeus, et aucun ne fournit la durée du programme.

Recommandation : financer d'abord un lot représentatif, avec comportement de référence, exceptions et tests indépendants, puis mesurer le coût par comportement validé, la couverture et les écarts inexpliqués. Estimer séparément le gain lié à l'IA, celui des outils de migration classiques et celui du changement de plateforme.

Hypothèse budgétaire pour une cellule pilote, et non pour un programme de plusieurs millions de lignes : 500 à 5 000 € par mois d'infrastructure GPU européenne ou 6 000 à 10 000 € par mois pour l'enveloppe SecNumCloud retenue dans ce guide. Sur six mois, cela représente respectivement 3 000 à 30 000 € et 36 000 à 60 000 €, avant équipe, analyse, licences, tests, exploitation parallèle et sécurité ; ces montants restent à revalider par devis et ne dimensionnent pas le débit nécessaire.

La phase initiale doit donc décider de la classification réelle, du périmètre qualifié exigé, de la compatibilité technique et de la capacité de vérification. Un gros volume n'impose pas en soi SecNumCloud, et produire un code cible ne justifie aucun déclassement automatique.

### Synthèse comparative des deux scénarios

| Dimension | From scratch | Migration d'un gros logiciel |
|---|---|---|
| Confidentialité | Classification avant le premier prompt, même sans code ancien | Classification de l'existant et de tous ses dérivés |
| Décision initiale | Quel problème mérite un produit, plutôt qu'un prototype ? | Que préserver, corriger, retirer ou remplacer ? |
| Goulot à mesurer | Découverte, spécification, revue et apprentissage d'usage | Compréhension, architecture, preuves et bascule |
| Gain lié à l'IA | À mesurer, sans coefficient global présumé | À mesurer par lot et type d'activité |
| Investissement initial | Pilote API si autorisé ; infrastructure dédiée si nécessaire | Pilote représentatif et outillage de comparaison |
| Risque principal | Produit conforme à une demande mal choisie ; dette de compréhension | Défauts hérités pris pour des règles ; écarts inexpliqués |
| Mesure pilote clé | Coût accepté, défauts et utilité observée | Coût par comportement validé, écarts et aptitude à l'exploitation |

Dans les deux scénarios, la recommandation est de financer conjointement réalisation, preuve, transmission et exploitation. Le résultat recherché n'est pas simplement un logiciel généré en Europe, mais un produit utile que l'organisation peut comprendre, accepter, maintenir et reprendre sans dépendre d'un fournisseur unique.

## 13. Synthèse des recommandations

1. Traiter la souveraineté comme une propriété de toute la chaîne (modèle, inférence, agent, IDE, forge, CI), pas seulement du modèle.
2. Distinguer open weight (contrôle des poids) et souverain (contrôle de l'opérateur) : un modèle chinois ou américain auto-hébergé en Europe peut être plus souverain qu'une API européenne mal contractualisée.
3. Lire chaque licence : les seuils de chiffre d'affaires et les droits liés à un hébergeur changent la donne.
4. Commencer par un pilote dans un environnement autorisé pour les artefacts traités ; utiliser des API européennes si leur périmètre le permet.
5. Investir d'abord dans la passerelle et le banc d'essai : ce sont eux qui permettent de changer de modèle quand la génération suivante arrive.
6. Accepter une phase mixte : garder l'accès aux meilleurs outils pour le code public tant que l'écart de qualité est réel, et le mesurer régulièrement.
7. Instruire séparément les champs de NIS2, du CRA, du RGPD et de l'AI Act ; documenter les fournisseurs, les vulnérabilités et les notifications applicables.
8. Constituer un patrimoine transmissible : règles, décisions, spécifications, preuves et exploitation, avec provenance et responsables.
9. Séparer confidentialité des artefacts, permissions des agents et acceptation des changements ; aucun de ces axes ne remplace les autres.
10. En migration, distinguer comportement existant et cible, puis prouver équivalence, correction métier et aptitude à l'exploitation.
11. Financer la preuve et la maintenance dans la durée ; présenter les gains et retours sur investissement comme des hypothèses tant que le pilote ne les a pas mesurés.

Ce qui changerait cette conclusion : un écart de qualité très important sur vos tâches réelles en faveur d'outils US (le coût de la souveraineté devient alors élevé), ou au contraire un modèle compact suffisant, qui rendrait l'auto-hébergement complet simple et peu coûteux.

## Annexe : concordance avec SPD-AI

La comparaison porte sur la version 1.0 du document principal, consultée le 21 octobre 2026 ; le dépôt affiche alors a261f2e comme dernière révision visible ([SPD-AI, dépôt et README](https://github.com/fdepierre/SPD-AI)). Les correspondances suivantes décrivent les modifications de ce guide, sans prétendre valider à nouveau toutes les références du document principal.

| Référence SPD-AI | Apport repris | Modification dans ce guide |
|---|---|---|
| Sections 1.2-1.3 et annexe H | Statut explicite des affirmations et inconnues | Convention de lecture et registre de réserves |
| Sections 3.2 et 4.1 | Choix du problème et patrimoine transmissible | Ajout de la découverte, des fichiers de connaissance et de la transmission |
| Section 4.2 | Spécification évolutive ; existant distinct de la cible | Révision des deux scénarios et boucle inverse proposée |
| Section 5.1 | Permissions distinctes de la confidentialité | Accès, modification, validation, escalade et réversibilité |
| Section 5.2 | Trois acceptations et limites de la supervision | Preuves indépendantes, autorité compétente et pouvoir de refus |
| Section 5.3 | Architecture vérifiable, composable et reprenable | Contrats, séparation des composants et substitution testée |
| Section 6.1 | Huit phases de modernisation | Ajout du comportement cible et de l'exploitation |
| Section 7.2 | Coût complet et capacité humaine/IA | Correction du calcul API, du taux d'usage et du retour sur investissement |
| Section 7.3 | Produit, organisation, données et hébergement | Grille de champ et retrait des garanties automatiques |
| Section 8.1 | Futurs conditionnels, sans scénario imposé | Prospective en trois trajectoires |

Les références de cette table renvoient au [document principal de SPD-AI](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md). Ce guide reste autonome et complémentaire : il ne copie pas l'ensemble de ses annexes et ne reprend pas comme établis ses éléments signalés « à vérifier ».

## Annexe : réserves et vérifications avant publication

Cette révision corrige les conclusions excessives repérées par comparaison, sans constituer une revue juridique complète ni une actualisation de tous les prix et modèles. Comme dans l'annexe H de [SPD-AI](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md), les réserves restent visibles pour éviter qu'une répétition transforme une hypothèse en fait.

| Élément | Statut dans cette version | Vérification nécessaire avant décision |
|---|---|---|
| Gain de 20 à 40 % sur une migration de type Amadeus | Sensibilité, sans validation empirique ; pas un résultat publié par Amadeus | Pilote représentatif incluant revue, reprises et preuves |
| Modèles et paramètres exacts cités | Repères hérités, pas un catalogue certifié au 21 octobre | Fiche officielle, licence de la version exacte, disponibilité |
| Seuils des licences Mistral et droits via hébergeur | Information héritée de références à revalider | Texte contractuel primaire et compatibilité avec l'entité utilisatrice |
| Tarifs API, GPU, matériel et TCO H100 | Repères budgétaires, certains issus de sources secondaires | Devis, devise, taxes, région, durée, support et méthode TCO |
| Offre GPU présentée comme SecNumCloud | Qualification exacte du service non établie ici | Décision de qualification et périmètre du service GPU/inférence |
| Formules « immunité », « seul dispositif » et seuils capitalistiques | Analyses héritées, pas une garantie juridique générale | Référentiel officiel, structure de contrôle, contrats et conseil juridique |
| EUCS, CADA, C5, ENS, ACN, HDS et comparaisons ISO 27001 | Tableau conservé comme cartographie de travail | Statut officiel, version applicable et exigences du marché visé ; pas d'équivalence automatique |
| Transposition NIS2 en France | État exact non conclu dans cette révision | Textes publiés et dispositions d'entrée en vigueur |
| Calendrier AI Act, CRA et signalements | Repères cités, à contrôler selon le rôle et le produit | Texte consolidé, modifications, conditions déclenchantes et délais finaux |
| « Politique IA » et « autorité d'acceptation » | Recommandations d'organisation | Démontrer leur contribution aux obligations, sans les présenter comme rôles légaux imposés |
| Absence d'exfiltration, déclassement N3 vers N2 | Garanties automatiques retirées | Contrôle des flux réels et déclassement explicite |
| Droits sur les codes, binaires et sorties reconstruits | Question à instruire avant analyse et réutilisation | Contrats, licences, propriété intellectuelle et autorisations |

Recommandation avant engagement : traiter d'abord les points qui peuvent inverser une décision d'achat, de fournisseur ou de mise sur le marché. Les autres réserves peuvent rester dans un document de travail, à condition de ne pas être présentées dans le corps ou un résumé comme des faits définitivement acquis.

## Annexe : sources et références

Les liens ci-dessous regroupent les références utilisées ou conservées des versions successives, par thème ; leur présence ne signifie pas qu'elles ont toutes été relues et validées lors de la révision du 21 octobre 2026. Les réserves de l'annexe précédente s'appliquent aux montants, licences, calendriers et qualifications.

### Document de référence pour cette révision

- Franck Depierre, « Le futur du Product Management à l'ère des agents IA », version 1.0, octobre 2026 : [document dans SPD-AI](https://github.com/fdepierre/SPD-AI/blob/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md).
- Texte intégral lu pour la comparaison : [version brute du document principal](https://raw.githubusercontent.com/fdepierre/SPD-AI/main/Le%20futur%20du%20Product%20Management%20%C3%A0%20l%27%C3%A8re%20des%20agents%20IA.md).
- Objet, méthode, statut et licence du dépôt : [SPD-AI, README et navigation](https://github.com/fdepierre/SPD-AI).

### Cadre juridique et souveraineté

- CLOUD Act et niveaux de cloud souverain : [donneespersonnelles.fr – Cloud souverain](https://www.donneespersonnelles.fr/cloud-souverain)
- SecNumCloud 3.2, critères d'actionnariat : [Oodrive – 5 raisons de choisir SecNumCloud](https://www.oodrive.com/fr/blog/secnumcloud/infrastructure/5-raisons-choisir-environnement-qualifie-secnumcloud/)
- Immunité extraterritoriale, limites : [Cyber Networks – Guide SecNumCloud](https://cyber-networks.fr/cybersecurite/secnumcloud-qualification-anssi-guide/)
- Piles logicielles américaines, Bleu et S3NS : [Nexthop – SecNumCloud](https://www.nexthop.fr/secnumcloud/)
- Chapitre 19.x du référentiel : [Insurio – Immunité extraterritoriale SecNumCloud](https://www.insurio.fr/blog/immunite-extraterritoriale-secnumcloud-responsabilite-consultant)
- Critères capitalistiques détaillés : [dpliance – SecNumCloud](https://dpliance.com/blog/secnumcloud-entreprise/)

### Offres européennes d'inférence et modèles

- Catalogue Scaleway Generative APIs : [Scaleway – Supported models](https://www.scaleway.com/en/docs/generative-apis/reference-content/supported-models/)
- Documentation Generative APIs et hébergement à Paris : [Scaleway – Docs](https://www.scaleway.com/en/docs/generative-apis/) et [DeepWiki – Scaleway docs](https://deepwiki.com/scaleway/docs-content/5.1-generative-apis)
- Tarifs API Scaleway : [Scaleway – Generative APIs](https://www.scaleway.com/en/generative-apis/)
- Déploiements dédiés et cycle de vie : [Scaleway – FAQ](https://www.scaleway.com/en/docs/generative-apis/faq/) et [Scaleway – Model lifecycle](https://www.scaleway.com/en/docs/generative-apis/reference-content/model-lifecycle/)
- Qwen3.8 27B et DeepSeek-V4-Flash sur Scaleway : [Scaleway – Docs](https://www.scaleway.com/en/docs/generative-apis/)
- OVHcloud AI Endpoints, hébergement UE et modèles open weight : [OVHcloud – AI Endpoints](https://www.ovhcloud.com/en/public-cloud/ai-endpoints/)
- Capacités et limites OVHcloud : [OVHcloud docs – Capabilities](https://docs.ovhcloud.com/en/guides/public-cloud/ai-machine-learning/ai-endpoints-capabilities.md)
- Cycle de vie OVHcloud : [OVHcloud docs – Billing and lifecycle](https://docs.ovhcloud.com/en/guides/public-cloud/ai-machine-learning/ai-endpoints-billing)
- Licences des modèles open weight, seuil Mistral : [Developers Digest – Open-weight model licenses](https://www.developersdigest.tech/local-models/licenses)

### AI Act
- Calendrier et application : [AI Act Service Desk – FAQ](https://ai-act-service-desk.ec.europa.eu/fr/faq?combine=) et [Commission européenne – AI Act](https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai)
- Résumé des obligations GPAI : [artificialintelligenceact.eu – Résumé de haut niveau](https://artificialintelligenceact.eu/fr/high-level-summary/)
- Application du chapitre V : [artificialintelligenceact.eu – Enforcement of Chapter V](https://artificialintelligenceact.eu/fr/enforcement-of-chapter-v-under-the-eu-ai-act/)
- Report des systèmes à haut risque : [Cabinet Persée – AI Act 2026](https://cabinetpersee.com/blog/posts/ai-act-ce-qui-change-2026/)
- Obligations GPAI en France : [vie-publique.fr – AI Act](https://www.vie-publique.fr/questions-reponses/292157-ai-act-le-reglement-europeen-sur-lintelligence-artificielle-ia)

### NIS2
- Cadre européen : [Commission européenne – NIS2 Directive](https://digital-strategy.ec.europa.eu/en/policies/nis2-directive) et [EUR-Lex – Directive (UE) 2022/2555](https://eur-lex.europa.eu/legal-content/FR/LSU/?uri=oj:JOL_2022_333_R_0002)
- Transposition française en cours, ReCyF : [ANSSI – Directive NIS 2](https://cyber.gouv.fr/reglementation/cybersecurite-systemes-dinformation/directives-nis-nis2-et-dispositif-saiv/directive-nis-2/)
- État de la transposition : [TS Monde – NIS2 France](https://tsmondo.eu/fr/nis2-france) et [NIS2 Directive – Transposition France](https://www.nis-2-directive.com/Transposition/France.html)
- Mesures des articles 20 et 21 : [ANSSI – FAQ NIS2](https://aide.monespacenis2.cyber.gouv.fr/fr/article/quelles-sont-les-exigences-en-matiere-de-cybersecurite-auxquelles-les-entites-regulees-a-la-directive-nis-2-devront-se-soumettre-193huwi/) et [NIS2 Directive – Article 21](https://www.nis-2-directive.com/NIS_2_Directive_Article_21.html)
- Enregistrement MonEspaceNIS2 : [FAQ MonEspaceNIS2 – Obligations](https://aide.monespacenis2.cyber.gouv.fr/fr/category/obligations-9vpf70/)
- Texte intégral : [nis2-info.eu – Full text](https://www.nis2-info.eu/regulation/nis2/fulltext-and-download-pdf/)

### Cyber Resilience Act
- Cadre et calendrier : [Commission européenne – Cyber Resilience Act](https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act) et [entreprises.gouv.fr – CRA](https://www.entreprises.gouv.fr/decryptages-de-nos-experts/cyber-resilience-act-cra-ce-qui-change-pour-les-entreprises-et-comment)
- Obligations de signalement : [Commission européenne – CRA Reporting](https://digital-strategy.ec.europa.eu/en/policies/cra-reporting)
- Plateforme unique CRA-SRP : [ENISA – The CRA Single Reporting Platform is launched](https://www.enisa.europa.eu/news/the-cra-single-reporting-platform-is-launched) et [BSI – Single Reporting Platform](https://www.bsi.bund.de/EN/Themen/Unternehmen-und-Organisationen/Informationen-und-Empfehlungen/Cyber_Resilience_Act/Single_Reporting_Platform-CRA/single_reporting_platform-cra.html)
- Analyse du régime de signalement : [CMS – Ready, respond, report](https://cms.law/en/int/legal-updates/ready-respond-report-the-cyber-resilience-act-s-reporting-regime-is-here)
- Période transitoire et FAQ officielle : [CRA ORCWG – Transition period](https://cra.orcwg.org/faq/official/transition/)
- Annexe I, exigences essentielles : [Cyber Resilience Act – Annex I](https://cyber-resilience-act.com/annexes/annex-i/) et [VamiSec – EU Cyber Resilience Act](https://vamisec.com/fr/wissen/grc/eu-cyber-resilience-act)
- Mise en œuvre et normes : [Commission européenne – CRA Implementation](https://digital-strategy.ec.europa.eu/en/factpages/cyber-resilience-act-implementation)

### Autres référentiels et certifications européennes

- EUCS, statut et blocage : [Wikipédia – EUCS](https://en.wikipedia.org/wiki/EUCS_(cloud_computing)), [Nexthop – EUCS](https://www.nexthop.fr/en/understand/eucs) et [Nexthop – EUCS, chronique d'une capitulation](https://www.nexthop.fr/blog/eucs-chronique-d-une-capitulation-europeenne-sur-la-souverainete-numerique/)
- Cadre européen de certification, EUCC et schémas en cours : [Commission européenne – European cybersecurity certification framework](https://digital-strategy.ec.europa.eu/en/factpages/european-cybersecurity-certification-framework)
- EUCC en fonctionnement : [ENISA – EUCC](https://certification.enisa.europa.eu/browse-topic/eucc_en?prefLang=ro)
- Souveraineté dans la commande publique, Cloud and AI Development Act : [IT SOCIAL – EUCS et CADA](https://itsocial.fr/cybersecurite/cybersecurite-articles/eucs-et-cada-leurope-abandonne-la-souverainete-dans-son-label-cloud-et-la-reintroduit-dans-la-commande-publique/)
- Comparaison des schémas nationaux (C5, SecNumCloud, ENS, ACN) : [CloudPick – EU Member-State Cloud Security Schemes](https://docs.cloudpick.kr/en/eu/national-schemes/)
- C5:2026 : [BSI – Sicheres Cloud-Computing](https://www.bsi.bund.de/DE/Service-Navi/Presse/Pressemitteilungen/Presse2026/260407_C5_Cloud_Computing.html) et [BSI – FAQ C5](https://www.bsi.bund.de/EN/Themen/Unternehmen-und-Organisationen/Informationen-und-Empfehlungen/Empfehlungen-nach-Angriffszielen/Cloud-Computing/Kriterienkatalog-C5/C5-FAQ/kriterienkatalog-c5-faq.html)
- ENS Espagne : [Ministère de l'Économie – Esquema Nacional de Seguridad](https://portal.mineco.gob.es/es-es/ministerio/estrategias/Paginas/Esquema_Nacional_de_Seguridad.aspx)
- HDS, exigences et EEE : [Agence du Numérique en Santé – Hébergement des données de santé](https://esante.gouv.fr/labels-certifications/hebergement-des-donnees-de-sante) et [sante.gouv.fr – Référentiel HDS](https://sante.gouv.fr/actualites-presse/presse/communiques-de-presse/article/publication-au-journal-officiel-du-referentiel-de-certification-hds)
- Référentiel HDS V2.1, chapitre 7 souveraineté : [ANS – Référentiel de certification](https://esante.gouv.fr/sites/default/files/media/document/R%C3%A9f%C3%A9rentiel_certification_HDS%20-%20FR%20-%20V2.1%20-%20post%20concertation.pdf)
- EUCS vu par l'ANSSI, SecNumCloud comme base du niveau élevé : [ANSSI – Cadre de certification européen](https://cyber.gouv.fr/reglementation/reglementation-identite-confiance-numerique/cadre-de-certification-de-cybersecurite-europeen/)

### Scénarios from scratch et migration

- Cas Amadeus, effort et calendrier : [Amadeus – One year fully open systems](https://amadeus.com/en/blog/articles/celebrating-one-year-fully-open-systems) et [Amadeus – Rapport global 2017](https://amadeus.com/content/dam/amadeus/corporate/documents/en/resources/corporate-information/corporate-documents/global-reports/2017/9-technology-and-innovation.pdf)
- Expérimentation randomisée 4 867 développeurs : [SSRN – paper 4945566](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4945566)
- Essais METR : [METR – Uplift update, février 2026](https://metr.org/blog/2026-02-24-uplift-update/) et [METR – Early 2025 study](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/)
- Spec-driven development, état du mouvement : [sdd.sh – SDD Is Eating Software Engineering](https://sdd.sh/2026/04/sdd-is-eating-software-engineering-the-methodology-that-went-from-blog-post-to-industry-movement/), [étude de terrain sur les frameworks SDD](https://github.com/ianhxu/agentic-engineering-field-study/blob/main/04-spec-driven-development.md) et [Itential – From Vibes to Specs](https://www.itential.com/resource/blog/vibes-to-specs-development/)
- Chaînes agentiques de migration : [AWS – Tackling large mainframe portfolios](https://aws.amazon.com/blogs/migration-and-modernization/tackling-large-mainframe-portfolio-with-agentic-ai-and-aws-transform/), [Google Cloud – Mainframe migration and modernization with AI](https://cloud.google.com/blog/products/infrastructure-modernization/mainframe-migration-and-modernization-with-ai) et [AWS – Reimagining mainframe applications](https://aws.amazon.com/blogs/migration-and-modernization/reimagining-mainframe-applications-with-aws-transform-and-claude-code/)
- Panorama des outils de modernisation : [Pixelmatters – Best application modernization software 2026](https://www.pixelmatters.com/insights/application-modernization-software)
- Pattern strangler fig : [Moweb – Legacy System Modernisation with AI](https://www.moweb.com/blog/legacy-system-modernisation-ai-enterprise-upgrade) et [SnowmanLabs – AI-Powered Legacy Modernization](https://snowmanlabs.com/insights/ai-powered-legacy-modernization)

### Prix GPU et matériel
- Tarifs Scaleway GPU : [Scaleway – GPU pricing](https://www.scaleway.com/en/pricing/gpu/)
- H100 chez Scaleway et OVHcloud : [Qovery – GPU pricing comparison](https://www.qovery.com/blog/gpu-pricing-comparison-method-aws-gcp-azure-scaleway-2026), [GPU Finder – Scaleway](https://gpufinder.dev/providers/scaleway) et [OVHcloud – AI offer](https://corporate.ovhcloud.com/en/newsroom/news/ai-offer/)
- Comparateurs de marché : [computeprices.com – Scaleway](https://computeprices.com/providers/scaleway) et [GPU Cloud HQ – Alternatives](https://gpucloudhq.com/alternatives)
- Nœud 8x H100 : [GPU Finder – 8x H100](https://gpufinder.dev/gpu/h100/8x)
- Serveur Cloud Temple 2x H100 en SecNumCloud : [Pipook – Cloud Temple](https://pipook.fr/outil/cloud-temple/) et [Cloud Temple – Tarifs publics](https://www.cloud-temple.com/nos-tarifs-publics/)
- Prix d'achat des cartes RTX PRO 6000 Blackwell : [Idealo](https://www.idealo.fr/prix/207353877/nvidia-rtx-pro-6000-blackwell-server-edition.html), [Sabre PC](https://www.sabrepc.com/900-2G153-0000-000-NVIDIA-S8845543) et serveurs complets : [Blackwell Cloud](https://www.blackwellcloud.com/nvidia-rtx-pro-6000-gpu-servers)
- Prix des serveurs H100 : [Mercatus AI – H100 price](https://www.mercatus-ai.com/blog/h100-server-price), [CloudZero – H100 GPU cost](https://www.cloudzero.com/blog/h100-gpu-cost/)
- TCO on-premise : [AI Intel Report – On-Premise AI Cost & TCO](https://aiintelreport.com/enterprise-ai/on-premise-ai-cost-tco) et électricité petite config : [LocalIA – Combien coûte un serveur IA pour PME](https://getlocalia.com/blog/combien-coute-serveur-ia-pme-2026)
- Comparaison location et achat : [GPUNEX – Rent vs buy GPU server](https://www.gpunex.com/fr/blog/rent-vs-buy-gpu-server/)
