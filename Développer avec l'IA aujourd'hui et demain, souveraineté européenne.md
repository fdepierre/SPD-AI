# Développer avec l'IA : aujourd'hui et demain, avec un objectif de souveraineté européenne

Date de génération de cette version : 21 octobre 2026
Statut : Brouillon pour étude, données commerciales et calculs non vérifiés pour l'instant

Ce document étudie une chaîne de développement logiciel assisté par IA qui privilégie, à terme, des services européens et des modèles open weight. Il couvre deux situations : créer un produit neuf et moderniser un logiciel important, avec leurs exigences de sécurité, de preuve, d'exploitation et de conformité.

Les montants servent à cadrer une décision, pas à remplacer un devis. Les références réglementaires doivent être appliquées au rôle de l'entreprise, au produit et au service effectivement retenus ; ce document ne remplace pas un avis juridique.

## Objet, périmètre et convention de lecture

L'objectif proposé est de réduire les dépendances critiques et de conserver la capacité de comprendre, vérifier, exploiter et remplacer les composants de la chaîne. La localisation en Europe, l'ouverture des poids, la sécurité et la conformité sont des dimensions distinctes ; aucune ne suffit, seule, à établir toutes les autres.

Le texte distingue :

- **Fait documenté** : information établie par la référence citée, dans son périmètre.
- **Déclaration d'un acteur** : engagement, caractéristique ou résultat annoncé par un fournisseur, sans validation indépendante présumée.
- **Hypothèse** : scénario de coût, de charge ou d'évolution à tester.
- **Recommandation** : choix de méthode proposé pour le projet.
- **Question ouverte** : point qui nécessite une mesure, une preuve ou une clarification contractuelle.

Deux distinctions s'appliquent à tout le guide. Développer avec l'IA n'est pas nécessairement fournir un système ou un modèle d'IA ; maîtriser l'hébergement ne démontre pas le fait que logiciel est correct.

## Souveraineté juridique et maîtrise de la chaîne

### CLOUD Act : la localisation et la nationalité ne suffisent pas

Le CLOUD Act permet d'exiger d'un fournisseur soumis à la juridiction américaine des données sous sa possession ou son contrôle, indépendamment de leur lieu de stockage ; le Department of Justice précise que cette juridiction n'est pas limitée aux sociétés américaines et que le contrôle au sein d'un groupe dépend des faits ([DOJ, FAQ 24 et 25](https://www.justice.gov/criminal/media/999616/dl?inline)). Un fournisseur européen ou une région européenne ne constitue donc pas, à lui seul, une garantie d'absence d'exposition.

Recommandation : examiner l'entité contractante, le contrôle du groupe, les sous-traitants, les accès techniques, les lieux d'administration et de support, ainsi que les procédures de réquisition. La promesse à rechercher est une maîtrise documentée et vérifiable, pas une formule générale d'« immunité ».

Pour un assistant de code, l'analyse de risques proposée inclut les dépôts et extraits envoyés, les prompts, les fichiers ouverts, les sorties de compilation, les traces d'agents, les secrets accidentels, la télémétrie et les index sémantiques. Une inférence autorisée ne suffit pas si les autres composants créent des flux non autorisés.

### SecNumCloud : une qualification précise, pas celle de tout un fournisseur

SecNumCloud v3.2 fixe notamment des exigences d'établissement dans l'UE, de contrôle capitalistique, de maîtrise technique des tiers et de localisation ; le § 19.6.b porte sur le capital et les droits de vote, directement ou indirectement, avec des limites de 24 % individuellement et 39 % collectivement pour les entités tierces définies par le référentiel ([ANSSI, § 19.6](https://cyber.gouv.fr/documents/388/secnumcloud-referentiel-exigences-v3.2.pdf)). Ces pourcentages ne remplacent pas les autres conditions, notamment celles relatives au veto, aux organes de direction, aux accès des tiers et à l'autonomie d'exploitation.

Le stockage, le traitement, les données techniques, l'administration et la supervision respectent les conditions de localisation UE ; certaines opérations de support hors UE restent possibles sous les conditions du § 19.2.e ([ANSSI, § 19.1 et 19.2](https://cyber.gouv.fr/documents/388/secnumcloud-referentiel-exigences-v3.2.pdf)). Il faut donc vérifier le service et ses modalités, plutôt qu'affirmer qu'aucune intervention hors UE n'est possible.

Le référentiel précise aussi ses limites de protection technique contre l'accès du prestataire aux données ; des moyens complémentaires de chiffrement maîtrisés par le client peuvent être nécessaires, et la qualification ne se substitue pas aux autres obligations applicables ([ANSSI, § 3.3.2](https://cyber.gouv.fr/documents/388/secnumcloud-referentiel-exigences-v3.2.pdf)). Recommandation : distinguer le chiffrement au repos, les accès d'administration et les données effectivement manipulées pendant l'inférence.

La décision ANSSI n° 3389 qualifie « IAAS - SECURE TEMPLE », notamment le baremetal, jusqu'au 30 mai 2028 ; elle ne nomme ni H100 ni LLMaaS et exclut de ce périmètre les services managés additionnels ([décision du 31 juillet 2026](https://messervices.cyber.gouv.fr/visas/2026_3389_np.pdf)). Pour une offre GPU ou d'inférence, obtenir par écrit son rattachement exact au périmètre qualifié.

Recommandation : demander une qualification lorsque le risque, le contrat, le client ou un texte applicable la justifie. Ne pas déduire que tout code OT exige automatiquement SecNumCloud, ni qu'un service installé sur une infrastructure qualifiée devient lui-même qualifié.

## Modèles open weight : contrôle des poids et conditions d'usage

### Ce que l'ouverture permet, et ce qu'elle ne démontre pas

Disposer des poids et d'un moteur d'inférence déployable permet d'envisager une exécution sur une infrastructure choisie ; les fiches Qwen et Z.ai décrivent plusieurs moyens de déploiement, sans démontrer la sécurité d'une installation particulière ([Qwen](https://huggingface.co/Qwen/Qwen3.8-27B), [Z.ai](https://huggingface.co/zai-org/GLM-5.3)). Recommandation : contrôler les dépendances, téléchargements, télémétries et sorties réseau avant de conclure qu'aucune requête ne quitte le périmètre.

La grille de décision proposée sépare quatre questions :

| Question | Contrôle à rechercher | Ce qui ne suffit pas |
|---|---|---|
| Qui peut accéder au code et aux requêtes ? | Opérateur, droits, flux, sous-traitants et traces | Origine géographique du laboratoire |
| Le modèle peut-il être remplacé ou conservé ? | Poids, licence, moteur, versions et procédure de sortie | Accès à une API |
| L'usage commercial est-il autorisé ? | Licence exacte et contrat couvrant l'usage | Mention « open weight » |
| Le modèle est-il adapté au produit ? | Résultats sur les tâches, erreurs et coût complet | Classement public ou taille du modèle |

### Licences vérifiées sur les versions identifiées

| Modèle ou version | Licence ou condition constatée | Conséquence pratique |
|---|---|---|
| Qwen3.8-27B | Apache 2.0 ; modèle de langage annoncé à 27 milliards de paramètres, 28 milliards dans la métadonnée globale incluant d'autres composants ([fiche officielle](https://huggingface.co/Qwen/Qwen3.8-27B)) | Candidat compact à évaluer ; tenir compte de tous les composants et du contexte. |
| Devstral Small 2 24B, version 2512 | Apache 2.0 ([fiche officielle](https://huggingface.co/mistralai/Devstral-Small-2-24B-Instruct-2512)) | Candidat européen pour un pilote local ; ne pas extrapoler sa licence aux autres Devstral. |
| Devstral 2 123B, version 2512 | MIT modifiée : droits exclus si le revenu mensuel consolidé mondial de l'entreprise, ou de l'employeur, dépasse 20 millions de dollars pour le mois précédent ([licence officielle](https://huggingface.co/mistralai/Devstral-2-123B-Instruct-2512/raw/main/LICENSE)) | Vérifier le groupe et l'usage ; une licence commerciale peut être nécessaire. |
| Mistral Medium 3.5 128B | Même type de condition de revenu dans la licence MIT modifiée ([licence officielle](https://huggingface.co/mistralai/Mistral-Medium-3.5-128B/raw/main/LICENSE)) | Ne pas présenter cette licence comme MIT standard. |
| Mistral Small 4 et Mistral Large 3 | Apache 2.0 selon l'éditeur ; Small 4 est annoncé à 119 milliards de paramètres totaux, Large 3 à 675 milliards ([Small 4](https://mistral.ai/news/mistral-small-4/?id=MistralSmall4), [Large 3](https://docs.mistral.ai/models/mistral-large-3-25-12.md)) | Le nom « Small » ne constitue pas un dimensionnement matériel. |
| GLM-5.3 | Licence propre ; une activité de Model-as-a-Service et un revenu agrégé supérieur à 10 milliards de dollars sur douze mois consécutifs peuvent déclencher une revue de sécurité Z.ai avant usage commercial, selon les conditions de la licence ([licence officielle](https://huggingface.co/zai-org/GLM-5.3/raw/main/LICENSE)) | Ne pas l'assimiler à MIT ; analyser les affiliés, la définition du MaaS et le cas d'usage. |

Scaleway indique que des partenariats peuvent couvrir certains usages qui seraient restreints par les licences d'origine ; ces droits de service ne sont pas automatiquement ceux d'un déploiement autonome ([documentation des modèles](https://www.scaleway.com/en/docs/generative-apis/reference-content/supported-models/)). Recommandation : conserver, pour chaque version, les poids, la licence, le moteur validé et les droits contractuels, sans supposer qu'ils s'étendent aux générations suivantes.

## Services européens et outils de développement

### Offres d'inférence : distinguer catalogue, service réel et contrat

Scaleway liste notamment GLM-5.3, Qwen3.8-27B, Mistral Medium 3.5 et DeepSeek-V4.1-Flash ; les limites de contexte et de sortie dépendent de l'offre ([catalogue officiel](https://www.scaleway.com/en/docs/generative-apis/reference-content/supported-models/)). Les qualificatifs de performance figurant sur ces pages restent des déclarations du fournisseur, pas des résultats sur le code du projet.

Une contradiction concerne Devstral 2 : le catalogue le marque disponible en serverless, mais le tableau de cycle de vie indique une fin au 1er août 2026 avec routage vers un autre modèle ; il n'apparaît pas dans le tarif serverless courant ([catalogue et fin de vie](https://www.scaleway.com/en/docs/generative-apis/reference-content/supported-models/), [tarifs](https://www.scaleway.com/en/pricing/model-as-a-service/)). Recommandation : ne pas le retenir comme endpoint de production disponible sans vérifier le modèle réellement servi et les modalités de déploiement dédié.

OVHcloud annonce plus de vingt modèles open weight, une exécution dans l'UE, l'absence d'entraînement sur les données client, une API compatible OpenAI et des intégrations comme OpenCode, Continue et LiteLLM ; la page conserve une réserve pour les données nécessaires à la facturation ([AI Endpoints](https://www.ovhcloud.com/en/public-cloud/ai-endpoints/)). Le détail des traces, de leur durée et des sous-traitants reste à obtenir dans les documents contractuels.

OVHcloud prévoit trois mois de grâce pour certains retraits ; Mistral-Small-3.2-24B-Instruct-2506 doit être retiré le 4 novembre 2026, après annonce du 4 août, avec réponse 404 après extinction ([documentation du cycle de vie](https://docs.ovhcloud.com/en/guides/public-cloud/ai-machine-learning/ai-endpoints-billing)). Recommandation : désigner un destinataire des annonces, fixer les versions lorsque c'est possible et rejouer les tests lors de tout changement.

Cloud Temple décrit une offre GPU et un service LLMaaS sur une infrastructure qu'il présente comme qualifiée SecNumCloud et certifiée HDS ; cette formulation porte sur l'infrastructure et ne démontre pas, seule, la qualification du service d'inférence complet ([offre IA](https://www.cloud-temple.com/en/ai-offer/)). Le contrat, la décision ANSSI et le périmètre technique doivent être examinés ensemble.

### Choisir les outils sans déduire la souveraineté de leur interface

Recommandation : privilégier un IDE et un agent configurables, un routage maîtrisé, une forge hébergée dans le périmètre autorisé et une exécution des tâches isolée. Une API compatible OpenAI facilite l'intégration, mais ne démontre ni l'absence de relais cloud, ni l'égalité de qualité ou de comportement entre modèles.

Le dossier d'évaluation proposé couvre :

- **IDE et agent** : indexation, télémétrie, relais, mises à jour, authentification et outils externes.
- **Inférence** : opérateur, modèle réel, licence, contexte, quota, disponibilité et retrait.
- **Forge et CI** : dépôt, permissions, compilation, tests, artefacts et secrets.
- **Exécution** : sandbox, filtrage réseau, dépendances et accès aux systèmes tiers.
- **Exploitation** : surveillance, support, restauration, réversibilité et compétences.

## Référentiels européens à considérer

La sécurité du produit, la gouvernance de l'organisation, la protection des données et la qualification de l'hébergement doivent être instruits séparément. Le tableau suivant présente leur utilité, sans présumer leur équivalence ni leur application automatique au projet.

| Dispositif | Périmètre et repère documentaire | Utilisation proposée |
|---|---|---|
| SecNumCloud | Qualification française d'un service cloud dans un périmètre défini ; exigences de maîtrise technique, de localisation et de protection vis-à-vis du droit extra-européen ([référentiel ANSSI](https://cyber.gouv.fr/documents/388/secnumcloud-referentiel-exigences-v3.2.pdf)) | Choix d'hébergement lorsque le risque ou une exigence applicable le justifie. |
| EUCS | La Commission le classe parmi les schémas en préparation ; la page ne permet pas de conclure au contenu définitif d'un futur schéma ([cadre européen](https://digital-strategy.ec.europa.eu/en/factpages/european-cybersecurity-certification-framework)) | Veille ; ne pas bâtir une garantie sur un certificat ou des critères futurs présumés. |
| EUCC | Certification de produits TIC ; application depuis le 27 février 2025, niveaux substantiel et élevé ; durée en principe de cinq ans maximum, avec dérogation possible ([règlement 2024/482, art. 4, 12 et 50](https://eur-lex.europa.eu/eli/reg_impl/2024/482/oj/eng), [ENISA](https://certification.enisa.europa.eu/browse-topic/eucc_en)) | Évaluation de sécurité d'un produit dans un périmètre choisi, pas label général de souveraineté. |
| C5:2026 | Attestation allemande ; 168 critères dans 17 domaines, avec calendrier de transition des audits autour du 1er juin 2027 ([BSI, FAQ](https://www.bsi.bund.de/EN/Themen/Unternehmen-und-Organisationen/Informationen-und-Empfehlungen/Empfehlungen-nach-Angriffszielen/Cloud-Computing/Kriterienkatalog-C5/C5-FAQ/kriterienkatalog-c5-faq.html)) | Exigences clients et preuve de sécurité cloud ; ne pas parler de « certificat C5 ». |
| C3A | Cadre de souveraineté publié par le BSI le 27 avril 2026, complémentaire de C5, sans portée réglementaire contraignante en lui-même ([annonce BSI](https://www.bsi.bund.de/DE/Service-Navi/Presse/Pressemitteilungen/Presse2026/260427_C3A.html), [cadre C3A](https://www.bsi.bund.de/EN/Themen/Unternehmen-und-Organisationen/Informationen-und-Empfehlungen/Empfehlungen-nach-Angriffszielen/Cloud-Computing/C3A/C3A.html)) | Grille d'autonomie juridique, opérationnelle et technique, selon les critères pertinents pour le cas d'usage. |
| ENS | Schéma espagnol du secteur public et de certains fournisseurs contractuels ; déclaration ou certification selon la catégorie du système ([RD 311/2022, art. 2 et 38](https://www.boe.es/buscar/act.php?id=BOE-A-2022-7191)) | Examiner les exigences des marchés publics espagnols visés. |
| Qualifications ACN | Qualification des services cloud pour l'administration italienne, selon la classification des données et services et le catalogue ACN ([règlement ACN](https://www.acn.gov.it/portale/en/cloud/regolamento-cloud-per-la-pa)) | Vérifier le service et le niveau requis pour le marché italien. |
| HDS | Certification d'hébergement de données de santé dans son champ légal ; le référentiel v2.0 exige notamment ISO 27001, stockage EEE et encadrement des accès hors EEE ([ANS, référentiel](https://esante.gouv.fr/sites/default/files/media_entity/documents/referentiel_certification_hds---fr--v2.pdf)) | Analyser le champ de l'hébergement concerné ; HDS ne démontre pas, seul, une absence d'exposition aux lois étrangères. |
| Cloud and AI Development Act | Proposition COM(2026) 502 présentée le 3 juin 2026, avec un cadre de souveraineté et des mécanismes pour le secteur public ([proposition Commission](https://digital-strategy.ec.europa.eu/en/library/proposal-cloud-and-ai-development-act-cada), [quatre niveaux](https://digital-strategy.ec.europa.eu/en/policies/cloud-and-ai-development-act)) | Veille sur les achats publics ; distinguer les dispositions proposées des obligations déjà applicables. |

Le référentiel HDS v2.0 est associé à l'arrêté du 26 avril 2024, avec une transition des hébergeurs déjà certifiés jusqu'au 16 mai 2026 ; le PDF v2.1 accessible contient des dates d'arrêté non renseignées et ne suffit pas, seul, à établir son opposabilité ([v2.0](https://esante.gouv.fr/sites/default/files/media_entity/documents/referentiel_certification_hds---fr--v2.pdf), [transition ANS](https://esante.gouv.fr/faq/comment-sorganise-la-transition-avec-la-nouvelle-version-du-referentiel), [PDF v2.1](https://esante.gouv.fr/sites/default/files/media/document/R%C3%A9f%C3%A9rentiel_certification_HDS%20-%20FR%20-%20V2.1%20-%20post%20concertation.pdf)). Recommandation : citer la version réglementaire applicable et vérifier l'arrêté lors d'un engagement.

Recommandation : construire un système de management de la sécurité cohérent, puis établir la correspondance avec les marchés visés. Un certificat ISO 27001 ne donne pas automatiquement une attestation C5, et aucun tableau comparatif ne remplace l'analyse des exigences propres à chaque dispositif ([BSI, FAQ C5](https://www.bsi.bund.de/EN/Themen/Unternehmen-und-Organisationen/Informationen-und-Empfehlungen/Empfehlungen-nach-Angriffszielen/Cloud-Computing/Kriterienkatalog-C5/C5-FAQ/kriterienkatalog-c5-faq.html)).

## Architecture recommandée et patrimoine transmissible

### Trois niveaux de confidentialité proposés

Ces niveaux sont une politique de travail, pas des catégories réglementaires. Ils s'appliquent aux artefacts et à leurs dérivés, pas automatiquement à une phase de projet.

| Niveau | Exemples | Règle de traitement proposée |
|---|---|---|
| N1 : public | Code et documentation effectivement publics, sans secret ni données restreintes | Services et outils approuvés par l'organisation, sans exigence générale d'inférence interne. |
| N2 : interne | Applications métier, spécifications et tests internes | Fournisseurs et destinations autorisés après revue des contrats et des flux, en privilégiant l'UE. |
| N3 : sensible | Règles propriétaires critiques, sécurité, données clients sensibles, éléments OT selon analyse | Environnement interne ou service expressément autorisé ; qualification et exigences sectorielles selon le risque et le contrat. |

Recommandation : une spécification dérivée de règles sensibles conserve leur classification jusqu'à un déclassement explicite. Un produit neuf peut être N3 dès le départ ; un ancien dépôt n'est pas N3 du seul fait de son âge.

### Séparer inférence et exécution

```text
Développeur, IDE et agent configurés
                  |
     Politique d'accès et passerelle d'inférence
                  |
       +----------+------------------+
       |                             |
API européenne autorisée    Inférence interne ou hébergée
selon les artefacts         dans le périmètre autorisé

L'agent travaille séparément dans une sandbox :
forge -> branche -> compilation -> tests -> preuves -> acceptation

La fusion et le déploiement restent soumis aux droits
et décisions prévus par le processus de livraison.
```

La passerelle proposée applique les destinations, quotas et journaux nécessaires, et aide à détecter les secrets identifiables. Elle ne remplace ni le filtrage des autres sorties réseau, ni le contrôle des outils, ni l'analyse des droits d'administration ; la détection de secrets ne doit pas être présentée comme exhaustive.

Recommandation : garder des interfaces et contrats testables entre le moteur métier, les canaux d'accès et l'infrastructure. Vérifier la possibilité de changer de modèle et d'agent par un essai de substitution, pas seulement par la présence d'une API compatible.

### Conserver les connaissances nécessaires à une reprise

Le patrimoine proposé comprend le contexte, les règles validées, les décisions, les spécifications, le code, les preuves et les retours d'exploitation. Le tableau ci-dessous est une méthode de travail, pas une norme imposant ces noms de fichiers.

| Fichier proposé | Contenu minimal | Responsable proposé |
|---|---|---|
| `contexte.md` | Utilisateurs, objectifs, périmètre, exclusions et inconnues | Product et métier |
| `regles.md` | Définitions, unités, calculs, exceptions, sources et validité | Référent métier ou industriel |
| `decisions.md` | Options retenues ou rejetées, raisons, risques et responsables | Décideur identifié selon le sujet |
| `verification.md` | Cas de référence, résultats attendus, preuves et limites | Ingénierie, métier et qualité |
| `exploitation.md` | Versions, accès, support, incidents, sauvegarde et reprise | Exploitation et sécurité |
| `marche.md`, si utile | Segments, alternatives, intégrations et hypothèses d'achat datées | Product |

Recommandation : tenir séparément l'approbation métier d'une règle, son implémentation et sa couverture de tests. Limiter le contexte automatique des agents aux informations utiles et mesurer l'effet des consignes, plutôt qu'injecter toute la documentation dans chaque requête.

## Permissions, sécurité et acceptation

### Permissions explicites

La confidentialité des artefacts, les permissions de l'agent et l'acceptation du résultat sont trois décisions distinctes. Les règles suivantes sont proposées pour un produit partagé ou critique.

| Permission | Règle de départ | Contrôle attendu |
|---|---|---|
| Accès | Seulement les artefacts et destinations nécessaires et autorisés | Identité, périmètre et journal |
| Modification | Branche de travail ou sandbox, sans écriture de production | Droits techniques limités |
| Validation | L'agent propose un dossier, sans auto-accepter le changement | Décision de l'autorité désignée |
| Escalade | Arrêt sur règle ambiguë, secret, effet irréversible ou écart inexpliqué | Critères d'arrêt et interlocuteur |
| Réversibilité | Retour arrière vérifié avant une action engageante | Sauvegarde, restauration et procédure testées |

Recommandation : ne pas donner à l'agent un droit autonome de fusion ou de déploiement sur les produits concernés. Isoler son exécution, filtrer les sorties, protéger les secrets et contrôler les dépendances qu'il propose.

### Trois acceptations et des preuves indépendantes

Le processus proposé distingue :

- **Acceptation technique** : compilation, tests, sécurité, intégration, performances et maintenabilité.
- **Acceptation métier** : justesse des règles, unités, exceptions et résultats attendus.
- **Acceptation produit et exploitation** : utilité, risques résiduels, support, surveillance et capacité de reprise.

Recommandation : affecter chaque décision à une personne compétente disposant de temps, d'informations et d'un pouvoir réel de refus, sans attribuer toutes les responsabilités au Product Manager. Conserver la décision, les réserves, la version du logiciel et les preuves examinées.

Les contrôles proposés comprennent SAST, analyse des dépendances, tests de non-régression et vérification des paquets introduits. Protéger les tests d'acceptation et les jeux de référence contre les modifications non approuvées ; l'avis d'un autre modèle peut aider, mais ne remplace pas ces preuves.

Pour le code OT et PLC, prévoir une revue de domaine et des essais adaptés sur simulateur ou banc avant tout essai sur équipement. La génération de code ne modifie pas les conditions d'autorisation et de sûreté retenues par l'organisation.

## Conformité : NIS2, CRA, données et AI Act

### Analyser le champ avant de constituer le dossier

Les pièces ci-dessous sont des propositions de preuve et de gouvernance, pas une certification de conformité. Le rôle de l'entreprise et la qualification du service doivent être examinés avant de transformer cette grille en obligations contractuelles.

| Niveau | Question préalable | Pièces recommandées |
|---|---|---|
| Produit | Quel produit, mode de fourniture et rôle de fabricant sont concernés ? | Analyse de champ, risques, composants, tests, vulnérabilités et support |
| Organisation | L'entité relève-t-elle de NIS2 et selon quelle transposition ? | Gouvernance, risques, fournisseurs, continuité et notifications |
| Données | Quels traitements, destinataires et transferts doivent être examinés ? | Inventaire, sous-traitants, lieux, conservation et accès |
| Hébergement | Quel service est effectivement qualifié et avec quelles conditions ? | Décision, périmètre, contrat et partage des responsabilités |
| IA | Utilise-t-on un outil de développement ou fournit-on aussi un système ou modèle d'IA ? | Analyse des rôles, usages, intégrations et obligations applicables |

### NIS2 : gouvernance et sécurité du développement

La directive NIS2 prévoit notamment l'approbation et la supervision des mesures par les organes de direction, leur formation et la sécurité des fournisseurs directs, de l'acquisition, du développement et de la maintenance ([directive 2022/2555, art. 20 et 21](https://eur-lex.europa.eu/eli/dir/2022/2555/oj/eng)). Elle n'impose pas un document intitulé « politique IA » ni l'utilisation générale de SecNumCloud.

Selon la page ANSSI consultée le 21 octobre 2026, la transposition française est en cours et l'ensemble des textes est attendu ; un service de pré-enregistrement est déjà accessible ([MesServicesCyber](https://messervices.cyber.gouv.fr/nis2)). Cette indication doit être actualisée lors d'une décision et ne remplace pas l'examen des textes publiés.

L'ANSSI met à disposition ReCyF depuis le 17 mars 2026 comme document de travail, par défaut non obligatoire, dont les futurs assujettis peuvent se prévaloir ; cela ne constitue pas une garantie automatique de conformité ([ANSSI, NIS2](https://cyber.gouv.fr/reglementation/cybersecurite-systemes-dinformation/directives-nis-nis2-et-dispositif-saiv/directive-nis-2/)). Recommandation : l'utiliser pour préparer la cartographie, les écarts et les actions, en vérifiant les exigences propres aux catégories d'entités.

| Exigence NIS2 documentée | Déclinaison proposée pour la chaîne IA |
|---|---|
| Gouvernance des risques, article 20 ([directive](https://eur-lex.europa.eu/eli/dir/2022/2555/oj/eng)) | Politique d'usage approuvée, responsabilités et revue périodique. |
| Fournisseurs directs, article 21(2)(d) et 21(3) ([directive](https://eur-lex.europa.eu/eli/dir/2022/2555/oj/eng)) | Évaluer inférence, IDE, agents, forge et services associés. |
| Développement et vulnérabilités, article 21(2)(e) ([directive](https://eur-lex.europa.eu/eli/dir/2022/2555/oj/eng)) | Appliquer au code généré les mêmes règles de sécurité, correction et divulgation. |
| Continuité, accès et maîtrise des risques, article 21 ([directive](https://eur-lex.europa.eu/eli/dir/2022/2555/oj/eng)) | Sandbox, permissions, sauvegarde, reprise et contrôle des flux. |

Pour les incidents importants, l'article 23 prévoit notamment une alerte sous 24 heures, une notification sous 72 heures et un rapport final dans le mois suivant la notification, avec des règles particulières pour les incidents persistants et certains prestataires ([NIS2, article 23](https://eur-lex.europa.eu/eli/dir/2022/2555/oj/eng)). Recommandation : ne pas qualifier automatiquement toute fuite liée à un assistant d'incident NIS2 ; examiner l'entité concernée, les impacts et le déclencheur applicable.

### CRA : produit, vulnérabilités et période de support

Le CRA s'applique aux produits avec éléments numériques dans son champ, selon le rôle et le mode de fourniture ; le traitement distant couvert répond à une définition précise et tous les SaaS ne relèvent pas automatiquement de ce règlement ([règlement 2024/2847, art. 3(2) et considérant 12](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng)). Le code généré par IA n'est pas exonéré : le dossier doit porter sur le produit et les processus applicables.

| Date ou exigence | Repère vérifié |
|---|---|
| 11 juin 2026 | Application du chapitre IV sur les organismes d'évaluation de conformité ([article 71](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng)). |
| 11 septembre 2026 | Application de l'article 14 aux fabricants concernés ; lancement de la plateforme de signalement ([article 71](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng), [ENISA](https://www.enisa.europa.eu/news/the-cra-single-reporting-platform-is-launched)). |
| 11 décembre 2027 | Application générale du règlement, selon les dispositions transitoires ([articles 69 et 71](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng)). |
| Composants et SBOM | Format courant lisible par machine, couvrant au moins les dépendances de premier niveau ; le texte n'impose pas de ce fait une publication générale de tout le SBOM ([annexe I, partie II](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng)). |
| Mises à jour de sécurité | Diffusion sans retard et en principe gratuite, avec exception contractuelle B2B pour un produit sur mesure ([annexe I, partie II, point 8](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng)). |
| Support | En principe au moins cinq ans ; lorsque l'usage attendu du produit est inférieur, la période correspond à cet usage attendu, dans les conditions du texte ([article 13(8)](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng)). |

Les délais de signalement doivent conserver leur point de départ :

| Événement CRA | Alerte et notification | Rapport final |
|---|---|---|
| Vulnérabilité activement exploitée | Sans retard injustifié, au plus tard 24 h puis 72 h après prise de connaissance ([art. 14(2)](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng)) | Au plus tard 14 jours après disponibilité d'une mesure corrective ou d'atténuation ([art. 14(2)](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng)). |
| Incident grave ayant un impact sur la sécurité du produit | Sans retard injustifié, au plus tard 24 h puis 72 h après prise de connaissance ([art. 14(4)](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng)) | Dans le mois suivant la notification d'incident ([art. 14(4)](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng)). |

L'article 69 prévoit le traitement des produits antérieurs au 11 décembre 2027 et l'application des obligations de signalement aux produits concernés ; l'ancienneté n'est donc pas, à elle seule, une exonération de l'article 14 ([CRA, article 69](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng)). Les obligations de signalement des stewards open source démarrent le 11 décembre 2027 dans le périmètre précisé par l'ENISA ; maintenir un dépôt ne suffit pas à établir ce statut ([ENISA](https://www.enisa.europa.eu/news/the-cra-single-reporting-platform-is-launched)).

Recommandation : relier les exigences, composants, tests, modifications, vulnérabilités, correctifs et versions du produit. Ne pas fusionner les procédures NIS2 et CRA sous prétexte de délais initiaux proches : leurs champs, déclencheurs et responsabilités doivent être instruits séparément.

### AI Act : distinguer l'utilisateur d'outils et le fournisseur d'IA

La Commission confirme l'application des obligations GPAI depuis le 2 août 2025 et la date générale d'application du 2 août 2026, sous réserve des régimes et exceptions applicables ([Commission, AI Act](https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai)). Le simple usage d'un assistant de code ne transforme pas automatiquement son utilisateur en fournisseur de modèle GPAI.

Le règlement modificatif 2026/1744 fixe le 2 décembre 2027 pour les dispositions visées concernant les systèmes à haut risque de l'annexe III et le 2 août 2028 pour ceux de l'annexe I ; il ne s'agit pas d'un report général de tout l'AI Act ([article 1, point 40](https://eur-lex.europa.eu/legal-content/FR/ALL/?uri=CELEX:32026R1744)). Le même texte remplace l'article 4 : fournisseurs et déployeurs doivent prendre des mesures pour favoriser la maîtrise de l'IA, sans devoir garantir un niveau spécifique par individu ([article 1, point 5](https://eur-lex.europa.eu/legal-content/FR/ALL/?uri=CELEX:32026R1744)).

Recommandation : documenter les usages, former les équipes selon les risques, puis analyser séparément les obligations si le logiciel livré contient lui-même un système d'IA. Ne pas déduire d'« open weight » l'ensemble des exemptions éventuellement prévues pour le libre et l'open source.

## Ordres de grandeur économiques

Les prix publics suivants ont été vérifiés documentairement le 21 octobre 2026 et peuvent évoluer. Ils sont distincts des hypothèses de charge, des enveloppes d'investissement et des résultats de performance, qui restent à mesurer.

### Mémoire : un ordre de grandeur, pas un matériel minimal

| Modèle | Base de calcul | Poids théoriques en 4 bits, avant surcoûts |
|---|---|---:|
| Qwen3.8-27B | Environ 27 à 28 milliards de paramètres selon le périmètre retenu ([fiche Qwen](https://huggingface.co/Qwen/Qwen3.8-27B)) | Environ 13,5 à 14 Go |
| Devstral 2 123B | 123 milliards annoncés dans l'identifiant de version ([éditeur](https://huggingface.co/mistralai/Devstral-2-123B-Instruct-2512/raw/main/LICENSE), [catalogue de déploiement](https://www.scaleway.com/en/docs/generative-apis/reference-content/supported-models/)) | Environ 61,5 Go |
| GLM-5.3 | 753 milliards de paramètres ([fiche Z.ai](https://huggingface.co/zai-org/GLM-5.3)) | Environ 376,5 Go |

Ces chiffres sont des calculs décimaux de paramètres multipliés par un demi-octet, pas des mesures de mémoire réelle. Ajouter métadonnées de quantification, composants, moteur, cache de contexte, traitements temporaires et sessions concurrentes ; vérifier également que le format retenu fonctionne avec le moteur choisi.

La fiche GLM ne fixe pas un minimum de huit H100 ; Scaleway rattache son déploiement dédié à B300-SXM-8 ([Z.ai](https://huggingface.co/zai-org/GLM-5.3), [Scaleway](https://www.scaleway.com/en/docs/generative-apis/reference-content/supported-models/)). Recommandation : ne pas acheter une configuration sur la seule division du nombre de paramètres par la mémoire d'une carte.

### Scénario A : API européennes

Les prix serverless suivants sont affichés hors taxes, par million de tokens ; ils ne démontrent pas une qualité équivalente entre modèles ([tarif Scaleway](https://www.scaleway.com/en/pricing/model-as-a-service/)). Le calcul illustratif retient 100 millions de tokens d'entrée et 10 millions de sortie par personne et par mois, sans remise ni cache.

| Modèle | Entrée par million | Sortie par million | Calcul mensuel par personne | Calcul pour cinq personnes identiques |
|---|---:|---:|---:|---:|
| Mistral Medium 3.5 | 1,50 € ([tarif](https://www.scaleway.com/en/pricing/model-as-a-service/)) | 7,50 € ([tarif](https://www.scaleway.com/en/pricing/model-as-a-service/)) | 225 € | 1 125 € |
| GLM-5.3 | 1,80 € ([tarif](https://www.scaleway.com/en/pricing/model-as-a-service/)) | 5,50 € ([tarif](https://www.scaleway.com/en/pricing/model-as-a-service/)) | 235 € | 1 175 € |
| Qwen3.8-27B | 0,60 € ([tarif](https://www.scaleway.com/en/pricing/model-as-a-service/)) | 3,30 € ([tarif](https://www.scaleway.com/en/pricing/model-as-a-service/)) | 93 € | 465 € |
| DeepSeek-V4.1-Flash | 0,60 € ([tarif](https://www.scaleway.com/en/pricing/model-as-a-service/)) | 1,80 € ([tarif](https://www.scaleway.com/en/pricing/model-as-a-service/)) | 78 € | 390 € |

Hypothèse de cadrage : réserver 250 à 3 000 € par mois de consommation API pour une équipe pilote, puis ajuster selon les traces réelles. Ce n'est ni une borne maximale, ni le budget complet du projet ; les tentatives, contextes répétés, sorties de raisonnement et outils associés peuvent le modifier.

### Scénario B : GPU loués et inférence dédiée

Les instances GPU et l'inférence managée sont des produits différents ; les prix sont publiés sur deux pages distinctes ([GPU Scaleway](https://www.scaleway.com/en/pricing/gpu/), [inférence dédiée Scaleway](https://www.scaleway.com/en/pricing/model-as-a-service/)). Les équivalents mensuels ci-dessous sont recalculés sur 730 heures.

| Offre | Prix horaire HT | Calcul à 730 h |
|---|---:|---:|
| Instance L4-1-24G | 0,79 €/h ([GPU](https://www.scaleway.com/en/pricing/gpu/)) | 576,70 €/mois |
| Inférence dédiée L4-1-24G | 0,93 €/h ([managé](https://www.scaleway.com/en/pricing/model-as-a-service/)) | 678,90 €/mois |
| Inférence dédiée H100-1-80G | 3,40 €/h ([managé](https://www.scaleway.com/en/pricing/model-as-a-service/)) | 2 482 €/mois |
| Inférence dédiée H100-SXM-2-80G | 7,95 €/h ([managé](https://www.scaleway.com/en/pricing/model-as-a-service/)) | 5 803,50 €/mois |
| Inférence dédiée H100-SXM-8-80G | 30,06 €/h ([managé](https://www.scaleway.com/en/pricing/model-as-a-service/)) | 21 943,80 €/mois |

Ce tableau ne certifie aucun modèle sur une configuration et ne comprend pas nécessairement stockage, réseau ou intégration. Une enveloppe pilote de 600 à 6 000 € par mois est une hypothèse à adapter ; elle ne couvre pas un grand nœud de huit H100 à temps plein aux tarifs ci-dessus.

À raison de 8 heures pendant 20 jours, 160 heures représentent environ 21,9 % de 730 heures. Une économie n'est obtenue que si la ressource peut être libérée et sa facturation arrêtée ; les agents peuvent aussi continuer de travailler hors des heures des développeurs.

Le prix OVHcloud de 2,80 €/h provient d'un communiqué de janvier 2024 ; la page internationale actuelle consultée affiche 2,99 dollars pour h100-380, pas 2,99 euros ([communiqué historique](https://corporate.ovhcloud.com/en/newsroom/news/ai-offer/), [tarif actuel consulté](https://www.ovhcloud.com/en/public-cloud/prices/)). Le prix actuel en euros, dans la région retenue, reste à confirmer avant comparaison.

### Scénario C : hébergement avec exigence SecNumCloud

Cloud Temple publie les prix suivants, avec leurs unités et engagements ; ces montants ne suffisent pas à démontrer le rattachement de toute prestation associée au périmètre qualifié ([tarifs publics](https://www.cloud-temple.com/nos-tarifs-publics/)). La location d'infrastructure, la colocation d'un matériel acheté et l'inférence managée doivent faire l'objet de devis et responsabilités distincts.

| Configuration publiée | Prix HT par mois | Engagement | Total arithmétique des seules mensualités |
|---|---:|---|---:|
| BM:V3:PERF5, 2 H100 80 Go, 512 Go RAM | 6 141,60 € ([tarif](https://www.cloud-temple.com/nos-tarifs-publics/)) | 24 mois ([tarif](https://www.cloud-temple.com/nos-tarifs-publics/)) | 147 398,40 € |
| OpenShift, 3 workers avec 2 H100 chacun | 26 954,41 € ([tarif](https://www.cloud-temple.com/nos-tarifs-publics/)) | 24 mois ([tarif](https://www.cloud-temple.com/nos-tarifs-publics/)) | 646 905,84 € |

Le tableau OpenShift est indiqué hors licence OpenShift ; il faut clarifier les autres composants et prestations nécessaires ([tarifs Cloud Temple](https://www.cloud-temple.com/nos-tarifs-publics/)). Le montant de 26 954,41 € est donc une mensualité pour six GPU et des workers, pas le coût total de deux GPU sur 24 mois.

La page affiche également une grille LLMaaS avec une unité d'un million de tokens : 1,80 € pour l'entrée, 8 € pour la sortie et 8 € pour le raisonnement, dans une colonne libellée « € HT/mois » ([grille LLMaaS](https://www.cloud-temple.com/nos-tarifs-publics/)). Recommandation : obtenir le mode de décompte, le modèle réel, les éventuels doubles comptes de raisonnement et le périmètre de service avant d'en déduire une facture.

Hypothèse budgétaire : retenir environ 6 100 à 10 000 € par mois pour étudier une solution autour du serveur deux H100, avant confirmation des services inclus. Le nombre de développeurs ne démontre pas la capacité de ce serveur ; la charge et la concurrence doivent être testées.

### Scénario D : achat et exploitation

La fourchette européenne de 18 000 à 23 000 € pour une RTX PRO 6000 Server Edition n'a pas été confirmée : Idealo ne présente pas d'offre, et SabrePC affiche un prix en dollars avec des précisions fiscales et de contenu à clarifier ([Idealo](https://www.idealo.fr/prix/207353877/nvidia-rtx-pro-6000-blackwell-server-edition.html), [SabrePC](https://www.sabrepc.com/900-2G153-0000-000-NVIDIA-S8845543)). Les prix fermes pour un serveur adapté restent à obtenir auprès d'un intégrateur.

Les enveloppes suivantes sont des hypothèses de cadrage en euros, pas des prix de marché validés ni des conversions de prix américains. Elles servent uniquement à distinguer les paliers d'engagement.

| Palier de budget proposé | Enveloppe initiale hypothétique | Condition préalable |
|---|---:|---|
| Station ou petit serveur | 25 000 à 40 000 € | Modèle compact validé, quantification et concurrence mesurées. |
| Serveur intermédiaire multi-GPU | 50 000 à 120 000 € | Besoin de mémoire, débit, support et disponibilité démontré. |
| Grand nœud GPU | 250 000 à 500 000 € ou davantage selon devis | Configuration complète validée ; ne garantit pas l'exécution de GLM-5.3 ou d'un futur modèle. |

Les fourchettes de 250 000 à 320 000 dollars pour certains serveurs huit H100 apparaissent dans des analyses secondaires, sans devis fournisseur attaché et comparable au projet ([Mercatus](https://www.mercatus-ai.com/blog/h100-server-price), [CloudZero](https://www.cloudzero.com/blog/h100-gpu-cost/)). Elles ne valident pas à elles seules les enveloppes en euros du tableau.

Le coût complet proposé doit couvrir :

- **Matériel et financement** : serveur, réseau, stockage, intégration, garantie, pièces et renouvellement.
- **Énergie et locaux** : puissance moyenne mesurée, heures de fonctionnement, refroidissement et contraintes du site.
- **Exploitation** : installation, mises à jour, surveillance, incidents, tests et support.
- **Continuité** : sauvegarde, restauration, indisponibilité, capacité de secours et reprise.
- **Évolution** : moteurs, formats, modèles, licences et compétences.

Exemple de calcul, sans tarif énergétique de marché revendiqué : 10 kW moyens pendant 8 760 heures, à 0,20 €/kWh, donnent 17 520 € par an avant refroidissement. Avec un facteur hypothétique de 1,3, le total énergétique serait de 22 776 € ; ne pas ajouter ce poste à une colocation qui l'inclut déjà.

### TCO H100 : un scénario retrouvé, pas une étude indépendante

La fourchette de 712 000 à 948 000 dollars sur trois ans provient d'un scénario Spheron repris par AI Intel Report ; l'original détaille 711 950 à 947 730 dollars, notamment avec 0,5 ETP, une exploitation continue et des hypothèses de coûts américaines ([source originale](https://www.spheron.network/blog/llm-inference-on-premise-vs-cloud/), [article de reprise](https://aiintelreport.com/enterprise-ai/on-premise-ai-cost-tco)). Spheron est lui-même fournisseur de GPU cloud et compare sa propre offre : ce résultat ne doit pas être présenté comme une validation indépendante du coût local.

Recommandation : reconstruire le TCO en euros sur le même périmètre que la location, sans imposer 0,5 ETP ou un taux d'utilisation universel. Ne pas compter à la fois l'achat et son amortissement comme deux coûts du matériel.

### Achat contre location : calculer plutôt qu'annoncer un seuil

La formule simplifiée proposée est :

\[
\text{Délai de retour en mois} =
\frac{\text{investissement initial net}}
{\text{location mensuelle évitée} - \text{coûts mensuels internes supplémentaires}}
\]

Avec des hypothèses de 50 000 € investis, 2 300 €/mois de location comparable évitée et 800 €/mois de coûts internes supplémentaires, le résultat est d'environ 33 mois. Si le dénominateur est nul ou négatif, ce modèle ne donne pas de retour financier.

Cette formule ne représente pas à elle seule l'obsolescence, le risque, la disponibilité et la flexibilité. Recommandation : tester plusieurs scénarios d'usage réel, de prix et de renouvellement, plutôt que retenir un seuil général de 12 à 18 mois.

### Récapitulatif budgétaire

| Option | Repère proposé | Statut du montant | Décision à prendre |
|---|---|---|---|
| API | 250 à 3 000 €/mois pour un pilote | Enveloppe hypothétique ; tarifs unitaires documentés plus haut | Volume, qualité, artefacts autorisés et contrats. |
| GPU loués | 600 à 6 000 €/mois pour un pilote limité | Enveloppe hypothétique ; hors grand nœud huit GPU à temps plein | Infrastructure brute ou service managé, moteur et exploitation. |
| Offre avec exigence SecNumCloud | Environ 6 100 à 10 000 €/mois autour d'un serveur deux H100 | Hypothèse s'appuyant sur une ligne publique, hors compléments à préciser | Périmètre qualifié, engagement, frais et capacité. |
| Achat | 25 000 à 500 000 € ou davantage selon le palier, puis exploitation | Hypothèses de cadrage à remplacer par des devis | Charge stable, compétences, support, risques et financement. |

Commencer par le scénario autorisé pour les données et artefacts, pas systématiquement par une API. Ni un prix bas ni la présence d'une région UE ne dispense de l'analyse de sécurité.

## Deux scénarios : création et migration

### État de l'art et niveau de preuve

L'étude sur 4 867 développeurs rapporte 26,08 % de tâches terminées en plus dans trois expérimentations, avec une incertitude statistique ; elle ne mesure pas un gain identique sur tout l'effort d'une migration ([SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4945566)). METR avait mesuré un ralentissement de 19 % dans son essai de début 2025 et juge son suivi de février 2026 insuffisant pour estimer solidement l'effet actuel des outils récents ([METR](https://metr.org/blog/2026-02-24-uplift-update/)).

Les fournisseurs décrivent des outils d'analyse, d'extraction, de transformation et de comparaison, notamment AWS Transform et Google Dual Run ; ces descriptions ne démontrent pas un résultat sur tout patrimoine ni dans une chaîne souveraine équivalente ([AWS](https://aws.amazon.com/blogs/migration-and-modernization/tackling-large-mainframe-portfolio-with-agentic-ai-and-aws-transform/), [Google Cloud](https://cloud.google.com/blog/products/infrastructure-modernization/mainframe-migration-and-modernization-with-ai)). Recommandation : les utiliser comme repères fonctionnels, puis mesurer une chaîne autorisée sur un lot représentatif.

Le développement piloté par des spécifications, ou SDD, est ici une méthode proposée : versions, règles, décisions et critères orientent la génération et la vérification. Il ne remplace pas la découverte du problème à résoudre et n'est pas présenté comme une méthode universelle démontrée supérieure.

### Créer un logiciel souverain from scratch

Hypothèse de travail : une équipe de cinq développeurs, un nouveau produit logiciel et un horizon de 18 à 24 mois. L'absence de code ancien ne dispense pas de classifier les règles propriétaires, données et spécifications dès le départ.

| Étape | Pratique proposée | Preuve ou décision attendue |
|---|---|---|
| Découverte | Vérifier besoin, utilisateurs et alternatives | Décider ce qui mérite un produit, pas seulement un prototype. |
| Spécification | Approuver règles, exceptions et critères | Distinguer choix produit et solution technique. |
| Génération | Autoriser les agents, modèles et destinations | Relier les modifications à des exigences. |
| Revue | Séparer les trois acceptations | Consigner preuves, réserves et responsabilités. |
| Livraison | Tester sécurité, reprise et exploitation | Autoriser la mise à disposition du produit. |
| Apprentissage | Observer usage, défauts et maintenance | Réviser le produit et la documentation. |

Le gain de génération ne doit pas être présumé maximal : sa valeur dépend de la nouveauté, du domaine, de la vérifiabilité et des reprises. Recommandation : mesurer séparément vitesse de réalisation, correction métier, utilité et capacité d'un autre mainteneur à reprendre le produit.

Une enveloppe API hypothétique de 250 à 3 000 €/mois représente 4 500 à 54 000 € sur 18 mois, ou 6 000 à 72 000 € sur 24 mois. Ajouter l'équipe, la préparation du contexte, les tests, la sécurité, la plateforme et l'exploitation ; ce calcul n'est pas le budget complet du produit.

Si un artefact est sensible dès le départ, l'environnement autorisé doit être disponible immédiatement. La location dédiée peut aussi se justifier par le débit, la latence, la disponibilité ou le coût mesuré, pas uniquement par la confidentialité.

### Migrer un gros logiciel

Hypothèse de travail : plusieurs millions de lignes, une activité continue et des exigences transactionnelles fortes. La découverte vise autant la connaissance métier et les dépendances que le code à remplacer.

Classifier les sources et les dérivés : code, binaires, interfaces, captures, données, journaux, index, règles extraites et spécifications. Le comportement cible n'est pas automatiquement moins sensible que l'existant.

| Phase | Contribution possible de l'IA | Décision humaine | Preuve attendue |
|---|---|---|---|
| Découverte | Cartographie, dépendances et données | Confirmer droits, périmètre et inconnues | Carte reliée aux sources inspectées. |
| Extraction des règles | Description des comportements | Distinguer intention, contournement, exception et défaut | Catalogue relié au code et aux observations. |
| Comportement cible | Propositions et questions | Approuver ce qui reste, change ou disparaît | Spécification cible distincte de l'existant. |
| Architecture cible | Options de découpage et intégration | Arbitrer transactions, performance et maintenance | Décisions motivées. |
| Génération | Code, adaptateurs et configuration | Accepter des lots limités | Modifications reliées aux exigences. |
| Équivalence | Comparaison et analyse des écarts | Définir les écarts autorisés | Rapport classé et risques résiduels. |
| Bascule | Scripts et contrôles préparatoires | Autoriser la bascule ou l'arrêt | Réconciliation, restauration et repli testés. |
| Exploitation | Surveillance et corrections proposées | Évolutions et retrait de l'ancien | Incidents, support et transmission. |

Recommandation : vérifier le support exact des langages, transactions, ordonnanceurs, bases et formats. Une démonstration sur COBOL/z/OS ne démontre pas une migration de TPF, d'automates ou d'un système distribué.

### Décrire l'existant sans le transformer en vérité métier

La démarche inverse proposée part du logiciel autorisé à l'analyse pour reconstruire des comportements et des inconnues, puis fait valider la cible avant reconstruction. Conserver deux livrables : description de l'existant et spécification cible, avec sources, versions, niveau de confiance et validateurs.

Une analyse de binaire, d'exécution ou d'interface peut compléter des sources insuffisantes, mais ne prouve ni l'intention d'origine ni l'équivalence générale. Recommandation : examiner séparément les droits d'accéder, d'analyser, de réutiliser et de distribuer avant l'essai.

### Trois preuves avant la bascule

Le dossier proposé sépare l'équivalence avec l'ancien, la correction métier et l'aptitude à l'exploitation. Reproduire un défaut ancien peut satisfaire la première sans satisfaire la deuxième.

Classer chaque différence en changement approuvé, défaut du nouveau, défaut découvert dans l'ancien ou différence inexpliquée. Les critères proposés incluent arrondis, unités, dates, tris, délais, erreurs, reprises, concurrence et garanties transactionnelles.

Pour l'exécution parallèle, prévoir le rejeu ou un mode sans effets réels, avec une seule chaîne autorisée à déclencher un paiement, une écriture ou une commande industrielle. La coexistence progressive doit budgéter les adaptateurs, synchronisations, réconciliations et fenêtres de double exploitation, sans les assimiler à un doublement automatique de tout le coût.

### Amadeus : repère historique et sensibilité, pas prévision IA

Amadeus rapporte environ 2 000 personnes-années, plus de 400 ingénieurs au pic et la fin du dernier mainframe fin 2018 ; il s'agit d'une déclaration de l'entreprise, pas d'une ventilation auditée des tâches ([rétrospective Amadeus](https://amadeus.com/en/blog/articles/celebrating-one-year-fully-open-systems)). Elle ne mesure pas une migration comparable réalisée aujourd'hui avec l'IA.

| Hypothèse de sensibilité sur une base de 2 000 personnes-années | Effort arithmétique |
|---|---:|
| Surcoût de 10 % | 2 200 personnes-années |
| Aucun gain net | 2 000 personnes-années |
| Réduction de 20 % | 1 600 personnes-années |
| Réduction de 30 % | 1 400 personnes-années |
| Réduction de 40 % | 1 200 personnes-années |

Aucun de ces chiffres n'est une estimation actuelle d'Amadeus ni un calendrier. Recommandation : distinguer le gain de l'IA de celui des outils classiques et du changement de plateforme, puis mesurer les fonctionnalités acceptées, les reprises, les écarts et la performance sur un domaine limité.

Pour une cellule pilote, une hypothèse GPU de 600 à 6 000 €/mois représente 3 600 à 36 000 € sur six mois ; une enveloppe de 6 100 à 10 000 €/mois représente 36 600 à 60 000 €. Ajouter l'équipe, l'analyse, les licences, les jeux de référence, la sécurité et la coexistence : ces enveloppes ne financent ni ne dimensionnent à elles seules un programme de plusieurs millions de lignes.

### Comparaison des deux trajectoires

| Dimension | Création | Migration |
|---|---|---|
| Décision initiale | Quel problème mérite le produit ? | Que préserver, corriger, retirer ou remplacer ? |
| Confidentialité | Classifier avant le premier prompt | Classifier l'existant et ses dérivés |
| Goulot à mesurer | Découverte, spécification, revue et usage | Compréhension, architecture, preuves et bascule |
| Gain IA | À mesurer, sans coefficient présumé | À mesurer par activité et par lot |
| Risque principal | Produit conforme à une demande mal choisie ; dette de compréhension | Défauts hérités pris pour des règles ; écarts inexpliqués |
| Mesure du pilote | Coût accepté, défauts et utilité | Coût par comportement validé, écarts et aptitude à l'exploitation |

## Mesurer et financer le résultat

L'indicateur de gestion proposé est le coût complet par modification acceptée et maintenue sur une fenêtre d'observation explicite. Cette fenêtre doit correspondre au cycle du produit et ne dispense pas de traiter immédiatement les défauts graves.

\[
\text{Coût par modification acceptée} =
\frac{\text{coûts complets de la période, reprises et défauts inclus}}
{\text{modifications acceptées et maintenues sur la fenêtre retenue}}
\]

Décomposer les coûts en préparation du contexte, génération, évaluations automatiques, revue, corrections, déploiement, surveillance et défauts après acceptation. Affecter une seule fois les coûts partagés et éviter d'ajouter une seconde fois un temps humain déjà compris dans le budget de l'équipe.

Les indicateurs proposés comprennent :

- **Qualité** : acceptation sans retouche, écarts métier, régressions et vulnérabilités.
- **Temps humain** : revue, reprise, analyse d'impact et résolution d'incidents.
- **Exploitation** : disponibilité, retours arrière, restauration et performance.
- **Souveraineté** : flux dans les périmètres autorisés, dépendances et substitution testée.
- **Transmission** : capacité d'un autre ingénieur à expliquer une règle et maintenir le produit.
- **Valeur** : usage réel, satisfaction et effet observé, pas seulement nombre de tickets fermés.

Exemple hypothétique : cinq personnes consacrant deux heures par semaine à la preuve et à la transmission représentent environ 40 heures sur quatre semaines. À un coût complet choisi de 80 €/h, cela représente 3 200 €/mois à rendre visible, sans le compter deux fois si les salaires sont déjà inclus.

## Feuille de route proposée

### Cadrer et mesurer : zéro à trois mois

- **Inventaire** : classifier artefacts et outils existants, identifier droits, responsables et destinations.
- **Connaissance** : constituer le patrimoine minimal et les critères de décision.
- **Pilote** : sélectionner 30 à 50 tickets ou comportements représentatifs, avec acceptation indépendante.
- **Comparaison** : tester trois ou quatre modèles dans un périmètre autorisé, sans achat lourd par défaut.
- **Gouvernance** : fixer permissions, escalades, arrêts et autorité d'acceptation.

### Étendre avec des preuves : trois à neuf mois

- **Plateforme** : déployer passerelle, sandbox, journaux nécessaires et contrôles.
- **Charge** : mesurer concurrence, mémoire, latence, consommation et coût complet.
- **Sécurité** : scanners, dépendances, SBOM lorsque requis et suivi des vulnérabilités.
- **Contrats** : confirmer sous-traitants, rétention, modèle servi, qualification et réversibilité.
- **Compétences** : financer la revue, la preuve, la transmission et la maintenance.

### Réduire les dépendances : neuf à vingt-quatre mois

- **Choix économique** : décider achat, location ou API sur les mesures et devis.
- **Substitution** : tester le remplacement du modèle, de l'agent et de l'opérateur.
- **Évolution** : rejouer le banc d'essai à chaque changement significatif.
- **Exploitation** : vérifier support, restauration, incidents et maintien des preuves.

Pour une migration, une phase préalable de découverte peut être nécessaire avant cette feuille de route. Son environnement est déterminé par les artefacts et les contraintes, pas par la seule taille du patrimoine.

## Demain : horizon de douze à trente-six mois

Les trajectoires suivantes sont des hypothèses, pas des prévisions de disponibilité ou de performance. Elles servent à vérifier si les investissements restent utiles lorsque les capacités des outils changent.

| Trajectoire possible | Effet envisagé | Réponse proposée |
|---|---|---|
| Autonomie accrue des métiers | Plus de prototypes et d'outils locaux | Règle d'industrialisation et de reprise lorsqu'un outil devient partagé ou critique. |
| Spécification devenue artefact principal | Davantage de génération et de régénération | Conserver règles, décisions, preuves et compréhension humaine. |
| Automatisation plus large | Moins d'intervention sur certains lots vérifiables | Permissions proportionnées, capacité d'arrêt et indépendance de l'acceptation. |
| Modèle compact suffisant | Infrastructure plus légère possible | Redimensionner après mesure, pas selon le seul nombre de paramètres. |
| Écart durable en faveur de modèles fermés | Coût d'opportunité d'un choix souverain | Mesurer l'écart ; garder les cas publics séparés des cas sensibles. |

Recommandation : ne pas investir sur l'hypothèse d'une disparition de la revue du code ni sur celle d'une supériorité durable d'un laboratoire. Les actifs à conserver sont les données autorisées, les interfaces, les règles, les tests, les décisions, les procédures de reprise et les compétences.

## Décisions et vérifications encore nécessaires

Les sources vérifiées ne doivent plus être présentées comme inconnues, mais elles ne ferment pas les questions propres au projet. Le tableau suivant limite les réserves aux points qui nécessitent encore une preuve ou un engagement.

| Point ouvert | Ce qui est établi | Ce qui reste à obtenir |
|---|---|---|
| Juridiction et accès | La nationalité et la localisation ne suffisent pas | Analyse du groupe, contrats, sous-traitants, accès et réquisitions |
| Qualification de l'offre GPU/inférence | Décision IaaS et tarifs publics disponibles | Rattachement exact de la configuration et services associés |
| Devstral 2 serverless Scaleway | Documentation contradictoire | Confirmation du modèle réellement servi et de sa durée de vie |
| Licences | Conditions vérifiées pour les versions citées | Applicabilité à l'entité, au groupe, au service et aux dérivés |
| Capacité matérielle | Paramètres et configurations publiées documentés | Essai du moteur, du contexte, du débit et des sessions |
| Achat européen | Enveloppes de cadrage proposées | Devis exacts, taxes, intégration, garantie, délais et support |
| TCO local | Origine du scénario H100 retrouvée | Coûts locaux, charge, continuité et périmètre comparable |
| Réglementation | Références et calendriers documentés | Analyse de champ, textes actualisés et exigences sectorielles |
| Migration | Méthode et critères proposés | Droits, références indépendantes, écarts et bascule autorisée |
| Gains de l'IA | Études contextualisées et sensibilité distinguées | Mesures sur le travail réellement accepté et maintenu |

La décision proposée n'est pas de choisir un unique « modèle souverain », mais de construire une chaîne dont les dépendances et les preuves restent maîtrisées. Un achat important ou un engagement de conformité ne devrait intervenir qu'après traitement des points pouvant inverser le choix.

## Annexe : sources et références

Les liens suivants regroupent toutes les références citées dans cette version. Les sources primaires établissent les textes, décisions, licences et prix dans leur périmètre ; les sources fournisseurs et estimations secondaires restent identifiées comme telles dans le corps.

### Droit et qualification cloud

- Department of Justice, CLOUD Act et juridiction : [FAQ officielle, notamment questions 24 et 25](https://www.justice.gov/criminal/media/999616/dl?inline).
- ANSSI, SecNumCloud v3.2 : [référentiel d'exigences, notamment § 3.3.2, 19.1, 19.2 et 19.6](https://cyber.gouv.fr/documents/388/secnumcloud-referentiel-exigences-v3.2.pdf).
- ANSSI, Cloud Temple : [décision de qualification n° 3389 du 31 juillet 2026](https://messervices.cyber.gouv.fr/visas/2026_3389_np.pdf).

### Modèles et licences

- Qwen : [Qwen3.8-27B, fiche officielle](https://huggingface.co/Qwen/Qwen3.8-27B).
- Z.ai : [GLM-5.3, fiche officielle](https://huggingface.co/zai-org/GLM-5.3) et [licence](https://huggingface.co/zai-org/GLM-5.3/raw/main/LICENSE).
- Mistral : [Devstral Small 2 24B, version 2512](https://huggingface.co/mistralai/Devstral-Small-2-24B-Instruct-2512).
- Mistral : [licence Devstral 2 123B, version 2512](https://huggingface.co/mistralai/Devstral-2-123B-Instruct-2512/raw/main/LICENSE).
- Mistral : [licence Mistral Medium 3.5 128B](https://huggingface.co/mistralai/Mistral-Medium-3.5-128B/raw/main/LICENSE).
- Mistral : [annonce Small 4](https://mistral.ai/news/mistral-small-4/?id=MistralSmall4) et [documentation Large 3](https://docs.mistral.ai/models/mistral-large-3-25-12.md).

### Services et tarifs

- Scaleway : [modèles, configurations, licences et cycle de vie](https://www.scaleway.com/en/docs/generative-apis/reference-content/supported-models/).
- Scaleway : [tarifs Model-as-a-Service, serverless et dédié](https://www.scaleway.com/en/pricing/model-as-a-service/).
- Scaleway : [tarifs des instances GPU](https://www.scaleway.com/en/pricing/gpu/).
- OVHcloud : [AI Endpoints, engagements et intégrations annoncés](https://www.ovhcloud.com/en/public-cloud/ai-endpoints/).
- OVHcloud : [facturation et cycle de vie des modèles](https://docs.ovhcloud.com/en/guides/public-cloud/ai-machine-learning/ai-endpoints-billing).
- OVHcloud : [page tarifaire internationale consultée](https://www.ovhcloud.com/en/public-cloud/prices/).
- OVHcloud : [communiqué historique du 24 janvier 2024](https://corporate.ovhcloud.com/en/newsroom/news/ai-offer/).
- Cloud Temple : [offre IA et formulation du périmètre d'infrastructure](https://www.cloud-temple.com/en/ai-offer/).
- Cloud Temple : [tarifs publics, GPU, OpenShift et LLMaaS](https://www.cloud-temple.com/nos-tarifs-publics/).

### Référentiels européens

- Commission : [cadre européen de certification et état des schémas](https://digital-strategy.ec.europa.eu/en/factpages/european-cybersecurity-certification-framework).
- EUR-Lex : [règlement EUCC 2024/482](https://eur-lex.europa.eu/eli/reg_impl/2024/482/oj/eng).
- ENISA : [présentation EUCC](https://certification.enisa.europa.eu/browse-topic/eucc_en).
- BSI : [FAQ C5, critères, attestation et transition](https://www.bsi.bund.de/EN/Themen/Unternehmen-und-Organisationen/Informationen-und-Empfehlungen/Empfehlungen-nach-Angriffszielen/Cloud-Computing/Kriterienkatalog-C5/C5-FAQ/kriterienkatalog-c5-faq.html).
- BSI : [publication de C3A, 27 avril 2026](https://www.bsi.bund.de/DE/Service-Navi/Presse/Pressemitteilungen/Presse2026/260427_C3A.html) et [cadre C3A](https://www.bsi.bund.de/EN/Themen/Unternehmen-und-Organisationen/Informationen-und-Empfehlungen/Empfehlungen-nach-Angriffszielen/Cloud-Computing/C3A/C3A.html).
- Espagne, BOE : [Real Decreto 311/2022, ENS](https://www.boe.es/buscar/act.php?id=BOE-A-2022-7191).
- Italie, ACN : [règlement cloud pour l'administration](https://www.acn.gov.it/portale/en/cloud/regolamento-cloud-per-la-pa).
- ANS : [référentiel HDS v2.0](https://esante.gouv.fr/sites/default/files/media_entity/documents/referentiel_certification_hds---fr--v2.pdf) et [FAQ de transition](https://esante.gouv.fr/faq/comment-sorganise-la-transition-avec-la-nouvelle-version-du-referentiel).
- ANS : [PDF HDS v2.1 avec dates d'arrêté non renseignées, non retenu seul pour établir l'opposabilité](https://esante.gouv.fr/sites/default/files/media/document/R%C3%A9f%C3%A9rentiel_certification_HDS%20-%20FR%20-%20V2.1%20-%20post%20concertation.pdf).
- Commission : [proposition CADA](https://digital-strategy.ec.europa.eu/en/library/proposal-cloud-and-ai-development-act-cada) et [présentation des niveaux de souveraineté](https://digital-strategy.ec.europa.eu/en/policies/cloud-and-ai-development-act).

### NIS2, CRA et AI Act

- EUR-Lex : [directive NIS2 2022/2555, notamment articles 20, 21 et 23](https://eur-lex.europa.eu/eli/dir/2022/2555/oj/eng).
- ANSSI : [NIS2, état de la transposition et pré-enregistrement](https://messervices.cyber.gouv.fr/nis2).
- ANSSI : [NIS2 et statut de ReCyF](https://cyber.gouv.fr/reglementation/cybersecurite-systemes-dinformation/directives-nis-nis2-et-dispositif-saiv/directive-nis-2/).
- EUR-Lex : [CRA 2024/2847, notamment articles 3, 13, 14, 69, 71 et annexe I](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng).
- ENISA : [plateforme CRA et dates de signalement](https://www.enisa.europa.eu/news/the-cra-single-reporting-platform-is-launched).
- Commission : [AI Act, calendrier et périmètres](https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai).
- EUR-Lex : [règlement modificatif 2026/1744, notamment article 1, points 5 et 40](https://eur-lex.europa.eu/legal-content/FR/ALL/?uri=CELEX:32026R1744).

### Matériel et TCO

- Idealo : [référence RTX PRO 6000 Blackwell Server Edition, sans offre lors du contrôle](https://www.idealo.fr/prix/207353877/nvidia-rtx-pro-6000-blackwell-server-edition.html).
- SabrePC : [référence 900-2G153-0000-000, prix et configuration à clarifier avant devis](https://www.sabrepc.com/900-2G153-0000-000-NVIDIA-S8845543).
- Mercatus : [estimation secondaire des prix H100](https://www.mercatus-ai.com/blog/h100-server-price).
- CloudZero : [analyse secondaire des coûts H100](https://www.cloudzero.com/blog/h100-gpu-cost/).
- Spheron : [scénario original de TCO et comparaison cloud, publié par un fournisseur](https://www.spheron.network/blog/llm-inference-on-premise-vs-cloud/).
- AI Intel Report : [article reprenant la fourchette TCO](https://aiintelreport.com/enterprise-ai/on-premise-ai-cost-tco).

### Productivité et migration

- Cui et al. : [trois expérimentations sur l'assistance au code, SSRN 4945566](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4945566).
- METR : [actualisation du 24 février 2026 et limites de mesure](https://metr.org/blog/2026-02-24-uplift-update/).
- AWS : [description de Transform sur des portefeuilles mainframe](https://aws.amazon.com/blogs/migration-and-modernization/tackling-large-mainframe-portfolio-with-agentic-ai-and-aws-transform/).
- Google Cloud : [description de modernisation mainframe et Dual Run](https://cloud.google.com/blog/products/infrastructure-modernization/mainframe-migration-and-modernization-with-ai).
- Amadeus : [rétrospective de la migration vers les systèmes ouverts](https://amadeus.com/en/blog/articles/celebrating-one-year-fully-open-systems).
