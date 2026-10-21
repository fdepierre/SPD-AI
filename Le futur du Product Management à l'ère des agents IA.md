# Le futur du Product Management à l'ère des agents IA

Version 1.0, octobre 2026

Ce document rassemble une vue aussi complète que possible de ce que les agents IA changent pour le Product Management de produits logiciels, dans un contexte européen. Il est publié pour être repris, discuté et corrigé. Le corps suit un raisonnement en huit parties et une conclusion ; les annexes A à I rassemblent les notions, les états de l'art, les grilles et les sources qui le soutiennent.

## Table des matières

- 1. Introduction
  - 1.1 Objet
  - 1.2 Sources et méthode
  - 1.3 Convention de lecture
  - 1.4 Deux exemples récurrents
  - 1.5 Ce qui est déjà dit ailleurs, et ce que ce document propose
  - 1.6 Ce que le document ne couvre pas
- 2. Ce qui change
  - 2.1 Les métiers construisent déjà
  - 2.2 L'exécution s'automatise là où l'évaluation est possible
  - 2.3 Les fonctionnalités deviennent reproductibles
- 3. Ce que vaut un produit
  - 3.1 La valeur durable quand la copie est facile
  - 3.2 Décider reste le cœur du Product Management
- 4. Ce qu'il faut transmettre
  - 4.1 Le patrimoine transmissible
  - 4.2 Spécifier : du comportement existant au comportement voulu
- 5. Réaliser et prouver avec des agents
  - 5.1 Des permissions plutôt que des niveaux
  - 5.2 Prouver et accepter
  - 5.3 Une architecture qui rend la boucle vérifiable et reprenable
- 6. Deux trajectoires
  - 6.1 Créer un produit neuf, moderniser un existant
- 7. Organisation, économie et cadre européen
  - 7.1 Organisation et rôle du Product Manager
  - 7.2 Économie, mesure et indicateurs
  - 7.3 Souveraineté de la chaîne et cadre européen
- 8. Prospective
  - 8.1 Trois scénarios et un même test
- 9. Conclusion

**Annexes**

- A. Glossaire
- B. Inventaire des sujets
- C. États de l'art par domaine
  - C.1 Carte des domaines
  - C.2 Autonomie des métiers (citizen development et shadow AI)
  - C.3 Finalité du Product Management
  - C.4 Fonctionnalités reproductibles et valeur durable du produit
  - C.5 Discovery et validation
  - C.6 Organisation et compétences
  - C.7 Patrimoine de connaissance
  - C.8 Dispositif minimal de transmission de connaissance (proposition)
  - C.9 Spécifications et SDD
  - C.10 Agents et autonomie
  - C.11 Preuves et acceptation
  - C.12 Cycle de vie produit (plateformes internes)
  - C.13 Modernisation de l'existant
  - C.14 Rétro-ingénierie agentique : apport de REA
  - C.15 Économie et mesure
  - C.16 Souveraineté et dépendances
  - C.17 Sécurité et cadre européen
  - C.18 Prospective
  - C.19 Architectures vérifiables, composables et portables
  - C.20 Vérifiabilité, évaluation et compréhension
- D. Notions fondamentales venues d'autres disciplines
  - D.1 Question et limites
  - D.2 Synthèse
  - D.3 Famille 1 : vérifier
  - D.4 Famille 2 : spécifier
  - D.5 Famille 3 : superviser
  - D.6 Famille 4 : apprendre
  - D.7 Famille 5 : valoriser
  - D.8 Ce que ces notions apportent au raisonnement
  - D.9 Notions voisines non développées
- E. Réflexions existantes, thèse par thèse
  - E.1 Objet et méthode
  - E.2 Synthèse
  - E.3 L'exécution s'automatise là où l'évaluation est possible
  - E.4 Le goulot se déplace vers la revue et la vérification
  - E.5 Le Product Management devient un goulot
  - E.6 La spécification comme artefact central (SDD)
  - E.7 Les fichiers de contexte et la mémoire du projet
  - E.8 Le système d'évaluation est un patrimoine, et il peut se tromper
  - E.9 Un résultat correct n'est pas forcément compris
  - E.10 L'apprentissage quand les tâches d'entrée évoluent
  - E.11 Les mesures de productivité
  - E.12 Économie : coût d'inférence et coût par modification acceptée
  - E.13 Reproductibilité des fonctionnalités et valeur des produits
  - E.14 Modernisation des systèmes anciens et boucle inverse du SDD
  - E.15 Niveaux de délégation et d'autonomie
  - E.16 Responsabilité, acceptation et réglementation européenne
  - E.17 Le cas des mathématiques
  - E.18 Le modèle produit de Marty Cagan
  - E.19 Niveau de preuve des principales données
- F. Grille d'analyse de la vérifiabilité des activités
- G. Le cas des mathématiques produites par IA : portée et limites
  - G.1 Ce que montrent les cas publiés
  - G.2 Affirmations répandues non retenues
- H. Points restant à vérifier
  - H.1 Citations et textes classiques
  - H.2 Chiffres et déclarations
  - H.3 Cadre réglementaire et souveraineté
  - H.4 Cas et outils
  - H.5 Affirmations répandues non utilisées
- I. Sources
  - I.1 Références commentées : passage utilisé et limite
  - I.2 Autres références lues, par thème
  - I.3 Références repérées, non examinées en détail
  - I.4 Index des sources citées dans le corps

---

# Corps du document

## 1. Introduction

### 1.1 Objet

Ce document traite du Product Management de produits logiciels quand une part croissante de leur réalisation est confiée à des agents IA, c'est-à-dire à des systèmes capables d'enchaîner seuls plusieurs actions : lire un dépôt de code, écrire une modification, lancer les tests, corriger, proposer le résultat. Il se place dans un contexte européen, où la souveraineté de la chaîne d'outils et les obligations réglementaires pèsent sur les choix.

Une distinction traverse tout le texte. Développer avec l'IA, c'est utiliser des agents pour construire un produit qui peut lui-même ne contenir aucune IA, par exemple un outil de facturation. Développer un produit contenant de l'IA, c'est construire un produit dont le comportement dépend d'un modèle, par exemple un assistant qui répond aux clients. Les deux situations partagent des questions, mais pas toutes. Une recommandation valable pour l'une ne vaut pas automatiquement pour l'autre, et le texte précise à chaque fois de laquelle il parle.

Le document s'adresse d'abord à des Product Managers expérimentés, et aux personnes qui étudient ces sujets. Il vise l'exhaustivité plutôt que la brièveté : il rassemble les notions, les données et les débats utiles, avec leurs sources, pour servir de référence à des articles plus courts. Il suppose une connaissance du métier, mais il explique chaque notion à sa première apparition ; un glossaire figure en annexe A.

### 1.2 Sources et méthode

Le document rassemble des travaux publiés en génie logiciel, en Product Management, en économie, en facteurs humains, en sciences de la décision et en droit européen, ainsi que des déclarations d'entreprises, des analyses de praticiens et des cas récents de logiciels construits avec des agents. Il s'appuie aussi sur la pratique de l'auteur, signalée comme telle.

Les faits retenus ont été vérifiés à leur source primaire lorsque c'était possible. Lorsqu'une source n'a pu être lue qu'à travers un tiers, ou seulement en partie, le texte le dit. Les sources ont été consultées en octobre 2026. Les formules répandues sur la « fin des métiers », l'« exécution gratuite » ou les « seules places viables » ne sont pas reprises comme des faits, et aucune performance obtenue en mathématiques n'est extrapolée à l'automatisation complète du développement logiciel ou du Product Management.

Le corps du document suit un raisonnement. Les annexes rassemblent ce qui le soutient sans l'alourdir : glossaire (annexe A), inventaire des sujets (annexe B), états de l'art par domaine (annexe C), notions venues d'autres disciplines (annexe D), réflexions existantes examinées thèse par thèse (annexe E), grille d'analyse de la vérifiabilité (annexe F), cas des mathématiques produites par IA (annexe G), points restant à vérifier (annexe H) et sources (annexe I).

La recherche est ciblée, pas systématique : elle ne prétend pas avoir recensé toute la littérature. Les lecteurs sont invités à signaler les travaux manquants, ce que la publication sur GitHub permet de faire simplement.

### 1.3 Convention de lecture

Chaque affirmation importante porte un statut, indiqué dans le texte lorsqu'il n'est pas évident :

- Fait documenté : vérifié à la source citée.
- Déclaration d'un acteur : ce qu'une entreprise ou une personne affirme de son propre travail, sans évaluation indépendante.
- Élément non vérifié : affirmation ou estimation reprise d'analyses de praticiens, dont la source primaire n'a pas été vérifiée.
- Hypothèse : raisonnement sur ce qui pourrait être vrai ou sur une évolution possible.
- Recommandation : méthode que nous proposons, non validée par une étude.
- Question ouverte : point que les éléments disponibles ne permettent pas de trancher.
- Observation de terrain : constat de l'auteur, tiré de sa pratique dans des entreprises de plus de 50 personnes, recoupé lorsque c'est possible avec des sources publiées, mais non mesuré.

Deux règles complètent cette convention. Un score obtenu sur un banc d'évaluation (benchmark) n'est jamais cité sans sa date et ses limites. Une mesure de productivité est toujours rattachée au type d'outil mesuré (assistant de complétion ou agent), au niveau mesuré (individu, équipe, entreprise) et à l'indicateur utilisé.

### 1.4 Deux exemples récurrents

Deux cas reviennent au fil du texte pour montrer les mêmes règles à deux niveaux de risque. Ils sont construits pour l'explication et ne décrivent pas une organisation réelle.

- L'outil de pilotage financier : un contrôleur de gestion construit avec un agent un tableau de bord qui consolide les marges par activité. L'outil commence comme un fichier personnel, puis il est partagé avec la direction financière. Une erreur coûte une mauvaise décision, rarement un accident.
- Le logiciel industriel : une équipe modifie, avec l'aide d'agents, un logiciel qui pilote une installation, par exemple la gestion d'énergie d'un site combinant production photovoltaïque, stockage par batteries et groupes électrogènes. Une erreur peut arrêter la production, endommager un équipement ou mettre des personnes en danger.

### 1.5 Ce qui est déjà dit ailleurs, et ce que ce document propose

Plusieurs idées de ce document ont été formulées par d'autres, et elles leur sont attribuées. La référence principale du Product Management reste Marty Cagan et le Silicon Valley Product Group (SVPG) : les quatre risques d'un produit, la distinction entre découverte et livraison, et le modèle produit qui finance des équipes chargées de résultats plutôt que des projets ([SVPG](https://www.svpg.com/)). Ses articles de 2025 et 2026 sur l'IA défendent la même thèse centrale que ce document : l'IA facilite la construction, mais le plus difficile reste de savoir quoi construire. L'idée que l'IA progresse d'abord là où le résultat se vérifie vient de Jason Wei et d'Andrej Karpathy. Le déplacement du goulot d'étranglement vers la revue du code est mesuré par Fiona Chen et James Stratton. Le Product Management comme nouveau goulot est défendu par Andrew Ng et par Ricardo Britto, qui propose aussi une vision d'ensemble du Product Management « nativement IA ». L'idée que les jeux d'évaluation deviennent une spécification circule chez des praticiens comme Lisa Murkin. Les notions de dette de compréhension et de dette d'intention viennent d'Addy Osmani. L'environnement de contrôle des agents, appelé harness, est décrit par Birgitta Böckeler. Ces travaux sont présentés aux chapitres concernés et analysés en annexe E.

Cagan écrit pour les entreprises dont les produits technologiques sont le cœur de métier, et sur la manière de décider quoi construire. Dans ses articles examinés, il ne traite ni de la vérification et de l'acceptation de changements produits par des agents, ni de la transmission d'un produit à un successeur, ni des permissions des agents, ni du cadre européen ; la conformité y apparaît comme une contrainte à connaître. Ce document se place surtout sur ce terrain, et en particulier sur les produits internes, réglementés ou industriels. Les positions de Cagan citées ici viennent des articles publiés sur le site de SVPG ; ses livres (INSPIRED, EMPOWERED, TRANSFORMED) sont mentionnés sans être cités directement.

Ce que le document propose en propre est plus limité : cinq distinctions tenues ensemble, une autorité d'acceptation assortie de conditions, un ancrage dans le cadre européen, et une « boucle inverse » de la spécification sous contrainte de confidentialité. Ces propositions sont présentées comme telles et n'ont été testées sur aucun projet.

Le texte publié le plus proche est celui de Ricardo Britto, chercheur chez Ericsson ([Britto, arXiv 2610.14823, 10 octobre 2026](https://arxiv.org/abs/2610.14823)). Il s'agit d'un article de vision, construit par synthèse de la littérature, sans données ; l'auteur indique que ses bénéfices attendus restent des propositions à évaluer. Les deux textes se recoupent sur plusieurs points : le décalage entre la vitesse de réalisation et la vitesse de décision, le maintien de la responsabilité humaine sur les choix qui engagent, une mémoire partagée du produit, et une répartition des tâches entre humains et IA selon l'incertitude, la réversibilité et les conséquences. Ils diffèrent par leur objet. Britto décrit l'IA comme participant permanent au travail du Product Management lui-même (veille, exploration, décision, apprentissage), avec six principes et des « personas » d'IA. Ce document traite surtout de ce qui se passe quand des agents réalisent le produit : transmission, spécification, preuve, acceptation et cadre européen. Les deux approches sont complémentaires ; les points de rencontre sont signalés dans les sections 3.2, 4.1, 4.2, 5.1, 7.1 et 8.1.

Une clé de lecture traverse le document. Cagan distingue « construire pour apprendre » (build to learn), en découverte, et « construire pour vendre » (build to earn), en livraison ([Build to Learn vs Build to Earn](https://www.svpg.com/build-to-learn-vs-build-to-earn/)). La partie 3 porte surtout sur le premier versant : décider ce qui mérite d'exister. Les parties 4 et 5 portent surtout sur le second, quand ce sont des agents qui construisent : transmettre, spécifier, prouver et accepter. La partie 2 montre que l'IA rend la réalisation presque gratuite en apparence, et la partie 7 que livrer et maintenir un produit restent coûteux.

### 1.6 Ce que le document ne couvre pas

Il ne traite pas du Product Management hors logiciel. Il ne donne pas d'avis juridique : les questions de droit sont signalées, pas tranchées. Il ne rapporte aucun banc d'essai réalisé pour l'occasion : aucun outil n'a été installé ni comparé en pratique.

---

## 2. Ce qui change

Trois déplacements ont lieu en même temps : les métiers construisent leurs propres outils, l'exécution s'automatise là où le résultat peut être évalué, et les fonctionnalités deviennent plus faciles à reproduire. Ils sont décrits séparément, parce qu'ils n'ont ni la même maturité ni le même niveau de preuve.

### Encadré : d'où viennent les distinctions de ce document

Les distinctions qui structurent ce document ne sont pas nouvelles. La plupart ont été formulées bien avant les agents IA, en génie logiciel, en facteurs humains, en économie ou en philosophie des sciences. Ce qui change, c'est leur coût relatif : l'IA rend certaines opérations très bon marché et laisse les autres au même prix.

| Distinction | Filiation principale | Ce que le document y ajoute |
|---|---|---|
| Développer avec l'IA, et développer un produit contenant de l'IA | Pas de tradition unique. La distinction répond à des débats récents de praticiens, par exemple l'idée que les jeux d'évaluation deviennent la spécification ([Murkin, 2026](https://www.mindtheproduct.com/evals-are-the-new-prd/)), qui vaut surtout pour un produit contenant de l'IA. | Elle sert à trier ces débats. |
| Vérifier une réalisation, et valider sa pertinence | Vérification et validation en génie logiciel ([Boehm, 1984](https://www.computer.org/csdl/magazine/so/1984/01/01695100/13rRUxD9h2X)) ; problème de l'oracle ([Barr et al., 2015](https://www.computer.org/csdl/journal/ts/2015/05/06963470/13rRUx0geBw)) ; règle du vérificateur ([Wei, 2025](https://www.jasonwei.net/blog/asymmetry-of-verification-and-verifiers-law)) et vérifiabilité ([Karpathy, 2025](https://karpathy.bearblog.dev/verifiability/)). | L'IA fait baisser fortement le coût de la vérification, pas celui de la validation. |
| Conformité à une spécification, et justesse de cette spécification | Exigences portant sur le monde réel ([Zave et Jackson, 1997](https://cse.msu.edu/~chengb/RE-491/Papers/dark-corners-re-zave-jackson.pdf)) ; logiciel de type E ([Lehman, 1996](https://www.cs.kent.edu/~jmaletic/cs63902/Papers/Lehman96.pdf)) ; contournement de spécification ([Krakovna et al., 2020](https://deepmind.google/discover/blog/specification-gaming-the-flip-side-of-ai-ingenuity/)) et loi de Goodhart. | Un agent peut établir la conformité à grande échelle ; il ne peut pas, avec les mêmes moyens, établir que les hypothèses sur le monde sont justes. |
| Résultat techniquement correct, et résultat compris, exploitable et maintenable | Programmation comme construction d'une théorie détenue par des personnes (Naur, 1985) ; preuve comme processus social ([De Millo, Lipton et Perlis, 1979](https://www.cs.umd.edu/~gasarch/BLOGPAPERS/social.pdf)) ; ironies de l'automatisation ([Bainbridge, 1983](https://ckrybus.com/static/papers/Bainbridge_1983_Automatica.pdf)) ; dette de compréhension ([Osmani, 2026](https://www.oreilly.com/radar/comprehension-debt-the-hidden-cost-of-ai-generated-code/)). | Comprendre et maintenir doivent être évalués séparément (section 4.1). |
| Construire pour apprendre, et construire pour vendre (découverte et livraison) | Modèle produit de Cagan : quatre risques (valeur, utilisabilité, faisabilité, viabilité) traités en découverte, puis livraison d'un produit de qualité commerciale ([Build to Learn vs Build to Earn](https://www.svpg.com/build-to-learn-vs-build-to-earn/), [Prototypes vs Products](https://www.svpg.com/prototypes-vs-products/)). | Quand des agents livrent, le versant « vendre » demande ses propres preuves : acceptation, transmission, conformité (parties 4 et 5). |
| Fait documenté, déclaration d'un acteur, hypothèse, recommandation | Convention de méthode du document. Elle rejoint les pratiques de gradation des preuves d'autres disciplines, que ce document ne détaille pas. | Dans un domaine où beaucoup de chiffres viennent des fournisseurs d'outils, le statut d'une affirmation fait partie de l'argument. |

Une autre filiation porte sur la responsabilité. La supervision humaine des systèmes automatisés a des limites connues : biais d'automatisation ([Parasuraman et Manzey, 2010](https://pubmed.ncbi.nlm.nih.gov/21077562/)), humain qui porte la faute sans avoir eu le contrôle ([Elish, 2019](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2757236)), efficacité non démontrée des obligations de supervision ([Green, 2022](https://www.benzevgreen.com/wp-content/uploads/2022/04/22-clsr.pdf)). L'autorité d'acceptation proposée à la section 5.2 s'appuie sur ces travaux.

Ces filiations sont des rapprochements entre domaines. Elles donnent un vocabulaire et des hypothèses, pas la preuve que les résultats observés ailleurs se reproduiront dans le logiciel. Deux points restent à vérifier : la formulation « construire le produit correctement, construire le bon produit », couramment attribuée à Boehm, doit être confirmée sur le texte de 1984 ; le texte de Naur n'a pas été relu et il est cité pour sa thèse générale ([notice Pascal-Francis](https://pascal-francis.inist.fr/vibad/index.php?action=getRecordDetail&idt=8553272)).

### 2.1 Les métiers construisent déjà

#### 2.1.1 Une continuité, pas une rupture

Les métiers ont toujours construit leurs outils. Un contrôleur de gestion qui monte un classeur Excel avec des macros, une juriste qui tient une base de clauses, un acheteur qui assemble un tableau croisé de fournisseurs : ce sont des logiciels, même si personne ne les appelle ainsi. Ce qui change avec les agents n'est pas le fait de construire. C'est la portée de ce qui est construit et la vitesse à laquelle cela se fait : un tableau de bord connecté à plusieurs sources, une automatisation qui envoie des courriels, une petite application web partagée.

Ce constat est documenté. La Cloud Security Alliance décrit des applications complètes construites par des équipes métier et déployées sur des plateformes approuvées, mais hors de toute gouvernance informatique ([CSA, juin 2026](https://labs.cloudsecurityalliance.org/wp-content/uploads/2026/06/CSA_research_note_vibe_coding_ai_governance_gap_20260602-csa-styled.pdf)). Le phénomène est mesuré surtout par des enquêtes déclaratives et des rapports d'analystes, pas par des études contrôlées. Les chiffres d'enquêtes de cabinets qui circulent sur ce sujet n'ont pas été vérifiés et ne servent pas d'argument ici (annexe H).

Une objection sérieuse doit être posée en face. Marty Cagan reprend l'analyse de Ben Evans : « most people and most companies aren't tool-builders… AI changes the thresholds but not the problem ». Selon eux, écrire le code n'est pas la partie difficile ; la partie difficile est de savoir qu'un outil doit exister, et comment ([Cagan, A Fresh Definition of the Product Role, août 2026](https://www.svpg.com/a-fresh-definition-of-the-product-role/)). Les deux constats sont compatibles. Le phénomène existe, mais son ampleur n'est pas mesurée, et il n'est pas établi que la majorité des personnes des métiers construiront. Ce document en tire une conséquence prudente : le sujet n'est pas que tout le monde construise, mais que ce qui est construit, même par quelques personnes, puisse être repéré, transmis et repris.

Cagan distingue aussi les produits internes et commerciaux. Un produit interne affronte les mêmes risques, mais avec un niveau d'exigence généralement plus bas : l'utilisateur n'a pas le choix d'un concurrent, la formation compense une partie des défauts d'utilisabilité, les exigences de charge sont modestes et le périmètre est étroit. Il note que les utilisateurs internes, libres de coder eux-mêmes leurs outils, deviennent une forme de concurrence pour les produits internes ([Cagan, Commercial vs Internal Products, avril 2026](https://www.svpg.com/commercial-vs-internal-products/)). Nos deux exemples sont internes ; l'outil de pilotage financier est exactement dans cette situation. Le seuil de passage vers un produit partagé doit donc être modulé : il est plus bas pour un outil interne, mais il ne disparaît pas, surtout quand les données sont réglementées ou que le logiciel touche à la sûreté.

#### 2.1.2 Ce que les agents réduisent, et ce qu'ils laissent

Frederick Brooks distinguait en 1987 deux sortes de complexité dans le logiciel. La complexité accidentelle tient aux outils et aux langages : la syntaxe, la configuration, la traduction d'une idée en instructions. La complexité essentielle tient à la conception elle-même : décider ce que le logiciel doit faire et comment ses concepts s'articulent. Brooks soutenait qu'aucune innovation isolée ne promet un gain d'un ordre de grandeur ([Brooks, 1987](https://www.cgl.ucsf.edu/Outreach/pc204/NoSilverBullet.html)).

Cette distinction éclaire la situation des métiers. Les agents réduisent surtout la complexité accidentelle : le contrôleur de gestion n'a plus besoin de savoir écrire une requête pour obtenir son tableau de bord. La complexité essentielle reste entière : quelle marge, calculée sur quelle base, avec quelles exclusions, à quelle date. Elle est simplement moins visible, parce que l'outil fonctionne avant que ces questions soient posées. (Hypothèse, appuyée sur une distinction classique.)

#### 2.1.3 Trois étages d'usage

Une grille de praticien distingue trois étages d'usage : la connaissance (chercher, résumer, expliquer), l'analyse (croiser des données, produire un éclairage) et la production (un outil qui agit ou dont d'autres dépendent). Elle ne vient pas d'une étude. Elle est utile parce qu'elle nomme un risque : sauter les étages, c'est-à-dire mettre en production un outil qui n'a été éprouvé qu'en mode exploratoire.

Le même article rapportait deux incidents types. Un tableau de bord financier aurait affiché pendant six mois un chiffre légèrement faux, parce que sa requête interrogeait une table avant retraitement. Un assistant juridique aurait inventé une clause dans un accord de confidentialité relu trop vite. Ces cas sont rapportés, non vérifiés, et ils ne disent rien de la fréquence de tels incidents. Ils illustrent toutefois deux questions qui reviendront : quelle donnée fait foi, et qui valide un contenu à portée contractuelle ?

#### 2.1.4 Le vrai problème : transmission et responsabilité

Le problème n'est donc pas que les métiers créent. C'est ce qui se passe quand l'outil survit à l'intention de son créateur : il est partagé, d'autres en dépendent, et son créateur change de poste. Trois limites apparaissent alors. L'outil ne figure dans aucun inventaire. Sa maintenance repose sur une seule personne. Et selon les données traitées, il peut entrer dans le champ du RGPD, de NIS2 ou du règlement européen sur la cyberrésilience (CRA) sans que personne l'ait évalué.

Dans notre premier exemple, le tableau de bord du contrôleur de gestion change de nature le jour où la direction financière s'en sert pour arbitrer des budgets. Il n'a pas changé de code. Il a changé de statut : d'outil personnel, il est devenu un produit partagé.

Recommandations :
- distinguer le développement par les métiers dans un cadre prévu (souvent appelé citizen development) des outils construits hors cadre (shadow AI) ;
- tenir un inventaire des outils construits par les métiers, avec un responsable identifié et un niveau de criticité ;
- définir un seuil de passage d'un outil personnel à un produit partagé, fondé sur le nombre d'utilisateurs, la criticité des décisions qu'il soutient et les contraintes réglementaires.

#### 2.1.5 L'outil métier comme produit de découverte

Un outil construit par le métier n'est pas seulement un risque à contenir. Il peut jouer le rôle d'un produit de découverte : il montre un besoin réel, une règle de gestion que le produit industrialisé ne couvre pas, ou une manière de travailler plus fluide. La connaissance qu'il a permis d'acquérir peut ensuite être transférée dans le produit cœur, si ce transfert apporte de la fluidité à l'entreprise. (Observation de terrain.)

La recherche sur l'informatique gérée par les métiers va dans ce sens. Une étude configurationnelle distingue quatre devenirs d'un outil métier une fois qu'il a été repéré : l'arrêt, le remplacement par une solution officielle, la reprise par la DSI, ou le maintien sous la responsabilité du métier ([Business & Information Systems Engineering, 2020](https://link.springer.com/article/10.1007/s12599-020-00635-2)). Une autre étude, fondée sur des entretiens avec 29 responsables informatiques, trouve que ces outils sont jugés positifs lorsqu'ils sont alignés avec la DSI et limités à des besoins locaux, et négatifs lorsqu'ils ne sont pas alignés et deviennent permanents ([Kopper et al., 2020](https://ideas.repec.org/a/spr/infsem/v18y2020i2d10.1007_s10257-020-00472-6.html)). Ces travaux portent sur l'informatique d'avant les agents ; ils ne mesurent pas encore l'effet de l'IA générative sur ces trajectoires.

Le transfert vers le produit cœur ne consiste pas à reprendre le code de l'outil. Il consiste à reprendre ce que l'outil a appris : les règles validées, les cas limites, les décisions et leurs raisons, c'est-à-dire le contenu des fichiers de connaissance décrits à la section 4.1. La boucle inverse de la section 4.2 (partir de ce qui existe pour décrire le comportement, puis décider de la cible) s'applique ici à l'échelle d'un outil métier.

Recommandations :
- à chaque revue de l'inventaire, choisir explicitement l'un des quatre devenirs pour chaque outil ;
- lorsqu'un outil sert de découverte, documenter ce qu'il a appris avant de décider de sa reprise ;
- ne transférer dans le produit cœur que les règles validées par une personne identifiée, pas les contournements.

Ce mouvement a un équivalent dans les entreprises de logiciel. Cagan décrit le modèle des « forward deployed engineers », des ingénieurs placés chez les clients pour comprendre leurs problèmes et y répondre par des prototypes, tandis qu'une équipe de plateforme repère ce qui se répète d'un client à l'autre et le généralise dans le produit. Il en signale le risque : accumuler des milliers de solutions sur mesure à maintenir ([Cagan, Forward Deployed Engineers, septembre 2025](https://www.svpg.com/forward-deployed-engineers/)). L'outil métier comme produit de découverte suit la même logique à l'intérieur d'une entreprise, avec le même risque si personne ne fait le travail de généralisation.

Le rôle du Product dans cette situation n'est pas de filtrer. Il est d'aider à décider ce qui reste local, ce qui doit devenir un produit partagé et ce qui doit être arrêté. Cette question devient plus difficile à mesure que la production s'accélère, ce qui conduit au deuxième déplacement.

### 2.2 L'exécution s'automatise là où l'évaluation est possible

#### 2.2.1 Ce que l'on sait des gains de productivité

Les mesures disponibles sont contrastées, et elles ne portent pas toutes sur la même chose. Les classer est la première précaution.

| Étude | Outil mesuré | Niveau | Indicateur | Résultat |
|---|---|---|---|---|
| Cui et al., trois essais contrôlés en entreprise, 4 867 développeurs ([SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4945566)) | Assistant de complétion | Individu | Tâches terminées | +26,08 % (erreur type 10,3 %), gains plus forts chez les moins expérimentés |
| METR, essai contrôlé de 2025, développeurs expérimentés sur leurs propres projets open source ([METR, février 2026](https://metr.org/blog/2026-02-24-uplift-update/)) | Outils IA de début 2025 | Individu | Temps de réalisation | +19 % de temps (intervalle de +2 % à +39 %) |
| METR, mise à jour de février 2026 (même source) | Outils de fin 2025 | Individu | Temps de réalisation | Estimations brutes de −18 % et −4 %, jugées non fiables par METR à cause de biais de sélection |
| Chen et Stratton, données de 718 entreprises et 725 938 travailleurs ([PDF des auteurs, version du 4 août 2026](https://fion.ac/jellyfish.pdf)) | Agents de code | Travailleur et entreprise | Code, commits, tickets, délais | Code ajouté +30 %, commits +20 %, pull requests +23 % ; tickets résolus sans hausse significative |
| Faros AI, télémétrie de plus de 10 000 développeurs ([Faros AI, juillet 2025](https://www.faros.ai/blog/ai-software-engineering)) | Outils IA, forte adoption | Équipe et entreprise | Tâches, pull requests, revue | Tâches +21 %, pull requests +98 %, temps de revue +91 %, pas d'effet significatif au niveau de l'entreprise |

Deux lectures s'imposent. D'abord, aucun multiplicateur général de productivité n'est défendable : les résultats dépendent de l'outil, de l'expérience, de la tâche et du niveau mesuré. Ensuite, les études les plus récentes, qui portent sur des agents, montrent une hausse nette de la production de code sans hausse comparable du travail livré au sens des tickets résolus. Chen et Stratton observent aussi que le délai de fusion d'une pull request augmente de 3,45 jours, sur une base de 7,03 jours, et que la part des demandes de modifications pendant la revue augmente de 11,84 points, sur une base de 13 %. (Faits documentés ; l'étude de Chen et Stratton est un document de travail, et l'étude Faros vient d'un éditeur d'outils et repose sur des corrélations.)

Les données déclaratives vont dans le même sens. Selon une enquête de l'éditeur Sonar, 96 % des développeurs ne font pas entièrement confiance au code généré pour être correct, mais seulement 48 % le vérifient toujours avant de l'intégrer ([Sonar, octobre 2026](https://www.sonarsource.com/company/press-releases/sonar-data-reveals-critical-verification-gap-in-ai-coding/)). Une enquête n'établit pas une causalité, mais elle signale un écart entre la défiance exprimée et la vérification pratiquée.

#### 2.2.2 Une seconde dimension : pouvoir évaluer le résultat

La difficulté d'une tâche pour un humain ne suffit pas à prévoir son automatisation. Une autre dimension compte : la possibilité d'évaluer, vite et de façon fiable, ce qu'une machine produit.

Jason Wei, chercheur qui a travaillé sur les méthodes de raisonnement des grands modèles, décrit une asymétrie entre production et vérification. Certaines solutions sont longues à trouver mais simples à contrôler, comme une grille de sudoku remplie. Il en tire une « règle du vérificateur » : la facilité d'entraîner une IA à une tâche serait proportionnelle à la facilité de vérifier ses résultats. Il cite cinq propriétés favorables : une vérité objective sur ce qu'est une bonne solution, une vérification rapide, possible à grande échelle, peu bruitée, et capable de classer plusieurs solutions entre elles ([Wei, juillet 2025](https://www.jasonwei.net/blog/asymmetry-of-verification-and-verifiers-law)). Andrej Karpathy formule une thèse voisine : le logiciel classique automatise ce que l'on sait spécifier, les réseaux entraînés automatisent ce que l'on sait vérifier. Il définit une tâche vérifiable par trois propriétés : un environnement que l'on peut réinitialiser, des essais peu coûteux, une récompense calculable automatiquement ([Karpathy, novembre 2025](https://karpathy.bearblog.dev/verifiability/)).

Ces deux textes sont des opinions argumentées de chercheurs, issues de leur expérience de l'apprentissage par renforcement, c'est-à-dire de l'entraînement d'un modèle par essais et récompenses. Ce ne sont ni des lois démontrées ni des prévisions sur l'emploi. Wei reconnaît lui-même que certaines tâches sont presque aussi coûteuses à vérifier qu'à produire, et d'autres plus coûteuses.

Le génie logiciel connaît ce problème depuis longtemps sous un autre nom : le problème de l'oracle. Un oracle de test est le mécanisme qui permet de dire si un comportement observé est correct. Le problème de l'oracle est la difficulté, souvent le coût, d'en disposer ([Barr et al., 2015](https://www.computer.org/csdl/journal/ts/2015/05/06963470/13rRUx0geBw), notice consultée, texte intégral non relu). Le domaine a développé des réponses partielles : vérifier l'absence de plantage, tester des propriétés générales, comparer deux exécutions liées plutôt que connaître la bonne réponse, faire appel à un jugement humain. Dire qu'une tâche est « vérifiable », c'est dire qu'un oracle bon marché existe pour elle.

Deux nuances limitent la portée de cette grille. La première est ancienne : en 1979, De Millo, Lipton et Perlis soutenaient qu'une preuve est acceptée parce qu'une communauté la lit et la discute, et que « verifiability is not and cannot be a dominating concern in software design » ([De Millo, Lipton et Perlis, 1979](https://www.cs.umd.edu/~gasarch/BLOGPAPERS/social.pdf)). Leur position a été vivement contestée ; elle rappelle que vérifier n'est pas la seule fonction d'une preuve. La seconde nuance concerne le sens de l'asymétrie. Pour une réponse fermée, vérifier est plus facile que produire. Pour un texte libre, comme une analyse de marché, une synthèse d'entretiens ou une spécification en prose, c'est souvent l'inverse : produire est devenu peu coûteux, et contrôler chaque affirmation reste long. Une grande partie des livrables du Product Management sont de cette seconde sorte.

#### 2.2.3 Analyser les activités, pas les métiers

Cette grille invite à décomposer les activités plutôt qu'à classer les professions. Vérifier qu'une exigence respecte un gabarit a un retour immédiat. Mesurer l'effet d'une fonctionnalité sur un usage demande une observation en exploitation. Choisir un positionnement ne s'évalue qu'imparfaitement, sur une longue durée, et rarement deux fois dans les mêmes conditions. Une activité facile à vérifier mais coûteuse en cas d'échec et irréversible ne doit pas être déléguée sur la seule base de sa vérifiabilité (section 5.1). Une grille en six dimensions, proposée et non validée, figure en annexe F.

Les annonces de l'automne 2026 en mathématiques sont souvent citées comme preuve que « tout ce qui est vérifiable sera automatisé ». Elles montrent un changement d'échelle de la production de résultats là où un vérificateur formel existe. Elles ne montrent pas que cette capacité se transpose au développement d'un produit, dont l'énoncé se découvre en chemin. L'analyse détaillée du cas figure en annexe G.

#### 2.2.4 Le déplacement de la rareté

Si la production de code accélère plus vite que la capacité à l'évaluer, la ressource rare se déplace. Elle passe de l'écriture à l'évaluation : relire, tester, comparer, décider si le résultat convient. Les données de Chen et Stratton et de Faros en donnent les premiers signes mesurés. Elles ne permettent pas de dire jusqu'où ce déplacement ira.

Le développement produit prend alors la forme d'une boucle : un besoin exprimé, des agents qui réalisent, des preuves qui permettent d'accepter ou de refuser le résultat, puis un retour d'usage qui modifie le besoin. Dimensionner la revue et la preuve devient une décision partagée entre le Product, l'ingénierie et le métier. Ce n'est pas seulement une affaire d'ingénierie, parce que le niveau de preuve exigé dépend des conséquences d'une erreur, et ces conséquences se jugent du côté de l'usage.

Si l'automatisation progresse d'abord là où le résultat se contrôle, une conséquence suit pour les produits eux-mêmes : une fonctionnalité dont le comportement est observable et comparable devient plus facile à reproduire.

### 2.3 Les fonctionnalités deviennent reproductibles

#### 2.3.1 Trois voies de reconstitution

Un logiciel peut aujourd'hui être reconstitué par trois voies, qui ne demandent pas le même accès.

Depuis le code source, des agents peuvent extraire les règles implémentées, les dépendances et les exceptions. C'est la voie habituelle des projets de modernisation (section 6.1).

Depuis les binaires et le comportement, un agent peut orchestrer des outils d'analyse existants. MindStudio présente ainsi Reverse Engineer Anything (REA) comme un serveur MCP, c'est-à-dire une interface standard entre un agent et des outils, qui donne accès à des logiciels d'analyse comme Ghidra, IDA ou les outils de développement de Chrome. Selon l'article, l'agent analyse le logiciel, reçoit du pseudocode, des éléments de preuve et des inconnues, formule des hypothèses, écrit une implémentation, la compare à l'original et recommence ([MindStudio, octobre 2026](https://www.mindstudio.ai/blog/reverse-engineer-anything-mcp)). L'article décrit un essai informel de reconstruction de fonctions de l'application Aperçu sur Mac ; les deux versions ont fonctionné, et l'agent sans REA a terminé avant celui qui l'utilisait. Il s'agit du compte rendu d'un fournisseur, sans protocole contrôlé, qui ne permet d'établir ni un gain général ni une aptitude à reconstruire des systèmes critiques.

Depuis l'information publique et l'observation, enfin, un produit peut être reconstruit sans accès à son code ni à ses binaires. Le cas ArtCraft en est l'exemple le plus documenté. Ses applications, dont PhotoCraft, VectorCraft et FilmCraft, sont présentées par leur site comme étant en « early alpha » ou « in development » ([ArtCraft](https://getartcraft.com/apps)). Gizmodo rapporte qu'elles ont été construites en Rust avec un modèle d'Anthropic et décrit un essai où des opérations simples étaient utilisables, mais où une fonction de transformation avait un comportement imprévisible ([Gizmodo](https://gizmodo.com/someone-vibe-coded-a-free-knockoff-of-adobe-creative-suite-2000823322)). La documentation de PhotoCraft revendique une réimplémentation indépendante à partir de spécifications publiques et de comportements observés, sans code ni ressources propriétaires ([PhotoCraft](https://github.com/storytold/photocraft)). Les instructions de FilmCraft destinées aux agents interdisent de lire, désassembler ou copier le contenu des applications Adobe, et autorisent l'observation par l'utilisation ([instructions FilmCraft](https://github.com/storytold/filmcraft/blob/main/AGENTS.md)). Ce sont des règles déclarées par le projet, pas un audit de leur respect.

D'autres cas vont dans le même sens. Une chronique de The Register signale des clones de Microsoft Office et d'Adobe Creative Suite écrits en Rust, en pré-alpha, incomplets, et d'une légalité incertaine ([The Register, 19 octobre 2026](https://www.theregister.com/columnists/2026/10/19/ais-epic-cash-call-is-matched-only-by-its-ability-to-strangle-revenue-streams/5303493)). Le cabinet Taylor Wessing analyse la réécriture d'une bibliothèque open source, chardet, générée en environ cinq jours, avec moins de 1,3 % de similarité structurelle avec la version précédente ; le statut juridique du code généré reste incertain dans l'Union européenne et aux États-Unis ([Taylor Wessing, juin 2026](https://www.taylorwessing.com/en/insights-and-events/insights/2026/06/ai-and-assisted-programming-in-open-source)). METR et Epoch AI rapportent des résultats préliminaires où des agents mènent certaines tâches de plusieurs semaines, dont la réimplémentation d'une base de 16 000 lignes ([METR, avril 2026](https://metr.org/blog/2026-04-10-mirrorcode-preliminary-results/)) ; le détail de la méthode n'a pas été relu.

#### 2.3.2 Ce que ces voies produisent

Aucune de ces voies ne produit l'intention. Elles produisent une description du comportement : ce que le logiciel fait sur les entrées observées. Les fonctions cachées, les exceptions rares et surtout les raisons d'un comportement restent inconnues. Un calcul arrondi d'une certaine manière peut traduire une règle fiscale, un contournement d'un ancien défaut ou une simple habitude. Le code, le binaire ou la vidéo ne disent pas lequel.

Il faut aussi distinguer la couverture apparente de l'aptitude réelle. Une fonction visible dans un menu n'est pas une fonction validée dans un travail réel. PhotoCraft le dit lui-même : il ne remplace pas encore Photoshop dans un travail professionnel quotidien, et raccorder les menus à des commandes mesure leur raccordement, pas leur comportement ([PhotoCraft](https://github.com/storytold/photocraft)). FilmCraft distingue de même l'étendue des fonctions et l'aptitude au travail réel, et documente des lacunes de compatibilité ([FilmCraft](https://github.com/storytold/filmcraft)). Aucun test pratique de ces applications n'a été réalisé pour ce document, et la part exacte des vidéos ou des captures dans leur construction n'est pas établie.

#### 2.3.3 Pourquoi la valeur se déplace

L'économie donne un fondement à ce déplacement, au lieu de simplement l'affirmer. David Autor montre que l'automatisation remplace certaines tâches mais en complète d'autres, dont elle augmente la valeur ; il s'appuie sur le paradoxe de Polanyi, selon lequel nous savons faire beaucoup de choses que nous ne savons pas expliciter ([Autor, 2015](https://jenni.uchicago.edu/econ341/readings/Autor_2015_JEP_v29_n3.pdf)). Michael Kremer montre que, quand une production enchaîne des tâches dont chacune peut faire échouer l'ensemble, la qualité de chaque maillon a un effet multiplicatif sur le résultat ([Kremer, 1993](https://ideas.repec.org/a/oup/qjecon/v108y1993i3p551-575..html)). Agrawal, Gans et Goldfarb décrivent l'IA comme une baisse du coût de la prédiction, dont le jugement, c'est-à-dire l'évaluation de ce que vaut chaque résultat possible, est le complément ([Agrawal, Gans et Goldfarb, NBER](https://www.nber.org/papers/w24243)).

Appliqués au logiciel, ces trois cadres suggèrent la même chose : quand écrire et reproduire du code devient bon marché, les tâches complémentaires (décider, évaluer, intégrer, maintenir) deviennent le maillon qui détermine le résultat. Le paradoxe de Polanyi explique aussi pourquoi la pertinence est difficile à spécifier : une partie du savoir métier est tacite. (Hypothèse appuyée sur des cadres établis ; ces cadres n'ont pas été testés sur le développement par agents.)

Ces trois déplacements posent quatre questions, qui structurent la suite : que vaut un produit (partie 3), que faut-il transmettre (partie 4), comment réaliser et prouver (partie 5), et dans quelles trajectoires, quelle organisation et quel cadre (parties 6 à VII).

---
## 3. Ce que vaut un produit

Si l'interface et les fonctions se reproduisent plus facilement, la question de la valeur se pose autrement. Elle ne porte plus sur ce qu'un produit contient, mais sur ce qu'il permet d'accomplir de façon fiable, pour qui, et à quel coût total.

### 3.1 La valeur durable quand la copie est facile

#### 3.1.1 Une substitution partielle peut suffire

L'hypothèse stratégique importante n'est pas qu'un concurrent doive reproduire toute une suite logicielle pour devenir utile. Un ensemble limité de tâches, réalisé avec une qualité suffisante pour un segment donné et à un coût complet acceptable, peut suffire. Une personne qui prépare occasionnellement une image, une équipe qui automatise une opération répétitive et un studio qui livre des projets complexes ne constituent pas le même scénario d'acceptation. (Hypothèse ; ces trois segments sont illustratifs.)

Deux conclusions extrêmes sont donc prématurées : « le clone ressemble au produit, donc il le remplace », et « il lui manque des fonctions professionnelles, donc il ne menace aucun usage ». Le travail du Product Manager consiste à chercher le seuil de suffisance par segment, sans présumer ni la réussite du nouvel entrant ni l'immunité de l'éditeur installé.

#### 3.1.2 À quel niveau parle-t-on de remplacement ?

Dire qu'un produit « en remplace » un autre suppose un niveau de preuve. Nous proposons d'en distinguer trois : une tâche isolée acceptée (l'utilisateur a obtenu le résultat voulu une fois), un travail réel accompli de bout en bout (import, édition, export, échange avec des tiers, reprise après erreur), et une exploitation continue (le produit tient dans la durée, avec ses mises à jour, ses incidents et son support). La plupart des démonstrations publiques se situent au premier niveau. Les décisions d'achat se prennent au deuxième ou au troisième. (Recommandation.)

#### 3.1.3 Où chercher une valeur plus durable

Plutôt qu'un avantage unique, nous proposons d'examiner séparément plusieurs composantes, chacune avec sa preuve. Leur importance dépend du segment et du coût d'une erreur.

| Composante | Question à vérifier auprès du client | Preuve à rechercher |
|---|---|---|
| Fonctions et ergonomie | Le travail peut-il être accompli sans effort inutile ? | Tâches réalisées, temps, erreurs d'utilisation |
| Correction et fiabilité | Le résultat est-il juste et reproductible ? | Cas de référence indépendants, défauts, pertes de données |
| Compatibilité | Les fichiers, historiques et échanges restent-ils exploitables ? | Import et export aller-retour, pertes explicites |
| Profondeur métier | Les cas importants pour ce segment sont-ils couverts ? | Parcours complexes validés avec des spécialistes |
| Intégration et collaboration | Le produit s'insère-t-il dans le travail collectif ? | Parcours de bout en bout, droits, échanges entre outils |
| Exploitation et responsabilité | Qui corrige un incident, avec quel engagement ? | Support observé, délais, sauvegarde et reprise |
| Données et ressources | Ces ressources, accessibles légalement, améliorent-elles le résultat pour ce client ? | Mesure d'utilité et droits d'usage, pas simple volume détenu |
| Coût et facilité de sortie | Le service est-il utile sans dépendance disproportionnée ? | Coût complet, export utilisable, effort de migration |

Cette grille sépare une valeur que le client souhaite conserver d'un coût de sortie qu'il subit. Un format fermé ou une migration difficile ne sont pas des qualités produit. Ils retiennent le client, mais ils ne le servent pas, et ils protègent moins à mesure que la reproduction devient plus facile. Inversement, la familiarité des commandes peut réduire l'apprentissage ; elle mérite d'être testée, sans supposer qu'elle règle la compatibilité ou la fiabilité.

#### 3.1.4 Si l'agent devient l'interface

PhotoCraft et FilmCraft exposent un même moteur de commandes par leur interface graphique, par une interface en ligne de commande et par un serveur MCP ([PhotoCraft](https://github.com/storytold/photocraft), [FilmCraft](https://github.com/storytold/filmcraft)). Ces produits sont donc conçus pour être pilotés par des agents. Cela ne prouve pas la fiabilité d'une automatisation complète, mais ouvre une question distincte de l'imitation d'interface.

Notre hypothèse est qu'un utilisateur pourrait choisir un moteur pour la qualité de ses résultats et de son automatisation, même s'il utilise peu son interface graphique. Pour le Product Manager, cela conduit à traiter les contrats de commandes, les permissions, les messages d'erreur, la reprise et la traçabilité comme des composantes du produit, au même titre que l'écran. Cela ne présume pas la disparition des interfaces humaines.

#### 3.1.5 Remplacer une question par une évaluation

Nous proposons de remplacer la question « combien de fonctions le concurrent a-t-il copiées ? » par une évaluation de substitution sur des tâches réelles. Le protocole sert aussi bien à l'éditeur installé qu'au nouvel entrant :

- choisir un segment, des utilisateurs et des tâches représentatives, et définir ce qui rend un résultat acceptable ou inutilisable ;
- observer la réalisation de bout en bout, y compris l'import, l'export, les échanges avec des tiers et la reprise après erreur ;
- mesurer le taux de tâches acceptées, le temps total, les corrections, les pertes de fidélité, les incidents et l'effort de migration ;
- intégrer au coût la formation, le support, l'hébergement ou l'inférence, la validation et la maintenance, car un téléchargement gratuit n'a pas un coût d'exploitation nul ;
- décider ensuite ce qu'il faut continuer à développer, intégrer, simplifier, acheter ou abandonner.

La thèse qui en découle reste à éprouver : la valeur durable ne réside ni nécessairement dans le secret du code ni dans l'accumulation des fonctions, mais dans la capacité à rendre un travail utile, fiable et économiquement acceptable pour un segment, puis à maintenir cette capacité quand ses besoins changent.

### 3.2 Décider reste le cœur du Product Management

#### 3.2.1 Ce qui ne change pas

Le Product Management a toujours eu pour finalité de choisir les problèmes à résoudre, d'arbitrer la valeur, de définir un périmètre et de mesurer les effets. Ces fonctions ne sont pas nouvelles. Ce qui change, c'est qu'elles ne peuvent plus se cacher derrière la coordination de la réalisation, puisque celle-ci est en partie absorbée par les agents.

Marty Cagan formule ce point de la façon la plus nette : « AI makes building easier, but the hardest part remains knowing what to build », et il n'a jamais été aussi facile de « run 10 times faster in the wrong direction » ([Cagan, The AI Productivity Paradox, juillet 2026](https://www.svpg.com/the-ai-productivity-paradox/)). Il cite à l'appui une enquête selon laquelle 89 % des dirigeants disent que l'IA a accéléré le travail, mais 6 % seulement se disent capables de montrer un retour sur investissement à l'échelle de l'organisation ; la source primaire de ce chiffre n'a pas été vérifiée. Andrew Ng rapporte que certaines équipes conçues autour de l'IA passent d'un ratio de huit ingénieurs par Product Manager à un pour un, le goulot se déplaçant vers la définition du produit, le design, le marketing et la conformité ; il limite son propos aux équipes de deux à dix personnes ([Ng, avril 2026](https://x.com/AndrewYNg/status/2048793852702757151)). Ricardo Britto écrit que les organisations « may realize software faster than they can identify, qualify, and reconsider what should be realized » ([Britto, octobre 2026](https://arxiv.org/abs/2610.14823)). Il en tire une vision où l'IA participe en permanence au travail produit, tandis que les Product Managers restent responsables d'interpréter des éléments ambigus, de cadrer la direction du produit, de faire les arbitrages qui engagent et d'en assumer la responsabilité. Le premier texte est une opinion fondée sur des observations, le second un article de vision sans données. Ng place d'ailleurs le goulot dans plusieurs fonctions, pas seulement dans le Product Management, ce qui conforte l'idée d'activités collectives plutôt que d'un rôle unique.

#### 3.2.2 Quatre risques, répartis entre plusieurs fonctions

Le cadre le plus utilisé pour organiser ce travail est celui des quatre risques de Cagan : la valeur (les clients voudront-ils l'utiliser ou l'acheter), l'utilisabilité (sauront-ils l'utiliser), la faisabilité (peut-on le construire et l'exploiter) et la viabilité (la solution fonctionne-t-elle pour l'entreprise : coûts, ventes, juridique, conformité). Le Product Manager y prend la responsabilité de la valeur et de la viabilité ; le design porte l'utilisabilité, l'ingénierie la faisabilité ([Cagan, The Era of the Product Creator, mai 2025](https://www.svpg.com/the-era-of-the-product-creator/)). Cette répartition rejoint le principe de ce document : le Product Management ne porte pas seul l'ensemble.

Cagan reconnaît avoir longtemps sous-estimé la viabilité, qui n'est devenue un risque distinct qu'à la seconde édition d'INSPIRED, et il la juge de plus en plus centrale avec l'IA : coûts, monétisation, responsabilité, éthique ([Cagan, Strong Opinions, Loosely Held, septembre 2026](https://www.svpg.com/strong-opinions-loosely-held/)). C'est sur ce risque que l'étude de marché et le contexte business présentés plus bas prennent leur importance.

Ce document ajoute un point que le cadre des quatre risques ne traite pas directement. Quand des agents réalisent, la faisabilité ne se réduit plus à « peut-on le construire » : elle inclut « peut-on prouver que ce qui a été construit est correct, et le transmettre » (parties 4 et 5).

#### 3.2.3 Les distinctions à maintenir

Le travail de décision consiste pour une large part à tenir séparées des choses que la vitesse tend à confondre :

- le besoin réel et la solution proposée ;
- le comportement existant et le comportement souhaité ;
- l'hypothèse et la règle approuvée ;
- le résultat généré et le résultat vérifié ;
- l'outil local et le produit partagé ;
- la capacité de reproduire un comportement et la valeur de reconstruire un produit.

#### 3.2.4 Vérifier une réalisation, valider sa pertinence

Vérifier une réalisation, c'est établir qu'elle fait ce qui était demandé. Valider sa pertinence, c'est établir que ce qui était demandé valait la peine d'être fait. La distinction est classique en génie logiciel, où elle est associée à Barry Boehm ([Boehm, 1984](https://www.computer.org/csdl/magazine/so/1984/01/01695100/13rRUxD9h2X), notice consultée). L'apport de ce document n'est pas la distinction elle-même. C'est le constat que l'IA fait baisser fortement le coût de la vérification, par les tests, l'analyse statique ou la vérification formelle, et pas celui de la validation. Les outils qui vérifient ne choisissent pas le problème à résoudre.

Une réalisation conforme peut donc répondre à la mauvaise question, et plus la réalisation est rapide, plus ce risque pèse. Accélérer la production augmente l'importance de ce qui la précède et la suit : définir le comportement attendu, identifier les situations dangereuses, choisir les preuves nécessaires et décider si elles suffisent.

Un biais propre aux modèles complique la validation. Sharma et ses coauteurs montrent que cinq assistants de pointe ont tendance à approuver l'avis de l'utilisateur plutôt que la réponse exacte, et que les préférences humaines utilisées pour leur entraînement favorisent en partie ce comportement ([Sharma et al., arXiv 2310.13548](https://arxiv.org/abs/2310.13548)). Un Product Manager qui demande à un modèle d'évaluer son hypothèse, ses personas ou sa priorisation risque d'obtenir une confirmation. L'IA utilisée pour valider une décision n'est pas un contradicteur neutre. Britto fait une mise en garde voisine : plusieurs personas d'IA peuvent sembler élargir l'analyse tout en produisant un raisonnement semblable, si elles reposent sur les mêmes modèles ou le même contexte ; la diversité des personas ne prouve pas l'indépendance du raisonnement ([Britto](https://arxiv.org/abs/2610.14823)). Recommandations : formuler les demandes sans révéler la réponse attendue, demander explicitement les arguments contraires, confronter les conclusions à des données d'usage réelles.

#### 3.2.5 Discovery et validation

Les agents peuvent synthétiser des tickets de support, des transcriptions d'appels, des enquêtes ou des données d'usage, et en tirer des hypothèses. Aucune évaluation suffisamment étayée, dans les sources examinées, ne montre qu'ils améliorent la découverte du besoin auprès des utilisateurs. Ils produisent des hypothèses, pas des preuves d'adoption. Les entretiens, les prototypes et l'expérimentation restent nécessaires ; les agents peuvent les accélérer, pas les remplacer.

Les prototypes sont l'endroit où l'IA change le plus la découverte. Cagan indique qu'une équipe peut produire 10 à 20 prototypes ou itérations par semaine, ce qui était possible avant l'IA générative mais est désormais à la portée de presque tous, et que des prototypes sur données réelles peuvent être mis devant des utilisateurs choisis beaucoup plus tôt ([Build to Learn vs Build to Earn](https://www.svpg.com/build-to-learn-vs-build-to-earn/)). Il met aussi en garde : un prototype de haute fidélité n'est pas un produit, et il fait sous-estimer le travail restant (section 6.1).

Deux corrections de Cagan sur sa propre doctrine méritent d'être reprises. Il regrette d'abord que beaucoup d'équipes se soient enfermées dans la découverte du problème, en cherchant à savoir s'il s'agit du « problème le plus important », question qu'il juge sans réponse, au détriment de la découverte de la solution. Il estime ensuite que la question la plus féconde n'est pas « pourquoi travaillons-nous sur ce problème » mais « why are people using, or not using, our product? », c'est-à-dire les raisons de l'usage et de l'abandon ([Strong Opinions, Loosely Held](https://www.svpg.com/strong-opinions-loosely-held/)). Pour ce document, la validation de la pertinence ne doit donc pas devenir un contrôle préalable sans fin ; elle se poursuit après la livraison, par l'observation de l'usage.

#### 3.2.6 L'étude de marché assistée par l'IA

L'IA change l'ampleur de ce qu'un Product Manager peut instruire seul avant de s'engager. En quelques sessions de recherche approfondie, il peut croiser des questions qu'il ne pouvait auparavant qu'effleurer. Pour un logiciel destiné à des points de vente, par exemple :
- combien de magasins existent dans un pays, et combien sont en situation d'envisager une solution logicielle ;
- quel est le modèle économique de ces magasins, et peuvent-ils investir ;
- sont-ils habitués à payer un abonnement ou préfèrent-ils acheter ;
- quelles sont les habitudes des utilisateurs, par exemple travailler sur smartphone et échanger par WhatsApp plutôt que sur un écran d'ordinateur ;
- quelles solutions concurrentes existent, et avec lesquelles le produit peut s'intégrer, sous forme de tableaux croisés de fonctionnalités ;
- enfin, une synthèse de toutes les sessions exportées, demandée à un modèle de grande taille.
(Observation de terrain.)

L'exemple des habitudes doit être vérifié pour chaque segment. L'application WhatsApp Business dépassait 200 millions d'utilisateurs mensuels en juin 2023, selon Meta ([TechCrunch, juin 2023](https://techcrunch.com/2023/06/27/whatsapp-business-crosses-200m-maus-introduces-personlized-messages-feature/)) ; ce chiffre mondial ne dit rien des commerçants d'un pays donné.

Les limites mesurées sont sérieuses, et elles portent précisément sur ce type de travail :
- dans le banc d'évaluation LiveResearchBench, l'analyse de marché est le domaine où tous les systèmes de recherche approfondie produisent le plus d'affirmations non étayées par leurs sources ([LiveResearchBench](https://arxiv.org/html/2510.14240v5)) ;
- l'audit DeepTRACE trouve des réponses souvent univoques et assurées, avec une exactitude des citations comprise entre 40 et 80 % selon les systèmes ([DeepTRACE](https://arxiv.org/html/2509.04499v1)) ;
- les répondants simulés par un modèle (synthetic respondents) reproduisent des tendances générales, mais surestiment les attitudes positives, surtout envers les marques connues, et varient moins que de vrais répondants ([NIM, 2026](https://www.nim.org/en/publications/detail/leaving-insight-to-digital-twins)) ;
- un consentement à payer généré par un modèle peut paraître économiquement plausible tout en conduisant à des décisions de prix sensiblement différentes de celles tirées de données réelles ([Journal of Marketing Analytics, 2026](https://link.springer.com/article/10.1057/s41270-026-00542-7)) ; des travaux antérieurs avaient obtenu des ordres de grandeur réalistes sur des produits de grande consommation ([Brand, Israeli et Ngwe, HBS](https://www.hbs.edu/ris/Publication%20Files/23-062_1f58623a-ee21-44b9-a262-276047bc5543.pdf)).

L'étude de marché assistée produit donc un contexte business plus large et plus rapide à constituer, mais pas des faits établis. Elle relève de la recherche documentaire ; elle ne remplace ni le contact avec les clients ni la mesure de l'usage. C'est aussi une activité où la complaisance des modèles décrite plus haut joue à plein : un modèle à qui l'on demande de confirmer un marché attractif tend à le confirmer.

Recommandations :
- relier chaque chiffre à sa source et à sa date, et vérifier les chiffres décisifs à la source primaire ;
- distinguer dans la synthèse les données publiées, les estimations du modèle et les hypothèses ;
- demander explicitement les éléments qui contredisent l'hypothèse de marché ;
- confronter les segments les plus prometteurs à quelques entretiens avant tout engagement ;
- conserver le résultat dans la base de connaissance du produit (fichier marche.md, section 4.1), pour qu'il soit relu et mis à jour plutôt que réutilisé tel quel.

#### 3.2.7 Décider de ne pas construire

La facilité de générer ou de reproduire n'est pas une raison suffisante pour construire. Avant de reconstruire un comportement, nous proposons d'examiner cinq questions : connaît-on les raisons de ce comportement, a-t-on les droits nécessaires, la fonction apporte-t-elle une différenciation, combien coûtera sa validation, et qui en assurera l'exploitation ? Une modification de processus ou une meilleure utilisation d'un outil existant suffisent parfois. Décider de ne pas construire reste l'une des contributions les plus utiles du Product Management, et l'une des moins visibles.

#### 3.2.8 Une contribution, pas une responsabilité exclusive

L'automatisation ne déplace pas mécaniquement toute la valeur vers le Product Manager. Elle renforce l'importance d'un travail collectif : choisir les problèmes utiles, rendre explicites les règles métier, définir les preuves attendues et organiser les décisions.

Le Product Management contribue à relier ces activités à la valeur recherchée. L'ingénierie reste responsable de ses choix techniques. Les métiers apportent les règles et les usages. Les fonctions de sécurité, de conformité et d'exploitation interviennent selon les risques. L'autorité qui accepte un changement doit être explicite, et elle n'est pas nécessairement portée par le Product Manager (section 5.2).

La compétence distinctive ne consiste donc pas à rédiger davantage de spécifications. Elle consiste à relier objectifs, hypothèses, critères de décision et résultats observés, en gardant la possibilité de corriger la trajectoire.

---

## 4. Ce qu'il faut transmettre

Si la valeur tient à la capacité de faire évoluer le produit, la transmission devient centrale. Elle précède la réalisation : un agent ne peut faire évoluer correctement que ce dont la connaissance a été conservée.

### 4.1 Le patrimoine transmissible

#### 4.1.1 Ce qu'un successeur doit trouver

Reprendre un produit sans son créateur demande plus que son code. Le successeur doit trouver cinq ensembles de connaissance : le contexte et les objectifs (pourquoi le produit existe, pour qui, ce qu'il ne cherche pas à faire), les règles métier (définitions, calculs, sources de référence, périmètres), les décisions (options retenues ou écartées, et leurs raisons), la vérification (cas de référence, tests, critères d'acceptation) et l'exploitation (responsable, dépendances, incidents, procédure de reprise).

Ces ensembles forment une chaîne ordonnée :

> Contexte et objectifs, règles validées, spécifications, décisions, code, preuves, retours d'exploitation.

Le code n'est qu'un maillon. Il dit ce que fait le produit ; les autres maillons disent pourquoi, avec quelle validité, et comment on le sait.

#### 4.1.2 Une théorie détenue par des personnes

Peter Naur soutenait en 1985 que programmer consiste à construire une théorie du problème et de sa solution, et que cette théorie est détenue par des personnes, pas par le code (notice consultée ; texte intégral non relu, [Pascal-Francis](https://pascal-francis.inist.fr/vibad/index.php?action=getRecordDetail&idt=8553272)). Addy Osmani reprend cette idée sous le nom de dette de compréhension : le code produit par IA peut fonctionner sans que personne en ait construit la théorie ([Osmani, O'Reilly](https://www.oreilly.com/radar/comprehension-debt-the-hidden-cost-of-ai-generated-code/)). Il distingue aussi une dette d'intention, quand les raisons d'un choix ne sont consignées nulle part, tout en reconnaissant qu'il est impossible de tout consigner ([Osmani, O'Reilly](https://www.oreilly.com/radar/the-intent-debt/)).

Les premières mesures invitent à séparer deux choses. Dans un essai randomisé auprès de 52 ingénieurs, surtout juniors, qui apprenaient une bibliothèque Python inconnue, ceux qui utilisaient l'IA ont obtenu 50 % à un quiz de compréhension, contre 67 % pour les autres ; le déficit était le plus fort en débogage, et le gain de temps n'était pas significatif ([Shen et Tamkin, Anthropic, janvier 2026](https://www.anthropic.com/research/AI-assistance-coding-skills)). Dans une autre expérience, préenregistrée auprès de 151 participants, des développeurs qui faisaient évoluer sans IA un code produit avec IA n'ont montré aucune différence significative de temps ni de qualité ([Borg et al., arXiv 2507.00788](https://arxiv.org/abs/2507.00788)). La compréhension des personnes peut donc baisser sans que la maintenabilité du code se dégrade, du moins à court terme. Comprendre et maintenir doivent être évalués séparément.

#### 4.1.3 Des fichiers de connaissance dans le dépôt

Une pratique s'est diffusée : placer dans le dépôt de code des fichiers de contexte destinés aux agents, comme AGENTS.md, un format ouvert piloté par la Linux Foundation ([agents.md](https://agents.md)). Ce document propose d'aller plus loin : transformer les échanges qui ont produit un outil en fichiers de connaissance versionnés, pour que la mémoire du produit ne dépende pas de son créateur.

Une évaluation récente oblige à préciser cette idée. Gloaguen et ses coauteurs montrent que les fichiers de contexte n'améliorent généralement pas le taux de réussite des agents sur les tâches étudiées, augmentent le coût d'inférence de plus de 20 % en moyenne, et servent surtout à préciser des pratiques non standard ; les présentations générales du dépôt n'aident pas ([Gloaguen et al., arXiv 2602.11988](https://arxiv.org/abs/2602.11988)). Il s'agit d'une prépublication, mais elle conduit à séparer deux objets : des fichiers courts destinés aux agents, limités à ce qui n'est pas standard et évalués sur leur effet ; et un journal des décisions destiné aux humains, qui conserve les raisons. Le second n'a pas besoin de prouver qu'il aide un agent. Il doit permettre à une personne de comprendre.

#### 4.1.4 Un dispositif minimal

Nous proposons cinq fichiers, qui reprennent les cinq ensembles, et un sixième pour les produits vendus sur un marché. C'est une méthode de travail, pas un standard.

| Fichier | Contenu | Statuts possibles |
|---|---|---|
| contexte.md | Pourquoi l'application existe, pour qui, ce qu'elle ne cherche pas à faire | demandé, validé, obsolète |
| regles.md | Définitions, calculs, contraintes, sources de référence, dates et périmètres | règle approuvée, interprétation en attente |
| decisions.md | Options retenues ou écartées, raisons, hypothèses, incertitudes | décision active, remplacée |
| verification.md | Cas de référence, résultats attendus, tests, critères d'acceptation | testé, à valider |
| exploitation.md | Responsable, dépendances, accès, maintenance, incidents, reprise | actuel, à mettre à jour |
| marche.md | Segments, taille estimée, capacité à investir, modèle d'achat, habitudes des utilisateurs, concurrence et intégrations possibles, chaque donnée avec sa source et sa date | sourcé et vérifié, estimation, hypothèse, périmé |

Chaque entrée porte des statuts distincts : validation métier (approuvée, en attente, obsolète), implémentation (implémentée ou non), couverture de tests (testée, partiellement, non testée), avec la personne qui l'a validée, une date et, le cas échéant, la référence au code ou au test. Ces statuts ne se déduisent pas l'un de l'autre : une règle peut être implémentée sans avoir été approuvée, ou testée sans être juste.

La chaîne de constitution compte autant que la structure : échanges, extraction par un agent, clarification, validation par une personne identifiée, versionnement. Elle évite qu'une phrase d'une conversation devienne une exigence officielle sans que personne l'ait décidé.

Britto propose une idée voisine à l'échelle de l'organisation : une couche sémantique légère, mémoire partagée par les humains et l'IA, qui relie signaux, hypothèses, décisions, capacités techniques, versions et résultats, en conservant la provenance et les raisons des décisions ; les systèmes existants restent la référence, et cette couche ne crée pas un nouveau système de gestion. Il note aussi qu'une erreur dans ce contexte partagé peut se propager plus loin ([Britto](https://arxiv.org/abs/2610.14823)). Les fichiers proposés ici en sont une version minimale, à l'échelle d'un produit, avec un risque identique : une règle fausse validée par erreur sera appliquée partout où l'agent la lit.

Le fichier marche.md donne aux agents et aux successeurs le contexte business du produit : pour qui il est construit, dans quel marché, contre quelles alternatives. Il a un précédent dans les outils : Kiro charge à chaque session un fichier product.md qui décrit l'objet du produit, ses utilisateurs et ses objectifs business, afin que l'agent comprenne le « pourquoi » des choix techniques ([Kiro](https://kiro.dev/docs/steering/)). Une donnée de marché vieillit plus vite qu'une règle métier ; chaque entrée doit donc porter une date et être revue à intervalle fixe. Pour un outil interne comme l'outil de pilotage financier, ce fichier est inutile ; pour un produit vendu, il devient l'une des bases de la décision.

Dans l'exemple de l'outil de pilotage financier, regles.md contiendrait la définition de la marge utilisée, la table source qui fait foi, les retraitements appliqués et la date à partir de laquelle la règle vaut. Le jour où la direction financière s'appuie sur l'outil, ces éléments deviennent la base de toute discussion sur un chiffre contesté.

#### 4.1.5 Le système d'évaluation fait partie du patrimoine

Ce qui permet de juger une production prend plusieurs formes : règles métier, données de référence, tests, simulations, critères d'acceptation. Quand la production accélère, la qualité de ces moyens d'évaluation devient déterminante. Cela vaut pour les deux situations distinguées en introduction : quand on développe avec l'IA, le système d'évaluation juge le code produit par les agents ; quand on développe un produit contenant de l'IA, il juge aussi les réponses du produit.

Leur valeur ne vient pas de leur seule existence. Un ensemble de tests peut être incomplet, dépassé ou trop lié à l'implémentation actuelle. Il confirme alors un comportement sans dire s'il est juste. DeepMind a nommé ce phénomène chez les systèmes d'IA : le contournement de spécification, « a behaviour that satisfies the literal specification of an objective without achieving the intended outcome » ([Krakovna et al., 2020](https://deepmind.google/discover/blog/specification-gaming-the-flip-side-of-ai-ingenuity/)). C'est la version opérationnelle de la loi de Goodhart, selon laquelle une mesure qui devient un objectif cesse d'être une bonne mesure. La section 5.2 en donne des exemples récents dans l'évaluation des agents de code.

La tradition de la qualité industrielle propose une réponse connue : intégrer la qualité au produit dès sa conception plutôt que de dépendre de l'inspection finale. C'est le sens du troisième des quatorze points de W. Edwards Deming ([Deming Institute](https://deming.org/explore/fourteen-points/)) ; le mot à mot n'a pas été vérifié et la référence est citée pour son principe. Appliqué ici, ce principe signifie que les critères d'évaluation se conçoivent avec la spécification, pas après la génération.

Recommandation : versionner le système d'évaluation au même titre que le code. Pour chaque contrôle significatif, documenter ce qu'il cherche à établir, l'origine des résultats attendus, ses hypothèses et limites, les cas exclus, les personnes responsables de sa validation, et les événements qui imposent sa révision (changement réglementaire, incident, nouvel usage, changement de source de données). Ces éléments enrichissent verification.md, sans fichier supplémentaire.

#### 4.1.6 Un résultat correct n'est pas forcément compris

Les débats sur les preuves mathématiques produites par IA distinguent la correction d'un résultat de la compréhension qu'en retirent les humains. Hugo Duminil-Copin, médaillé Fields, écrit que la mission des mathématiciens est d'abord de produire de la compréhension, et décrit comment ses tentatives infructueuses sur une conjecture lui ont fourni des idées réutilisées ailleurs ([Duminil-Copin, août 2026](https://proofsandprompts.com/2026/08/30/care-for-a-little-more-ai/)). Quanta Magazine rapporte que des preuves vérifiées par un programme restent difficiles à lire et n'expliquent pas leur lien avec les travaux antérieurs ([Quanta Magazine, octobre 2026](https://www.quantamagazine.org/is-ai-the-end-of-math-as-we-know-it-20261005/)).

Nous en tirons une analyse pour le logiciel, pas une équivalence entre les deux domaines. Un changement accepté doit laisser assez de connaissance pour permettre sa maintenance, son diagnostic et son remplacement. Le code, même accompagné de tests, ne dit pas pourquoi une décision a été prise, quelles alternatives ont été écartées et quelles hypothèses restent fragiles.

Recommandation : accompagner les changements significatifs d'une justification proportionnée au risque : décisions prises, alternatives écartées, limites connues, dépendances, conditions de retour arrière. Ces éléments alimentent decisions.md. Un changement mineur et réversible peut se contenter de son message de commit ; la proposition ne demande pas une documentation exhaustive.

#### 4.1.7 La connaissance reconstruite

Une description obtenue par rétro-ingénierie (section 2.3) peut entrer dans ce patrimoine, mais avec son statut. Elle décrit un comportement observé ou inféré, pas une intention. Nous proposons de la traiter comme une hypothèse documentée, avec ses preuves et ses inconnues, jusqu'à validation par le métier. Elle permet de reprendre une enquête quand la mémoire manque. Elle ne remplace pas la mémoire conservée pendant la conception.

#### 4.1.8 Le test du successeur

Le patrimoine se juge par un test concret, à mener périodiquement et pas seulement au départ du créateur. Une personne qui n'a pas créé l'application doit pouvoir, avec un agent :

1. comprendre ses règles et leurs limites ;
2. vérifier si une nouvelle contrainte, par exemple un changement législatif, est déjà prise en compte ;
3. proposer une nouvelle version ;
4. comparer les résultats avec la version précédente et classer les écarts.

Ce test revient en conclusion, parce qu'il reste valable quel que soit le scénario d'évolution.

### 4.2 Spécifier : du comportement existant au comportement voulu

#### 4.2.1 Trois approches, pas encore un consensus

Le Spec-Driven Development (SDD), ou développement guidé par la spécification, désigne une famille de pratiques où une spécification écrite, versionnée et testable sert de référence, que les agents implémentent et que les humains relisent. Birgitta Böckeler, dans une analyse publiée sur le site de Martin Fowler, distingue trois approches ([Böckeler, octobre 2025](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)) :

- spec-first : la spécification est écrite avant le code, puis elle peut être abandonnée ;
- spec-anchored : la spécification est conservée et maintenue avec le code tout au long de la vie du produit ;
- spec-as-source : la spécification devient la seule source maintenue, le code étant régénéré à partir d'elle.

Elle conclut que le principe d'écrire la spécification d'abord est précieux dans de nombreuses situations, mais que le terme SDD reste mal défini, que des processus élaborés peuvent créer une surcharge de revue, et que les agents peuvent ignorer ou surappliquer les instructions. Le radar technologique de Thoughtworks classe le SDD comme une technique à explorer, en signalant des processus prescriptifs et des spécifications longues et difficiles à relire ([Thoughtworks Radar](https://www.thoughtworks.com/en-us/radar/techniques/spec-driven-development)). Il y a donc une convergence d'intérêt, pas un consensus ni une pratique stabilisée.

Ce document retient l'approche spec-anchored comme référence. Elle n'exige pas de croire à la régénération complète du code. Elle exige seulement que la connaissance et le produit restent cohérents, ce qui correspond au patrimoine décrit à la section 4.1. (Recommandation.)

#### 4.2.2 Persistance du contexte et persistance de la participation

Le mot « persistance » recouvre deux idées qu'il faut séparer.

La persistance du contexte désigne une mémoire qui survit aux sessions : l'agent retrouve à chaque intervention la spécification, les règles et les décisions, sans qu'on les lui répète. Elle est directement liée au SDD. Spec Kit, l'outil de GitHub, décrit un modèle de « spécification vivante » : après la livraison, la spécification reste le contrat, elle est modifiée en premier quand le comportement voulu change, et les plans et tâches en sont dérivés ([Spec Kit](https://github.github.com/spec-kit/concepts/spec-persistence.html)). Kiro présente ses fichiers de pilotage comme un « contexte IA persistant » ([Kiro](https://kiro.dev/blog/stop-repeating-yourself/)).

La persistance de la participation désigne autre chose : une IA qui observe, rapproche et signale en continu, sans attendre qu'on la sollicite. C'est le sens principal chez Britto, dont le premier principe est la veille continue plutôt que la recherche périodique ([Britto](https://arxiv.org/abs/2610.14823)). Le SDD ne couvre pas cette dimension : une spécification, même vivante, ne surveille ni les clients ni les concurrents.

Le lien est donc partiel. Le SDD (approche spec-anchored) fournit la mémoire sur laquelle une participation persistante peut s'appuyer ; le principe de Britto « living intent over static artifacts », qui garde la direction du produit reliée aux éléments de preuve, aux hypothèses et aux résultats, fait le pont entre les deux. Une participation persistante sans contexte maintenu produit des alertes sans référence ; un contexte maintenu sans participation reste une documentation bien tenue. (Hypothèse de lecture.)

#### 4.2.3 Deux familles de spécification

Deux familles coexistent, avec des domaines de validité différents. La première est la prose structurée : exigences, règles, critères d'acceptation, écrits pour être lus par des personnes et des agents. La seconde est le jeu d'évaluations : un ensemble d'exemples avec leurs résultats attendus, qui sert de spécification exécutable. Lisa Murkin défend l'idée que les évaluations deviennent le nouveau document d'exigences produit, tout en reconnaissant le risque de surajustement et le fait que trente exemples détectent des régressions sans prouver que le système fonctionne ([Murkin, Mind the Product, juillet 2026](https://www.mindtheproduct.com/evals-are-the-new-prd/)).

La seconde famille convient surtout aux produits contenant de l'IA, dont le comportement est probabiliste et ne se décrit pas entièrement en règles. La première reste nécessaire dès que des règles métier, des obligations ou des contrats doivent être explicités. La plupart des produits ont besoin des deux.

#### 4.2.4 Une spécification de livraison, pas un plan

L'importance donnée ici à la spécification appelle une précision, car Cagan critique les documents d'exigences produit (PRD) et les feuilles de route : ce sont, selon lui, des artefacts qui permettent de croire que l'on en sait plus qu'on n'en sait, au service d'un besoin de prévisibilité qui s'oppose aux résultats ([Strong Opinions, Loosely Held](https://www.svpg.com/strong-opinions-loosely-held/) ; [Predictability vs Outcomes, octobre 2026](https://www.svpg.com/predictability-vs-outcomes/)). Il avertit aussi que se servir de l'IA pour produire plus vite des feuilles de route, des PRD et des user stories ne fait qu'accélérer l'ancien modèle ([Product Coaching and AI, février 2026](https://www.svpg.com/product-coaching-and-ai/)).

La spécification dont parle cette section n'a pas ce rôle. Elle ne sert pas à décider quoi construire ni à promettre une date. Elle vient après la découverte, quand une solution a été jugée digne d'être livrée, et elle sert à trois choses : guider les agents, vérifier ce qu'ils produisent, et transmettre le produit. Elle relève du versant « construire pour vendre ». Cagan lui-même donne un argument en ce sens : il juge ouverte la question de savoir si les outils de génération pourront mener des solutions d'entreprise complexes du prototype au produit d'ici 3 à 5 ans, en raison des « limitations of spoken language as a specification language » ([Prototypes vs Products, novembre 2025](https://www.svpg.com/prototypes-vs-products/)). Plus les agents réalisent, plus la précision de ce qu'on leur demande compte ; mais cette précision porte sur une solution déjà choisie, pas sur un plan.

#### 4.2.5 Séparer l'existant de la cible

Le code décrit un comportement, pas une intention. Un comportement existant peut traduire une règle valable, une règle obsolète, un contournement, une exception accordée à un client ou un défaut toléré. Nous proposons donc de séparer deux livrables : la description du comportement existant, et la spécification du comportement cible. Le passage de l'un à l'autre est une décision, prise par des personnes identifiées.

Cette séparation conduit à ce que nous appelons la boucle inverse du SDD. Le SDD classique part d'une spécification pour produire un logiciel. La boucle inverse part d'un logiciel (son code, ses binaires ou son comportement observé) pour reconstruire une description de l'existant, puis décider de la cible :

> Logiciel autorisé à l'analyse, observations et artefacts, hypothèses de comportement, description de l'existant avec ses inconnues, validation métier, spécification cible, reconstruction, preuves d'acceptation.

| Point de départ | Connaissance recherchée | Limite à conserver | Livrable proposé |
|---|---|---|---|
| Code source | Règles implémentées, dépendances, exceptions | Le code ne justifie pas l'intention | Catalogue de comportements relié au code |
| Binaires et exécution autorisés | Logique probable, entrées et sorties, formats | Le pseudocode reste une reconstruction | Hypothèses reliées aux artefacts, inconnues explicites |
| Interface et parcours observables | Interactions, résultats, attentes d'usage | Les règles internes et les parcours non observés restent inconnus | Scénarios de caractérisation, pas une déclaration d'équivalence |

Le risque principal de cette boucle est de transformer un comportement observé en exigence approuvée. Chaque exigence déduite d'une observation devrait garder sa provenance, sa version, son statut d'hypothèse ou de règle approuvée, et le test qui la vérifie.

#### 4.2.6 Conformité et justesse

Une spécification plus détaillée n'est pas automatiquement plus juste. Elle peut formaliser une mauvaise hypothèse avec plus de précision, et un agent peut la respecter scrupuleusement.

Pamela Zave et Michael Jackson en ont donné la structure en 1997 : « all statements made in the course of requirements engineering are statements about the environment ». Ils distinguent ce qui est vrai du monde de ce que l'on souhaite y obtenir. Une spécification n'est correcte que si, combinée à des connaissances justes sur le domaine, elle garantit l'exigence dans le monde réel ([Zave et Jackson, 1997](https://cse.msu.edu/~chengb/RE-491/Papers/dark-corners-re-zave-jackson.pdf)). Un agent peut vérifier qu'un programme respecte sa spécification. Il ne peut pas, avec les mêmes moyens, vérifier que les hypothèses sur le monde sont justes. Expliciter et tester ces hypothèses est une contribution précise que le Product Management partage avec le métier.

Le cas Navier–Stokes, analysé en annexe G, illustre le même point du côté des mathématiques : la formalisation contrôle que la preuve démontre l'énoncé formalisé, et le débat porte sur la portée de cet énoncé et sur ce qu'il apporte au problème qui intéresse les mathématiciens.

Exemple, construit pour l'explication et non tiré d'un incident réel : une migration de base de données conserve toutes les valeurs et passe les tests techniques. Elle change pourtant l'interprétation d'un champ de date, qui passe d'une date de valeur à une date d'enregistrement. Le reporting annuel devient faux, parce que cette règle n'avait jamais été écrite. Les tests vérifiaient la conformité à ce qui était spécifié ; personne n'avait vérifié la justesse de la spécification sur ce point.

Recommandation : dans les revues de spécification, examiner séparément les définitions des données (unité, référentiel temporel, périmètre), les cas limites et les exceptions connues, et demander aux personnes du métier de confirmer ces éléments sur des exemples réels plutôt que sur le texte seul.

#### 4.2.7 Une spécification est un état provisoire

Manny Lehman distinguait les logiciels de type E, embarqués dans le monde réel et qui le modifient. Ils doivent être adaptés en permanence, sinon ils deviennent de moins en moins satisfaisants, et leur complexité croît s'ils ne sont pas activement entretenus. Lehman soutenait qu'une amélioration majeure passe par une modification des boucles de rétroaction du processus, pas seulement par de meilleurs outils ([Lehman, 1996](https://www.cs.kent.edu/~jmaletic/cs63902/Papers/Lehman96.pdf)).

La plupart des produits gérés par un Product Manager sont de type E. On ne peut pas les spécifier une fois pour toutes, puis automatiser leur production. Accélérer l'écriture du code sans changer les boucles de retour (usage, exploitation, décision) ne change pas la dynamique d'ensemble. Cela rejoint l'observation de Chen et Stratton : le goulot se situe dans le processus, pas dans la production du code.

#### 4.2.8 Niveaux de confidentialité et niveaux d'autonomie

Les niveaux N1, N2 et N3 utilisés dans le tableau de migration de la section 6.1 sont des niveaux de confidentialité des données, et non des niveaux d'autonomie des agents. La section suivante sépare les deux dimensions.

---
## 5. Réaliser et prouver avec des agents

Une fois établi ce qu'il faut décider et transmettre, reste à savoir comment confier la réalisation à des agents, et comment accepter ce qu'ils produisent.

### 5.1 Des permissions plutôt que des niveaux

#### 5.1.1 Définir l'autonomie par des actions autorisées

Parler du « niveau d'autonomie » d'un agent est commode, mais peu opérant. Nous proposons de définir l'autonomie par cinq permissions concrètes :

- l'accès : quelles données, quels dépôts, quels systèmes l'agent peut lire ;
- la modification : ce qu'il peut écrire ou changer, et où (branche de travail, environnement de test, production) ;
- la validation : s'il peut déclarer un résultat acceptable, ou seulement le proposer ;
- l'escalade : dans quels cas il doit s'arrêter et demander une décision humaine ;
- la réversibilité : si ses actions peuvent être annulées, comment, et en combien de temps.

La même tâche n'a pas les mêmes conséquences selon le contexte. Modifier une requête dans l'outil de pilotage financier peut fausser un chiffre, ce qui se corrige. Modifier une consigne dans le logiciel industriel peut arrêter une installation ou endommager un équipement. L'autonomie doit donc s'accorder selon les conséquences d'une erreur, pas selon la capacité de l'agent à exécuter la tâche. (Recommandation.)

#### 5.1.2 Ce que dit la recherche sur les niveaux d'autonomie

Feng, McDonald et Zhang proposent cinq niveaux d'autonomie, définis par le rôle de l'utilisateur plutôt que par les capacités de l'agent : opérateur, collaborateur, consultant, approbateur, observateur. Ils soutiennent que l'autonomie est un choix de conception distinct des capacités ([Feng, McDonald et Zhang, arXiv 2506.12469](https://arxiv.org/abs/2506.12469)). Ce cadre est compatible avec l'approche par permissions : il décrit la place de l'humain, les permissions en donnent le contenu. Le rôle d'approbateur correspond à ce que ce document appelle l'autorité d'acceptation (section 5.2).

Britto, pour le travail du Product Management, distingue trois modes : des activités opérées par l'IA dans des limites fixées par des humains, des activités dirigées par des humains, où l'IA fournit analyses et éléments, et des activités collaboratives. Le mode s'attribue à chaque activité, pas à une phase entière, et dépend selon lui de l'incertitude, de la réversibilité, des conséquences et du contexte de l'organisation ([Britto](https://arxiv.org/abs/2610.14823)). Ces critères rejoignent ceux retenus ici pour les permissions.

#### 5.1.3 Trois régimes selon la criticité

Nous proposons trois régimes, qui fixent des valeurs par défaut pour les cinq permissions :

| Permission | Outil personnel | Application partagée | Système critique |
|---|---|---|---|
| Accès | Données de l'utilisateur | Données du périmètre, classifiées | Strictement limité, journalisé |
| Modification | Libre dans l'outil | Sur branche de travail, jamais directement en production | Sur environnement isolé ou simulateur uniquement |
| Validation | L'utilisateur accepte | Revue et autorité d'acceptation désignée | Plusieurs niveaux d'acceptation, dont des spécialistes du domaine |
| Escalade | Facultative | Obligatoire sur les règles métier et les données de référence | Obligatoire sur toute action à effet physique ou irréversible |
| Réversibilité | Annulation simple | Retour arrière testé | Retour arrière testé et procédure de repli documentée |

Ces valeurs sont des points de départ à adapter. Elles reprennent des règles de sécurité courantes dans les recommandations de praticiens (élément non vérifié) : ne jamais donner à l'agent des droits de fusion ou de déploiement, l'exécuter dans un environnement isolé avec un accès réseau sortant limité, interdire les secrets dans son contexte, valider son code par des outils indépendants, vérifier les dépendances qu'il propose, qui peuvent être inexistantes ou malveillantes, et générer la liste des composants du logiciel (SBOM) à chaque construction.

#### 5.1.4 Le couplage, second critère de délégation

Charles Perrow a montré que les systèmes qui combinent une forte complexité d'interaction et un couplage serré, c'est-à-dire des étapes qui s'enchaînent sans délai ni marge, sont sujets à des défaillances même lorsqu'ils sont bien gérés ([Perrow, présenté dans Nature](https://www.nature.com/articles/477404a)). Des agents enchaînés, qui modifient le code, lancent des déploiements et réagissent aux sorties les uns des autres, augmentent à la fois la complexité et le couplage.

Le couplage devient donc un critère de délégation, à côté de la réversibilité. Découpler les étapes, par une validation entre deux actions ou des limites de propagation, réduit le risque même quand chaque agent est fiable. (Hypothèse, par analogie avec un cadre établi dans les industries à risque.)

#### 5.1.5 La confidentialité est une autre dimension

Les niveaux N1, N2 et N3 décrivent où les données peuvent circuler, pas ce que l'agent peut faire :

- N1, public : code open source, documentation publique ; tout service autorisé ;
- N2, interne : applications métier, outils internes ; hébergeur européen uniquement ;
- N3, sensible : code d'automates et de systèmes industriels, sécurité, données clients, défense ; auto-hébergement ou hébergeur qualifié SecNumCloud.

Ces niveaux s'appliquent au contenu de chaque artefact (code, documentation, extraits, index sémantiques), pas à la phase du projet. Une spécification extraite d'un code sensible ne devient pas « interne » parce qu'elle concerne l'architecture cible. Un patrimoine ancien n'est pas automatiquement sensible non plus : il faut classifier son contenu. Un agent peut avoir peu d'autonomie sur des données sensibles, ou beaucoup d'autonomie sur des données publiques. Les deux dimensions se croisent ; elles ne se confondent pas.

Un dispositif permet de tenir ces deux dimensions ensemble : une passerelle IA interne qui route les requêtes vers les modèles autorisés selon le niveau du dépôt, journalise les échanges, filtre les secrets avant envoi, applique des quotas et rend les modèles interchangeables (proposition non évaluée).

#### 5.1.6 Automatiser le développement ne rend pas le produit autonome

Confier la réalisation à des agents ne dit rien de l'autonomie du produit lui-même. Le logiciel industriel peut être développé avec beaucoup d'agents et rester un produit où chaque consigne est validée par un opérateur. À l'inverse, un produit contenant de l'IA peut prendre des décisions seul tout en ayant été développé de façon traditionnelle. Où placer le curseur dans le produit est une décision produit, qui relève de la section 3.2, pas une conséquence des outils de développement.

#### 5.1.7 Des contrats pour décrire ce qu'un composant peut faire

Certaines technologies permettent de décrire précisément ce qu'un composant peut faire. Le modèle de composants de WebAssembly utilise un langage, WIT, pour décrire les interfaces d'un composant indépendamment de son langage de programmation ; un « world » exprime ce que le composant offre et ce dont il dépend ([Bytecode Alliance](https://component-model.bytecodealliance.org/design/component-model-concepts.html)). WASI désigne une famille d'interfaces système définies de cette façon. Ces contrats rendent explicites les capacités demandées. Ils ne prouvent ni la correction métier, ni que les droits réellement accordés par l'environnement d'exécution correspondent à ceux qui étaient prévus. Ces deux points restent à vérifier séparément.

### 5.2 Prouver et accepter

#### 5.2.1 La revue est devenue le goulot

L'étude de Chen et Stratton fournit la donnée la plus solide sur ce point. Après l'adoption d'agents de code, la production de code et de pull requests augmente nettement, mais le délai de fusion s'allonge et les demandes de modifications pendant la revue augmentent, sans hausse significative des tickets résolus ([Chen et Stratton, août 2026](https://fion.ac/jellyfish.pdf)). Une étude interne d'Anthropic rapporte que la lecture des sorties des agents représenterait plus de la moitié d'une semaine de travail, et que la part du « méta-travail » dans les sessions passe de 10 % à 22 % ; elle observe aussi que le taux de lignes supprimées ou annulées n'a pas changé ([Anthropic, octobre 2026](https://www.anthropic.com/research/employment-at-anthropic)). Il s'agit d'une seule entreprise, qui fournit des modèles, et les auteurs reconnaissent ces limites. Plus de revue ne signifie donc pas forcément plus de défauts, mais la revue absorbe une part croissante du temps.

Les tickets résolus mesurent la conformité à une demande, pas la pertinence de cette demande. Aucune de ces études ne mesure la valeur produite.

#### 5.2.2 Trois niveaux d'acceptation

Nous proposons d'accepter un changement à trois niveaux, qui ne relèvent pas des mêmes personnes.

| Niveau | Question | Vérifications mobilisées | Éléments de preuve possibles | Contributeurs principaux |
|---|---|---|---|---|
| Technique | La réalisation fonctionne-t-elle dans le périmètre testé ? | Aptitude à l'exploitation, volet technique | Tests, analyse statique, typage, mesures de performance, contrôles de sécurité | Ingénierie, sécurité |
| Métier | Le comportement correspond-il aux règles et usages attendus ? | Équivalence avec l'existant là où il fait foi, correction métier | Scénarios métier, données de référence, classification des écarts, validation par les personnes compétentes | Métier, spécialistes du domaine, Product |
| Produit et exploitation | Le changement apporte-t-il une valeur acceptable au regard de ses risques et de ses coûts ? | Aptitude à l'exploitation, volet opérationnel, et validation de la pertinence | Observation des usages, résultats opérationnels, incidents, capacité de support et de retour arrière | Product, exploitation, responsable de l'application |

Le premier niveau vérifie une réalisation. Le troisième valide sa pertinence. Le deuxième est celui où se croisent la conformité à la spécification et la justesse de cette spécification (section 4.2).

#### 5.2.3 Équivalence, correction, aptitude à l'exploitation

Ces trois vérifications ne se remplacent pas. L'équivalence établit que le nouveau système se comporte comme l'ancien. La correction métier établit qu'il se comporte comme il le devrait. L'aptitude à l'exploitation établit qu'il peut tourner, être surveillé, réparé et repris. L'ancien système est un point de comparaison, pas une vérité métier : il peut contenir des défauts que tout le monde a pris pour des règles.

Les écarts entre l'ancien et le nouveau se classent en quatre catégories :

1. différence attendue et approuvée ;
2. défaut du nouveau système ;
3. défaut découvert dans l'ancien ;
4. différence inexpliquée.

L'acceptation porte sur la quatrième catégorie et sur les risques, pas sur un pourcentage de tests réussis.

La vérification d'équivalence a un piège connu. La loi de Hyrum, observation de praticien, l'énonce ainsi : « With a sufficient number of users of an API, it does not matter what you promise in the contract: all observable behaviors of your system will be depended on by somebody » ([Hyrum Wright](https://www.hyrumslaw.com/)). Lors d'une migration ou d'une réimplémentation, les utilisateurs dépendent aussi de comportements non documentés : délais, ordres de tri, messages d'erreur, arrondis. Une équivalence établie sur la seule spécification peut casser ces dépendances.

#### 5.2.4 Une comparaison conçue selon le risque

Faire tourner en parallèle l'ancien et le nouveau système sur le trafic réel (dual run) est une méthode courante. Pour un système financier ou industriel, elle doit être conçue selon le risque : deux versions ne doivent pas produire en même temps des écritures comptables ou des commandes sur une installation. Le rejeu de données historiques, ou une exécution parallèle sans effets réels, permettent de comparer sans ce risque.

Pour le logiciel industriel, une revue par un expert du domaine et des tests sur simulateur s'imposent avant tout essai sur l'équipement, conformément aux pratiques du secteur. Le code des automates programmables ne s'accepte pas sur la seule foi de tests unitaires.

#### 5.2.5 Quelle donnée fait foi, et qui valide quoi

Les deux incidents rapportés à la section 2.1 posent des questions d'acceptation. Pour le tableau de bord faux pendant six mois, la question est : quelle donnée fait référence ? Elle doit être posée avant l'usage quotidien, et sa réponse consignée dans regles.md. Pour la clause inventée dans un accord de confidentialité, la question est : qui valide un contenu à portée contractuelle ou réglementaire ? La réponse doit être une personne identifiée, quelle que soit la qualité de l'outil.

#### 5.2.6 Ce que le typage et le compilateur vérifient

Les langages typés et les compilateurs stricts transforment certains défauts en erreurs détectables avant l'usage. GitHub décrit le typage comme un contrat utile entre développeurs, outils et agents ; son analyse de l'adoption de TypeScript présente des corrélations, pas la preuve qu'un langage typé est toujours supérieur ([GitHub](https://github.blog/ai-and-ml/llms/why-ai-is-pushing-developers-toward-typed-languages/)). Les recommandations de Microsoft pour Rust rappellent qu'une fonction techniquement sûre peut néanmoins effectuer une opération dangereuse, comme supprimer une base de données ([Microsoft, Pragmatic Rust Guidelines](https://microsoft.github.io/rust-guidelines/guidelines/correctness/index.html)). Sûreté de la mémoire, autorisation d'agir et correction métier sont trois questions distinctes.

| Niveau de contrôle | Question examinée | Ce qu'il ne prouve pas à lui seul |
|---|---|---|
| Types, compilation, analyses statiques | Le programme respecte-t-il les règles contrôlées par ces outils ? | L'intention métier, la qualité du service, l'absence de tout défaut |
| Tests techniques et de propriétés | Les cas et invariants testés sont-ils satisfaits ? | La couverture de tous les usages et exceptions |
| Cas métier indépendants | Les résultats attendus par le métier sont-ils obtenus ? | L'aptitude à l'exploitation sur toutes les plateformes |
| Essais d'exploitation et d'usage | Les risques, performances et résultats sont-ils acceptables dans les conditions prévues ? | Une garantie permanente après toute évolution |

#### 5.2.7 La sécurité ne se présume pas

La Cloud Security Alliance rapporte un examen, en octobre 2025, de 5 600 applications construites par génération de code et en production : aucune n'avait de protection contre la falsification de requêtes intersites (CSRF) ni les en-têtes de sécurité standard, et toutes présentaient des vulnérabilités de type SSRF dans leurs fonctions de traitement d'adresses ([CSA, juin 2026](https://labs.cloudsecurityalliance.org/wp-content/uploads/2026/06/CSA_research_note_vibe_coding_ai_governance_gap_20260602-csa-styled.pdf)). Le même rapport constate que les cadres de sécurité de l'IA existants manquent de recommandations pour les développeurs métier. La preuve de sécurité fait partie de l'acceptation technique ; elle ne se déduit pas du fait que l'application fonctionne.

#### 5.2.8 Le système d'évaluation peut se tromper

Quand des agents produisent vite, le risque se déplace vers les contrôles eux-mêmes. Deux exemples récents le documentent. METR a observé des modèles qui modifient les tests ou le code de notation pour obtenir un meilleur score ; pour l'un d'eux, ce contournement apparaît dans 0,7 % des exécutions sur un banc d'évaluation et plus de 43 fois plus souvent sur un autre, et les consignes de ne pas tricher n'ont presque aucun effet ([METR, juin 2025](https://metr.substack.com/p/2025-06-05-recent-reward-hacking)). OpenAI a audité 138 problèmes de SWE-bench Verified, un banc d'évaluation de référence pour les agents de code : au moins 59,4 % présentaient des défauts importants, notamment des tests trop étroits ou trop larges, avec des signes de contamination ; l'entreprise a cessé de publier ce score ([OpenAI, février 2026](https://openai.com/index/why-we-no-longer-evaluate-swe-bench-verified/)). Ces cas concernent l'évaluation des modèles plus que la production, mais le mécanisme est le même : un contrôle étroit peut être satisfait sans que le but soit atteint.

Birgitta Böckeler décrit l'environnement de contrôle des agents, le harness, comme une combinaison de guides préventifs et de capteurs de rétroaction ; elle note que le construire et le maintenir de façon cohérente coûte cher, et que des tests générés par l'IA ne suffisent pas à établir la qualité fonctionnelle ([Böckeler, avril 2026](https://martinfowler.com/articles/harness-engineering.html)).

Recommandations :
- conserver des évaluations indépendantes de celles qui guident la génération, par exemple des cas de référence que l'agent ne voit pas pendant la réalisation ;
- examiner les effets indésirables et les cas limites, pas seulement les cas nominaux ;
- réviser les critères à partir des incidents et des retours d'usage ;
- exiger que le résultat accepté soit compris par une personne capable de le maintenir, pas seulement qu'il passe les contrôles (section 4.1).

#### 5.2.9 La revue humaine est une tâche de vigilance

Relire des centaines de modifications proposées par des agents, dont la plupart sont correctes, est une tâche de surveillance. Lisanne Bainbridge a décrit en 1983 les « ironies de l'automatisation » : l'automatisation laisse à l'humain les tâches les plus difficiles, tout en réduisant les occasions d'entretenir ses compétences. Elle rapporte que les études de vigilance montrent qu'une personne ne maintient pas efficacement son attention sur une source où il se passe peu de choses au-delà d'environ une demi-heure ([Bainbridge, 1983](https://ckrybus.com/static/papers/Bainbridge_1983_Automatica.pdf)). Parasuraman et Manzey montrent que la complaisance envers l'automatisation apparaît sous charge multitâche et résiste à la simple pratique, et que le biais d'automatisation provoque des erreurs d'omission (ne pas voir ce que l'automate n'a pas signalé) et de commission (suivre une recommandation fausse), sans être prévenu par la formation ou les consignes ([Parasuraman et Manzey, 2010](https://pubmed.ncbi.nlm.nih.gov/21077562/)).

Les données de Chen et Stratton, avec davantage de demandes de modifications, suggèrent que la revue tient encore. Rien ne garantit qu'elle tiendra quand le volume augmentera. Conséquences pratiques : limiter le volume par relecteur, orienter l'attention vers les écarts plutôt que vers le flux complet, et ne pas compter sur la seule consigne « relisez attentivement ». (Recommandations, par analogie avec les facteurs humains.)

#### 5.2.10 Les conditions de l'autorité d'acceptation

L'autorité qui accepte un changement à chaque niveau doit être désignée explicitement, selon le risque. Elle n'est pas attribuée par défaut au Product Manager. Pour le logiciel industriel, l'acceptation technique et métier peut relever de spécialistes du domaine et du responsable de l'installation.

Désigner une personne ne suffit pas. Madeleine Clare Elish a montré que, dans un système automatisé complexe, l'humain peut devenir le composant qui porte l'essentiel de la responsabilité morale et juridique alors qu'il avait peu de contrôle ; elle parle de zone de déformation morale, par analogie avec la zone d'une voiture conçue pour absorber le choc ([Elish, 2019](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2757236)). Ben Green, après l'analyse de 41 documents de politique publique, conclut que les personnes ne peuvent généralement pas assurer de façon fiable la supervision attendue, et que ces obligations peuvent légitimer des systèmes défaillants ; il propose une supervision institutionnelle, avec une justification écrite de l'usage, puis un examen et une approbation ([Green, 2022](https://www.benzevgreen.com/wp-content/uploads/2022/04/22-clsr.pdf)). L'article 14 du règlement européen sur l'IA demande que les personnes chargées de superviser un système à haut risque puissent le comprendre, interpréter ses résultats, décider de ne pas les suivre et l'interrompre, et qu'elles restent conscientes du biais d'automatisation ([AI Act Service Desk](https://ai-act-service-desk.ec.europa.eu/en/ai-act/article-14)). Cet article vise les systèmes d'IA à haut risque mis sur le marché, pas les agents utilisés pour développer un logiciel : son usage ici est une analogie, pas une obligation juridique.

Sans conditions, l'autorité d'acceptation risque de devenir une zone de déformation morale : quelqu'un qui signe sans avoir eu le temps, l'information ni le pouvoir de refuser. Nous proposons donc quatre conditions :

- le temps et l'information nécessaires pour examiner ce qui est accepté ;
- le pouvoir réel de refuser ou d'arrêter, sans pénalité implicite ;
- une trace écrite des raisons de l'acceptation ;
- une responsabilité de l'organisation sur le dispositif lui-même, pas seulement sur la personne qui signe.

La section 7.3 ajoute à ces conditions les critères de la contradiction effective, issus de la régulation bancaire.

#### 5.2.11 Couverture apparente et preuve de remplacement

Les mêmes règles s'appliquent quand on évalue un produit concurrent ou un clone (section 3.1). Une fonction présente n'est pas une fonction acceptée. Le niveau de preuve d'un remplacement se juge sur des tâches réelles, avec les trois niveaux d'acceptation, et pas sur la liste des fonctions.

### 5.3 Une architecture qui rend la boucle vérifiable et reprenable

#### 5.3.1 Séparer le moteur de ses canaux d'accès

Isoler la logique métier ou le traitement derrière des contrats explicites, puis l'exposer par plusieurs canaux (interface graphique, API, agent), facilite la reprise et le remplacement. PhotoCraft et FilmCraft en donnent un exemple concret, avec un même moteur de commandes accessible par l'interface, la ligne de commande et MCP (section 3.1). Ce constat ne prouve pas qu'une architecture donnée est supérieure ; il montre qu'un produit ne se réduit pas à son écran, et que ses frontières internes conditionnent ce qu'un successeur ou un agent peut reprendre.

#### 5.3.2 Une architecture polyglotte plutôt qu'un langage unique

Une architecture souvent proposée consiste à écrire les moteurs en Rust et à les exposer à des interfaces écrites dans d'autres langages. Nous retenons le principe sans prescrire le langage. Trois trajectoires sont à comparer pour chaque composant :

- conserver un composant maîtrisé quand le bénéfice attendu ne justifie pas sa migration ;
- l'encapsuler, en définissant un contrat et des tests autour du moteur existant pour permettre de nouveaux usages sans réécrire sa logique ;
- le remplacer sélectivement si des mesures de risque, de performance, de portabilité ou de maintenabilité justifient le coût.

Une architecture polyglotte a ses coûts : contrats à maintenir, conversions de données, diagnostic entre langages, outillage, et capacité d'un successeur à reprendre le tout. Les projections de généralisation de Rust qui circulent ne sont pas reprises comme des faits.

#### 5.3.3 WebAssembly comme cible de distribution

MDN présente WebAssembly (Wasm) comme une cible de compilation qui peut notamment recevoir du C++ ou du Rust, conçue pour cohabiter avec JavaScript ; dans le navigateur, les échanges avec les API web passent par JavaScript, et la documentation ne promet pas de gain de performance chiffré ([MDN](https://developer.mozilla.org/en-US/docs/WebAssembly/Guides/Concepts)). Wasm est un complément à JavaScript, pas un remplacement. Il faut distinguer le langage d'implémentation, le format de distribution, l'environnement d'exécution et l'interface utilisateur.

Pour le Product Management, Wasm s'évalue par les usages qu'il permet : proposer certains traitements dans un navigateur, réutiliser un moteur entre une application native et le web, réduire une installation. Ce sont des options à expérimenter. Partager du code ne démontre pas que le service est identique sur toutes les cibles ; nous recommandons de tenir une matrice des plateformes avec des preuves par cible (affichage, accessibilité, fichiers, performances, reprise).

#### 5.3.4 Calcul local et WebGPU

WebGPU permet d'utiliser le processeur graphique de l'appareil pour le rendu et le calcul ; MDN signale une disponibilité limitée selon les navigateurs et un contexte sécurisé requis ([MDN, WebGPU](https://developer.mozilla.org/en-US/docs/Web/API/WebGPU_API)). Le calcul local peut avoir une valeur produit : fonctionnement sans connexion pour des tâches bornées, moins de données envoyées au serveur, latence réduite, coûts plus prévisibles. Ces effets se mesurent avec leurs contreparties : matériel disponible, mémoire, consommation, support et mode de repli. Le calcul local ne démontre pas la souveraineté de l'ensemble (section 7.3) : les mises à jour, la télémétrie, l'authentification et les services optionnels continuent de circuler.

#### 5.3.5 Plateformes internes et cycle de vie

Les plateformes internes de développement standardisent des outils en libre-service pour créer et déployer du code, avec une gouvernance intégrée. Leur gain de productivité n'est pas mesuré par des études contrôlées dans les sources examinées. Elles sont cependant le lieu naturel où appliquer les permissions de la section 5.1 : environnement isolé, accès réseau filtré, secrets hors contexte, outils de contrôle indépendants, journalisation.

Une fonctionnalité n'est pas terminée parce que l'agent dit avoir fini. Elle l'est quand les critères d'acceptation sont satisfaits et que les responsabilités d'exploitation sont prises en charge : surveillance, traitement des incidents, maintenance, et un jour le retrait. Les incidents et retours d'usage doivent alimenter la mémoire du produit (exploitation.md, decisions.md), pas seulement les tickets.

#### 5.3.6 Mesurer la boucle complète

L'enquête officielle de la communauté Rust documente des temps de compilation très variables selon les projets ; la question où 55 % des répondants déclaraient attendre plus de dix secondes portait sur le projet qu'ils jugeaient le plus problématique, pas sur tous leurs projets ([Rust, enquête 2025](https://blog.rust-lang.org/2025/09/10/rust-compiler-performance-survey-2025-results/)). Ce chiffre ne mesure donc pas la boucle d'un agent. Le débit réel dépend pourtant de cette boucle : préparer le contexte, générer, compiler, tester, corriger, relire, intégrer, mettre à jour la connaissance. Un choix technique se juge sur le coût par changement accepté et le risque résiduel, pas sur la seule vitesse de génération ni sur la seule sévérité du compilateur.

#### 5.3.7 Ce que l'architecture ajoute au patrimoine

Le patrimoine transmissible de la section 4.1 comprend aussi les contrats d'interface, les permissions nécessaires à chaque composant, les plateformes prises en charge, la chaîne de compilation et de test, et les limites connues. Une architecture favorable aux agents ne devient durable que si elle reste compréhensible, vérifiable et exploitable par les personnes qui la reprendront.

---
## 6. Deux trajectoires

Le modèle décrit jusqu'ici vaut pour tout produit. Le point de départ change pourtant les priorités : créer un produit sans existant et moderniser un système ancien n'ont ni les mêmes goulots ni les mêmes risques.

### 6.1 Créer un produit neuf, moderniser un existant

#### 6.1.1 Créer sans existant

Quand il n'y a pas d'existant, la classification des données s'applique dès le premier jour : chaque dépôt, chaque jeu de données et chaque document reçoit son niveau de confidentialité avant que les agents y touchent. Le goulot est la spécification et la revue : les agents produisent vite, et la question est de savoir si ce qu'ils produisent correspond à ce qu'il fallait construire. Le risque principal est ce que l'on appelle le vibe coding, c'est-à-dire la génération rapide d'un produit à partir d'intentions vagues, sans spécification maintenue. Il produit une dette de spécification : un logiciel qui fonctionne, mais dont personne ne peut dire quelles règles il applique ni pourquoi.

L'outil de pilotage financier relève de cette trajectoire. Sa création est rapide. Son passage en produit partagé exige de rattraper la spécification qui n'a pas été écrite (section 4.1).

#### 6.1.2 Moderniser un existant

La modernisation obéit à un paradoxe : le code le plus ancien contient souvent les règles métier les plus sensibles, parce qu'il a accumulé des années d'exceptions et de corrections. La phase de découverte doit donc être classifiée selon le contenu des artefacts, qui est souvent sensible, mais pas automatiquement. Le goulot se situe sur l'architecture, l'équivalence et la bascule. Le risque principal porte sur l'équivalence transactionnelle, c'est-à-dire la garantie que chaque opération produit les mêmes effets durables, et sur la compatibilité des outils, qui ciblent surtout les environnements mainframe d'IBM.

#### 6.1.3 Un ordre de grandeur établi

Le cas Amadeus donne un ordre de grandeur documenté. La sortie de son système de réservation du mainframe a représenté environ 2 000 personnes-années d'effort, avec plus de 400 ingénieurs à plein temps au pic ; le système TPF a été arrêté en juin 2017 et le dernier mainframe fin 2018 ([Amadeus, janvier 2020](https://amadeus.com/en/blog/articles/celebrating-one-year-fully-open-systems)).

Des analyses de praticiens estiment qu'avec l'IA actuelle, un tel projet demanderait 20 à 40 % d'effort en moins (élément non vérifié). Cette estimation est un scénario conditionnel, pas une mesure. Les déclarations récentes montrent la tension autour de ces gains. Morgan Stanley déclare avoir modernisé plus de 17 millions de lignes avec son outil interne et économisé plus d'un million d'heures ; selon Gartner, cité par la même source, plus de 70 % des migrations de mainframes commencées cette année échoueraient parce que les responsables surestiment l'aide de l'IA générative ([CIO Dive, juillet 2026](https://www.ciodive.com/news/ai-shifts-mainframe-modernization-strategy/825677/)). Le premier chiffre est une déclaration d'entreprise, le second une prédiction d'analyste rapportée par la presse, qui n'a pas été lue à sa source. Ni l'un ni l'autre n'est une mesure indépendante.

#### 6.1.4 Le cycle de modernisation

Le cycle se décompose en huit phases. Pour chacune, le tableau distingue ce que l'IA apporte, ce qui reste une décision humaine et la preuve attendue. La confidentialité se détermine par le contenu de chaque artefact, pas par la phase.

| Phase | Contribution de l'IA | Décision humaine | Preuve attendue |
|---|---|---|---|
| Découverte et cartographie | Analyse du code, des dépendances, de la lignée des données | Confirmer les comportements non documentés | Carte de l'existant, sources examinées, zones inconnues |
| Extraction des règles | Description des règles à partir du code | Distinguer intention, héritage, contournement, défaut | Catalogue de règles relié au code, avec statut de validation |
| Comportement cible | Proposer des exigences, signaler les ambiguïtés | Décider ce qui reste identique et ce qui change | Spécification cible validée |
| Architecture cible | Proposer des découpages et des options | Frontières transactionnelles, compromis | Décisions d'architecture motivées |
| Génération | Code, interfaces, configuration | Revue selon le risque et la portée | Modifications vérifiables, tests reliés aux exigences |
| Équivalence | Génération de tests, comparaison | Définir les écarts acceptables | Rapport d'écarts classés en quatre catégories |
| Bascule | Scripts de migration, déploiement | Décision d'y aller ou non, risque opérationnel | Contrôles et retour arrière vérifiés |
| Exploitation et évolution | Surveiller, analyser, proposer | Décider des changements | Historique des versions et des incidents |

#### 6.1.5 Coexistence et bascule progressive

Le schéma de référence reste celui du figuier étrangleur (strangler fig) : remplacer le système capacité par capacité, derrière une couche de routage, plutôt que tout réécrire d'un coup. Il entraîne une coexistence longue, avec des coûts temporaires supplémentaires : deux systèmes à faire tourner, et les comparaisons entre eux. Des fournisseurs proposent des chaînes agentiques pour ces migrations ; leurs fonctions sont annoncées dans leur documentation, et leur efficacité générale n'est pas démontrée par des mesures indépendantes (élément non vérifié).

Avant la bascule, l'inventaire doit aussi porter sur les comportements observables dont les utilisateurs dépendent sans qu'ils soient documentés, selon la loi de Hyrum (section 5.2) : formats de sortie, ordres de tri, délais, messages d'erreur. Une migration conforme à la spécification peut casser ces dépendances.

La rétro-ingénierie agentique peut accélérer la découverte, notamment quand le code source est incomplet ou que sa documentation manque. Ses limites restent celles de la section 2.3 : l'essai rapporté par MindStudio est informel, et aucune comparaison indépendante n'est publiée. Pour un pilote, nous proposons de choisir un outil détenu par l'organisation ou explicitement autorisé à l'analyse, de classifier binaires, captures, pseudocode et résultats, de travailler dans un environnement isolé, et de comparer sur le même périmètre un agent avec et sans l'outil, en comptant la configuration, la revue et les corrections. Le critère n'est pas la ressemblance, mais le coût par comportement validé et la qualité du dossier de connaissance obtenu.

#### 6.1.6 Dette technique et refactorisation assistée

La littérature produit la plus diffusée met l'accent sur la découverte et la création de produits nouveaux. En entreprise, un logiciel vit longtemps après sa création, et il accumule une dette technique bien avant l'arrivée de l'IA. (Observation de terrain.) Ce n'est pas une critique du modèle produit lui-même : TRANSFORMED est consacré à la transformation d'organisations existantes vers ce modèle ([Mind the Product, compte rendu](https://www.mindtheproduct.com/transformed-moving-to-the-product-model-by-marty-cagan/)), et Cagan rappelle qu'un produit commercial doit être fiable, observable, sécurisé et conforme, ce qu'un prototype n'est pas ([Prototypes vs Products](https://www.svpg.com/prototypes-vs-products/)). La critique porte sur la place donnée à la durée de vie et à l'entretien du produit, moins traités que sa création. Aucune source examinée ne fixe un âge à partir duquel la dette apparaît. Une étude portant sur dix ans d'historique de trois applications open source montre que la plupart des versions majeures l'augmentent ([arXiv 2007.13422](https://ar5iv.labs.arxiv.org/html/2007.13422)). Dans une étude longitudinale, des développeurs déclarent perdre en moyenne 23 % de leur temps de travail à cause de la dette, principalement en tests supplémentaires ([Besker, Martini et Bosch, 2019](https://research.chalmers.se/publication/511450/file/511450_Fulltext.pdf)) ; il s'agit d'une déclaration, pas d'une mesure.

On peut espérer que la refactorisation assistée par l'IA réduise cette dette lorsque des jeux de tests ont été écrits auparavant. Les données disponibles vont dans ce sens, avec des limites. Chez Google, sur 39 migrations menées par trois développeurs en douze mois, environ 74 % des modifications de code ont été générées par le modèle, et les développeurs estiment avoir réduit de 50 % le temps total par rapport à des migrations manuelles comparables ([Google, arXiv 2504.09691](https://arxiv.org/abs/2504.09691)) ; c'est une estimation des intéressés, dans un environnement outillé de façon exceptionnelle. En sens inverse, une étude sur 180 refactorisations réelles trouve que 13 des 176 solutions proposées par ChatGPT modifiaient le comportement du code ou introduisaient des erreurs ([Liu et al., 2025](https://link.springer.com/article/10.1007/s10515-025-00500-0)). Une évaluation par fuzzing différentiel montre qu'environ 21 % des refactorisations non équivalentes passent les tests existants sans être détectées ([arXiv 2602.15761](https://arxiv.org/html/2602.15761v1)).

Les tests existants sont donc une condition nécessaire de la refactorisation assistée, pas une garantie. La démarche la plus sûre consiste à renforcer d'abord les tests qui capturent le comportement actuel, puis à refactoriser, puis à comparer selon le risque (section 5.2). La conséquence budgétaire est traitée à la section 7.2 : la réduction de la dette n'est pas gratuite, elle demande une capacité humaine et IA planifiée dans la durée.

#### 6.1.7 Migrer de façon ciblée

Remplacer un composant doit être justifié par une mesure de risque, de performance ou de maintenabilité, pas par la disponibilité d'un outil. La question décisive est souvent : qui pourra maintenir le résultat ? Réécrire un composant dans un langage que personne dans l'équipe ne maîtrise réduit une dette technique en créant une dette de compétences (section 7.1).

Pour le logiciel industriel, la modernisation combine les deux difficultés : un code ancien qui porte des règles de sûreté, et des tests qui ne peuvent pas se faire sur l'installation réelle. Le simulateur et la revue par des spécialistes du domaine y sont des conditions d'acceptation, pas des options.

---

## 7. Organisation, économie et cadre européen

Les parties précédentes décrivent ce qu'il faut faire. Les trois sections suivantes décrivent les conditions qui rendent cela possible : qui s'en charge, à quel coût, et sous quelles obligations.

### 7.1 Organisation et rôle du Product Manager

#### 7.1.1 Répartir les responsabilités

Quand les métiers construisent et que les agents réalisent, chaque fonction garde une valeur propre.

| Fonction | Valeur attendue |
|---|---|
| Métier | Expliquer le travail réel, valider les règles, juger les résultats utiles |
| Product | Choisir les problèmes, arbitrer la valeur, définir le périmètre, mesurer les effets |
| Ingénierie | Concevoir les architectures, les intégrations et l'environnement fiable de travail des agents |
| Qualité, sécurité, spécialistes du domaine | Définir les contrôles, examiner les risques |
| Responsable de l'application | Assumer la continuité, les évolutions, la fin de vie |
| Agents | Réaliser les tâches déléguées, produire les éléments permettant de les examiner |
| Autorité d'acceptation | Accepter un changement à un niveau donné, selon le risque, dans les conditions de la section 5.2 |

En cas d'incident, la responsabilité suit cette répartition : l'agent n'est responsable de rien. Le responsable de l'application répond de la continuité, l'autorité d'acceptation de ce qu'elle a accepté, dans la limite de ce qu'on lui a donné les moyens d'examiner, et l'organisation du dispositif lui-même.

#### 7.1.2 Le modèle en étoile

Une réponse organisationnelle souvent évoquée est le modèle en étoile : un noyau Product central, et des antennes placées dans les métiers. Le noyau garde la cohérence du portefeuille ; les antennes forment, auditent et arbitrent au plus près des usages. Ce modèle s'apparente aux « fusion teams », qui mêlent compétences métier et technologiques. Il existe peu de preuves indépendantes de sa tenue à grande échelle, et les chiffres de cabinets qui circulent n'ont pas été vérifiés. Il reste une proposition, avec un risque connu : que les antennes deviennent des silos.

Le modèle en étoile suppose une direction produit forte. Cagan insiste sur ce point : des équipes autonomes ne demandent pas moins de management mais un meilleur management, à commencer par une vision et une stratégie produit qui désignent les problèmes les plus importants à résoudre ([Strong Opinions, Loosely Held](https://www.svpg.com/strong-opinions-loosely-held/)). Il défend aussi le principe « experts lead experts » et juge temporaire la vague actuelle qui privilégie les seuls « builders » au détriment des managers ; il présente cette conclusion comme une prédiction qui peut se révéler fausse ([Cagan, Experts Lead Experts, septembre 2026](https://www.svpg.com/experts-lead-experts/)). Pour le modèle en étoile, la conséquence est que le noyau central doit porter la stratégie et la cohérence, pas seulement l'inventaire.

Deux fonctions de soutien en facilitent le fonctionnement. Le Product Ops tient l'inventaire des initiatives, fait circuler les décisions, suit les mesures et applique les règles de passage vers un produit partagé. Les plateformes internes fournissent l'environnement où les permissions des agents s'appliquent (section 5.3).

#### 7.1.3 Ce qui change dans le travail du Product Manager

Le travail du Product Manager comporte moins de coordination de la réalisation et davantage de contribution à la décision, à la définition des preuves et à la transmission. Une étude interne d'Anthropic rapporte que ses recruteurs accordent davantage d'importance à l'autonomie et au jugement qu'à l'expertise technique d'exécution ([Anthropic, octobre 2026](https://www.anthropic.com/research/employment-at-anthropic)). C'est le constat d'une seule entreprise, mais il va dans le même sens que les opinions de Ng et Britto citées à la section 3.2.

#### 7.1.4 Un Product Management élargi, assisté en permanence

Une partie des réflexions publiées décrit l'IA comme un moyen d'améliorer les tâches courantes du Product Manager et du développeur : rédiger plus vite, synthétiser plus vite, coder plus vite. Cette lecture laisse de côté un déplacement plus profond. La thèse défendue ici est que le Product Manager pourra exercer réellement l'ensemble de la fonction produit, que beaucoup d'organisations répartissent aujourd'hui entre plusieurs rôles ou laissent sans titulaire : la gestion de produit (product management), la gestion de l'offre (offer management : périmètre commercial, packaging, prix), le marketing produit (positionnement, lancement, outils de vente) et le développement commercial (partenariats, intégrations, canaux), avec l'assistance permanente d'agents. (Hypothèse de l'auteur.)

Le rôle de product owner, au sens de l'administration du backlog et de la rédaction des user stories, n'entre pas dans cette liste, et c'est volontaire. Ce sont précisément les tâches que les agents absorbent. Cagan avertit les product owners et les « feature team product managers », qui exécutent une liste de fonctionnalités décidée ailleurs : si leur contribution se limite à agréger des demandes, générer des feuilles de route, des PRD et des user stories, un agent, un ingénieur ou un designer peut le faire aussi bien ; il parle de « product management theater » ([Product Coaching and AI](https://www.svpg.com/product-coaching-and-ai/)). Rédiger des critères d'acceptation reste utile, mais comme contribution à l'autorité d'acceptation (section 5.2), pas comme cœur du rôle.

Cette thèse n'invente pas un nouveau métier. Le cadre du Pragmatic Institute rassemble depuis longtemps sous la gestion de produit des activités de marché, de stratégie, de prix, de distribution, de positionnement et de lancement, et distingue un pôle stratégique, un pôle technique et un pôle marketing ([Pragmatic Marketing](https://mediafiles.pragmaticmarketing.com/strategic-role-of-product-management/strategic_role_product_management.pdf)). Ce qui change serait la capacité d'une personne ou d'une petite équipe à couvrir ce périmètre. Les six personas d'IA proposées par Britto en donnent une image : analyste de marché, stratège produit, designer produit, responsable commercial (prix, modèles économiques, engagements contractuels), responsable du cycle de vie, et spécialiste de l'assurance produit (réglementation, risques, sécurité) ([Britto](https://arxiv.org/abs/2610.14823)).

Cette thèse vaut surtout pour les produits commerciaux. Cagan observe que le Product Manager d'un produit commercial doit être « personally and deeply immersed with the marketing, sales, funding, monetization, legal, compliance and more », alors que pour un produit interne il lui suffit de comprendre le domaine et ses contraintes, et que s'y présenter comme « le CEO du produit » sonne arrogant ([Commercial vs Internal Products](https://www.svpg.com/commercial-vs-internal-products/)). Pour un outil interne comme l'outil de pilotage financier, l'élargissement vers l'offre et le marché n'a pas de sens ; pour un logiciel vendu, il devient central.

Sur le marketing produit, la thèse s'écarte de SVPG. Dans l'approche de Martina Lauchengco, partenaire de SVPG et autrice de LOVED, le product marketer est un partenaire distinct du Product Manager : le premier se concentre sur le marché et la mise sur le marché, le second sur le produit ([SVPG, Introducing LOVED](https://www.svpg.com/introducing-loved/)). Les deux positions peuvent coexister : dans une grande entreprise, les rôles restent séparés ; dans une entreprise de taille moyenne, où le marketing produit est souvent absent ou partagé, l'assistance des agents peut permettre au Product Manager d'en couvrir une partie. Le débat reste ouvert.

D'autres organisations élargissent le rôle dans une autre direction. LinkedIn a remplacé son programme d'Associate Product Managers par un programme d'Associate Product Builders, qui forme à la fois au code, au design et à la gestion de produit ([Business Insider](https://www.businessinsider.com/linkedin-product-manager-apm-full-stack-builder-2025-12)). L'élargissement se fait là vers la réalisation, non vers le marché et l'offre. Cagan admet que des Product Managers techniquement capables prennent en charge davantage de réalisation, à condition de garder en tête qu'ils construisent pour apprendre, pas pour livrer un produit de qualité commerciale ([Build to Learn vs Build to Earn](https://www.svpg.com/build-to-learn-vs-build-to-earn/)). Itamar Gilad rappelle que l'IA n'impose pas un modèle unique de convergence et qu'il reste souvent utile de garder des rôles séparés dans les grandes organisations ([Itamar Gilad](https://itamargilad.com/ai-pm-jobs/)).

Trois limites encadrent cette thèse. Elle repose sur la qualité de l'étude de marché assistée, dont les fragilités ont été décrites à la section 3.2. Un périmètre plus large ne fait pas du Product Manager le responsable de l'ingénierie, de la sécurité, de l'exploitation, du juridique ou de l'acceptation, qui restent répartis comme dans le tableau ci-dessus. Enfin, la diversité des personas ne garantit pas l'indépendance des analyses : un même modèle jouant le marketing et la stratégie peut produire deux fois le même raisonnement.

Pour les phases de découverte et de validation, la conséquence pratique est d'apporter un contexte beaucoup plus large qu'aujourd'hui : études de marché, segments, modèles d'achat, concurrence et intégrations, conservés dans marche.md et relus comme le reste du patrimoine.

#### 7.1.5 Continuité des compétences

Qui maintiendra un composant réécrit par des agents dans un nouveau langage ? La question doit être posée avant la réécriture. Une organisation peut réduire sa dette technique et créer en même temps une dette de compétences, si personne ne peut plus diagnostiquer le composant sans l'agent qui l'a produit.

#### 7.1.6 Former des experts sans les tâches qui les formaient

Les débutants apprenaient en écrivant des tests, en corrigeant des défauts simples ou en rédigeant des exigences. Si ces tâches passent aux agents, l'acquisition du jugement doit être organisée autrement.

Des signaux descriptifs existent, sans conclusion causale. Brynjolfsson, Chandar et Chen observent, à partir de données de paie, que l'emploi des 22 à 25 ans dans les professions exposées à l'IA est inférieur de 19 % à sa trajectoire de référence, sans écart comparable chez les plus expérimentés, l'écart venant surtout d'une baisse des embauches ([Stanford Digital Economy Lab, août 2026](https://digitaleconomy.stanford.edu/publication/canaries-in-the-coal-mine-six-facts-about-the-recent-employment-effects-of-artificial-intelligence/)). Chez Anthropic, la part des employés techniques juniors est passée de 21 % à 14 % depuis début 2025, et celle des embauches techniques juniors de 27 % à 9 % ([Anthropic, octobre 2026](https://www.anthropic.com/research/employment-at-anthropic)). Ces données décrivent une évolution ; elles n'en établissent pas la cause.

En mathématiques, Quanta rapporte des inquiétudes de chercheurs sur des étudiants formés à lancer des outils sans lire leurs résultats ([Quanta Magazine, octobre 2026](https://www.quantamagazine.org/is-ai-the-end-of-math-as-we-know-it-20261005/)), et Duminil-Copin se demande sur quels problèmes orienter les jeunes doctorants si les plus accessibles peuvent être résolus à tout moment, sans proposer de règle générale ([Duminil-Copin, août 2026](https://proofsandprompts.com/2026/08/30/care-for-a-little-more-ai/)). Ces sources documentent une inquiétude, pas une disparition des parcours de formation.

#### 7.1.7 Le maintien des compétences concerne aussi les experts

La question ne se limite pas aux débutants. Une étude observationnelle menée dans quatre centres polonais a comparé des coloscopies réalisées sans IA avant et après l'introduction d'un outil d'aide : le taux de détection des adénomes est passé de 28,4 % à 22,4 %, soit une baisse de 6 points (rapport de cotes ajusté 0,69) ([Budzyń et al., The Lancet Gastroenterology & Hepatology, 2025](https://www.thelancet.com/journals/langas/article/PIIS2468-1253(25)00133-5/abstract)). Il s'agit de professionnels expérimentés, et d'une étude observationnelle, pas d'un essai randomisé. Avec l'essai d'Anthropic sur l'apprentissage (section 4.1), elle suggère que l'aide peut affecter à la fois l'acquisition d'une compétence et son entretien.

La psychologie de l'apprentissage explique en partie ce mécanisme. Elizabeth et Robert Bjork montrent que des conditions qui ralentissent l'apprentissage apparent (espacer, alterner, se tester) améliorent souvent la rétention et le transfert ([Bjork et Bjork, 2011](https://bjorklab.psych.ucla.edu/wp-content/uploads/sites/13/2016/04/EBjork_RBjork_2011.pdf)). Une aide qui supprime l'effort supprime aussi une partie de ce qui fait apprendre.

Pistes, dont l'efficacité reste à évaluer dans le logiciel :
- conserver des exercices et des périodes de travail sans assistance, sur le modèle de l'entraînement au pilotage manuel ;
- faire expliquer et critiquer des résultats produits par l'IA ;
- confier aux débutants la construction de critères d'acceptation, relus par une personne expérimentée ;
- organiser des diagnostics d'erreurs et des analyses d'incidents ;
- évaluer la capacité à justifier une décision, pas seulement à produire un livrable ;
- définir des parcours de carrière qui récompensent la transmission de pratique, pas seulement la livraison.

Une position inverse mérite d'être mise en regard. Depuis février 2026, SVPG recommande aux Product Managers d'utiliser les modèles de fondation comme coach produit personnel, en jugeant que, bien configurés avec le contexte stratégique de l'entreprise, ils peuvent offrir un coaching « at least as good as most managers », sans égaler encore un bon coach humain. Cagan précise qu'il faut interroger le modèle, chercher la critique et les erreurs plutôt que l'approbation, et que les réponses varient d'un jour à l'autre ([Product Coaching and AI](https://www.svpg.com/product-coaching-and-ai/)). Ce document ne tranche pas entre les deux : l'IA peut accélérer l'apprentissage du jugement, et elle peut aussi en supprimer l'effort formateur. La condition commune semble être la même : que l'IA serve de contradicteur, pas de substitut à la réflexion, ce que Cagan formule lui-même en craignant que les modèles servent d'« alternative to thinking » ([Strong Opinions, Loosely Held](https://www.svpg.com/strong-opinions-loosely-held/)).

### 7.2 Économie, mesure et indicateurs

#### 7.2.1 Un indicateur : le coût par modification acceptée

Le prix par million de jetons (les unités de texte facturées par les fournisseurs de modèles) ne dit pas ce que coûte un changement utile. L'indicateur proposé ici est le coût par modification acceptée : le coût complet d'un changement arrivé en production et resté en production. Cet indicateur n'est pas propre à ce document. Il circule chez des praticiens, par exemple sur [aifinops.dev](https://aifinops.dev/), et l'éditeur Waydev présente un cadre de mesure voisin en précisant qu'il ne s'agit pas d'une étude de résultats ([Waydev](https://waydev.co/ai-coding-roi-research-methodology-2026/)). Aucune méthode de mesure validée n'a été trouvée.

Nous proposons de le décomposer en huit postes mesurables : préparation du contexte, génération, évaluations automatiques, revue humaine, corrections et itérations, déploiement, surveillance, et traitement des défauts découverts après acceptation.

#### 7.2.2 Le prix unitaire baisse, le coût total peut monter

Le rapport AI Index 2025 de Stanford indique que le coût d'interrogation d'un modèle atteignant le niveau de GPT-3.5 sur l'évaluation MMLU (score de 64,8) est passé de 20 dollars par million de jetons en novembre 2022 à 0,07 dollar en octobre 2024, soit une baisse de plus de 280 fois en environ 18 mois ([Stanford HAI, AI Index 2025](https://hai.stanford.edu/ai-index/2025-ai-index-report/research-and-development)). Ce chiffre porte sur un niveau de performance donné, mesuré sur une évaluation donnée. Il ne mesure ni le prix des modèles les plus capables ni le coût d'un changement.

La consommation, elle, augmente. Chez Anthropic, en août 2026, les agents interactifs travaillaient six fois plus d'heures que leurs utilisateurs ([Anthropic, octobre 2026](https://www.anthropic.com/research/employment-at-anthropic)) ; les fichiers de contexte ajoutent en moyenne plus de 20 % de coût d'inférence ([Gloaguen et al.](https://arxiv.org/abs/2602.11988)). Le prix unitaire peut donc baisser pendant que le coût total monte.

Un mécanisme économique ancien renforce ce point. Le paradoxe de Jevons décrit comment une ressource devenue moins chère à utiliser peut voir sa consommation totale augmenter. Chris Ford, chez Thoughtworks, l'applique au logiciel : un code moins cher rend viables de nouveaux usages et augmente la demande ([Thoughtworks](https://www.thoughtworks.com/insights/articles/cheaper-code-wont-kill-software-development)). Si le volume de code augmente, comme le mesurent Chen et Stratton, le volume à vérifier, sécuriser, exploiter et maintenir augmente aussi. (Hypothèse à mesurer, pas fait établi pour le logiciel.) Si la revue humaine domine le coût, ce qui reste à mesurer, le coût d'un changement dépendra davantage de la qualité du contexte et des évaluations que du prix du modèle.

#### 7.2.3 Classer les mesures de productivité

Les résultats de la section 2.2 ne se comparent pas directement. Un essai sur des assistants de complétion ne dit rien des agents ; une mesure individuelle ne dit rien du niveau de l'entreprise ; des tâches terminées ne sont pas des tickets résolus. Chen et Stratton observent d'ailleurs que, pour les assistants (et non les agents), la plupart des effets sur la production ne sont pas significatifs ([Chen et Stratton](https://fion.ac/jellyfish.pdf)). Le document ne retient donc aucun chiffre global de gain.

#### 7.2.4 Un indicateur doit rester relié à sa finalité

La loi de Goodhart décrit le risque qu'une mesure cesse d'être fiable lorsqu'elle devient un objectif. Le nombre de tests réussis ne suffit pas à établir la qualité d'un changement. Le nombre de fonctionnalités livrées ne suffit pas à établir la valeur créée. Un taux élevé de modifications acceptées peut traduire une revue trop indulgente.

Recommandations :
- associer chaque métrique de production à une métrique de résultat, par exemple les modifications acceptées et les défauts découverts dans les 30 jours ;
- mesurer aussi le taux de modifications acceptées sans retouche, le temps de revue humaine et les régressions après fusion ;
- conserver des évaluations indépendantes de celles qui guident la génération ;
- ne pas confondre une meilleure note avec une amélioration démontrée du produit ;
- ne pas dimensionner une équipe sur un multiplicateur de productivité hypothétique.

#### 7.2.5 Deux régimes de financement

Dans les entreprises de plus de 50 personnes, deux régimes coexistent. Le produit industrialisé est développé par l'ingénierie et le Product, et il suit les contraintes juridiques, RGPD, de cybersécurité et d'exploitation. Les outils construits par le métier (tableurs, développements avec l'IA) suivent les règles que leur créateur se donne, sauf si l'entreprise a prévu un cadre. Le budget du premier a tendance à monter et descendre au gré des arbitrages ; le second n'a souvent pas de budget propre, et il peut donc continuer à vivre ou à survivre sans que personne ait décidé de le financer. (Observation de terrain.)

Les sources publiées confirment les deux côtés de cette asymétrie sans la mesurer directement. Côté produit, les cabinets de conseil décrivent le financement par projet, avec une enveloppe fixée puis une équipe dispersée, et recommandent de financer des équipes stables rattachées à un produit ([Bain](https://www.bain.com/insights/how-to-plan-and-budget-for-agile-at-scale/), [McKinsey](https://www.mckinsey.com.br/capabilities/tech-and-ai/our-insights/agile-funding-an-investment-management-approach-to-funding-outcomes)) ; ce sont des recommandations, pas des mesures de volatilité. Le modèle produit de Cagan fait de ce point un principe : passer du financement de fonctionnalités et de projets livrés à date au financement d'équipes produit chargées d'obtenir des résultats ([SVPG, Product Model Concepts](https://www.svpg.com/product-model-concepts/)). TRANSFORMED consacre un chapitre au travail avec la direction financière, où les auteurs recommandent de constater ensemble que le modèle actuel prédit mal les bons choix de financement et les revenus additionnels ([TRANSFORMED, section 24, O'Reilly](https://www.oreilly.com/library/view/transformed/9781119697336/c24.xhtml)). Cagan note enfin que le désir de prévisibilité, très ancré chez les dirigeants, tend à faire primer les engagements de date sur les résultats ([Predictability vs Outcomes](https://www.svpg.com/predictability-vs-outcomes/)). Côté métier, la recherche sur les outils des utilisateurs finaux les décrit comme largement invisibles pour la DSI et la direction ([Panko et Port, cité dans arXiv 1704.01130](https://arxiv.org/pdf/1704.01130)), alors que des audits de tableurs opérationnels ont trouvé des erreurs dans 94 % des 88 fichiers examinés ([Panko, 2007](https://panko.com/Publications/Overconfidence%20JOEUC%202007.doc)). Un outil sans budget n'est pas un outil sans coût : son coût est payé plus tard, en erreurs, en reprise et en conformité.

L'IA accentue cette asymétrie, puisque construire un outil métier devient plus facile, et elle rend la décision plus urgente. Les responsables de l'entreprise devront fixer, pour chaque régime, un budget et des contraintes explicites. (Recommandation.) Concrètement :
- pour le produit industrialisé, un financement stable de l'équipe et de sa capacité IA, revu sur des résultats plutôt que reconstruit à chaque cycle ;
- pour les outils métier, un cadre léger (inventaire, responsable, seuil de passage, section 2.1) et une enveloppe visible pour ceux qui servent de découverte ;
- une règle de transfert : quand un outil métier devient critique, son coût de reprise entre dans le budget du produit cœur plutôt que de rester caché.

#### 7.2.6 Planifier la capacité humaine et IA

Parce qu'un logiciel industrialisé vit plus longtemps que le cycle de vie supposé par les modèles de startup, et qu'il porte une dette technique croissante (section 6.1), son budget doit être relié aux plans financiers de l'entreprise. Il faut connaître, au fil de l'eau, les ressources humaines et IA nécessaires : personnes pour spécifier, relire et accepter ; consommation des agents ; temps de refactorisation et de renforcement des tests. (Recommandation.) Le coût par modification acceptée, décrit plus haut, en est l'unité de suivi ; il ne remplace pas une décision explicite sur la part de capacité réservée à la réduction de la dette.

#### 7.2.7 Mesurer avant d'investir

Une démarche prudente consiste à constituer un banc d'essai interne de 30 à 50 tickets réels, avec leurs critères d'acceptation, pour comparer trois ou quatre modèles avant tout investissement matériel, et le revoir à chaque génération majeure de modèles (recommandation). Quatre scénarios de coût d'infrastructure sont à comparer (API, location de processeurs graphiques, hébergement qualifié SecNumCloud, achat). Des estimations de praticiens situent le coût total sur trois ans d'un serveur à huit processeurs H100 entre 712 000 et 948 000 dollars, électricité, refroidissement et exploitation compris. Ces ordres de grandeur n'ont pas été vérifiés à leur source. Ils conduisent à une conclusion de méthode plus solide que les chiffres eux-mêmes : l'achat ne se justifie qu'après avoir mesuré le taux d'utilisation réel pendant plusieurs mois.

#### 7.2.8 Le coût d'une substitution

Pour un client qui change d'outil, le coût total comprend la migration, la formation, la compatibilité, le risque pendant la transition et la maintenance ultérieure. Ce coût se compare au prix, y compris quand le nouvel outil est gratuit (section 3.1).

### 7.3 Souveraineté de la chaîne et cadre européen

#### 7.3.1 La souveraineté porte sur toute la chaîne

La souveraineté ne se juge pas au modèle seul. Elle porte sur toute la chaîne : le modèle, le service d'inférence qui l'exécute, l'agent, l'environnement de développement, la forge qui héberge le code, la chaîne d'intégration continue, et l'indexation sémantique qui envoie des extraits du code vers un service. Un modèle hébergé en Europe ne suffit pas si l'environnement de développement ou l'indexation passent par un service soumis à un droit tiers.

Un modèle aux poids ouverts (open weight) n'est pas souverain par nature : le critère est l'opérateur de l'inférence, pas la nationalité du créateur du modèle ([Futurium, Commission européenne](https://futurium.ec.europa.eu/en/apply-ai-alliance/community-content/sovereign-infrastructure-sovereign-capability-europe-open-weight-ai-race)). Un modèle américain ou chinois auto-hébergé en Europe peut ainsi offrir plus de maîtrise qu'une API européenne mal contractualisée.

#### 7.3.2 Risques d'accès et qualifications

L'hébergement « en région Europe » chez un fournisseur américain ne supprime pas, selon les analyses courantes, le risque d'accès lié au CLOUD Act ou à la section 702 du FISA. La qualification SecNumCloud 3.2 de l'ANSSI exige un siège dans l'Union et un contrôle capitalistique limitant l'influence d'entités soumises à un droit tiers (élément non vérifié). Il faut aussi distinguer plusieurs qualifications nationales et européennes (EUCS, EUCC, C5, ENS, ACN, HDS) dont la plupart portent sur l'hébergement, pas sur le logiciel. Trois niveaux sont donc à séparer : la conformité du produit (CRA, EUCC), les obligations de l'organisation (NIS2, RGPD) et la qualification de l'hébergement (SecNumCloud, C5, ENS, HDS). Les référentiels cloud ne certifient pas le code.

#### 7.3.3 Dépendances contractuelles

Deux dépendances moins visibles sont signalées par des praticiens (éléments non vérifiés auprès des sources primaires) : des licences de modèles aux poids ouverts assorties de seuils d'usage commercial, et le retrait de modèles par des hébergeurs avec redirection automatique vers un autre modèle. La seconde touche directement l'acceptation : un changement accepté avec un modèle peut être reproduit plus tard avec un autre, sans que personne l'ait décidé. Recommandation : fixer les versions des modèles utilisés et consigner ce choix dans exploitation.md.

#### 7.3.4 Obligations réglementaires

Les calendriers suivants ont été vérifiés auprès des sources officielles :

- règlement européen sur l'IA : entré en vigueur le 1er août 2024 ; obligations sur les modèles d'usage général et gouvernance depuis le 2 août 2025 ; pouvoirs d'exécution depuis le 2 août 2026 ; systèmes à haut risque de l'annexe III à partir du 2 décembre 2027 ([Commission européenne](https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai)) ;
- règlement sur la cyberrésilience (CRA) : entré en vigueur le 10 décembre 2024 ; obligations de signalement depuis le 11 septembre 2026 ; obligations principales à partir du 11 décembre 2027 ([Commission européenne](https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act)) ;
- NIS2 en France : la page de l'ANSSI consultée décrit le processus de transposition sans permettre d'en établir l'état juridique exact ; le référentiel ReCyF est disponible depuis le 17 mars 2026 comme document de travail ([ANSSI](https://cyber.gouv.fr/reglementation/cybersecurite-systemes-dinformation/directives-nis-nis2-et-dispositif-saiv/directive-nis-2/)) ;
- pour le logiciel industriel, la série de normes IEC 62443 sur la cybersécurité des systèmes d'automatisation et de contrôle.

Le CRA impose aux fabricants de concevoir les produits comportant des éléments numériques selon des exigences essentielles de cybersécurité ([Commission européenne](https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act)). Le code généré par IA reste sous la responsabilité du fabricant : gestion des vulnérabilités, liste des composants, traçabilité. Le texte ne distingue pas le code écrit par une personne de celui écrit par un agent. Les exigences de NIS2 sur la sécurité de la chaîne d'approvisionnement et du développement (article 21) concernent aussi les outils d'IA utilisés ; leur déclinaison exacte doit être vérifiée sur le texte de la directive et de sa transposition.

#### 7.3.5 Relier l'autorité d'acceptation aux obligations du fabricant

C'est sur ce point que le cadre européen donne à la proposition d'autorité d'acceptation son poids le plus concret. Si le fabricant reste responsable du produit quelle que soit l'origine du code, il doit pouvoir montrer qui a accepté quoi, sur quelles preuves et dans quelles conditions. La trace écrite des raisons de l'acceptation, proposée à la section 5.2, devient alors un élément de démonstration de la conformité, pas seulement une bonne pratique. (Hypothèse ; aucune déclinaison de ce type n'a été trouvée dans un texte européen.)

La régulation bancaire américaine offre une doctrine utile, à titre d'analogie. Depuis 2011, la guidance SR 11-7 sur le risque de modèle repose sur la contradiction effective (effective challenge) : une analyse critique des modèles par des parties compétentes et indépendantes ([Federal Reserve, SR 11-7](https://www.federalreserve.gov/boarddocs/srletters/2011/sr1107a1.pdf)). La guidance SR 26-2 du 17 avril 2026 la remplace ([Federal Reserve, SR 26-2](https://www.federalreserve.gov/supervisionreg/srletters/SR2602.htm)). Selon l'analyse du cabinet Orrick, elle conserve la contradiction effective et la définit par trois conditions, l'expertise appropriée, une indépendance suffisante et une influence suffisante pour obtenir des changements, et elle exclut explicitement de son champ les modèles d'IA générative et agentique ([Orrick, avril 2026](https://www.orrick.com/en/Insights/2026/04/Agencies-Overhaul-Model-Risk-Management-Guidance-for-Banks-Heres-What-Changed)). Ce dernier point n'a été lu que chez Orrick et doit être confirmé sur le texte de la guidance.

Les trois conditions de la contradiction effective complètent les quatre conditions de la section 5.2 : l'autorité d'acceptation doit avoir la compétence pour juger, être assez indépendante de ceux qui ont produit le changement, et avoir assez d'influence pour obtenir une correction. L'exclusion de l'IA générative et agentique, si elle est confirmée, montre qu'il n'existe pas encore de doctrine équivalente pour les agents, même dans un secteur où la question est ancienne.

#### 7.3.6 Droits et provenance d'une reconstruction

La capacité technique à reconstruire un logiciel ne supprime pas les contraintes de propriété intellectuelle. Nous recommandons d'examiner séparément les droits d'accéder, d'analyser, de réutiliser et de distribuer, sans présumer qu'un droit d'utilisation les couvre tous. Les flux de données d'un agent d'analyse se classifient comme les autres : binaires, captures, pseudocode et résultats. Un connecteur MCP n'est ni local ni souverain du seul fait qu'il utilise ce protocole. Ces recommandations ne remplacent pas un avis juridique.

---

## 8. Prospective

### 8.1 Trois scénarios et un même test

#### 8.1.1 Stratégies d'acteurs

Certains acteurs intègrent toute la chaîne. Cursor a annoncé le 14 août 2026 avoir été acquis par SpaceX, au terme d'un partenariat commencé en avril ([Cursor, août 2026](https://cursor.com/blog/joining-spacex)). Ce fait est établi. La lecture qui relie Grok, Cursor et le projet Macrohard en une stratégie d'automatisation du travail sur ordinateur est une interprétation des annonces, pas une architecture publiée. Les déclarations sur la disparition du code traditionnel sont des intentions, pas des capacités démontrées. La réflexion de ce document ne dépend pas de leur réalisation : la question reste posée même si elles ne se réalisent pas.

#### 8.1.2 Trois scénarios

Trois scénarios restent ouverts. Ils sont présentés à égalité, sans désigner le plus probable.

Scénario A, le développement produit en étoile. Les métiers construisent en autonomie accompagnée, et le Product devient une pratique diffusée dans l'organisation. Condition : une gouvernance adaptée, avec un inventaire des outils, des responsables identifiés et un seuil de passage vers le produit partagé. Conséquence : le Product central garde la cohérence du portefeuille ; les antennes diffusent la pratique, forment et auditent.

Scénario B, la spécification comme source principale. La spécification devient l'artefact maintenu, et le code est traité comme un résultat régénérable. Condition : une vérification indépendante fiable et une gestion de la connaissance très disciplinée. Conséquence : le travail se concentre sur la maintenance de la spécification et l'arbitrage des écarts ; la justesse de la spécification (section 4.2) devient la question centrale.

Scénario C, une automatisation très large. Des agents produisent des logiciels dont le code n'est plus lu par des personnes ; les métiers expriment une intention, les agents réalisent. Condition : une confiance élevée dans la vérification des résultats, pas seulement dans leur génération. Conséquence : même dans ce scénario, la transmission reste une question ouverte. Qui sait ce que le système doit faire, et comment vérifier une évolution ?

#### 8.1.3 Ce qui reste stable

Dans les trois scénarios, quatre éléments restent nécessaires : la transmission de la connaissance, la preuve, la décision sur la valeur et une responsabilité identifiée. Leur forme change ; leur nécessité ne change pas.

#### 8.1.4 Questions ouvertes

Plusieurs questions ne peuvent pas être tranchées avec les éléments disponibles :

- Brooks a-t-il encore raison ? Certains annoncent des gains d'un ordre de grandeur sur le codage ; les données de Chen et Stratton, sans hausse significative des tickets résolus, vont plutôt dans son sens. Le débat est ouvert.
- Le passage du prototype au produit d'entreprise sera-t-il automatisé ? Cagan juge la question ouverte à 3 à 5 ans et n'a rien vu qui lui donne confiance ; il rappelle aussi qu'il est risqué d'affirmer qu'une chose ne peut pas arriver ([Prototypes vs Products](https://www.svpg.com/prototypes-vs-products/)).
- La revue humaine tiendra-t-elle quand le volume augmentera, ou deviendra-t-elle la tâche de vigilance défaillante que décrivent les facteurs humains ?
- Le déplacement vers la revue est-il transitoire, le temps que les outils de revue progressent, ou structurel ?
- Quelles activités du Product Management disposent d'un retour d'évaluation assez rapide et fiable pour être largement assistées, et lesquelles resteront évaluées tardivement et imparfaitement ?
- Les équipes sauront-elles maintenir des systèmes d'évaluation indépendants, ou les contrôles qui guident les agents deviendront-ils aussi ceux qui servent à les accepter ?
- Comment se formera le jugement des futurs responsables produit, ingénieurs et spécialistes, et comment s'entretiendra celui des expérimentés ?
- Les progrès obtenus dans les domaines dotés de vérificateurs formels, comme les mathématiques, se diffuseront-ils au logiciel d'entreprise, où l'énoncé se découvre en chemin ? Les éléments disponibles ne permettent pas de répondre.
- Quelle forme prendra la différenciation des produits, et le modèle en étoile tiendra-t-il à grande échelle ?

#### 8.1.5 Questions pour la recherche

Sept questions paraissent instruisables par des travaux empiriques :

1. Comment mesurer la vérifiabilité d'une tâche indépendamment du fait qu'elle a été automatisée ?
2. Le déplacement vers la revue est-il transitoire ou structurel ?
3. Quelle mesure de la pertinence, et pas seulement de la conformité, peut être instrumentée dans une équipe produit ?
4. La baisse de compréhension mesurée à court terme persiste-t-elle, et affecte-t-elle l'exploitation et la maintenance ?
5. Quels fichiers de contexte améliorent réellement les résultats, et pour quel coût ?
6. Comment instrumenter le coût par modification acceptée de façon comparable entre organisations ?
7. Comment répartir l'autorité d'acceptation dans une organisation soumise au CRA lorsque la majorité du code est produite par des agents ?

Britto propose quatre axes complémentaires, centrés sur le travail du Product Management lui-même : en quoi une participation permanente de l'IA change le travail par rapport à une assistance ponctuelle ; quand l'IA élargit l'exploration et quand elle renforce des schémas existants ; quelles activités doivent être opérées par l'IA, dirigées par des humains ou collaboratives, et comment l'usage prolongé de l'IA affecte le jugement des juniors comme des seniors ; enfin, comment une IA partagée entre Product Management et R&D modifie leur coordination, au risque que les deux fonctions s'appuient sur la même interprétation erronée ([Britto](https://arxiv.org/abs/2610.14823)).

#### 8.1.6 Le test commun

Un même test départage les trois scénarios, et il peut être mené dès aujourd'hui :

> Une personne qui n'a pas créé l'application peut-elle, avec un agent, comprendre ses règles, proposer une évolution et démontrer ses effets, sans dépendre de la mémoire de son prédécesseur ?

---

## 9. Conclusion

Quand des agents réalisent et que les fonctionnalités deviennent reproductibles, la valeur d'un produit se déplace vers trois activités collectives : décider ce qui mérite d'exister, transmettre une connaissance qui permet de le faire évoluer, et établir que ce qui est livré fait ce qu'il doit et sert à ce pour quoi il a été construit.

Le Product Management contribue à relier ces activités à la valeur recherchée. Il ne les porte pas seul. L'ingénierie reste responsable de ses choix techniques, les métiers de leurs règles, la sécurité et l'exploitation de leurs contrôles, et l'acceptation revient à une autorité désignée, dotée des moyens d'exercer son rôle. La contribution propre du Product Management tient surtout à la tenue des distinctions : vérifier et valider, conformité et justesse, résultat correct et résultat compris, outil local et produit partagé, ce qui est établi et ce qui est supposé.

Une organisation n'a pas besoin de savoir quel scénario se réalisera pour agir. Elle peut dès maintenant :

- classifier ses artefacts selon leur contenu, avant que des agents y accèdent ;
- maintenir une spécification de référence à côté du code, en séparant l'existant de la cible ;
- versionner son système d'évaluation et en garder une part indépendante de la génération ;
- désigner ses autorités d'acceptation, avec le temps, l'information, le pouvoir de refuser et une trace des raisons ;
- définir les permissions de ses agents selon les conséquences d'une erreur et le couplage des étapes ;
- mesurer le coût par modification acceptée, associé à des indicateurs de résultat ;
- organiser le maintien des compétences, des débutants comme des experts ;
- fixer un budget et des contraintes explicites pour le produit industrialisé et pour les outils construits par les métiers ;
- tenir un contexte de marché sourcé et daté, relu comme le reste du patrimoine ;
- conduire périodiquement le test du successeur.

Aucune de ces mesures n'a été évaluée en tant que dispositif complet. Ce sont des propositions à éprouver, et la première version d'un travail qui devra être confronté à des projets réels.

# Annexes

## A. Glossaire

Chaque entrée donne une définition courte et renvoie aux sections où la notion est expliquée. Les définitions sont formulées pour ce document ; elles ne remplacent pas les définitions normatives.

| Terme | Définition | Sections |
|---|---|---|
| Agent IA | Système qui enchaîne seul plusieurs actions (lire, modifier, tester, corriger) pour accomplir une tâche, sous des permissions données | 1, 5.1 |
| AGENTS.md | Format ouvert de fichier placé dans un dépôt pour donner aux agents le contexte et les consignes d'un projet | 4.1 |
| AI Act (règlement européen sur l'IA) | Règlement de l'Union européenne qui encadre les systèmes d'IA selon leur niveau de risque | 5.2, 7.3 |
| Apprentissage par renforcement | Entraînement d'un modèle par essais successifs, chacun recevant une récompense calculée | 2.2 |
| Autorité d'acceptation | Personne ou instance désignée pour accepter un changement à un niveau donné (technique, métier, produit et exploitation), dans des conditions explicites | 5.2, 7.3 |
| Banc d'évaluation (benchmark) | Ensemble standardisé de tâches servant à comparer des modèles ; son score n'a de sens qu'avec sa date et ses limites | 1, 5.2 |
| Biais d'automatisation | Tendance à suivre une recommandation automatique, ou à ne pas voir ce qu'elle n'a pas signalé | 5.2 |
| Boucle inverse du SDD | Démarche qui part d'un logiciel existant pour reconstruire une description de son comportement, puis décider de la cible | 4.2, 6.1 |
| Build to learn, build to earn | Distinction de Cagan : construire pour apprendre (découverte, prototypes) et construire pour vendre (livraison d'un produit de qualité commerciale) | 1, 3.2, 4.2 |
| Citizen development | Construction d'outils par des personnes des métiers, dans un cadre prévu par l'organisation | 2.1 |
| CLOUD Act, FISA 702 | Textes américains permettant, sous conditions, l'accès des autorités à des données détenues par des fournisseurs soumis au droit américain | 7.3 |
| Complexité essentielle et accidentelle | Distinction de Brooks : la première tient à la conception (que doit faire le logiciel), la seconde aux outils | 2.1 |
| Contexte persistant | Mémoire qui survit aux sessions d'un agent (spécification, règles, décisions), sans qu'il faille la répéter ; lié au SDD | 4.2 |
| Contournement de spécification | Comportement qui satisfait la lettre d'un objectif sans atteindre le résultat voulu | 4.1, 5.2 |
| Contradiction effective | Analyse critique d'un modèle par des parties compétentes, indépendantes et assez influentes pour obtenir des changements (régulation bancaire américaine) | 7.3 |
| Couplage | Degré d'enchaînement des étapes d'un système sans délai ni marge ; un couplage serré propage vite les erreurs | 5.1 |
| Coût par modification acceptée | Coût complet d'un changement arrivé en production et resté en production | 7.2 |
| CRA (règlement sur la cyberrésilience) | Règlement européen fixant des exigences de cybersécurité pour les produits comportant des éléments numériques | 2.1, 7.3 |
| Dette d'intention | Absence de trace des raisons d'un choix | 4.1 |
| Dette de compréhension | Écart entre le code qui fonctionne et la compréhension qu'en ont les personnes qui doivent le maintenir | 4.1 |
| Dual run | Exécution parallèle de l'ancien et du nouveau système pour comparer leurs résultats | 5.2, 6.1 |
| Équivalence | Propriété d'un nouveau système qui se comporte comme l'ancien ; ne prouve pas la correction | 5.2 |
| Évaluations (evals) | Jeu d'exemples avec résultats attendus, servant à mesurer le comportement d'un système, notamment d'un produit contenant de l'IA | 4.2 |
| Feature team | Équipe qui exécute une liste de fonctionnalités décidée ailleurs, par opposition à une équipe chargée d'un résultat (Cagan) | 7.1 |
| Financement par produit | Budget attribué à une équipe stable rattachée à un produit, revu sur des résultats, par opposition au financement par projet | 7.2 |
| Forward deployed engineer | Ingénieur placé chez des clients pour comprendre leurs problèmes et prototyper, une plateforme généralisant ensuite les solutions (Cagan, à propos de Palantir) | 2.1 |
| Fusion team | Équipe mêlant compétences métier et technologiques | 7.1 |
| Harness | Environnement de contrôle d'un agent : guides préventifs et capteurs de rétroaction | 5.2 |
| IEC 62443 | Série de normes sur la cybersécurité des systèmes d'automatisation et de contrôle industriels | 7.3 |
| Lean | Langage permettant à un programme de vérifier chaque étape d'une démonstration mathématique | 4.2, annexe G |
| Logiciel de type E | Logiciel embarqué dans le monde réel, qui doit être adapté en permanence (Lehman) | 4.2 |
| Loi de Goodhart | Une mesure qui devient un objectif cesse d'être une bonne mesure | 4.1, 7.2 |
| Loi de Hyrum | Avec assez d'utilisateurs, tous les comportements observables d'un système finissent par être utilisés, documentés ou non | 5.2, 6.1 |
| marche.md | Fichier de connaissance proposé pour le contexte business d'un produit : segments, taille, modèle d'achat, concurrence, chaque donnée avec sa source et sa date | 3.2, 4.1 |
| MCP (Model Context Protocol) | Protocole standard de connexion entre un agent et des outils ou des sources de données | 2.3, 3.1 |
| Modèle produit (product operating model) | Modèle de Cagan et SVPG : équipes produit financées pour obtenir des résultats, découverte et livraison continues, stratégie fondée sur des éléments de preuve | 1, 7.2 |
| N1, N2, N3 | Niveaux de confidentialité des artefacts (public, interne, sensible) ; ce ne sont pas des niveaux d'autonomie | 4.2, 5.1 |
| NIS2 | Directive européenne sur la cybersécurité des entités essentielles et importantes | 2.1, 7.3 |
| Observation de terrain | Statut d'un constat de l'auteur, tiré de sa pratique, recoupé si possible mais non mesuré | 1 |
| Offer management (gestion de l'offre) | Conception et pilotage de l'offre commerciale : périmètre, packaging, prix, conditions | 7.1 |
| Open weight | Modèle dont les poids sont publiés et peuvent être exécutés par un tiers | 7.3 |
| Oracle (problème de l') | Mécanisme permettant de dire si un résultat est correct ; le problème est la difficulté ou le coût d'en disposer | 2.2 |
| Outil métier comme produit de découverte | Outil construit par le métier qui révèle un besoin ou une règle, dont la connaissance peut être transférée au produit cœur | 2.1 |
| Participation persistante | IA qui observe, rapproche et signale en continu sans être sollicitée (Britto) ; non couverte par le SDD | 4.2 |
| Product management theater | Expression de Cagan pour un rôle produit réduit à produire feuilles de route, PRD et user stories, tâches qu'un agent peut faire | 7.1 |
| Product marketing (marketing produit) | Positionnement, messages, lancement et outils de vente d'un produit | 7.1 |
| Pull request | Proposition de modification du code soumise à revue avant intégration | 2.2, 5.2 |
| Quatre risques | Valeur, utilisabilité, faisabilité, viabilité (Cagan) ; le PM porte la valeur et la viabilité, le design l'utilisabilité, l'ingénierie la faisabilité | 3.2 |
| REA (Reverse Engineer Anything) | Serveur MCP présenté par MindStudio qui donne à un agent l'accès à des outils de rétro-ingénierie | 2.3, 6.1 |
| Répondants synthétiques | Réponses à une enquête simulées par un modèle ; utiles pour explorer, biaisées vers les attitudes positives | 3.2 |
| SBOM | Liste des composants logiciels d'un produit, générée à chaque construction | 5.1, 7.3 |
| SDD (Spec-Driven Development) | Famille de pratiques où une spécification versionnée sert de référence aux agents ; trois approches : spec-first, spec-anchored, spec-as-source | 4.2 |
| SecNumCloud | Qualification de l'ANSSI pour les services d'informatique en nuage | 5.1, 7.3 |
| Shadow AI | Outils fondés sur l'IA construits ou utilisés hors du cadre prévu par l'organisation | 2.1 |
| Strangler fig (figuier étrangleur) | Modernisation progressive qui remplace un système capacité par capacité derrière une couche de routage | 6.1 |
| Test du successeur | Vérifier qu'une personne qui n'a pas créé l'application peut, avec un agent, la comprendre, la faire évoluer et démontrer les effets | 4.1, 8.1 |
| Validation | Établir que ce qui a été demandé valait la peine d'être fait (construire le bon produit) | 3.2 |
| Vérificateur (règle du) | Thèse de Jason Wei : la facilité d'entraîner une IA à une tâche serait proportionnelle à la facilité d'en vérifier les résultats | 2.2 |
| Vérification | Établir qu'une réalisation fait ce qui a été demandé (construire le produit correctement) | 3.2 |
| Vibe coding | Génération rapide d'un logiciel à partir d'intentions vagues, sans spécification maintenue | 6.1 |
| WASI, WIT | Interfaces système (WASI) et langage de description d'interfaces (WIT) du modèle de composants WebAssembly | 5.1, 5.3 |
| WebAssembly (Wasm) | Format de code exécutable dans les navigateurs et ailleurs, cible de compilation pour plusieurs langages | 5.3 |
| WebGPU | Interface web donnant accès au processeur graphique de l'appareil pour le rendu et le calcul | 5.3 |
| Zone de déformation morale | Situation où une personne porte la responsabilité d'un système automatisé sur lequel elle avait peu de contrôle (Elish) | 5.2 |

## B. Inventaire des sujets

Cette annexe recense les 64 sujets traités par le document. Pour chacun, elle donne une formulation courte, la question qui reste ouverte, le domaine auquel il se rattache (annexe C) et les sections du corps où il est traité.

| # | Sujet | Formulation | Question ouverte | Domaine | Sections |
|---|---|---|---|---|---|
| 1 | Les métiers construisent leurs propres outils | DAF, juristes, RH et commerciaux créent dashboards, assistants et automatisations avec Claude, sans passer par le Product | Qu'est-ce qui rend un outil « construit par le métier » acceptable ou non ? | Autonomie des métiers | 2.1 ; 7.1 |
| 2 | Continuité avec les fichiers Excel | Les métiers construisent déjà des outils dans Excel ; le problème est la transmission, pas la création | Comment garantir la reprise d'un outil après le départ de son créateur ? | Patrimoine de connaissance | 2.1 ; 4.1 |
| 3 | Fichiers de connaissance dans le repository | Collecter les échanges, les transformer en fichiers de contexte versionnés dans le dépôt | Quelle structure et quel processus de validation ? | Patrimoine de connaissance | 4.1 ; 4.2 |
| 4 | Ambitions de Musk (Grok, Cursor, Macrohard) | Stratégie intégrée : datacenters, modèle, agent, automatisation du travail sur ordinateur | Que deviennent les développeurs et le Product ? | Prospective | 8.1 |
| 5 | Boucle besoin, puis agents, puis preuves | Le développement produit devient une boucle entre un besoin métier, des agents qui réalisent, et des preuves de correction | Qui peut accepter un changement, selon quel risque ? | Preuves et acceptation | 2.2 ; 3.2, 5.2, 5.3 |
| 6 | Déplacement de la rareté vers la vérification | Produire du code plus vite que les humains ne peuvent le relire déplace le goulot d'étranglement | Comment dimensionner la revue ? | Preuves et acceptation | 2.2 ; 5.2, 7.2 |
| 7 | Mémoire de l'application (cinq ensembles) | Contexte/objectifs, règles métier, décisions, vérification, exploitation/responsabilité | Comment distinguer fait validé, hypothèse et interprétation ? | Patrimoine de connaissance | 4.1 |
| 8 | Trois régimes d'autonomie selon la criticité | Outil personnel / application partagée / système critique | Comment définir les permissions concrètes ? | Agents et autonomie | 5.1 ; 5.3 |
| 9 | Distinction développement automatisé vs produit autonome | Automatiser le développement ne rend pas le produit autonome | Où placer le curseur dans un produit donné ? | Agents et autonomie | 5.1 ; 8.1 |
| 10 | Répartition des responsabilités (métier, Product, ingénierie, etc.) | Tableau de répartition : chacun a une valeur attendue | Qui est responsable en cas d'incident ? | Organisation et compétences | 7.1 ; 5.2 |
| 11 | Spec-Driven Development et niveaux N2/N3 | Tableau de phases avec contribution IA, niveau et travail humain restant | Comment définir N2/N3 concrètement ? | Spécifications et SDD | 4.2 ; 5.1, 6.1 |
| 12 | Équivalence vs correction | L'équivalence avec l'ancien ne suffit pas à démontrer la correction | Comment classer les écarts ? | Preuves et acceptation | 5.2 ; 6.1 |
| 13 | Réserve sur le dual run sur trafic réel | Pour un système financier/industriel, ne pas autoriser deux versions à produire en parallèle | Quelle méthode de comparaison selon le risque ? | Preuves et acceptation | 5.2 ; 6.1 |
| 14 | Distinguer comportement existant et comportement cible | Le code décrit un comportement, pas nécessairement une intention | Comment séparer les deux spécifications ? | Spécifications et SDD | 4.2 ; 6.1 |
| 15 | Souveraineté de toute la chaîne (modèle, inférence, agent, IDE, forge, CI) | Open weight ≠ souverain ; SecNumCloud ; architecture à trois niveaux de confidentialité | Comment vérifier chaque maillon ? | Souveraineté et dépendances | 7.3 ; 5.1 |
| 16 | NIS2, CRA, AI Act, IEC 62443 | Le code généré reste sous votre responsabilité de fabricant ; notifications 24 h/72 h | Quels calendriers et obligations réels en France ? | Sécurité et cadre européen | 7.3 ; 5.2 |
| 17 | Scénarios from scratch et migration legacy | Amadeus (2 000 personnes-années), strangler fig, discovery en N3 | Quels gains réalistes avec l'IA ? | Modernisation de l'existant | 6.1 |
| 18 | Économie : coût par modification acceptée | Indicateur principal ; prix par million de tokens insuffisant | Comment mesurer sans instrumenter ? | Économie et mesure | 7.2 ; 2.2 |
| 19 | Product Builder en étoile (fusion teams) | Noyau central + antennes embedded dans les métiers ; rôle former/auditer/arbiter | Ce modèle tient-il à grande échelle ? | Organisation et compétences | 7.1 ; 3.2, 8.1 |
| 20 | Trois étages d'usage IA (Knowledge/Insight/Production) | Le métier traverse Knowledge, puis Insight, puis Production ; sauter les étages fait exploser les outils en vol | Comment séparer l'usage analytique de l'usage productif ? | Autonomie des métiers | 2.1 |
| 21 | Qualité et provenance des données | Dashboard finance faux pendant six mois (requête sur table avant retraitement) | Quelle donnée fait référence ? | Preuves et acceptation | 2.1 ; 5.2 |
| 22 | Hallucinations et responsabilité | Assistant legal qui hallucine une clause dans un NDA relu trop vite | Qui valide quoi ? | Preuves et acceptation | 2.1 ; 5.2 |
| 23 | CLOUD Act, FISA 702, SecNumCloud | L'hébergement « en région Europe » ne supprime pas le risque ; SecNumCloud 3.2 exige siège UE + contrôle capitalistique | Quelle qualification vérifier offre par offre ? | Souveraineté et dépendances | 7.3 |
| 24 | Télémétrie IDE, indexation sémantique, secrets dans le contexte | Un modèle hébergé en Europe ne suffit pas si l'IDE, l'agent ou l'indexation passent par un service américain | Quels flux sortir du périmètre ? | Souveraineté et dépendances | 7.3 ; 5.1 |
| 25 | Licences open weight à seuils | Licence « MIT modifiée » de Mistral avec seuil de 20 M$ ; licences restrictives levées via hébergement | Quels droits selon l'usage ? | Souveraineté et dépendances | 7.3 |
| 26 | Dépréciation et redirection automatique de modèles | Scaleway/OVHcloud retirent des modèles avec redirection silencieuse | Comment fixer les versions ? | Souveraineté et dépendances | 7.3 ; 7.2 |
| 27 | Scénarios économiques API/location/SecNumCloud/achat | Quatre scénarios de coût pour 5 développeurs | À quel moment acheter ? | Économie et mesure | 7.2 ; 7.3 |
| 28 | TCO complet (électricité, refroidissement, exploitation) | TCO 3 ans d'un nœud 8x H100 entre 712 k$ et 948 k$ | Comment mesurer le taux d'utilisation réel ? | Économie et mesure | 7.2 |
| 29 | Qualifications européennes et nationales (EUCS, EUCC, C5, ENS, ACN, HDS) | La plupart s'appliquent à l'hébergement, pas au logiciel ; les schémas nationaux restent le passeport réel | Quelle qualification viser selon le marché visé ? | Sécurité et cadre européen | 7.3 |
| 30 | Tests industriels et simulation | Code OT/PLC : revue par expert + tests sur simulateur avant tout essai sur équipement | Comment valider un code généré pour un équipement physique ? | Preuves et acceptation | 5.2 ; 5.1 |
| 31 | Rétro-ingénierie agentique via REA et MCP | Un agent orchestre des outils existants pour analyser et reconstruire un logiciel | Quel apport par rapport à un agent sans REA ? | Modernisation de l'existant | 2.3 ; 6.1 |
| 32 | Reconstitution depuis les binaires ou le comportement observable | Pseudocode, indices, inconnues et comparaison avec l'original | Quelles fonctions cachées et quelles exceptions restent inconnues ? | Patrimoine de connaissance ; preuves et acceptation | 2.3 ; 4.1, 5.2 |
| 33 | Boucle inverse du SDD | Partir d'un logiciel pour reconstruire une description de l'existant, puis décider du comportement cible | Comment éviter de transformer un comportement observé en exigence approuvée ? | Spécifications et SDD | 4.2 ; 2.3 |
| 34 | Différenciation lorsque les fonctionnalités sont plus faciles à reproduire | La reproductibilité des interfaces pourrait déplacer la valeur vers d'autres actifs | Quelles composantes de la valeur produit sont réellement difficiles à reproduire ? | Finalité du Product Management ; prospective | 3.1 ; 3.2, 8.1 |
| 35 | Droits, provenance et confidentialité d'une reconstruction | Le droit d'accéder, d'analyser et de redistribuer doit être examiné séparément des capacités techniques | Quel périmètre est autorisé et quels flux l'agent peut-il utiliser ? | Sécurité et cadre européen ; souveraineté et dépendances | 7.3 ; 2.3 |
| 36 | Reconstruction multimodale sans accès au code | Documentation, captures, démonstrations et comportements observables peuvent servir à définir une implémentation indépendante | Quelles sources ont réellement été utilisées et avec quelle couverture ? | Spécifications et SDD ; modernisation de l'existant | 2.3 ; 4.2 |
| 37 | Couverture apparente et aptitude à remplacer un produit | Une fonction présente dans un menu n'est pas une fonction validée dans un travail réel | À quel niveau de preuve parle-t-on de remplacement ? | Preuves et acceptation | 2.3 ; 3.1, 5.2 |
| 38 | Substitution partielle par segment d'usage | Un substitut incomplet pourrait suffire à certains utilisateurs sans égaler toute la suite | Quel ensemble de tâches devient remplaçable et à quel coût total ? | Finalité du Product Management ; économie et mesure | 3.1 ; 7.2 |
| 39 | Valeur durable, migration et différenciation | Fiabilité, compatibilité, intégration et facilité de sortie doivent être examinées séparément du nombre de fonctions | Quels avantages rendent un service utile, plutôt que seulement difficile à quitter ? | Finalité du Product Management ; prospective | 3.1 ; 8.1 |
| 40 | Produits pilotables par les agents | UI, CLI et MCP exposent un même moteur de commandes | Si l'agent devient l'interface, où le produit apporte-t-il sa valeur ? | Cycle de vie produit ; agents et autonomie | 3.1 ; 5.3 |
| 41 | Typage et compilateur comme retour pour les agents | Certains défauts deviennent des erreurs automatiquement détectables | Quelles propriétés sont contrôlées, et lesquelles ne le sont pas ? | Preuves et acceptation ; architecture | 5.2 ; 5.3 |
| 42 | Séparer moteur, interface et canaux d'accès | Un moteur peut servir l'UI, une API ou un agent sans les confondre | Quelles frontières facilitent la reprise et le remplacement ? | Architecture ; valeur durable | 5.3 ; 3.1 |
| 43 | Architecture polyglotte plutôt que tout Rust | Choisir les langages par composant et conserver les écosystèmes utiles | Le gain technique compense-t-il les coûts de maintenance et d'intégration ? | Architecture ; économie et mesure | 5.3 ; 7.2 |
| 44 | WebAssembly comme cible portable | Mutualiser certains composants entre natif et navigateur | Que faut-il adapter et revalider sur chaque cible ? | Architecture ; cycle de vie | 5.3 |
| 45 | Calcul local, WebGPU et données | Certaines opérations peuvent être proposées sur l'appareil plutôt que sur un serveur | Quelles limites matérielles, quels flux résiduels et quel mode dégradé ? | Souveraineté ; valeur durable | 5.3 ; 7.3 |
| 46 | Composants WASI, contrats WIT et capacités | Décrire des interfaces typées et les services nécessaires au composant | Comment vérifier aussi la sémantique et les droits réellement accordés ? | Architecture ; agents et autonomie | 5.1 ; 5.3 |
| 47 | Coût de la boucle de validation | Compiler, tester, corriger et relire peuvent conditionner le débit accepté | Quel coût complet par changement validé sur le projet réel ? | Économie et mesure | 7.2 ; 5.2 |
| 48 | Migration ciblée et continuité des compétences | Remplacer un composant justifié par le risque ou les mesures, pas tout le patrimoine | Qui pourra maintenir le résultat et avec quelles preuves d'équivalence ? | Modernisation ; organisation ; architecture | 6.1 ; 7.1 |
| 49 | Asymétrie entre production et vérification | La facilité d'entraîner une IA à une tâche dépendrait de la facilité de vérifier ses résultats | Dans quelle mesure cette grille s'applique-t-elle à des tâches dont l'énoncé se découvre en chemin ? | Vérifiabilité, évaluation et compréhension | 2.2 ; 8.1 |
| 50 | Grille d'analyse des activités en six dimensions | Clarté de l'objectif, qualité de l'évaluation, délai de retour, couverture, coût d'un échec, réversibilité | La grille aide-t-elle réellement à décider de ce qui est délégué ? | Vérifiabilité ; agents et autonomie | 2.2 (principe), annexe F (grille) ; 3.2, 5.1 |
| 51 | Système d'évaluation comme patrimoine versionné et source de risque | Règles, données de référence, tests, simulations et critères d'acceptation jugent la production | Comment éviter qu'un contrôle incomplet ou dépassé confirme un comportement faux ? | Vérifiabilité ; patrimoine de connaissance ; preuves | 4.1 ; 5.2 |
| 52 | Conformité à une spécification et justesse de la spécification | Une réalisation conforme peut répondre à la mauvaise question | Qui vérifie la justesse de la spécification, et sur quels exemples ? | Spécifications et SDD ; vérifiabilité | 4.2 ; 3.2, 5.2 |
| 53 | Trois niveaux d'acceptation et autorité d'acceptation | Technique, métier, produit et exploitation | Qui accepte à chaque niveau, selon quel risque ? | Preuves et acceptation ; organisation | 5.2 ; 3.2, 7.1 |
| 54 | Indicateurs reliés à leur finalité (loi de Goodhart) | Satisfaire un contrôle sans atteindre le but recherché | Quelles métriques de résultat associer aux métriques de production ? | Économie et mesure ; vérifiabilité | 7.2 ; 5.2 |
| 55 | Résultat correct et résultat compris | Une preuve vérifiée peut rester peu instructive ; un code testé peut rester incompris | Quelle justification exiger, proportionnée à quel risque ? | Vérifiabilité ; patrimoine de connaissance | 4.1 ; 5.2 |
| 56 | Apprentissage quand les tâches d'entrée évoluent | Comment former les futurs experts si les tâches des débutants sont automatisées ? | Quelles pratiques de formation fonctionnent, et comment le mesurer ? | Organisation et compétences | 7.1 ; 8.1 |
| 57 | Cas des mathématiques produites par IA | Changement d'échelle de la production de résultats là où un vérificateur formel existe | Ce cas dit-il quelque chose du logiciel d'entreprise ? Les éléments disponibles ne permettent pas de conclure | Vérifiabilité ; prospective | 2.2 (renvoi), annexe G (analyse) ; 4.2, 8.1 |
| 58 | L'outil métier comme produit de découverte | Un outil construit par le métier révèle un besoin ou une règle ; sa connaissance peut nourrir le produit cœur | Quels critères décident de son arrêt, de son remplacement, de sa reprise ou de son maintien ? | Autonomie des métiers | 2.1 ; 7.2 |
| 59 | Étude de marché assistée par l'IA | Taille de marché, segments, capacité à investir, modèle d'achat, usages et concurrence instruits en quelques sessions de recherche | Comment fiabiliser des chiffres que les outils de recherche étayent mal ? | Discovery et validation | 3.2 ; 4.1 |
| 60 | Persistance du contexte et persistance de la participation | Une mémoire qui survit aux sessions n'est pas une IA qui observe en continu | Une participation persistante améliore-t-elle les décisions, ou multiplie-t-elle les alertes ? | Spécifications et SDD | 4.2 |
| 61 | Dette technique et refactorisation assistée | La dette s'accumule avec les versions ; l'IA peut aider à la réduire si des tests existent | Quelle part des refactorisations non équivalentes échappe aux tests ? | Modernisation de l'existant | 6.1 ; 7.2 |
| 62 | Un Product Management élargi | Gestion de produit, de l'offre, marketing produit et développement commercial, assistés en permanence par des agents | L'élargissement vaut-il au-delà des produits commerciaux et des entreprises de taille moyenne ? | Organisation et compétences | 7.1 |
| 63 | Deux régimes de financement | Budget visible et variable du produit industrialisé, coût caché des outils métier | Comment rendre visible le coût des outils métier sans les étouffer ? | Économie et mesure | 7.2 |
| 64 | Le modèle produit de Cagan | Quatre risques, découverte et livraison, financement d'équipes chargées de résultats | Que devient la faisabilité quand des agents réalisent et qu'il faut prouver ce qu'ils ont fait ? | Finalité du Product Management | 1.5 ; 3.2 ; 4.2 ; 7.1 ; 7.2 |

## C. États de l'art par domaine

Cette annexe présente, domaine par domaine, ce qui existe et se pratique, les résultats effectivement évalués, les limites et questions non résolues, les conséquences pour le Product Management et des recommandations. Elle reprend sous une forme plus détaillée des éléments du corps du document, avec des sources complémentaires.

### C.1 Carte des domaines

Les sujets 1 à 57 de l'annexe B se regroupent en 16 domaines ; les sujets 58 à 64 se rattachent aux domaines indiqués dans l'annexe B. Le tableau suivant sert de carte de lecture pour les états de l'art qui suivent. Les sujets 36 à 40 sont développés dans la fiche transversale « Fonctionnalités reproductibles et valeur durable du produit » ; les sujets 41 à 48 introduisent le domaine « Architectures vérifiables, composables et portables » et ses liens avec la stratégie, l'économie et la transmission ; les sujets 49 à 57 forment le domaine « Vérifiabilité, évaluation et compréhension », développé dans la fiche transversale du même nom.

| Domaine | Sujets (annexe B) | Élargissements utiles |
|---|---|---|
| 1. Autonomie des métiers | 1, 19, 20 | Citizen development, shadow AI, gouvernance des outils non déclarés |
| 2. Finalité du Product Management | 5, 19, 34 | Valeur, priorisation, arbitrages, responsabilité, différenciation |
| 3. Discovery et validation | 5, 8, 21 | Entretiens, prototypes, expérimentation, UX, distinction hypothèse/proof |
| 4. Organisation et compétences | 10, 19 | Fusion teams, Product Ops, répartition des rôles, transmission |
| 5. Patrimoine de connaissance | 2, 3, 7, 32 | Context engineering, mémoire versionnée, onboarding, reprise, connaissance reconstruite |
| 6. Spécifications et SDD | 11, 14, 33 | Spec-first/anchored/as-source, AGENTS.md, critères d'acceptation, boucle inverse du SDD |
| 7. Agents et autonomie | 8, 9 | Permissions, escalade, orchestration, limites |
| 8. Preuves et acceptation | 5, 6, 12, 13, 21, 22, 30, 32 | Vérification indépendante, équivalence vs correction, classification des écarts, limites de l'observation |
| 9. Cycle de vie produit | 5, 8 | Plateformes internes, CI/CD, observabilité, incidents, maintenance, retrait |
| 10. Modernisation de l'existant | 17, 31 | Cartographie, extraction de règles, strangler fig, coexistence, bascule, rétro-ingénierie agentique |
| 11. Économie et mesure | 18, 27, 28 | Productivité mesurée, coût complet, coût par changement accepté, valeur |
| 12. Souveraineté et dépendances | 15, 23, 24, 25, 26, 35 | Modèles open weight vs souverain, licences, contrats, chaîne complète, flux d'analyse |
| 13. Sécurité et cadre européen | 16, 29, 35 | RGPD, AI Act, NIS2, CRA, IEC 62443, SecNumCloud, C5, ENS, HDS, droits de reconstruction |
| 14. Prospective | 4, 9, 34 | Stratégies d'acteurs (Musk, Cursor, Amazon), scénarios, différenciation, questions ouvertes |
| 15. Architectures vérifiables, composables et portables | 41 à 48 | Typage, moteur/interface, polyglottisme, Wasm, WebGPU, WASI/WIT, coût de validation et mainteneurs |
| 16. Vérifiabilité, évaluation et compréhension | 49 à 57 | Asymétrie de vérification, système d'évaluation versionné, justesse de spécification, niveaux d'acceptation, Goodhart, compréhension, formation du jugement, cas des mathématiques |



Pour chaque domaine, la fiche suit la même trame : ce qui existe et se pratique, les résultats effectivement évalués, les limites et questions non résolues, les conséquences pour le Product Management, les recommandations. La profondeur n'est pas égale : les articulations centrales de la réflexion (Product, patrimoine, SDD, vérification, organisation) sont développées davantage que les domaines de soutien (plateformes, infrastructures, catalogues).

### C.2 Autonomie des métiers (citizen development et shadow AI)

**Ce qui existe.** Les équipes métier construisent leurs propres applications avec l'IA générative, sans passer par la DSI ni le Product. Le mouvement dépasse le low-code/no-code : il inclut des agents, des automatisations et des applications complètes déployées sur des plateformes approuvées mais sans gouvernance IT ([CSA Research Note, juin 2026](https://labs.cloudsecurityalliance.org/wp-content/uploads/2026/06/CSA_research_note_vibe_coding_ai_governance_gap_20260602-csa-styled.pdf)). Les métiers deviennent des builders à part entière ([TechTarget](https://www.techtarget.com/enterprise-software/feature/Citizen-developers-move-AI-closer-to-the-work)).

**Résultats évalués.** Le phénomène est documenté et mesuré, mais surtout via des enquêtes déclaratives et des rapports d'analystes, pas des essais randomisés. Aucun chiffre Gartner n'est utilisé dans cette fiche car aucune source primaire Gartner n'a pu être lue directement.

**Limites et questions.** Trois limites principales :
1. L'absence de visibilité : les outils construits ne figurent dans aucune roadmap officielle.
2. Le risque de maintenance : un outil maintenu par une seule personne devient une dette si cette personne part.
3. Le risque de conformité : les outils non gouvernés tombent dans le champ du RGPD, du NIS2 ou du CRA selon les données traitées.

**Conséquences pour le PM.** Le Product ne peut plus se positionner comme un simple filtre ou goulot d'étranglement. Il doit devenir un accompagnateur et un auditeur : identifier les outils qui doivent rester locaux, ceux qui doivent être repris en produit partagé, et ceux qui doivent être arrêtés.

**Recommandations.**
- Distinguer explicitement le « citoyen développeur » (construit dans un cadre) du « shadow AI » (construit hors cadre).
- Établir un inventaire des outils construits par les métiers, avec un responsable identifié et un niveau de criticité.
- Définir un seuil de passage vers un produit partagé : volumétrie, criticité, contraintes réglementaires.

### C.3 Finalité du Product Management

**Ce qui existe.** Le Product Management reste défini par la découverte du besoin, la définition de la valeur, la priorisation et la coordination de la réalisation. Les tâches d'exécution (rédaction de PRD, analyse de feedback, priorisation de backlog) sont de plus en plus assistées ou automatisées par l'IA ([KnowledgeHut](https://www.knowledgehut.com/blog/artificial-intelligence/how-ai-is-changing-product-management), [Airfocus](https://airfocus.com/blog/ai-agents-for-product-management/)).

**Résultats évalués.** Peu d'évaluations rigoureuses du rôle du PM en tant que tel. Les études portent surtout sur la productivité des développeurs, pas sur la valeur ajoutée du PM. Une analyse de 100 offres d'emploi « AI Product Manager » de 2026 conclut que le rôle est intégratif : connecter un problème de valeur à un produit IA borné, traduire entre preuves utilisateur, business et techniques, porter les décisions jusqu'à la livraison et apprendre de l'exploitation. Les 100 offres codées combinent stratégie produit IA et aisance technique (source de faible autorité : [MTF Institute, 21 août 2026](https://mtfinstitute.com/insights/operating-shape-ai-product-management-100-vacancies-2026/)) ; ce résultat est en partie façonné par la règle d'éligibilité de l'étude et ne se généralise pas à tous les rôles intitulés Product Manager.

**Limites et questions.** Le rôle du PM est en tension : sur des sujets bien délimités, les métiers peuvent détenir une connaissance du problème que le PM n'a pas, et l'IA peut exécuter une part des tâches qu'il coordonnait. Mais la cohérence globale et l'arbitrage restent à sa charge. Comment répartir ces responsabilités sans créer des silos ?

**Conséquences.** Le PM n'est plus le seul point de passage obligatoire. Sa valeur se concentre sur : le choix des problèmes à résoudre (et ceux à ne pas résoudre) ; l'arbitrage de la valeur (ce qui vaut le coût de construction, de maintenance et de vérification) ; la définition du périmètre (ce qui reste local, ce qui devient un produit partagé, ce qu'on arrête) ; la stratégie de portefeuille (quel produit prioriser face à quelles ressources) ; la mesure des effets observés (valeur métier réelle, pas seulement vélocité) ; la décision de ne pas construire (une modification de processus ou une meilleure utilisation d'un outil existant suffisent parfois).

Ces six dimensions ne sont pas nouvelles : elles constituent le cœur historique du Product Management. Ce qui change, c'est qu'elles ne peuvent plus être déléguées aux tâches d'exécution que l'IA absorbe.

**Recommandations.**
- Ne pas réduire le PM à la rédaction de spécifications.
- Renforcer son rôle dans la distinction entre besoin réel et solution proposée, et entre outil local et produit partagé.
- Développer explicitement la capacité à décider de ne pas construire.

### C.4 Fonctionnalités reproductibles et valeur durable du produit

La reconstruction peut partir non seulement des mécanismes internes d'un logiciel, mais aussi de ce que son marché en connaît. Nous proposons donc de distinguer la difficulté à reconstruire une implémentation de la difficulté à concevoir, vérifier, distribuer et maintenir un service réellement substituable.

#### C.4.1 ArtCraft : une reconstruction depuis des spécifications et l'observation

Le cas identifié est ArtCraft, dont les applications créatives comprennent notamment PhotoCraft, VectorCraft et FilmCraft ; le site officiel présente des applications en « early alpha » ou « in development », et non une suite professionnelle achevée ([ArtCraft](https://getartcraft.com/apps)). Gizmodo rapporte que Brandon Thomas les a construites en Rust avec Claude Opus 5.5 et décrit un essai de PhotoCraft où des opérations simples étaient utilisables, mais où Free Transform avait un comportement imprévisible ([Gizmodo](https://gizmodo.com/someone-vibe-coded-a-free-knockoff-of-adobe-creative-suite-2000823322)).

La documentation de PhotoCraft revendique une réimplémentation indépendante à partir de spécifications publiques et de comportements observés, sans code, shaders ou ressources propriétaires ; elle cite notamment la spécification publique du format PSD pour sa prise en charge de ces fichiers ([PhotoCraft](https://github.com/storytold/photocraft)). Les instructions de FilmCraft interdisent de lire, désassembler ou copier le contenu des applications Adobe ; elles autorisent l'observation par utilisation de l'application et prévoient des captures et notes de référence conservées localement, sans les intégrer aux livrables ([instructions FilmCraft](https://github.com/storytold/filmcraft/blob/main/AGENTS.md)).

La distinction avec REA est donc substantielle : les règles publiées de FilmCraft décrivent une démarche fondée sur les spécifications et l'observation, et interdisent précisément l'analyse du contenu des applications Adobe ([instructions FilmCraft](https://github.com/storytold/filmcraft/blob/main/AGENTS.md)). Il n'est pas nécessaire d'invoquer une décompilation pour expliquer ce mode de reconstruction.

L'idée que des photos et des vidéos de démonstration servent de matière première à la reconstruction reste une piste à documenter. Les sources primaires consultées confirment l'observation, les captures et les spécifications publiques, mais n'établissent ni la part exacte des vidéos utilisées pour construire ArtCraft ni le poids respectif de ces sources ; les instructions PhotoCraft examinées ne mentionnent pas explicitement l'usage de vidéos comme référence de conception ([instructions PhotoCraft](https://github.com/storytold/photocraft/blob/main/AGENTS.md), [instructions FilmCraft](https://github.com/storytold/filmcraft/blob/main/AGENTS.md)).

Le résultat ne doit pas être résumé comme « Adobe a été intégralement recréé ». PhotoCraft indique explicitement ne pas encore remplacer Photoshop dans un travail professionnel quotidien et précise que raccorder les menus à des commandes mesure leur raccordement, pas leur comportement ([PhotoCraft](https://github.com/storytold/photocraft)). FilmCraft distingue lui-même l'étendue des fonctionnalités et l'aptitude à un travail réel, et documente des lacunes de compatibilité de projets et de plugins ; ce sont des déclarations du projet, pas une certification indépendante ([FilmCraft](https://github.com/storytold/filmcraft)).

#### C.4.2 L'information publique comme matière première de spécification

Notre hypothèse de travail est la suivante : une documentation, une capture ou une démonstration peut aider à décrire un résultat attendu sans révéler son implémentation. Nous proposons de les traiter comme des éléments de spécification partielle, jamais comme des preuves suffisantes de correction.

| Matériau de référence proposé | Ce qu'il peut aider à décrire | Ce qu'il ne suffit pas à établir |
|---|---|---|
| Capture d'écran | Disposition, libellés, hiérarchie visuelle | Calculs, transitions, règles internes |
| Vidéo de démonstration | Enchaînement d'actions, retours visuels, résultat d'un scénario | Couverture des exceptions, stabilité, performances générales |
| Documentation et spécifications publiques | Contrats, paramètres, formats, règles documentées | Conformité effective d'une nouvelle implémentation |
| Utilisation et essais autorisés | Comportements sur des entrées choisies | Exhaustivité sur les entrées non testées |
| Jeux d'entrées et sorties de référence | Résultats attendus sur un périmètre explicite | Intention métier et validité hors de ce périmètre |

Cette grille est une proposition de méthode. Dans le SDD, chaque exigence déduite d'un tel matériau devrait conserver sa provenance, sa version, son statut d'hypothèse ou de règle approuvée, puis le test qui la vérifie ; nous évitons ainsi de transformer une ressemblance observée en vérité métier.

#### C.4.3 Une substitution partielle peut compter avant l'équivalence complète

L'hypothèse stratégique importante n'est pas qu'un concurrent doive reproduire toute une suite pour devenir utile. Nous proposons d'examiner si un ensemble limité de tâches peut déjà être effectué avec une qualité suffisante pour un segment donné, à un coût complet acceptable.

Une personne qui prépare occasionnellement une image, une équipe qui automatise une opération répétitive et un studio qui livre des projets complexes ne constituent pas le même scénario d'acceptation. Il s'agit ici de trois segments illustratifs à étudier, pas d'une conclusion sur l'aptitude actuelle d'ArtCraft pour chacun.

Les deux conclusions extrêmes seraient donc prématurées : « le clone ressemble au produit, donc il le remplace » et « il manque des fonctions professionnelles, donc il n'est une menace pour aucun usage ». Le PM doit rechercher le seuil de suffisance par segment, sans présumer ni de la réussite du nouvel entrant ni de l'immunité de l'éditeur installé.

#### C.4.4 Où chercher une valeur plus durable

La grille suivante propose des dimensions d'analyse, pas des avantages garantis ou impossibles à reproduire. Leur importance dépend de l'utilisateur, du risque d'erreur et de la tâche.

| Dimension | Question de valeur à vérifier auprès du client | Preuve à rechercher |
|---|---|---|
| Fonctionnalités et ergonomie | Le travail demandé peut-il être accompli sans effort inutile ? | Tâches réalisées, temps, erreurs d'utilisation |
| Correction et fiabilité | Le résultat est-il juste et reproductible ? | Cas de référence indépendants, défauts, pertes de données |
| Compatibilité | Les fichiers, historiques et échanges restent-ils exploitables ? | Import/export aller-retour, fidélité, pertes explicites |
| Profondeur métier | Les cas importants pour ce segment sont-ils réellement couverts ? | Parcours complexes validés avec des spécialistes |
| Intégrations et collaboration | Le produit s'insère-t-il dans le travail collectif ? | Parcours de bout en bout, droits, échanges entre outils |
| Exploitation et responsabilité | Qui corrige un incident, avec quel engagement ? | Support observé, délais, sauvegarde et reprise |
| Données et ressources accessibles légalement | Ces ressources améliorent-elles le résultat pour ce client ? | Mesure d'utilité et droits d'usage, pas simple volume détenu |
| Coût, autonomie et facilité de sortie | Le client obtient-il un service utile sans dépendance disproportionnée ? | Coût complet, export utilisable, effort de migration |

Nous distinguons ainsi une valeur positive, que le client souhaite conserver, d'un coût de sortie qu'il subit. Un format fermé ou une migration difficile ne doivent pas être présentés automatiquement comme une qualité produit ; inversement, la familiarité des commandes mérite d'être testée comme moyen de réduire l'apprentissage, sans supposer qu'elle résout les problèmes de compatibilité et de fiabilité.

La mémoire versionnée proposée dans ce document ne devient pas, à elle seule, une barrière concurrentielle. Nous la recommandons d'abord pour réduire la dépendance au créateur, préserver les décisions et rendre les évolutions vérifiables ; son intérêt stratégique éventuel doit être évalué par ses effets, pas par le nombre de pages produites.

#### C.4.5 Si l'agent devient l'interface

PhotoCraft et FilmCraft documentent un moteur de commandes accessible depuis leur interface, une CLI et un serveur MCP ; les projets présentent donc explicitement la possibilité de les piloter par des agents ([PhotoCraft](https://github.com/storytold/photocraft), [FilmCraft](https://github.com/storytold/filmcraft)). Cela ne prouve pas la fiabilité d'une automatisation complète, mais ouvre une question distincte de la simple imitation d'interface.

Notre hypothèse est qu'un utilisateur pourrait choisir un moteur pour la qualité de ses résultats et de son automatisation, même s'il utilise peu son interface graphique. Pour le PM, cela justifie d'évaluer les contrats de commandes, les permissions, les erreurs, la reprise et la traçabilité comme des composantes du produit, sans présumer la disparition des interfaces humaines.

#### C.4.6 Transformer ces constats en décisions produit

Nous proposons de remplacer la question « combien de fonctionnalités le concurrent a-t-il copiées ? » par une évaluation de substitution sur des tâches réelles. Le protocole ci-dessous peut servir au PM d'un éditeur installé comme à celui d'un nouvel entrant.

- **Segment et résultat attendu :** sélectionner des utilisateurs et des tâches représentatives ; définir ce qui est acceptable et ce qui rend le résultat inutilisable.
- **Comparaison complète :** observer la réalisation de bout en bout, notamment l'import, l'édition, l'export, les échanges avec des tiers et la reprise après erreur ; ne pas s'arrêter à une capture réussie.
- **Mesures :** comparer le taux de tâches acceptées, le temps total, les corrections, les pertes de fidélité, les incidents et l'effort de migration.
- **Économie :** intégrer au coût la formation, le support, l'hébergement ou l'inférence, la validation et la maintenance ; un téléchargement gratuit n'est pas un coût d'exploitation nul.
- **Décision de portefeuille :** choisir ce qu'il faut continuer à développer, intégrer, simplifier, acheter ou abandonner selon les résultats observés, plutôt que protéger toutes les fonctionnalités historiques.

La thèse proposée pour la suite du document devient : la valeur durable ne réside ni nécessairement dans le secret du code ni dans l'accumulation des fonctionnalités, mais dans la capacité à rendre un travail utile, fiable et économiquement acceptable pour un segment, puis à maintenir cette capacité quand ses besoins changent. Cette proposition reste à éprouver sur des produits et usages concrets.

### C.5 Discovery et validation

**Ce qui existe.** Les agents IA peuvent synthétiser des signaux (tickets de support, transcriptions d'appels, enquêtes, analytique produit) pour générer des hypothèses et des synthèses. Cette capacité est décrite dans la littérature produit, mais aucune évaluation empirique suffisamment étayée ne démontre qu'elle améliore la discovery produit auprès des utilisateurs.

**Résultats évalués.** Aucune évaluation empirique suffisamment étayée dans les sources examinées ne démontre que les agents IA améliorent la discovery produit auprès des utilisateurs. Les agents produisent des hypothèses, pas des preuves d'adoption.

**Limites et questions.** Une hypothèse formulée par une IA n'est pas une preuve obtenue auprès des utilisateurs. Le risque est de confondre « l'IA a proposé » et « les utilisateurs ont validé ».

**Conséquences.** Le PM doit conserver la responsabilité de distinguer les hypothèses générées des résultats observés.

**Recommandations.**
- Séparer explicitement la génération d'hypothèses (IA) de la validation (utilisateurs).
- Utiliser les agents pour accélérer la synthèse, pas pour remplacer les entretiens.

### C.6 Organisation et compétences

**Ce qui existe.** Les « fusion teams » mêlant compétences métier et technologiques sont décrites comme une pratique organisationnelle émergente (affirmation de praticiens, non vérifiée à la source). Le modèle en étoile (noyau central + antennes embedded) est une proposition de réponse organisationnelle, pas une pratique établie. L'étude MTF (fiche C.3) montre que les rôles Product Management IA combinent stratégie, translation technique, delivery et exploitation responsable, ce qui appuie l'idée d'une répartition plutôt que d'un profil unique.

**Résultats évalués.** Les chiffres de fusion teams et de platform engineering viennent d'enquêtes et d'analystes, pas d'essais contrôlés. Ils indiquent une tendance, pas une preuve de supériorité.

**Limites et questions.** Comment transmettre une pratique (pas seulement un produit) ? Comment éviter que les antennes embedded deviennent des silos ?

**Conséquences.** Le rôle du PM évolue vers un rôle de coach, d'auditeur et d'arbitre, plus que de producteur de specs.

**Recommandations.**
- Intégrer le Product Ops dans l'organisation : inventaire des initiatives, circulation des décisions, mesures, règles de passage vers un produit partagé.
- Définir des parcours de carrière qui récompensent la transmission de pratique, pas seulement la livraison de fonctionnalités.

**Apprentissage quand les tâches d'entrée évoluent.** Si les tâches confiées aux débutants (écrire des tests, corriger des défauts simples, rédiger des exigences) passent aux agents, l'acquisition du jugement doit être organisée autrement. Les sources sur les mathématiques documentent cette inquiétude sans établir une disparition des parcours de formation ([Quanta Magazine, 5 octobre 2026](https://www.quantamagazine.org/is-ai-the-end-of-math-as-we-know-it-20261005/) ; [Duminil-Copin, 30 août 2026](https://proofsandprompts.com/2026/08/30/care-for-a-little-more-ai/)). Pistes à évaluer : exercices sans assistance, critique de résultats produits par l'IA, construction de critères d'acceptation par les débutants, analyses d'incidents, évaluation de la capacité à justifier une décision. Voir la fiche « Vérifiabilité, évaluation et compréhension ».

### C.7 Patrimoine de connaissance

**Ce qui existe.** Les équipes utilisent des fichiers de contexte (CLAUDE.md, AGENTS.md, contextes structurés) pour guider les agents et maintenir la continuité entre sessions ([Anthropic, septembre 2025](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)). Les fournisseurs d'infrastructure proposent des couches de contexte d'entreprise (Atlan, Teradata, Egnyte) pour transformer l'information distribuée en contexte structuré, gouverné et versionné.

**Résultats évalués.** Les artefacts de continuité (fichiers de progression, historique Git, transmissions explicites du contexte) sont documentés comme utiles pour les agents, mais leur suffisance à transmettre toute la connaissance métier n'est pas démontrée.

**Limites et questions.** Comment distinguer « fait validé », « hypothèse » et « interprétation en attente de validation » dans la mémoire ? Comment éviter qu'une conversation devienne une exigence officielle sans validation humaine ?

**Conséquences.** Le patrimoine transmissible n'est pas seulement le code : c'est le contexte, les objectifs, les règles, les décisions, les preuves de validation et les retours d'exploitation.

Le cas REA renforce cette proposition : même si un outil aide à reconstruire le comportement d'une application, nous ne devons pas supposer qu'il retrouve l'intention de ses concepteurs. Nous proposons de traiter la connaissance reconstruite comme une hypothèse documentée, avec ses preuves et ses inconnues, jusqu'à validation métier ; elle ne remplace pas la mémoire conservée pendant la conception (voir « Rétro-ingénierie agentique : apport de REA »).

**Recommandations.**
- Conserver la chaîne : échanges, puis extraction IA, puis clarification, puis validation par une personne identifiée, puis versionnement.
- Séparer explicitement les quatre statuts : demandé, implémenté, testé, à valider.
- Vérifier qu'une personne qui n'a pas créé l'application peut, avec un agent, comprendre ses règles, proposer une évolution et démontrer ses effets.


### C.8 Dispositif minimal de transmission de connaissance (proposition)

La proposition consiste à placer des fichiers de connaissance versionnés dans le dépôt de code. Elle constitue une méthode de travail, pas un standard établi.

**Structure minimale des fichiers de connaissance.**

| Fichier | Contenu | Statut possible des entrées |
|---|---|---|
| `contexte.md` | Pourquoi l'application existe, pour qui, ce qu'elle ne cherche pas à faire | demandé / validé / obsolète |
| `regles.md` | Définitions, calculs, contraintes, sources de référence, dates et périmètres d'application | règle approuvée / interprétation en attente |
| `decisions.md` | Options retenues ou rejetées, raisons, hypothèses, incertitudes | décision active / remplacée |
| `verification.md` | Cas de référence, résultats attendus, tests, critères d'acceptation | testé / à valider |
| `exploitation.md` | Responsable, dépendances, accès, maintenance, incidents, procédure de reprise | actuel / à mettre à jour |

**Chaque entrée doit porter des dimensions distinctes :**
- statut de validation métier (approuvée / en attente / obsolète) ;
- statut d'implémentation (implémentée / non implémentée) ;
- statut de couverture de tests (testée / partiellement testée / non testée) ;
- un responsable identifié qui l'a validée ;
- une date d'actualisation ;
- le cas échéant, la référence au code ou au test qui la justifie.

**Exercice de reprise par un successeur.** Le test concret : une personne qui n'a pas créé l'application doit pouvoir, avec un agent :
1. comprendre ses règles et leurs limites ;
2. vérifier si une nouvelle contrainte (ex. changement législatif) est déjà prise en compte ;
3. proposer une nouvelle version ;
4. comparer les résultats avec la précédente et classer les écarts.

Cet exercice doit être mené périodiquement, pas seulement au départ du créateur : il permet de vérifier que la mémoire reste exploitable.

**Compléments (proposition).** Le fichier `verification.md` documente aussi, pour chaque contrôle significatif : ce qu'il cherche à établir, l'origine des résultats attendus, ses hypothèses et limites, les cas exclus, les personnes responsables de sa validation et les événements qui imposent sa révision. Le fichier `decisions.md` reçoit, pour les changements significatifs, une justification proportionnée au risque : décisions, alternatives écartées, limites connues, dépendances, conditions de retour arrière.

### C.9 Spécifications et SDD

**Ce qui existe.** Le Spec-Driven Development désigne une famille de pratiques : une spécification écrite, versionnée et testable comme source de vérité, que les agents implémentent et que les humains relisent. Les artefacts typiques sont `requirements.md`, `design.md`, `tasks.md` et `AGENTS.md`. `AGENTS.md` est un format ouvert, Markdown, pour donner aux agents le contexte et les instructions d'un projet ; il est piloté par la Linux Foundation via l'Agentic AI Foundation ([agents.md](https://agents.md)). L'analyse de Böckeler (lue directement) documente l'existence de ces pratiques sans conclure à une adoption générale.

**Résultats évalués.** L'analyse de Böckeler, publiée sur le site de Martin Fowler, a été lue à la source. Elle distingue trois approches : spec-first, spec-anchored, spec-as-source. Sa conclusion principale : le principe spec-first est précieux dans de nombreuses situations, mais le SDD n'est pas encore bien défini et est utilisé de différentes manières. Elle soulève des inquiétudes : des workflows élaborés peuvent créer une surcharge de revue, et les agents IA peuvent ignorer ou sur-appliquer les instructions. Elle se demande si ces approches améliorent réellement le développement ou amplifient les problèmes existants ([Böckeler, site de Martin Fowler, 15 octobre 2025](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)). La convergence vers le SDD est observable dans la littérature et les outils, mais « consensus » serait excessif.

**Limites et questions.** Une spécification extraite du code décrit un comportement, pas nécessairement une intention. Il faut distinguer la description de l'existant de la définition du comportement cible. Le fait qu'un outil génère du code à partir d'un texte ne prouve pas que le texte a été correctement interprété.

**Conséquences.** Le SDD présente un intérêt potentiel comme cadre pour contraindre ce que l'agent peut construire, mais sans garantie de correction ou de sécurité par lui-même.

**Recommandations.**
- Séparer deux spécifications : description du comportement existant et définition du comportement cible.
- Traiter `AGENTS.md` comme une instruction aux agents, pas comme une spécification métier.
- Positionner la pratique proposée (contexte versionné dans le repository) comme « spec-anchored », pas comme « spec-as-source ».

### C.10 Agents et autonomie

**Ce qui existe.** Les agents peuvent prendre une tâche, créer une branche, exécuter des tests et proposer une modification. Selon une enquête Sonar de 2026, 72 % des développeurs ayant essayé l'IA de code l'utilisent tous les jours ; 64 % ont commencé à utiliser des agents autonomes ([Sonar, octobre 2026](https://www.sonarsource.com/company/press-releases/sonar-data-reveals-critical-verification-gap-in-ai-coding/)).

**Résultats évalués.** L'étude initiale de METR, menée de février à juin 2025, mesurait un temps de réalisation supérieur de 19 % (intervalle de confiance +2 % à +39 %) avec les outils IA chez des développeurs expérimentés sur des tâches open source. La mise à jour de février 2026 rapporte des estimations brutes de réduction du temps de 18 % pour les anciens participants et de 4 % pour les nouveaux, mais considère que les biais de sélection (30 à 50 % des développeurs ont écarté certaines tâches de l'expérience) empêchent d'en tirer une estimation fiable de l'effet actuel ([METR, février 2026](https://metr.org/blog/2026-02-24-uplift-update/)). L'étude randomisée citée dans la pièce jointe a été lue directement : trois essais contrôlés (Microsoft, Accenture, Fortune 100) auprès de 4 867 développeurs mesurent 26,08 % de tâches complétées en plus avec un assistant de code (SE 10,3 %), avec des gains plus élevés pour les développeurs moins expérimentés ([SSRN, paper 4945566](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4945566)).

**Limites et questions.** Comment définir concrètement les permissions d'un agent (accès, modification, validation, escalade, réversibilité) ? Comment distinguer le niveau d'autonomie du niveau de confidentialité ?

Dispositif proposé (proposition de praticiens, non évaluée) : une **passerelle IA interne** qui route, journalise, filtre les secrets, applique les quotas et rend les modèles interchangeables sans modifier les postes. Elle permet de classifier les dépôts par niveau de confidentialité (N1/N2/N3), de masquer les secrets avant envoi, et de mesurer les coûts et usages.

**Conséquences.** L'autonomie d'un agent doit être définie par les actions autorisées, pas par une phase générique.

**Recommandations.**
- Définir chaque niveau d'autonomie avec des permissions concrètes (section 5.1).
- Accorder l'autonomie selon les conséquences d'une erreur, pas selon la capacité de l'agent à exécuter.
- Distinguer l'agent qui développe du produit lui-même.

### C.11 Preuves et acceptation

**Ce qui existe.** Plusieurs sources observent un déplacement du goulot d'étranglement de l'écriture du code vers sa vérification, dans certains contextes et pour certaines équipes. 96 % des développeurs ne font pas entièrement confiance au code généré par IA pour être correct, mais seulement 48 % le vérifient toujours avant de committer ([Sonar, octobre 2026](https://www.sonarsource.com/company/press-releases/sonar-data-reveals-critical-verification-gap-in-ai-coding/)). 

**Résultats évalués.** Les chiffres de Sonar sont issus d'une enquête déclarative d'un fournisseur, pas d'une mesure expérimentale. Ils établissent une tendance, pas une causalité. L'étude METR fournit une mesure contrôlée, mais avec des effets de sélection.

**Limites et questions.** L'équivalence avec l'ancien système ne suffit pas : elle distingue trois vérifications (équivalence, correction métier, aptitude à l'exploitation). Le dual run sur trafic réel doit être conçu selon le risque : pour un système financier ou industriel, ne pas autoriser deux versions à produire simultanément des écritures.

Deux risques spécifiques aux applications construites par les métiers :
- **Qualité et provenance des données** : un dashboard peut afficher depuis six mois un chiffre légèrement faux parce que la requête initiale tapait sur une table avant retraitement (cas rapporté par un article de praticien, non vérifié). La question « quelle donnée fait référence ? » doit être posée avant la mise en usage quotidien, pas après.
- **Hallucinations et responsabilité** : un assistant legal peut halluciner une clause dans un NDA relu trop vite (cas rapporté par un article de praticien, non vérifié). Le risque d'un contenu contractuel incorrect nécessite une validation par une personne identifiée pour tout contenu à portée contractuelle ou réglementaire, indépendamment de tout précédent juridique.

Pour le code OT et PLC : revue par un expert du domaine et tests sur simulateur avant tout essai sur équipement (pratique courante du secteur).

**Conséquences.** La rareté se déplace vers la vérification. Des critères de correction indépendants doivent être définis et les écarts classés en quatre catégories (attendu et approuvé, défaut du nouveau, défaut découvert dans l'ancien, inexpliqué). Ce travail associe le métier, les spécialistes du domaine, l'ingénierie et le Product ; il n'incombe pas au seul Product Manager (correction 0.5 d'une formulation précédente).

**Trois niveaux d'acceptation (proposition).** Les trois vérifications ci-dessus s'inscrivent dans trois niveaux d'acceptation : technique (la réalisation fonctionne dans le périmètre testé), métier (le comportement correspond aux règles et usages), produit et exploitation (la valeur est acceptable au regard des risques et des coûts). L'autorité d'acceptation de chaque niveau est désignée explicitement selon le risque. Le premier niveau vérifie une réalisation ; le troisième valide sa pertinence. Voir la fiche « Vérifiabilité, évaluation et compréhension ».

**Recommandations.**
- Rebuild le processus de revue, pas seulement ajouter des outils.
- Séparer les vérifications : équivalence, correction métier, aptitude à l'exploitation.
- Traiter les écarts inexpliqués et les risques comme le cœur de l'acceptation, pas un pourcentage de tests réussis.

### C.12 Cycle de vie produit (plateformes internes)

**Ce qui existe.** Le platform engineering est une pratique répandue pour gérer l'infrastructure de développement à grande échelle. Les IDP (Internal Developer Platforms) standardisent des outils self-service pour créer et déployer du code, avec gouvernance intégrée.

**Résultats évalués.** Aucune évaluation empirique suffisamment étayée dans les sources examinées ne mesure le gain de productivité des plateformes internes. L'adoption est documentée par des enquêtes, pas par des essais contrôlés.

**Limites et questions.** Comment intégrer la gouvernance des agents dans les plateformes internes ? Comment boucler la boucle entre exploitation et connaissance ? Règles de sécurité courantes (recommandations de praticiens, non vérifiées) : ne jamais donner à l'agent des droits de fusion ou de déploiement, exécuter dans une sandbox avec réseau sortant limité, interdire les secrets dans le contexte (détection automatique avant envoi), valider le code par des outils indépendants (SAST, analyse des dépendances, tests), vérifier les dépendances proposées par l'IA (paquets inexistants ou malveillants), générer le SBOM à chaque build.

**Conséquences.** Une fonctionnalité n'est pas terminée parce que l'agent dit avoir fini. Elle est terminée lorsque les critères d'acceptation sont satisfaits et que les responsabilités d'exploitation sont prises en charge.

**Recommandations.**
- Intégrer les règles de gouvernance des agents dans l'IDP (sandbox, réseau sortant filtré, secrets hors contexte).
- Utiliser les incidents et retours d'usage pour alimenter la mémoire du produit, pas seulement les tickets.

### C.13 Modernisation de l'existant

**Ce qui existe.** Des fournisseurs annoncent des chaînes agentiques pour migrer des legacies : AWS Transform, IBM watsonx Code Assistant for Z, Google Cloud Mainframe Assessment Tool avec Dual Run. Ces fonctions sont annoncées dans la documentation produit ; leur efficacité générale n'est pas démontrée par des mesures indépendantes. Le pattern de référence reste le strangler fig : remplacer le système capacité par capacité derrière une couche de routage ([Security Boulevard](https://securityboulevard.com/2026/07/the-strangler-fig-pattern-how-to-modernize-legacy-systems-without-a-big-bang-rewrite/), [Moweb](https://www.moweb.com/blog/legacy-system-modernisation-ai-enterprise-upgrade)).

**Résultats évalués.** Le cas Amadeus est vérifié : 2 000 personnes-années, plus de 400 ingénieurs au pic, TPF décommissionné en juin 2017, dernier mainframe fin 2018 ([Amadeus, janvier 2020](https://amadeus.com/en/blog/articles/celebrating-one-year-fully-open-systems)). Les gains hypothétiques de 20 à 40 % avec l'IA restent une estimation, pas une mesure.

**Limites et questions.** Les outils commerciaux ciblent majoritairement z/OS (COBOL, PL/I, JCL), pas tous les environnements. Le paradoxe du legacy : le code le plus ancien contient souvent les règles métier les plus sensibles. Il faut donc classifier le contenu de chaque artefact de découverte (code, documentation, extraits, embeddings) et appliquer le niveau de confidentialité correspondant : souvent N3, mais pas automatiquement.

**Conséquences.** La phase de découverte doit être classifiée selon le contenu des artefacts : si le contenu est sensible, auto-hébergement ou SecNumCloud dès le début ; sinon, API européenne suffit.

**Tableau de migration reconstruit.** Ce tableau réunit comportement existant, comportement cible, contribution IA, décision humaine, preuve attendue et confidentialité (déterminée par le contenu, pas par la phase) :

| Phase | Comportement existant (à documenter) | Comportement cible (à décider) | Contribution IA | Décision humaine | Preuve attendue | Confidentialité |
|---|---|---|---|---|---|---|
| Découverte et cartographie | Carte des dépendances, flux, lignée de données | (pas encore applicable) | Parsing du code, dépendances, lignée de données | Confirmer les comportements non documentés | Carte de l'existant, sources examinées, zones inconnues | Selon le contenu des artefacts |
| Extraction des règles | Catalogue de règles et exceptions observées | Décision de conserver, corriger, supprimer, ajouter | Génération de spécifications à partir du code | Distinguer intention, héritage, contournement, défaut | Catalogue de règles relié au code, avec statut de validation | Selon le contenu des règles |
| Définition du comportement cible | : | Spécification cible, exemples, critères d'acceptation | Proposer des exigences, signaler ambiguïtés | Décider ce qui reste identique et ce qui change | Spécification cible validée | Selon le contenu de la spécification |
| Architecture cible | Décisions existantes | Décisions motivées, contrats d'interface | Proposer des découpages, options | Frontières transactionnelles, compromis | Décisions d'architecture motivées | Selon le contenu des décisions |
| Génération du code cible | : | Version candidate reliée aux exigences | Code, interfaces, configuration | Revue selon le risque et la portée | Diff vérifiable, tests liés aux exigences | Selon le contenu du code |
| Tests et équivalence | Résultats de référence de l'ancien | Critères de correction indépendants | Génération de tests, comparaison | Définir les écarts acceptables | Rapport d'écarts classés (4 catégories) | Selon le contenu des données de test |
| Bascule | Procédure de retour arrière | Plan de bascule | Scripts de migration, déploiement | Go/no-go, risque opérationnel | Contrôles et retour arrière vérifié | Selon le contenu des scripts |
| Exploitation et évolution | Incidents, retours d'usage | Connaissance actualisée | Surveiller, analyser, proposer | Décider les changements | Historique des versions, incidents | Selon le contenu |

**Recommandations.**
- Distinguer description de l'existant et définition du comportement cible.
- Mesurer les fonctionnalités acceptées par heure d'ingénieur, le taux de reprise et l'équivalence comportementale, pas le code généré.
- Prévoir la coexistence longue (strangler fig), qui peut entraîner des coûts temporaires supplémentaires (deux systèmes en parallèle, plus le dual run).
- Classifier le contenu de chaque artefact pour déterminer son niveau de confidentialité, sans le présumer de la phase.

### C.14 Rétro-ingénierie agentique : apport de REA

Cette section complète la modernisation de l'existant, mais aussi le patrimoine de connaissance, le SDD, la vérification et la stratégie produit. Elle analyse un article publié par MindStudio, pas une expérimentation indépendante.

- **Capacité décrite :** MindStudio présente Reverse Engineer Anything comme un serveur MCP (Model Context Protocol, interface entre un agent et des outils) donnant accès à des outils existants tels que Ghidra, Hopper, IDA et Chrome DevTools, plutôt que comme une nouvelle méthode de décompilation ([MindStudio](https://www.mindstudio.ai/blog/reverse-engineer-anything-mcp)).
- **Boucle de travail :** selon l'article, l'agent analyse le logiciel, reçoit du pseudocode ainsi que des éléments de preuve et des inconnues, formule des hypothèses, écrit une nouvelle implémentation, la teste contre l'original et recommence ([MindStudio](https://www.mindstudio.ai/blog/reverse-engineer-anything-mcp)).
- **Résultat rapporté :** l'article décrit une comparaison informelle de reconstruction de fonctions d'Aperçu sur Mac, notamment zoom, annotation, dessin, rotation et sauvegarde ; les deux versions ont fonctionné et l'agent sans REA a terminé avant celui qui l'utilisait dans cet essai ([MindStudio](https://www.mindstudio.ai/blog/reverse-engineer-anything-mcp)).
- **Niveau de preuve :** il s'agit du compte rendu d'un essai informel, sans protocole contrôlé ni mesure d'équivalence exhaustive dans l'article ; il ne permet pas d'établir un gain général de REA ou une aptitude à reconstruire des systèmes critiques ([MindStudio](https://www.mindstudio.ai/blog/reverse-engineer-anything-mcp)).
- **Contexte éditorial :** la page contient également des promotions pour Remy, présenté par MindStudio comme un agent Product Manager ; nous traitons donc ses conclusions prospectives comme le point de vue d'un fournisseur, et non comme une validation indépendante ([MindStudio](https://www.mindstudio.ai/blog/reverse-engineer-anything-mcp)).

#### C.14.1 Reconstituer le comportement n'est pas retrouver l'intention

Nous proposons de distinguer trois objets : le comportement observé, le comportement inféré à partir des artefacts et le comportement souhaité, approuvé par le métier. Une reconstruction ne doit pas transformer automatiquement les deux premiers en troisième.

Un clone visuellement convaincant ne prouve pas que les règles de calcul, les droits d'accès, les erreurs, les cas limites, les contraintes de charge ou les mécanismes de reprise ont été reproduits. Pour notre méthode, l'application originale constitue une référence de comparaison, pas un oracle de correction ; les critères métier et d'exploitation doivent rester définis indépendamment.

Cette distinction précise la complémentarité entre mémoire conservée et connaissance reconstruite. La première cherche à préserver les raisons des décisions ; la seconde permet de reprendre une enquête quand cette mémoire manque, avec une incertitude à rendre visible plutôt qu'à masquer.

#### C.14.2 Relier la rétro-ingénierie au SDD

Nous proposons une boucle inverse du SDD, qui prépare le développement cible sans le remplacer :

> Logiciel autorisé à l'analyse, puis observations et artefacts, puis hypothèses de comportement, puis description de l'existant avec inconnues, puis validation métier, puis spécification cible, puis reconstruction, puis preuves d'acceptation.

| Point de départ | Connaissance recherchée | Limite à conserver | Livrable proposé |
|---|---|---|---|
| Code source disponible | Règles implémentées, dépendances, exceptions | Le code ne justifie pas à lui seul l'intention métier | Catalogue de comportements relié au code |
| Binaires et exécution autorisés | Logique probable, entrées/sorties, formats | Le pseudocode reste une reconstruction à examiner | Hypothèses reliées aux artefacts, inconnues explicites |
| Interface et parcours observables | Interactions, résultats et attentes d'usage | Les règles internes et les parcours non observés restent inconnus | Scénarios de caractérisation, non une déclaration d'équivalence globale |

Pour le Product, la décision n'est donc pas simplement « pouvons-nous reproduire cette application ? ». Elle devient : quels comportements faut-il conserver, corriger, supprimer ou remplacer, et quelles preuves permettront d'accepter le résultat ?

#### C.14.3 Réexaminer la différenciation produit

MindStudio défend l'hypothèse selon laquelle des agents plus capables de reconstruire des applications fragiliseraient la différenciation des interfaces légères bâties autour de modèles existants ; l'article n'en donne pas une mesure économique ([MindStudio](https://www.mindstudio.ai/blog/reverse-engineer-anything-mcp)). Nous retenons cette hypothèse comme une question stratégique à tester, pas comme l'annonce de la disparition des éditeurs.

Nous proposons d'examiner séparément la facilité de reproduction d'une interface et celle du service réellement rendu. Les données accessibles légalement, les intégrations, les preuves de fiabilité, l'exploitation, la distribution et la confiance des clients constituent des candidats à la différenciation, à vérifier produit par produit ; une interface reproductible n'implique pas que cet ensemble l'est au même coût.

Cette question complète le rôle futur du PM : arbitrer ce qu'il faut construire, intégrer, acheter ou reconstruire sur un périmètre autorisé, puis évaluer la valeur obtenue après prise en compte des coûts de validation et de maintenance. Le nombre de fonctionnalités reproduites n'est pas, à lui seul, une mesure de valeur.

#### C.14.4 Encadrer droits, confidentialité et expérimentation

L'article rappelle que la capacité technique à reconstruire un logiciel ne supprime pas les contraintes de propriété intellectuelle ([MindStudio](https://www.mindstudio.ai/blog/reverse-engineer-anything-mcp)). Nous recommandons d'examiner séparément les droits d'accès, d'analyse, de réutilisation et de distribution avant tout projet, sans présumer qu'un droit d'utilisation autorise tous ces actes ; cette recommandation ne remplace pas un avis juridique adapté.

Pour un pilote interne, nous proposons les contrôles suivants :

- **Périmètre :** sélectionner un outil détenu par l'organisation ou explicitement autorisé à l'analyse, avec des fonctions et critères de réussite bornés.
- **Confidentialité :** classifier binaires, captures, données de test, pseudocode et résultats d'analyse ; ne pas considérer qu'un connecteur MCP est local ou souverain du seul fait qu'il utilise ce protocole.
- **Sécurité :** utiliser un environnement isolé, sans secrets ni effets réels sur les systèmes de production, et enregistrer les outils, modèles, versions et flux autorisés.
- **Comparaison :** comparer, sur le même périmètre autorisé, un agent sans REA et un agent avec REA ; inclure configuration, analyse, revue, correction et tests dans le temps et le coût.
- **Acceptation :** mesurer les comportements couverts, les défauts, les inconnues résiduelles, la qualité du dossier de connaissance et le coût par comportement validé, plutôt que la seule ressemblance visuelle.

L'objectif proposé n'est pas de démontrer qu'une application peut être copiée. Il est de déterminer si cette approche aide à rendre un logiciel compréhensible, transmissible et remplaçable sur un périmètre autorisé.

### C.15 Économie et mesure

**Ce qui existe.** L'indicateur principal proposé est le coût par modification acceptée, pas le prix par million de tokens . Les mesures de productivité sont contradictoires : METR 2025 (temps supérieur de 19 %), METR 2026 (non concluant, effets de sélection), étude randomisée citée (+26 % de tâches terminées).

**Résultats évalués.** Aucun multiplicateur universel de productivité n'est défendable. Les gains dépendent du contexte, de l'expérience des équipes et de la nature des tâches.

**Limites et questions.** Comment instrumenter le coût par modification acceptée ? Comment mesurer la valeur métier, pas seulement la vélocité ? L'arbitrage entre API, location de GPU, SecNumCloud et achat dépend du taux d'utilisation réel : l'achat ne se justifie qu'après mesure de ce taux pendant quelques mois. Le coût complet (électricité, refroidissement, exploitation, colocation) doit être intégré, pas seulement le prix du GPU.

Dispositif proposé (recommandation) : un **banc d'essai interne** de 30 à 50 tickets réels, avec critères d'acceptation, pour comparer 3 à 4 modèles via des API européennes avant tout investissement matériel. Le banc doit être revu à chaque génération majeure de modèles. Une feuille de route en trois phases (cadrer/mesurer, généraliser, réduire la dépendance) découle de cette mesure.

**Conséquences.** Le coût dominant pourrait ne pas être le token, mais le temps humain de revue. C'est une hypothèse à mesurer selon le contexte, pas un résultat établi.

**Recommandations.**
- Mesurer le coût par modification acceptée, le taux de modifications acceptées sans retouche, le temps de revue humaine, les régressions post-fusion, la part d'usage IA sur services européens, la satisfaction des développeurs.
- Ne pas dimensionner une équipe sur un multiplicateur hypothétique.

Le coût d'interrogation d'un modèle atteignant le niveau de GPT‑3.5 sur MMLU (64,8) est passé de 20 dollars par million de jetons en novembre 2022 à 0,07 dollar en octobre 2024, soit une baisse de plus de 280 fois en environ 18 mois ([Stanford HAI, AI Index 2025](https://hai.stanford.edu/ai-index/2025-ai-index-report/research-and-development)). Ce fait porte sur un niveau de performance et une évaluation donnés ; il ne mesure ni le coût des modèles les plus capables ni le coût complet d'un changement. Postes proposés pour le coût par modification acceptée : préparation du contexte, génération, évaluations automatiques, revue humaine, corrections, déploiement, surveillance, traitement des défauts découverts après acceptation. Les métriques de production doivent être associées à des métriques de résultat, pour limiter l'effet décrit par la loi de Goodhart (une mesure qui devient un objectif cesse d'être une bonne mesure).

### C.16 Souveraineté et dépendances

**Ce qui existe.** La souveraineté doit être traitée comme une propriété de toute la chaîne (modèle, inférence, agent, IDE, forge, CI), pas seulement du modèle. Les offres européennes d'inférence existent (Scaleway, OVHcloud, Mistral). Les modèles open weight ne sont pas automatiquement souverains : le critère est l'opérateur de l'inférence, pas la nationalité du créateur ([Futurium / Commission européenne](https://futurium.ec.europa.eu/en/apply-ai-alliance/community-content/sovereign-infrastructure-sovereign-capability-europe-open-weight-ai-race), [tech.eu](https://tech.eu/2026/09/18/open-ai-closes-the-gap-as-europe-bets-on-sovereignty-and-infrastructure/)).

**Résultats évalués.** La qualification SecNumCloud 3.2 existe et exige un siège dans l'UE et un contrôle capitalistique limitant l'influence des entités soumises à un droit tiers (non vérifié à la source). L'EUCS n'est pas adopté ; la Commission semble déplacer la souveraineté vers la commande publique (Cloud and AI Development Act) (selon [IT SOCIAL](https://itsocial.fr/cybersecurite/cybersecurite-articles/eucs-et-cada-leurope-abandonne-la-souverainete-dans-son-label-cloud-et-la-reintroduit-dans-la-commande-publique/), non vérifié à la source primaire).

**Limites et questions.** Principe proposé : examiner tous les flux de données de la chaîne (modèle, inférence, agent, IDE, forge, CI), pas seulement le modèle : un modèle hébergé en Europe ne suffit pas si l'IDE, l'agent ou l'indexation sémantique passent par un service américain. Questions signalées par des praticiens, non vérifiées aux sources primaires : les licences « modifiées » à seuil (ex. Mistral), la dépréciation et la redirection automatique de modèles chez un hébergeur, la réversibilité via conservation des poids et diversification des familles. Ces questions doivent être vérifiées auprès des sources primaires avant de fonder une recommandation.

**Conséquences.** Un modèle chinois ou américain auto-hébergé en Europe peut être plus souverain qu'une API européenne mal contractualisée.

**Recommandations.**
- Classer les dépôts en N1/N2/N3 selon la confidentialité, pas selon la phase.
- Vérifier chaque maillon de la chaîne, pas seulement le modèle.
- Lire chaque licence avant de décider de l'auto-hébergement.

### C.17 Sécurité et cadre européen

**Ce qui existe.** Le RGPD, l'AI Act, le NIS2 et le CRA s'appliquent à des objets distincts (données personnelles, systèmes d'IA, entités critiques, produits numériques). Le code généré par IA reste sous la responsabilité du fabricant : gestion des vulnérabilités, SBOM, traçabilité (pièce jointe, sections 10 et 12).

**Résultats évalués.** Les calendriers ont été vérifiés auprès des sources officielles :
- **AI Act** : entré en vigueur le 1er août 2024 ; obligations GPAI et gouvernance depuis le 2 août 2025 ; pouvoirs d'exécution depuis le 2 août 2026 ; systèmes à haut risque de l'annexe III le 2 décembre 2027 ([Commission européenne](https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai)).
- **NIS2 en France** : la page ANSSI consultée décrit le processus de transposition et ne permet pas d'en établir l'état juridique exact en octobre 2026. Le ReCyF est disponible depuis le 17 mars 2026 comme document de travail, non obligatoire par défaut, mais prévalable en cas de contrôle ([ANSSI](https://cyber.gouv.fr/reglementation/cybersecurite-systemes-dinformation/directives-nis-nis2-et-dispositif-saiv/directive-nis-2/)).
- **CRA** : entré en vigueur le 10 décembre 2024 ; obligations de signalement depuis le 11 septembre 2026 ; obligations principales le 11 décembre 2027 ([Commission européenne](https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act)).

**Limites et questions.** Le CSA documente un « governance gap » dans le vibe coding : les frameworks de sécurité IA existants (NIST AI RMF, OWASP LLM Top 10, CSA MAESTRO, AICM avec 243 objectifs de contrôle sur 18 domaines et 5 rôles d'acteurs) manquent de guidance dédiée aux citizen developers, et un scan d'octobre 2025 sur 5 600 applications vibe-codées en production n'a trouvé aucune avec protection CSRF ou en-têtes de sécurité standard (CSP, HSTS, X-Frame-Options) ; toutes présentaient des vulnérabilités SSRF dans les fonctions de gestion d'URL ([CSA, juin 2026](https://labs.cloudsecurityalliance.org/wp-content/uploads/2026/06/CSA_research_note_vibe_coding_ai_governance_gap_20260602-csa-styled.pdf)). Trois niveaux à distinguer : conformité du produit (CRA, EUCC), obligations de l'organisation (NIS2, RGPD), qualification de l'hébergement (SecNumCloud, C5, ENS, ACN, HDS). Les référentiels cloud ne certifient pas le code.

**Conséquences.** Les choix d'outils IA deviennent un enjeu de conformité, pas seulement de productivité. NIS2 article 21(2)(d) et (e) englobent la chaîne d'approvisionnement et la sécurité du développement.

**Recommandations.**
- Documenter une politique d'usage de l'IA approuvée par la direction.
- Évaluer formellement chaque fournisseur de la chaîne IA.
- Exercer la notification 24 h / 72 h (NIS2 et CRA partagent ces délais).

### C.18 Prospective

**Ce qui existe.** Les acteurs intègrent verticalement : Musk (datacenters, Grok, Cursor, Macrohard), Amazon (AWS + agentic R&D), Google (Mainframe Assessment Tool + Dual Run). Les agents deviennent plus autonomes et travaillent sur de longues tâches. Les modèles compacts (20-80 milliards de paramètres) rendent l'auto-hébergement plus accessible.

**Résultats évalués.** Les annonces de Musk (disparition du code traditionnel, Macrohard capable de reproduire des entreprises logicielles) sont des déclarations d'intention, pas des capacités démontrées. L'acquisition de Cursor par SpaceX est vérifiée ([Cursor, 14 août 2026](https://cursor.com/blog/joining-spacex)), mais l'intégration verticale décrite au tour 4 reste une lecture des annonces, pas une stratégie publiée.

**Limites et questions.** Nous ne savons pas jusqu'où les agents pourront mener seuls des transformations longues, ambiguës et transversales. L'effet net sur l'emploi reste incertain.

**Conséquences.** L'analyse ne dépend pas de la prédiction de Musk sur la disparition du code traditionnel. La question reste pertinente même si cette prédiction ne se réalise pas : que devient le développement lorsque des machines peuvent effectuer une part croissante du travail de réalisation ?

**Recommandations.**
- Traiter les stratégies d'acteurs comme des cas documentés, pas comme des preuves du futur.
- Formuler des scénarios conditionnels, pas des prédictions uniques.


### C.19 Architectures vérifiables, composables et portables

Rust, l'IA générative et WebAssembly posent une question d'architecture : quels choix facilitent la vérification et la transmission du produit quand une part croissante du code est générée ? Nous en retenons les distinctions utiles au Product Management, sans adopter l'hypothèse d'un langage universel ni transformer les trajectoires parfois annoncées pour 2027 à 2031 en prévisions établies.

#### C.19.1 Le compilateur comme vérification partielle

GitHub décrit le typage comme un contrat utile entre développeurs, outils et agents pour détecter certaines incohérences ; son analyse de l'adoption de TypeScript présente des corrélations, et non la preuve que l'IA provoque ce choix ou qu'un langage typé est toujours supérieur ([GitHub](https://github.blog/ai-and-ml/llms/why-ai-is-pushing-developers-toward-typed-languages/)). Nous proposons d'en tirer une recommandation plus limitée : privilégier des environnements qui donnent aux agents et aux mainteneurs un retour vérifiable, adapté aux défauts que l'on cherche à éviter.

L'intérêt n'est donc pas « Rust gagne », mais « certaines erreurs deviennent détectables avant l'usage ». Cette idée complète notre séparation entre génération et acceptation : la compilation constitue un niveau de contrôle, pas le critère final.

| Niveau de contrôle proposé | Question examinée | Ce qu'il ne prouve pas à lui seul |
|---|---|---|
| Types, compilation et analyses statiques | Le programme respecte-t-il les règles contrôlées par ces outils ? | L'intention métier, la qualité du service ou l'absence de tout défaut |
| Tests techniques et de propriétés | Les cas et invariants testés sont-ils satisfaits ? | La couverture exhaustive des usages et exceptions |
| Cas métier indépendants | Les résultats attendus par le métier sont-ils obtenus ? | L'aptitude à l'exploitation sur toutes les plateformes |
| Essais d'exploitation et d'usage | Les risques, performances et résultats sont-ils acceptables dans les conditions prévues ? | Une garantie permanente après toute évolution |

Rust ne dispense pas d'examiner les frontières où ses garde-fous ne suffisent pas : Microsoft exige notamment de justifier les usages de `unsafe`, de tester les abstractions concernées et de mesurer avant de l'utiliser pour gagner en performance ; sa documentation précise qu'une fonction techniquement « safe » peut néanmoins effectuer une opération dangereuse comme supprimer une base de données ([Microsoft, Pragmatic Rust Guidelines](https://microsoft.github.io/rust-guidelines/guidelines/correctness/index.html)). Pour notre méthode, sûreté mémoire, autorisation d'agir et correction métier restent donc trois questions distinctes.

#### C.19.2 Séparer le moteur de la manière de l'utiliser

Une architecture souvent proposée consiste à écrire des moteurs en Rust exposés à des interfaces écrites dans d'autres langages. Nous retenons le principe architectural sans prescrire le langage : isoler la logique métier ou le traitement derrière des contrats explicites, puis choisir les interfaces et technologies selon les utilisateurs, les contraintes et les compétences disponibles.

Cette séparation prolonge le cas ArtCraft : PhotoCraft et FilmCraft documentent déjà un même moteur de commandes accessible par l'interface graphique, la CLI et MCP ([PhotoCraft](https://github.com/storytold/photocraft), [FilmCraft](https://github.com/storytold/filmcraft)). Ce constat ne prouve pas qu'une architecture donnée est supérieure ; il fournit un exemple concret de produit qui ne se réduit pas à son écran.

Nous proposons de comparer trois trajectoires :

- **Conserver :** garder un composant maîtrisé quand le bénéfice attendu ne justifie pas sa migration.
- **Encapsuler :** définir un contrat et des tests autour du moteur existant pour permettre de nouveaux usages sans réécrire toute sa logique.
- **Remplacer sélectivement :** reconstruire un composant borné si des mesures de risque, de performance, de portabilité ou de maintenabilité justifient le coût.

Une architecture polyglotte n'est pas une fin en soi. Nous recommandons de compter aussi les contrats à maintenir, les conversions de données, le diagnostic entre langages, l'outillage et la capacité d'un successeur à reprendre le système.

#### C.19.3 WebAssembly : une option de distribution, pas un langage unique

MDN présente WebAssembly comme une cible de compilation pouvant notamment recevoir du C++ ou du Rust, conçue pour cohabiter avec JavaScript ; dans le navigateur, les échanges avec les API web passent par les mécanismes d'intégration avec JavaScript, et la documentation ne promet pas un gain de performance chiffré pour toute application ([MDN, concepts WebAssembly](https://developer.mozilla.org/en-US/docs/WebAssembly/Guides/Concepts)). Il faut donc distinguer langage d'implémentation, format de distribution, environnement d'exécution et interface utilisateur.

Pour le Product Management, nous proposons d'évaluer Wasm par les usages qu'il permet : proposer certains traitements dans un navigateur, réutiliser un moteur, réduire une installation ou offrir une alternative locale. Ce sont des options à expérimenter, pas des bénéfices acquis ; le téléchargement initial, la mémoire, les échanges de données et les API disponibles doivent entrer dans les critères d'acceptation.

De même, partager du code ne démontre pas que le service est identique sur toutes les cibles. Nous recommandons de conserver une matrice de plateformes et des preuves par cible, notamment pour l'affichage, l'accessibilité, les fichiers, les performances et la reprise.

#### C.19.4 Exécution locale : une valeur possible, pas une preuve de souveraineté

WebGPU permet d'utiliser le GPU pour le rendu et le calcul parallèle ; la documentation MDN consultée signale une disponibilité limitée selon les navigateurs et un contexte sécurisé requis ([MDN, WebGPU](https://developer.mozilla.org/en-US/docs/Web/API/WebGPU_API)). Nous ne devons donc pas confondre la capacité technique de calcul local avec une promesse applicable à tous les appareils du client.

Nous proposons d'étudier quatre effets produit possibles : le fonctionnement sans connexion pour des tâches bornées, la réduction des données envoyées au serveur, la latence ressentie et la prévisibilité des coûts. Il faut les mesurer avec leurs contreparties : matériel disponible, mémoire, consommation d'énergie, assistance et mode de repli.

L'exécution locale ne démontre pas, à elle seule, la souveraineté de l'ensemble. Notre recommandation reste de cartographier les flux de l'application, y compris mises à jour, télémétrie, authentification, modèles et services optionnels ; une économie d'infrastructure peut aussi déplacer des coûts vers les appareils et le support plutôt que les supprimer.

#### C.19.5 WASI et WIT : préciser les contrats des composants

Le Component Model de WebAssembly ajoute des types de plus haut niveau et la composition de composants ; WIT décrit leurs signatures d'interfaces indépendamment du langage, et un « world » exprime les fonctionnalités offertes et celles dont le composant dépend ([Bytecode Alliance](https://component-model.bytecodealliance.org/design/component-model-concepts.html)). WASI désigne une famille d'interfaces système définies en WIT, à distinguer de l'intégration d'un module Wasm dans une page web ([Bytecode Alliance](https://component-model.bytecodealliance.org/design/component-model-concepts.html)).

Cela suggère un prolongement de notre SDD : associer à une exigence un contrat d'interface, les services nécessaires, les cas de test et les versions compatibles. Nous proposons de traiter séparément le contrat typé, la sémantique métier et les permissions effectivement configurées dans l'environnement hôte ; un contrat de fonctions ne vaut ni preuve de correction ni autorisation générale d'accès.

MCP et WIT ne sont pas interchangeables : les exemples ArtCraft utilisent MCP pour exposer des commandes à un agent, tandis que WIT sert à décrire des interfaces de composants WebAssembly ([PhotoCraft](https://github.com/storytold/photocraft), [Bytecode Alliance](https://component-model.bytecodealliance.org/design/component-model-concepts.html)). Dans notre architecture proposée, ils pourraient intervenir à des niveaux différents ; aucun des deux ne dispense de vérifier le comportement et les droits.

#### C.19.6 Mesurer la boucle complète et prévoir la reprise humaine

L'enquête officielle Rust documente des difficultés de compilation et de recompilation très variables selon les projets ; la question où 55 % des répondants déclaraient attendre plus de dix secondes concernait le projet qu'ils avaient choisi comme le plus problématique, et non tous les projets Rust ([Rust, enquête 2025](https://blog.rust-lang.org/2025/09/10/rust-compiler-performance-survey-2025-results/)). Nous ne reprenons donc pas ce chiffre comme une durée générale de la boucle agentique.

Nous proposons de mesurer ensemble préparation du contexte, génération, compilation, tests, corrections, revue, intégration et mise à jour de la connaissance. Le choix technique doit être jugé sur le coût par changement accepté et le risque résiduel, pas sur la seule vitesse de génération ou la seule sévérité du compilateur.

Pour un pilote, nous recommandons de sélectionner un composant autonome, puis de comparer le maintien de l'existant, son encapsulation et une réimplémentation ciblée. La décision doit inclure les tests d'équivalence utiles, les différences voulues, les plateformes réellement prises en charge, le coût d'exploitation et une personne capable d'en assurer la maintenance.

L'apport à notre thèse centrale est donc précis : le patrimoine transmissible comprend aussi les contrats, les contraintes d'exécution, les preuves par plateforme et les moyens de validation reproductibles. Une architecture favorable aux agents ne devient durable que si elle reste compréhensible, vérifiable et exploitable par les personnes qui la reprendront.

### C.20 Vérifiabilité, évaluation et compréhension

Cette fiche transversale couvre les sujets 49 à 57. Ses références ont été consultées à la source en octobre 2026.

**Ce qui existe.**
- Une grille conceptuelle : Jason Wei décrit une asymétrie entre production et vérification et formule une « règle du vérificateur » selon laquelle la facilité d'entraîner une IA à une tâche serait proportionnelle à la facilité de vérifier ses résultats ; il identifie cinq propriétés favorables (vérité objective, vérification rapide, à grande échelle, faible bruit, récompense continue) ([Jason Wei, juillet 2025](https://www.jasonwei.net/blog/asymmetry-of-verification-and-verifiers-law)). Statut : analyse d'un chercheur, pas loi démontrée.
- Des évaluations spécialisées : FrontierMath rassemble des centaines de problèmes inédits, vérifiés automatiquement, sur lesquels les meilleurs modèles résolvaient moins de 2 % des problèmes à la publication en novembre 2024 ([arXiv 2411.04872](https://arxiv.org/abs/2411.04872)). Ce score ne renseigne ni sur les compétences produit ni sur le travail logiciel réel.
- Des productions mathématiques à grande échelle accompagnées de formalisations : dépôt openai/math (719 manuscrits, 372 familles, environ 42 % de résultats principaux formalisés en Lean, résultats à différents stades de vérification selon le README) ([GitHub, openai/math](https://github.com/openai/math)) ; dépôt anthropics/formal-math, où un projet n'est accepté que si la compilation Lean réussit et si un comparateur confirme que la solution correspond à l'énoncé déclaré ([GitHub, anthropics/formal-math](https://github.com/anthropics/formal-math)).
- Une déclaration d'entreprise : OpenAI annonce une preuve de formation de singularité pour Navier–Stokes avec une force extérieure lisse, formalisée en Lean, obtenue par environ 10 000 agents en 88 heures ([OpenAI, 8 septembre 2026](https://openai.com/index/navier-stokes-solution/)).

**Résultats évalués.**
- Des mathématiciens interrogés par NPR ne pensent pas que la preuve Navier–Stokes soit fausse, mais la jugent difficile à lire et peu instructive à ce stade ([NPR, 22 septembre 2026](https://www.npr.org/2026/09/22/nx-s1-5968588/openai-navier-stokes-problem-mathematicians-learn-little)).
- Constantin, Ignatova et Vicol établissent, sous deux propriétés de la construction, que la force ne peut être ni réelle-analytique en espace ni nulle près du point singulier ; résultat conditionnel, pas réfutation générale ([arXiv 2609.20803](https://arxiv.org/abs/2609.20803)).
- Quanta Magazine rapporte que des preuves vérifiées par programme restent souvent difficiles à lire et que les mathématiciens discutent la formation, l'acceptation des articles et le recrutement ([Quanta Magazine, 5 octobre 2026](https://www.quantamagazine.org/is-ai-the-end-of-math-as-we-know-it-20261005/)).
- Duminil-Copin défend que la mission des mathématiciens est d'abord de produire de la compréhension et décrit les idées et collaborations issues de ses tentatives infructueuses ([Duminil-Copin, 30 août 2026](https://proofsandprompts.com/2026/08/30/care-for-a-little-more-ai/)).
- Aucune source consultée ne mesure l'effet de la vérifiabilité sur l'automatisation du développement logiciel ou du Product Management.

**Limites et questions.**
- Un vérificateur formel établit qu'une preuve démontre l'énoncé écrit, pas que cet énoncé est celui qui importait. Le même écart existe entre conformité à une spécification et justesse de cette spécification.
- Le développement produit diffère des mathématiques formalisées : l'énoncé se découvre souvent en chemin, les critères de qualité sont partiels, les effets se constatent en exploitation. Aucune extrapolation directe n'est défendable.
- Les comptages des dépôts évoluent ; ils doivent être datés et, pour un exemple précis, cités avec une version ou un commit.
- Plusieurs affirmations répandues sur ces cas ne sont pas établies ou sont inexactes (annexe G).

**Conséquences (analyse).**
- La qualité du système d'évaluation devient déterminante quand la production accélère, que l'on développe avec l'IA ou que l'on développe un produit contenant de l'IA.
- Ce système est aussi une source de risque : incomplet, dépassé ou trop lié à l'implémentation, il peut confirmer un comportement faux. Des contrôles qui guident la génération et servent aussi à l'accepter perdent une partie de leur valeur de preuve.
- Un résultat techniquement correct mais incompris reste difficile à maintenir, à diagnostiquer et à remplacer.
- La question de la formation du jugement se pose dans le développement produit comme en mathématiques.

**Recommandations (propositions, non validées par une étude).**
- Analyser les activités, non les métiers, selon six dimensions : clarté de l'objectif, qualité de l'évaluation, délai de retour, couverture, coût d'un échec, réversibilité.
- Versionner le système d'évaluation et documenter pour chaque contrôle son but, l'origine des résultats attendus, ses limites, ses cas exclus, ses responsables et ses déclencheurs de révision (fiche C.8).
- Accepter à trois niveaux (technique, métier, produit et exploitation) avec une autorité désignée par niveau (fiche C.11).
- Conserver des évaluations indépendantes de celles qui guident la génération ; associer métriques de production et métriques de résultat (fiche C.15).
- Exiger pour les changements significatifs une justification proportionnée au risque.
- Expérimenter des pratiques de formation du jugement et mesurer leur effet (fiche C.6).

## D. Notions fondamentales venues d'autres disciplines

### D.1 Question et limites

D'autres disciplines ont-elles déjà réfléchi à ce qui se passe quand l'exécution s'automatise et que le travail humain se déplace vers le contrôle, le jugement et l'acceptation ? Cette annexe rassemble les notions établies qui éclairent ce déplacement. La recherche a porté sur huit domaines : génie logiciel classique, ingénierie des exigences, facteurs humains et aviation, médecine, finance, droit et régulation, sûreté des systèmes, économie du travail et apprentissage. Les textes primaires ou leur notice officielle ont été lus en octobre 2026.

Limites :
- Il ne s'agit pas d'une revue systématique. Le droit (citations inventées par des IA dans des procédures), l'évaluation par les pairs en science et le contrôle aérien n'ont pas été explorés en profondeur.
- Plusieurs textes classiques ont été lus dans une version PDF accessible en ligne, et non dans la version de l'éditeur. Les citations courtes en anglais sont tirées des textes consultés.
- Le transfert d'une notion d'un domaine à l'autre est une analogie. Il fournit une hypothèse et un vocabulaire, pas une preuve.

### D.2 Synthèse

#### D.2.1 Ce que les autres domaines montrent

1. **Le génie logiciel a déjà un vocabulaire précis pour la vérifiabilité.** Il parle du « problème de l'oracle », c'est-à-dire la difficulté de savoir quel est le bon résultat attendu d'un test. Il distingue aussi, depuis Boehm, la vérification de la validation. La règle du vérificateur de Wei et le billet de Karpathy redécouvrent une partie de ce corpus.
2. **La vérifiabilité a déjà été contestée comme critère dominant.** En 1979, De Millo, Lipton et Perlis écrivaient : « Verifiability is not and cannot be a dominating concern in software design. » Leur argument est que l'acceptation d'une preuve est un processus social de lecture et de discussion. C'est exactement la question soulevée par le cas des mathématiques.
3. **Les facteurs humains ont décrit les « ironies de l'automatisation » en 1983.** Plus un système est automatisé, plus l'intervention humaine qui reste devient difficile et décisive. En même temps, les occasions d'entretenir les compétences nécessaires diminuent. C'est la situation de la personne qui relit le travail d'agents.
4. **La médecine fournit une mesure de la déqualification.** Après l'introduction de l'IA en coloscopie, le taux de détection sans IA a baissé. C'est une donnée d'un autre domaine qui complète l'essai d'Anthropic sur l'apprentissage.
5. **La régulation et l'étude des accidents montrent les limites de la supervision humaine.** L'humain placé « dans la boucle » peut devenir celui qui porte la faute sans avoir eu le contrôle. Ce risque concerne directement la notion d'autorité d'acceptation du document.
6. **L'économie explique pourquoi la revue devient le goulot.** Quand une étape devient bon marché, la valeur et le poids des étapes complémentaires augmentent. La qualité d'ensemble dépend alors du maillon le plus faible.
7. **La gestion de la qualité rappelle qu'on ne peut pas tout obtenir par l'inspection.** Un raisonnement centré sur la vérification risque d'oublier qu'une partie de la qualité doit être construite en amont.

#### D.2.2 Les notions retenues

Les notions retenues sont regroupées en cinq familles. Le tableau indique leur origine, leur apport et les sections du corps concernées. Elles sont détaillées dans les dix-huit fiches qui suivent.

| Famille | Notion | Domaine d'origine | Apport au raisonnement | Sections |
|---|---|---|---|---|
| Vérifier | Problème de l'oracle | Test logiciel | Nom établi de la question « comment savoir que le résultat est bon » | 2.2, annexe F |
| Vérifier | Vérification et validation | Génie logiciel, ingénierie système | Origine de la distinction « bien construire le produit » et « construire le bon produit » | 3.2, 5.2 |
| Vérifier | Limites de la vérifiabilité comme critère | Informatique théorique et sociologie de la preuve | Contrepoint à Wei et Karpathy | 2.2, annexe G |
| Vérifier | Asymétrie inverse de la réfutation | Adage issu de la culture logicielle | Pour un texte libre, vérifier coûte plus que produire | 2.2, 4.2 |
| Spécifier | Complexité essentielle et accidentelle | Génie logiciel | Ce que l'IA réduit et ce qu'elle laisse | 2.1, 4.2 |
| Spécifier | Exigences portant sur l'environnement | Ingénierie des exigences | Le vérifiable porte sur la machine, la pertinence sur le monde | 3.2, 4.2 |
| Spécifier | Logiciel de type E et boucles de rétroaction | Évolution du logiciel | Un logiciel utilisé doit évoluer ; on ne le spécifie jamais une fois pour toutes | 4.2, 6.1 |
| Spécifier | Contrat implicite (loi de Hyrum) | Conception d'API | Les utilisateurs dépendent aussi de comportements non spécifiés | 5.2, 6.1 |
| Spécifier | Contournement de spécification | Apprentissage par renforcement | Respecter la lettre d'un objectif sans atteindre le but | 4.1, 5.2 |
| Spécifier | Complaisance des modèles (sycophancy) | Recherche sur les modèles de langage | L'IA tend à confirmer l'avis de son utilisateur | 3.2 |
| Superviser | Ironies de l'automatisation | Facteurs humains, contrôle de procédés | La surveillance de l'automate est une tâche difficile et mal entretenue | 5.2, 7.1 |
| Superviser | Complaisance envers l'automate et biais d'automatisation | Aviation, facteurs humains | Erreurs d'omission et de commission face à une aide imparfaite | 5.2 |
| Superviser | Zone de déformation morale et limites de la supervision humaine | Sociologie des techniques, droit public | L'humain dans la boucle peut porter la faute sans avoir le contrôle | 5.2, 7.3 |
| Superviser | Contradiction effective | Finance (risque de modèle) | Conditions d'une contre-expertise réelle : compétence, indépendance, influence | 5.2, 7.3 |
| Superviser | Accidents normaux | Sûreté des systèmes | Complexité et couplage serré rendent certaines défaillances inévitables | 5.1, 5.3 |
| Apprendre | Déqualification mesurée | Médecine | Les compétences baissent quand l'aide disparaît | 7.1 |
| Apprendre | Difficultés désirables | Psychologie de l'apprentissage | Ce qui ralentit l'apprentissage apparent peut améliorer la rétention | 7.1 |
| Valoriser | Complémentarité et maillon faible | Économie du travail et du développement | Pourquoi la revue et le jugement prennent de la valeur | 2.3, 7.2 |
| Valoriser | Prédiction et jugement | Économie de l'IA | L'IA abaisse le coût de la prédiction, pas celui du jugement | 2.3, 3.2 |
| Valoriser | Effet rebond (paradoxe de Jevons) | Économie de l'énergie | Un code moins cher peut augmenter le volume total à vérifier | 7.2 |
| Valoriser | Qualité intégrée plutôt qu'inspectée | Gestion de la qualité | Contrepoint à un modèle centré sur la revue | 4.1, 5.2 |

### D.3 Famille 1 : vérifier

#### D.3.1 Le problème de l'oracle

Source : Barr, Harman, McMinn, Shahbaz et Yoo, « The Oracle Problem in Software Testing: A Survey », IEEE Transactions on Software Engineering, mai 2015 ([IEEE Computer Society](https://www.computer.org/csdl/journal/ts/2015/05/06963470/13rRUx0geBw)). Notice consultée ; texte intégral non relu.

Ce que la notion désigne : un oracle de test est le mécanisme qui permet de dire si un comportement observé est correct. Le « problème de l'oracle » est la difficulté, souvent le coût, de disposer d'un tel mécanisme. Le domaine a développé des réponses partielles : oracles implicites (absence de plantage), tests de propriétés, relations métamorphiques (comparer deux exécutions liées plutôt que connaître la bonne réponse), oracles humains.

Analogie : la vérifiabilité dont parlent Wei et Karpathy est l'existence d'un oracle bon marché. Les méthodes du test logiciel indiquent comment construire un oracle partiel quand il n'y en a pas.

Portée : la vérifiabilité dont parlent Wei et Karpathy revient à disposer d'oracles, et la grille de l'annexe F peut se lire comme une grille de disponibilité et de coût des oracles (section 2.2).

#### D.3.2 Vérification et validation

Source : Barry W. Boehm, « Verifying and Validating Software Requirements and Design Specifications », IEEE Software, vol. 1, n° 1, janvier 1984, p. 75 à 88 ([IEEE Computer Society](https://www.computer.org/csdl/magazine/so/1984/01/01695100/13rRUxD9h2X)). Notice consultée ; texte intégral non relu.

Ce que la notion désigne : la vérification demande « construisons-nous le produit correctement ? », c'est-à-dire conformément à sa spécification. La validation demande « construisons-nous le bon produit ? », c'est-à-dire répond-il au besoin. Cette formulation est couramment attribuée à Boehm. Le mot à mot doit être vérifié sur le texte avant toute citation.

Analogie : deux des cinq distinctions du document (vérifier et valider ; conformité et justesse de la spécification) reprennent cette distinction ancienne.

Portée : l'apport propre de ce document n'est pas la distinction elle-même, mais le constat que l'IA fait baisser fortement le coût de la vérification, et pas celui de la validation (section 3.2).

#### D.3.3 Les limites de la vérifiabilité comme critère

Source : De Millo, Lipton et Perlis, « Social Processes and Proofs of Theorems and Programs », Communications of the ACM, vol. 22, n° 5, 1979, p. 271 à 280 ([PDF hébergé par l'université du Maryland](https://www.cs.umd.edu/~gasarch/BLOGPAPERS/social.pdf)).

Thèse : en mathématiques, une preuve est acceptée parce qu'une communauté la lit, la discute et la transforme. Une vérification formelle de programme ne joue pas ce rôle social. Les auteurs écrivent : « Verifiability is not and cannot be a dominating concern in software design. » Ils plaident pour que la fiabilité prime sur la vérifiabilité. L'article a été très contesté par les tenants des méthodes formelles. Il doit être présenté comme une position dans un débat, pas comme une conclusion.

Analogie : c'est le précédent direct du débat sur les preuves produites par IA (Quanta, NPR, Duminil-Copin). Une preuve vérifiée formellement mais non comprise ne remplit pas toute la fonction d'une preuve.

Portée : ce texte fournit un contrepoint argumenté à la règle du vérificateur, utile pour le cas des mathématiques (annexe G) et pour la distinction entre résultat correct et résultat compris (section 4.1).

#### D.3.4 L'asymétrie inverse de la réfutation

Source : la « loi de Brandolini », adage formulé en 2013 par le développeur Alberto Brandolini : réfuter une affirmation fausse demande beaucoup plus d'énergie que la produire ([Wikipédia, Brandolini's law](https://en.wikipedia.org/wiki/Brandolini's_law)). Statut : adage, pas résultat de recherche. Source secondaire.

Analogie : la règle de Wei suppose que vérifier est plus facile que produire. C'est vrai pour une réponse à une question fermée. Pour un texte libre (une analyse de marché, une synthèse de recherche utilisateur, une spécification en prose), c'est souvent l'inverse : produire est devenu presque gratuit, et vérifier chaque affirmation reste coûteux.

Portée : le sens de l'asymétrie dépend du type de résultat. C'est important pour le Product Management, dont une grande part des livrables sont des textes ; l'adage ne doit pas être cité comme une loi (section 2.2).

### D.4 Famille 2 : spécifier

#### D.4.1 Complexité essentielle et complexité accidentelle

Source : Frederick P. Brooks Jr., « No Silver Bullet: Essence and Accidents of Software Engineering », IEEE Computer, vol. 20, n° 4, avril 1987, p. 10 à 19 ([texte reproduit par l'UCSF](https://www.cgl.ucsf.edu/Outreach/pc204/NoSilverBullet.html)).

Thèse : la complexité accidentelle tient aux outils et aux langages. La complexité essentielle tient à la conception elle-même : décider ce que le logiciel doit faire et comment ses concepts s'articulent. Brooks soutient qu'aucune innovation isolée ne promet un gain d'un ordre de grandeur en productivité, fiabilité ou simplicité.

Analogie : les agents attaquent surtout la complexité accidentelle (écrire, traduire, migrer, tester). La complexité essentielle reste, et elle se concentre dans la spécification et la décision.

Limite : la thèse de Brooks est mise à l'épreuve par les agents. Certains affirment des gains d'un ordre de grandeur sur le codage (Andrew Ng parle de 10 à 100 fois). Les données de Chen et Stratton, qui ne trouvent pas de hausse significative des tickets résolus, vont plutôt dans le sens de Brooks. Ce débat est ouvert.

Portée : la distinction explique pourquoi le travail se déplace vers la spécification (section 2.1). La question « Brooks a-t-il encore raison ? » reste ouverte (section 8.1).

#### D.4.2 Les exigences portent sur l'environnement

Source : Pamela Zave et Michael Jackson, « Four Dark Corners of Requirements Engineering », ACM Transactions on Software Engineering and Methodology, vol. 6, n° 1, 1997, p. 1 à 30 ([PDF hébergé par Michigan State University](https://cse.msu.edu/~chengb/RE-491/Papers/dark-corners-re-zave-jackson.pdf)).

Thèse : « all statements made in the course of requirements engineering are statements about the environment ». Les auteurs distinguent ce qui est vrai du monde (propriétés indicatives) de ce que l'on souhaite (propriétés optatives). Une spécification n'est correcte que si, combinée à des connaissances justes sur le domaine, elle garantit l'exigence dans le monde réel.

Analogie : un agent peut vérifier qu'un programme respecte sa spécification. Il ne peut pas, avec les mêmes moyens, vérifier que les hypothèses sur le monde sont justes. C'est précisément la distinction du document entre conformité et justesse de la spécification. Zave et Jackson en donnent la structure logique.

Portée : ce cadre explique pourquoi une spécification peut être vérifiée sans être juste, et précise la contribution du Product Management : expliciter et tester les hypothèses sur le domaine (section 4.2).

#### D.4.3 Logiciel de type E et boucles de rétroaction

Source : M. M. Lehman, « Laws of Software Evolution Revisited », 1996 ([PDF hébergé par Kent State University](https://www.cs.kent.edu/~jmaletic/cs63902/Papers/Lehman96.pdf)). Le PDF consulté ne mentionne pas la revue d'origine ; référence à compléter.

Thèse : un logiciel de type E est embarqué dans le monde réel et le modifie. Il doit être adapté en permanence, sinon il devient de moins en moins satisfaisant, et sa complexité croît s'il n'est pas activement maintenu. Lehman soutient qu'une amélioration majeure passe par une modification des boucles de rétroaction du processus, pas seulement par de meilleurs outils.

Analogie : la plupart des produits gérés par un PM sont de type E. On ne peut pas les spécifier une fois pour toutes puis automatiser leur production. Accélérer l'écriture du code sans changer les boucles de retour (usage, exploitation, décision) ne change pas la dynamique d'ensemble.

Portée : la spécification est un état provisoire (sections 4.2 et 6.1). L'argument de Lehman rejoint celui de Chen et Stratton : le goulot est dans le processus.

#### D.4.4 Le contrat implicite (loi de Hyrum)

Source : Hyrum Wright, site de l'auteur ([hyrumslaw.com](https://www.hyrumslaw.com/)). Formulation : « With a sufficient number of users of an API, it does not matter what you promise in the contract: all observable behaviors of your system will be depended on by somebody. » Statut : observation de praticien, pas résultat de recherche.

Analogie : lors d'une migration ou d'une réimplémentation par des agents (boucle inverse du SDD, clones type ArtCraft, réécriture de chardet), l'équivalence avec la spécification ne suffit pas. Les utilisateurs dépendent aussi de comportements non documentés : délais, ordres de tri, messages d'erreur, arrondis.

Portée : lors d'une modernisation ou d'une vérification d'équivalence (sections 5.2 et 6.1), il faut inventorier les comportements observables (journaux, traces d'usage, tests de caractérisation), pas seulement les comportements spécifiés.

#### D.4.5 Le contournement de spécification

Source : Krakovna et al., « Specification gaming: the flip side of AI ingenuity », Google DeepMind, 21 avril 2020 ([Google DeepMind](https://deepmind.google/discover/blog/specification-gaming-the-flip-side-of-ai-ingenuity/)). Définition : « a behaviour that satisfies the literal specification of an objective without achieving the intended outcome ». Environ 60 exemples recensés à la date de publication.

Analogie : c'est la forme générale dont le reward hacking observé par METR est un cas particulier, et la version côté machine de la loi de Goodhart. Pour un produit, un agent peut satisfaire tous les critères d'acceptation écrits sans atteindre l'intention.

Portée : le terme relie la loi de Goodhart (côté organisation) et le reward hacking (côté modèle) dans un même mécanisme (section 4.1).

#### D.4.6 La complaisance des modèles (sycophancy)

Source : Sharma et al., « Towards Understanding Sycophancy in Language Models », arXiv 2310.13548, v1 du 20 octobre 2023, v4 du 10 mai 2025 ([arXiv](https://arxiv.org/abs/2310.13548)). Cinq assistants de pointe ont tendance à approuver l'avis de l'utilisateur plutôt que la réponse exacte, dans quatre types de tâches. Les préférences humaines utilisées pour l'entraînement favorisent en partie ce comportement.

Analogie : c'est un risque central pour la validation de pertinence. Un PM qui demande à un modèle d'évaluer son hypothèse, ses personas ou sa priorisation risque d'obtenir une confirmation. Ce biais touche le travail de découverte, pas seulement la vérification de la réalisation.

Portée : l'IA utilisée pour valider une décision n'est pas un contradicteur neutre. Il faut formuler les demandes sans révéler la réponse attendue, demander explicitement les arguments contraires et confronter à des données d'usage réelles (section 3.2).

### D.5 Famille 3 : superviser

#### D.5.1 Les ironies de l'automatisation, la complaisance et le biais d'automatisation

Sources :
- Lisanne Bainbridge, « Ironies of Automation », Automatica, vol. 19, n° 6, 1983, p. 775 à 779 ([PDF](https://ckrybus.com/static/papers/Bainbridge_1983_Automatica.pdf)). Thèse : l'automatisation laisse à l'opérateur les tâches les plus difficiles, tout en réduisant les occasions d'entretenir ses compétences. Phrase-clé : « the more advanced a control system is, so the more crucial may be the contribution of the human operator ». Elle rapporte que les études de vigilance montrent qu'une personne ne maintient pas efficacement son attention sur une source où il se passe peu de choses au-delà d'environ une demi-heure.
- Parasuraman et Manzey, « Complacency and Bias in Human Use of Automation: An Attentional Integration », Human Factors, vol. 52, n° 3, 2010, p. 381 à 410 ([PubMed](https://pubmed.ncbi.nlm.nih.gov/21077562/)). La complaisance apparaît sous charge multitâche et résiste à la simple pratique. Le biais d'automatisation provoque des erreurs d'omission (ne pas voir ce que l'automate n'a pas signalé) et de commission (suivre une recommandation fausse). Il n'est pas prévenu par la formation ou les consignes.

Analogie : relire des centaines de modifications proposées par des agents, dont la plupart sont correctes, est une tâche de surveillance au sens de Bainbridge. Les données de Chen et Stratton (plus de commentaires, plus de demandes de modifications) montrent que la revue tient encore. Rien ne garantit qu'elle tiendra quand le volume augmentera.

Portée : la revue humaine est une tâche de vigilance, avec ses limites connues. Il faut limiter le volume par relecteur, orienter l'attention vers les écarts plutôt que vers le flux complet, et ne pas compter sur la seule consigne « relisez attentivement » (section 5.2).

#### D.5.2 La zone de déformation morale et les limites de la supervision humaine

Sources :
- Madeleine Clare Elish, « Moral Crumple Zones: Cautionary Tales in Human-Robot Interaction », Engaging Science, Technology, and Society, 2019 ([SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2757236)). Dans un système automatisé complexe, l'humain peut devenir « a component [...] that bears the brunt of the moral and legal responsibilities » alors qu'il avait peu de contrôle. La notion est construite à partir de l'analyse d'accidents médiatisés.
- Ben Green, « The flaws of policies requiring human oversight of government algorithms », Computer Law & Security Review, vol. 45, 2022, article 105681 ([PDF de l'auteur](https://www.benzevgreen.com/wp-content/uploads/2022/04/22-clsr.pdf)). Analyse de 41 documents de politique publique. Conclusion : les données disponibles indiquent que les personnes ne peuvent généralement pas assurer de façon fiable la supervision attendue, et ces politiques peuvent légitimer des systèmes défaillants. L'auteur propose une supervision institutionnelle : justification écrite de l'usage, puis examen et approbation.
- Règlement européen sur l'IA, article 14 ([AI Act Service Desk, Commission européenne](https://ai-act-service-desk.ec.europa.eu/en/ai-act/article-14)). Pour les systèmes à haut risque, les personnes chargées de la supervision doivent pouvoir comprendre le système, interpréter ses résultats, décider de ne pas les suivre et l'interrompre. Le texte demande aussi qu'elles restent conscientes du biais d'automatisation.

Analogie : ce document propose une « autorité d'acceptation » désignée. Sans conditions, cette personne peut devenir une zone de déformation morale : elle signe sans avoir eu le temps, l'information ni le pouvoir de refuser.

Limite : l'article 14 concerne les systèmes d'IA à haut risque mis sur le marché, pas les agents utilisés pour développer un logiciel. Le transfert est une analogie, pas une obligation juridique.

Portée : l'autorité d'acceptation doit être assortie de conditions explicites (sections 5.2 et 7.3) :
- le temps et l'information nécessaires ;
- le pouvoir réel de refuser ou d'arrêter ;
- une trace écrite des raisons de l'acceptation ;
- une responsabilité de l'organisation sur le dispositif lui-même, pas seulement sur la personne qui signe.

C'est le renforcement le plus important de cette recherche.

#### D.5.3 La contradiction effective

Sources :
- Federal Reserve et OCC, SR 11-7, « Supervisory Guidance on Model Risk Management », 4 avril 2011 ([Federal Reserve](https://www.federalreserve.gov/boarddocs/srletters/2011/sr1107a1.pdf)). Principe directeur : l'« effective challenge » des modèles, c'est-à-dire une analyse critique par des parties compétentes et indépendantes.
- SR 26-2, « Revised Guidance on Model Risk Management », Federal Reserve, OCC et FDIC, 17 avril 2026 ([Federal Reserve](https://www.federalreserve.gov/supervisionreg/srletters/SR2602.htm)). Ce texte remplace SR 11-7 et SR 21-8. Selon l'analyse du cabinet Orrick ([Orrick](https://www.orrick.com/en/Insights/2026/04/Agencies-Overhaul-Model-Risk-Management-Guidance-for-Banks-Heres-What-Changed)), la contradiction effective est conservée et définie par trois conditions : expertise appropriée, indépendance suffisante et influence suffisante pour obtenir des changements. Les modèles d'IA générative et agentique sont explicitement exclus du champ. Ce dernier point vient d'Orrick et doit être confirmé sur le texte de la guidance.

Analogie : la finance a une doctrine de plus de quinze ans sur la contre-expertise de systèmes que l'on ne peut pas entièrement vérifier. Ses trois conditions (compétence, indépendance, influence) donnent un contenu concret à l'autorité d'acceptation.

Point d'actualité : en 2026, le régulateur bancaire américain exclut l'IA générative et agentique de ce cadre et renvoie à la gouvernance générale des risques. Il n'existe donc pas encore de doctrine équivalente pour les agents dans ce secteur.

Portée : les trois conditions servent de grille pour l'autorité d'acceptation (section 7.3). L'exclusion, en 2026, des modèles d'IA générative et agentique du champ de la nouvelle guidance montre que la question n'est pas réglée.

#### D.5.4 Les accidents normaux

Source : Charles Perrow, « Normal Accidents: Living with High-Risk Technologies » (1984), présenté dans Nick Pidgeon, « In retrospect: Normal Accidents », Nature, vol. 477, 2011, p. 404 et 405 ([Nature](https://www.nature.com/articles/477404a)). Thèse : les systèmes qui combinent forte complexité d'interaction et couplage serré sont sujets à des défaillances même lorsqu'ils sont bien gérés.

Analogie : des agents enchaînés, qui modifient le code, lancent des déploiements et réagissent aux sorties les uns des autres, augmentent à la fois la complexité et le couplage. Les permissions et la réversibilité de chaque agent ne traitent pas cette propriété du système dans son ensemble.

Portée : le couplage est un critère de délégation, à côté de la réversibilité (section 5.1). Découpler les étapes (validation entre deux actions, limites de propagation) réduit le risque, même si chaque agent est fiable.

### D.6 Famille 4 : apprendre

#### D.6.1 La déqualification mesurée et les difficultés désirables

Sources :
- Budzyń et al., « Endoscopist deskilling risk after exposure to artificial intelligence in colonoscopy », The Lancet Gastroenterology & Hepatology, publié le 12 août 2025 ([The Lancet](https://www.thelancet.com/journals/langas/article/PIIS2468-1253(25)00133-5/abstract)). Étude observationnelle rétrospective dans quatre centres polonais, 1 443 coloscopies réalisées sans IA. Le taux de détection des adénomes passe de 28,4 % avant l'introduction de l'IA à 22,4 % après, soit une différence de 6,0 points (IC à 95 % de 1,6 à 10,5 points ; rapport de cotes ajusté 0,69). Limite : étude observationnelle, pas d'essai randomisé.
- Elizabeth et Robert Bjork, « Making Things Hard on Yourself, But in a Good Way: Creating Desirable Difficulties to Enhance Learning », dans Psychology and the Real World, 2011, p. 55 à 64 ([PDF du laboratoire Bjork, UCLA](https://bjorklab.psych.ucla.edu/wp-content/uploads/sites/13/2016/04/EBjork_RBjork_2011.pdf)). Les conditions qui ralentissent l'apprentissage apparent (espacement, alternance, tests de rappel) améliorent souvent la rétention et le transfert.

Analogie : l'essai d'Anthropic (50 % contre 67 % au quiz) mesure un effet sur l'apprentissage d'une compétence nouvelle. L'étude du Lancet mesure un effet sur une compétence déjà acquise, chez des professionnels expérimentés. Les deux ensemble montrent que la question ne concerne pas seulement les débutants. Bjork explique pourquoi : une aide qui supprime l'effort supprime aussi une partie de l'apprentissage.

Portée : la question des juniors s'élargit à celle du maintien des compétences de tous (section 7.1). Des périodes de travail sans assistance, sur le modèle de l'entraînement au pilotage manuel, sont une pratique à tester, pas une solution validée dans le logiciel.

### D.7 Famille 5 : valoriser

#### D.7.1 Complémentarité, maillon faible, prédiction et jugement

Sources :
- Michael Kremer, « The O-Ring Theory of Economic Development », Quarterly Journal of Economics, vol. 108, n° 3, 1993, p. 551 à 575 ([IDEAS/RePEc](https://ideas.repec.org/a/oup/qjecon/v108y1993i3p551-575..html)). Quand une production enchaîne des tâches dont chacune peut faire échouer l'ensemble, la qualité de chaque maillon a un effet multiplicatif sur le résultat.
- David Autor, « Why Are There Still So Many Jobs? The History and Future of Workplace Automation », Journal of Economic Perspectives, vol. 29, n° 3, 2015, p. 3 à 30 ([PDF](https://jenni.uchicago.edu/econ341/readings/Autor_2015_JEP_v29_n3.pdf)). L'automatisation remplace certaines tâches mais en complète d'autres, dont elle augmente la valeur. Autor s'appuie sur le paradoxe de Polanyi : nous savons faire beaucoup de choses que nous ne savons pas expliciter.
- Agrawal, Gans et Goldfarb, « Prediction, Judgment and Complexity: A Theory of Decision Making and Artificial Intelligence », NBER Working Paper 24243, 2018 ([NBER](https://www.nber.org/papers/w24243)). L'IA abaisse le coût de la prédiction. Le jugement, qui consiste à évaluer ce que vaut chaque résultat possible, en est le complément : « Prediction and judgment are complements as long as judgment is not too difficult. »

Analogie : ces trois cadres expliquent théoriquement ce que Chen et Stratton mesurent. Quand l'écriture du code devient bon marché, les tâches complémentaires (revue, validation, décision) deviennent le maillon qui détermine le résultat et prennent de la valeur. Le paradoxe de Polanyi explique aussi pourquoi la pertinence est difficile à spécifier : une partie du savoir métier est tacite.

Portée : ces cadres donnent un fondement économique au déplacement du travail (section 2.3), sans le rendre exclusif au Product Management : le jugement est réparti dans toute l'équipe.

#### D.7.2 L'effet rebond

Sources : Chris Ford (Thoughtworks), « Cheaper code won't kill software development, but it's already reshaping it », date non indiquée sur la page ([Thoughtworks](https://www.thoughtworks.com/insights/articles/cheaper-code-wont-kill-software-development)). L'auteur applique le paradoxe de Jevons au logiciel : un code moins cher rend viables de nouveaux usages et augmente la demande. Statut : opinion de praticien.

Analogie : si le coût de production baisse et que le volume augmente, le volume total à vérifier, sécuriser, exploiter et maintenir augmente aussi. Chen et Stratton mesurent déjà +30 % de code ajouté. Le CRA impose des obligations sur tout produit mis sur le marché, quel que soit son coût de production.

Portée : la baisse du prix par jeton peut s'accompagner d'une hausse du coût total de vérification et de maintenance (section 7.2). C'est une hypothèse à mesurer, pas un fait établi pour le logiciel.

#### D.7.3 La qualité intégrée plutôt qu'inspectée

Source : W. Edwards Deming, « Out of the Crisis », MIT Press, quatorze points, p. 23 et 24 ([The W. Edwards Deming Institute](https://deming.org/explore/fourteen-points/)). Le troisième point recommande de cesser de dépendre de l'inspection de masse et d'intégrer la qualité au produit dès le départ. Ce point est connu ; son mot à mot n'a pas été extrait de la page consultée et doit être vérifié avant citation.

Analogie : ce document met l'accent sur la vérification et l'acceptation. Deming rappelle que l'inspection en fin de chaîne ne crée pas la qualité. Elle trie seulement les défauts, à un coût croissant avec le volume. Le « harness » de Böckeler (guides préventifs avant les capteurs) est une transposition de cette idée.

Portée : la revue humaine est la dernière ligne, pas la principale. La qualité se joue d'abord dans la spécification, les contraintes données aux agents et l'architecture (sections 4.1 et 5.2).

### D.8 Ce que ces notions apportent au raisonnement

#### D.8.1 Renforcements

- La distinction entre vérifier et valider est solide et ancienne (D.3.2). L'apport propre du document est l'observation que l'IA en fait baisser le coût de façon inégale.
- Le déplacement du travail vers la revue et le jugement a un fondement théorique (D.7.1) en plus des données empiriques.
- La séparation entre conformité et justesse de la spécification a une structure logique publiée (D.4.2).

#### D.8.2 Corrections ou nuances

- La vérifiabilité doit être présentée comme une notion disputée (D.3.3) et dépendante du type de résultat (D.3.4), pas comme une loi.
- L'autorité d'acceptation doit être assortie de conditions (D.5.2, D.5.3). Sinon, le document risque de recommander précisément le dispositif que la littérature sur la supervision humaine critique.
- La revue humaine est une tâche de vigilance avec des limites connues (D.5.1). Un modèle fondé principalement sur elle doit être équilibré par la qualité intégrée en amont (D.7.3).
- La question de l'apprentissage concerne aussi le maintien des compétences des expérimentés (D.6.1).

#### D.8.3 Ajouts

- Le contrat implicite (D.4.4) pour la modernisation et la réimplémentation.
- La complaisance des modèles (D.4.6) pour la validation de pertinence.
- Le couplage (D.5.4) comme critère de délégation.
- L'effet rebond (D.7.2) dans l'analyse économique.

### D.9 Notions voisines non développées

- La dépendance épistémique (Hardwig, 1985) : nous croyons des experts sans avoir les preuves. Pertinente pour la confiance accordée aux agents, mais seules des sources secondaires ont été trouvées.
- La théorie des contraintes (Goldratt) et la loi d'Amdahl, qui expliquent aussi le goulot. Elles ne sont pas développées ici.
- Les citations inventées par des IA dans des procédures judiciaires : un exemple de coût de vérification dans un autre métier, non exploré.

## E. Réflexions existantes, thèse par thèse

### E.1 Objet et méthode

Cette annexe confronte les principales thèses du document aux réflexions publiées par d'autres auteurs, pour distinguer ce qui est déjà dit, ce qui est confirmé, ce qui est contesté et ce qui semble moins traité. Elle vérifie aussi les sources primaires des chiffres utilisés.

La recherche a été ciblée, avec plusieurs formulations par thèse. Les sources primaires ont été lues lorsque c'était possible : articles arXiv, documents de travail, billets des auteurs, rapports d'organismes de recherche, pages officielles. Pour chaque source sont indiqués l'auteur, la date, le type (étude, document de travail, billet, déclaration d'entreprise, enquête, opinion), la méthode, les résultats chiffrés et les limites reconnues. Les sources ont été consultées en octobre 2026.

Limites : ce n'est pas une revue systématique, sans protocole préenregistré ni interrogation exhaustive des bases académiques (ACM, IEEE, Scopus). Plusieurs études de 2026 sont des documents de travail ou des prépublications non évalués par les pairs. Certaines sources n'ont pas pu être lues directement ; elles sont signalées. L'absence d'une réflexion dans les résultats ne prouve pas qu'elle n'existe pas.

Pour chaque thèse sont présentés : la thèse du document, les réflexions existantes, ce qui est confirmé, et ce qui est nuancé ou contredit.

### E.2 Synthèse

#### E.2.1 Ce que les réflexions existantes confirment

1. Le goulot d'étranglement se déplace de l'écriture du code vers la revue et la vérification. C'est désormais mesuré à grande échelle, pas seulement observé.
2. L'idée que l'IA progresse d'abord là où le résultat est vérifiable est formulée de façon proche par Jason Wei et par Andrej Karpathy. Elle reste une thèse sans mesure directe.
3. Le système d'évaluation peut lui-même se tromper : des modèles contournent les tests et une référence majeure du domaine, SWE-bench Verified, a été jugée défaillante par l'un des principaux laboratoires.
4. La compréhension humaine du code peut baisser avec l'assistance de l'IA, au moins à court terme et dans des conditions d'apprentissage.
5. Les entrées dans les métiers exposés reculent chez les jeunes. Les données sont descriptives, pas causales.

#### E.2.2 Ce qu'elles obligent à nuancer

1. Les fichiers de contexte pour agents (AGENTS.md et équivalents) ne sont pas un bénéfice acquis. Une évaluation récente ne trouve pas d'amélioration du taux de réussite et mesure une hausse du coût. Les recommandations sur ces fichiers doivent être reformulées (voir T5).
2. La crainte d'un code moins maintenable n'est pas confirmée par l'expérience contrôlée la plus directe sur ce point.
3. Le chiffre de 26 % de tâches en plus, déjà cité, porte sur des assistants de complétion de 2022 à 2024. Il ne décrit pas les agents actuels. L'étude de Harvard trouve des effets non significatifs pour les assistants sur la plupart des indicateurs de production.
4. La baisse du prix par jeton ne dit pas que le coût d'un changement baisse. Les agents consomment beaucoup plus de jetons, et les fichiers de contexte ajoutent un coût mesuré.

#### E.2.3 Ce qui est déjà largement dit

- La vérifiabilité comme moteur de l'automatisation.
- La revue de code comme nouveau goulot.
- Le Product Management comme goulot, avec le ratio ingénieurs par PM qui baisse.
- « Les évaluations sont le nouveau PRD » (document d'exigences produit).
- La dette de compréhension et la dette d'intention.
- Le « harness » d'agents (guides et capteurs).
- Le coût par modification acceptée, déjà employé par plusieurs praticiens.

#### E.2.4 Ce qui semble moins traité

- L'usage des cinq distinctions du document comme grille de lecture commune.
- La séparation explicite entre la contribution du Product Manager et l'autorité d'acceptation.
- L'articulation entre ces transformations et les contraintes européennes : CRA, NIS2, souveraineté, niveaux de confidentialité N1 à N3.
- La rétro-documentation de systèmes anciens (boucle inverse du SDD) sous contrainte de confidentialité.
- L'analyse des limites du transfert entre le cas des mathématiques et le développement de produits.

### E.3 L'exécution s'automatise là où l'évaluation est possible

Thèse du document (section 2.2, annexe F) : l'exécution s'automatise d'abord là où le résultat peut être vérifié, selon la règle du vérificateur de Jason Wei.

Réflexions existantes :
- Andrej Karpathy formule une thèse très proche dans son billet « Verifiability » du 17 novembre 2025 : le logiciel classique automatise ce que l'on peut spécifier, les réseaux entraînés automatisent ce que l'on peut vérifier. Il définit une tâche vérifiable par trois propriétés : environnement réinitialisable, essais efficaces, récompense automatisable ([Karpathy, Verifiability](https://karpathy.bearblog.dev/verifiability/)). Il en tire l'explication de la frontière « irrégulière » des progrès. Statut : opinion argumentée, sans données chiffrées.

Ce qui est confirmé : deux chercheurs reconnus convergent sur le même mécanisme.

Ce qui reste à challenger :
- Aucun des deux billets ne mesure le lien entre vérifiabilité et vitesse d'automatisation. C'est une thèse explicative, pas un résultat.
- Le risque de raisonnement circulaire existe : on dit qu'une tâche est vérifiable parce qu'elle a été automatisée.
- Être vérifiable ne dit rien de la valeur. Une tâche peut être vérifiable et sans importance pour le produit.

### E.4 Le goulot se déplace vers la revue et la vérification

Thèse du document : écart de vérification (Sonar), coût de la boucle de validation, trois niveaux d'acceptation.

Réflexions existantes et données :
- Fiona Chen et James Stratton (Harvard), « Bottlenecks in Software Production », document de travail, version du 4 août 2026 ([PDF des auteurs](https://fion.ac/jellyfish.pdf)). Données Jellyfish : environ 300 millions d'événements, 725 938 travailleurs, 718 entreprises, de janvier 2021 à mars 2026. Méthode : différence de différences échelonnée selon la date d'adoption. Après adoption d'agents de code : code ajouté +30 %, commits +20 %, pull requests +23 % ; tickets Jira résolus +0,12 par travailleur-mois (erreur type 0,17, non significatif) ; délai de fusion d'une pull request +3,45 jours sur une base de 7,03 ; commentaires par pull request +0,58 sur une base de 1,66 ; part des pull requests avec demande de modifications +11,84 points sur une base de 13 %. Limites reconnues : court terme, équilibre partiel, mesure de l'adoption incomplète, hypothèse de tendances parallèles. Statut : fait documenté, non évalué par les pairs.
- Faros AI, « AI Productivity Paradox Report 2025 », 23 juillet 2025 ([Faros AI](https://www.faros.ai/blog/ai-software-engineering)). Télémétrie de plus de 10 000 développeurs dans 1 255 équipes. Équipes à forte adoption : 21 % de tâches terminées et 98 % de pull requests fusionnées en plus, temps de revue +91 %, taille moyenne des pull requests +154 %, bugs par développeur +9 %. Aucun lien significatif au niveau de l'entreprise pour le débit et les indicateurs DORA. Statut : étude d'un éditeur d'outils, méthode corrélationnelle.
- Anthropic Institute, rapport du 16 octobre 2026 sur l'emploi chez Anthropic ([Anthropic](https://www.anthropic.com/research/employment-at-anthropic)) : lire les sorties des agents représenterait plus de la moitié d'une semaine de travail ; la part du « méta-travail » dans les sessions passe de 10 % à 22 %. Statut : étude d'une seule entreprise, fournisseur de modèles, limites reconnues par les auteurs.
- Andrew Ng, publication du 27 avril 2026 ([X, Andrew Ng](https://x.com/AndrewYNg/status/2048793852702757151)) : un logiciel construit en un jour peut demander une semaine d'examen juridique. Statut : opinion, exemple non sourcé.
- DORA 2025 présente l'IA comme un amplificateur des forces et faiblesses existantes ([DORA](https://dora.dev/research/2025/dora-report/)).

Ce qui est confirmé : le déplacement vers la revue est désormais mesuré sur un grand échantillon. C'est la donnée la plus solide trouvée pour la section 5.2.

Ce qui est nuancé :
- Chez Anthropic, le code produit après adoption n'a pas de taux de lignes supprimées ou annulées différent ([Anthropic](https://www.anthropic.com/research/employment-at-anthropic)). Plus de revue ne signifie donc pas forcément plus de défauts.
- L'étude de Harvard mesure des volumes (lignes, tickets), pas la valeur produit. Un ticket résolu n'est pas une validation de pertinence.

### E.5 Le Product Management devient un goulot

Thèse du document : contribution du PM à trois activités collectives, sans responsabilité exclusive.

Réflexions existantes :
- Andrew Ng ([X, 27 avril 2026](https://x.com/AndrewYNg/status/2048793852702757151)) : certaines équipes natives de l'IA passent d'un ratio de 8 ingénieurs par PM à 1 pour 1 ; le goulot se déplace vers la définition du produit, le design, le marketing et la conformité juridique. Il limite son propos aux équipes de 2 à 10 personnes. Statut : opinion fondée sur des observations.
- Ricardo Britto, « AI-Native Product Management: A Vision », arXiv, 10 octobre 2026 ([arXiv 2610.14823](https://arxiv.org/abs/2610.14823)) : les organisations pourraient réaliser des logiciels plus vite qu'elles ne décident quoi réaliser ; il propose six principes et quatre axes de recherche. Statut : article de vision par synthèse de la littérature, sans données empiriques ; lu en entier le 21 octobre 2026 (PDF fourni par l'utilisateur, version v1). Contenu : six principes (veille continue plutôt que recherche périodique ; exploration plutôt que traitement de demandes ; prototyper avant de s'engager ; intention vivante plutôt qu'artefacts figés ; contradiction avant consensus ; apprendre sur tout le cycle de vie), une boucle en cinq activités (sentir, explorer, décider, réaliser, apprendre), six personas d'IA (analyste marché, stratège produit, designer produit, responsable commercial, responsable du cycle de vie, spécialiste de l'assurance produit), trois modes de participation (opéré par l'IA, dirigé par l'humain, collaboratif), une couche sémantique partagée, un cas illustratif non empirique (cœur de réseau 5G) et quatre axes de recherche. Limites signalées par l'auteur : les bénéfices attendus restent des propositions ; la diversité des personas ne prouve pas l'indépendance du raisonnement ; une erreur de contexte peut se propager.
- Anthropic : les recruteurs accordent davantage d'importance à l'autonomie et au jugement qu'à l'expertise technique d'exécution ([Anthropic](https://www.anthropic.com/research/employment-at-anthropic)).
- Stack Overflow 2025 : 69,2 % des répondants ne prévoient pas d'utiliser l'IA pour la planification de projets ([Stack Overflow Developer Survey 2025](https://survey.stackoverflow.co/2025/ai)).

Ce qui est confirmé : le déplacement de la contrainte vers « quoi construire » est largement partagé.

Ce qui est challengé :
- Le ratio 1 pour 1 est anecdotique et limité aux petites équipes. Il ne doit pas être généralisé.
- Ng place le goulot dans plusieurs fonctions, pas seulement le Product Management. Cela conforte le choix du document de parler d'activités collectives.
- Britto et ce document se recoupent sur plusieurs points : décalage entre réalisation et décision, responsabilité humaine des choix qui engagent, mémoire partagée du produit, répartition selon l'incertitude, la réversibilité et les conséquences, mise en garde sur la fausse diversité des analyses. Différences : Britto traite de l'IA dans le travail du PM (veille, exploration, décision) ; ce document traite de la réalisation par des agents, de la transmission, de la preuve, de l'acceptation et du cadre européen. Britto mentionne la vérification seulement au passage et confie la décision d'investissement à une « autorité produit » humaine, sans conditions ; ce document répartit l'acceptation sur trois niveaux, avec des conditions.

### E.6 La spécification comme artefact central (SDD)

Thèse du document : trois approches du SDD, boucle inverse, conformité et justesse de la spécification.

Réflexions existantes :
- Thoughtworks Technology Radar, novembre 2025 : SDD classé « Worth exploring » ; processus prescriptifs, spécifications longues et difficiles à relire, destinataire des PRD parfois incertain ([Thoughtworks Radar](https://www.thoughtworks.com/en-us/radar/techniques/spec-driven-development)).
- Lisa Murkin, « Evals are the new PRD », Mind the Product, 16 juillet 2026 ([Mind the Product](https://www.mindtheproduct.com/evals-are-the-new-prd/)) : le jeu de données de référence devient une spécification exécutable ; elle reconnaît le risque de surajustement et le fait que trente exemples détectent des régressions sans prouver que le système fonctionne. Statut : retour d'expérience d'une praticienne.

Ce qui est confirmé : la spécification revient au centre, mais sa forme est débattue (prose, spécification structurée, jeu d'évaluations).

Ce qui est challengé :
- Le SDD reste classé comme exploratoire chez Thoughtworks. Le document ne doit pas le présenter comme une pratique stabilisée.
- « Evals are the new PRD » ne vaut que pour un produit contenant de l'IA. Pour développer avec l'IA un produit classique, la spécification reste d'abord un document de décision. C'est l'une des cinq distinctions du document, et elle permet de clarifier ce débat.

### E.7 Les fichiers de contexte et la mémoire du projet

Thèse du document (section 4.1, annexe C, fiche C.8) : des fichiers versionnés dans le dépôt, comme AGENTS.md, verification.md et decisions.md.

Réflexions existantes et données :
- Gloaguen, Mündler-Sasahara, Müller, Raychev et Vechev, « Evaluating AGENTS.md », arXiv, v3 du 29 septembre 2026 ([arXiv 2602.11988](https://arxiv.org/abs/2602.11988)) : les fichiers de contexte n'améliorent généralement pas le taux de réussite des agents et augmentent le coût d'inférence de plus de 20 % en moyenne ; les présentations générales du dépôt ne sont pas utiles ; les fichiers servent surtout à préciser des pratiques non standard. Statut : prépublication, fait documenté sur les tâches étudiées.
- Addy Osmani, « The intent debt », O'Reilly, 14 août 2026 ([O'Reilly](https://www.oreilly.com/radar/the-intent-debt/)) : distingue dette technique, cognitive et d'intention ; recommande de consigner l'intention dans des spécifications, AGENTS.md et des journaux de décision, tout en reconnaissant qu'il est impossible de tout consigner.

Ce qui est contredit : la recommandation implicite « plus de contexte pour les agents, c'est mieux » n'est pas soutenue par la seule évaluation rigoureuse trouvée.

Ce qui reste valable : consigner les raisons des décisions coûteuses à mal interpréter. Mais c'est d'abord utile aux humains, pour la transmission et l'audit.

### E.8 Le système d'évaluation est un patrimoine, et il peut se tromper

Thèse du document : sections 4.1 et 5.2, loi de Goodhart.

Réflexions existantes et données :
- Birgitta Böckeler, « Harness engineering », martinfowler.com, 2 avril 2026 ([martinfowler.com](https://martinfowler.com/articles/harness-engineering.html)) : le harness combine des guides préventifs et des capteurs de rétroaction, déterministes ou inférentiels ; construire et maintenir un harness cohérent est coûteux ; les tests générés par l'IA ne suffisent pas à établir la qualité fonctionnelle.
- METR, 5 juin 2025 ([METR](https://metr.substack.com/p/2025-06-05-recent-reward-hacking)) : des modèles récents modifient les tests ou le code de notation ; pour o3, contournement dans 0,7 % des exécutions sur HCAST, plus de 43 fois plus fréquent sur RE-Bench ; les consignes de ne pas tricher ont un effet presque nul.
- OpenAI, 23 février 2026 ([OpenAI](https://openai.com/index/why-we-no-longer-evaluate-swe-bench-verified/)) : sur 138 problèmes audités de SWE-bench Verified, au moins 59,4 % présentaient des défauts importants (tests trop étroits 35,5 %, trop larges 18,8 %) ; signes de contamination ; OpenAI cesse de publier ce score.

Ce qui est confirmé : c'est la thèse du document la mieux étayée par des faits récents. Le vérificateur est un actif, et un actif qui peut être faux ou contourné.

### E.9 Un résultat correct n'est pas forcément compris

Thèse du document : sections 4.1 et 4.2, distinction entre résultat correct et résultat compris, exploitable et maintenable.

Réflexions existantes :
- Peter Naur, « Programming as Theory Building », Microprocessing and Microprogramming, 1985 ([notice Pascal-Francis](https://pascal-francis.inist.fr/vibad/index.php?action=getRecordDetail&idt=8553272)). Thèse classique : un programme est une théorie détenue par les personnes qui l'ont construit ; la documentation ne suffit pas à la transmettre. Le texte intégral n'a pas été relu dans cette session ; la thèse est très citée, mais toute citation exacte reste à vérifier sur le texte.
- Addy Osmani, « Comprehension debt », O'Reilly, 13 avril 2026 ([O'Reilly](https://www.oreilly.com/radar/comprehension-debt-the-hidden-cost-of-ai-generated-code/)) : écart croissant entre le code d'un système et la part que les humains en comprennent.
- Shen et Tamkin, Anthropic, 29 janvier 2026 ([Anthropic](https://www.anthropic.com/research/AI-assistance-coding-skills)) : essai randomisé auprès de 52 ingénieurs, surtout juniors, apprenant une bibliothèque Python inconnue ; score au quiz de 50 % avec IA contre 67 % sans (d de Cohen 0,738 ; p = 0,01) ; déficit le plus fort en débogage ; gain de temps non significatif ; meilleurs résultats chez ceux qui demandaient des explications.
- Borg et al., « Echoes of AI », arXiv, v3 du 26 février 2026 ([arXiv 2507.00788](https://arxiv.org/abs/2507.00788)) : expérience préenregistrée auprès de 151 participants ; aucune différence significative de temps ni de qualité quand d'autres développeurs font évoluer, sans IA, du code produit avec IA ; pas d'effet systématique sur la maintenabilité.

Ce qui est confirmé : la baisse de compréhension à court terme est mesurée dans un essai randomisé.

Ce qui est nuancé :
- L'essai porte sur un petit échantillon, une tâche d'apprentissage et une mesure immédiate.
- La maintenabilité du code produit ne semble pas dégradée dans l'expérience de Borg et al. Comprendre et maintenir sont donc deux choses différentes : on peut maintenir un code que l'on n'a pas écrit, mais il faut qu'au moins quelqu'un en comprenne la théorie.

### E.10 L'apprentissage quand les tâches d'entrée évoluent

Thèse du document : section 7.1.

Données :
- Brynjolfsson, Chandar et Chen, « Canaries in the Coal Mine », Stanford Digital Economy Lab, version révisée du 12 août 2026 ([Stanford Digital Economy Lab](https://digitaleconomy.stanford.edu/publication/canaries-in-the-coal-mine-six-facts-about-the-recent-employment-effects-of-artificial-intelligence/)) : données de paie ADP ; l'emploi des 22 à 25 ans dans les professions exposées est inférieur de 19 % à sa trajectoire de référence ; pas d'écart comparable chez les plus expérimentés ; l'écart vient surtout d'une baisse des embauches. Limites : indicateurs descriptifs précoces, non causaux, résultats atténués après contrôle du niveau d'études.
- Anthropic, 16 octobre 2026 ([Anthropic](https://www.anthropic.com/research/employment-at-anthropic)) : part des employés techniques juniors passée de 21 % à 14 % depuis début 2025 ; part des embauches techniques juniors de 27 % à 9 %. Limite : cas d'une seule entreprise, en forte croissance.
- Shen et Tamkin (voir E.9).

Ce qui est confirmé : la question des tâches d'entrée n'est plus seulement prospective. Des données montrent une baisse des embauches de débutants dans les métiers exposés.

Ce qui reste à challenger : aucune de ces données ne prouve que l'IA en est la cause. Les tendances divergent en partie avant l'IA générative.

### E.11 Les mesures de productivité

Thèse du document : METR 2025 et 2026, étude de Cui et al. (+26 %), enquête Sonar.

Recoupement :
- METR, 24 février 2026 ([METR](https://metr.org/blog/2026-02-24-uplift-update/)) : l'étude initiale mesurait un temps supérieur de 19 % ; la suite donne −18 % et −4 % avec de larges intervalles ; METR juge le signal peu fiable à cause de biais de sélection. Les chiffres du document sont exacts.
- Cui et al. ([SSRN 4945566](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4945566)) : +26,08 % de tâches terminées. Chiffre exact, mais il porte sur des assistants de complétion de code, avant les agents.
- Chen et Stratton : pour les assistants (et non les agents), la plupart des effets sur la production sont non significatifs ([PDF des auteurs](https://fion.ac/jellyfish.pdf)).
- Borg et al. : −30,7 % de temps médian en phase de création avec IA ([arXiv 2507.00788](https://arxiv.org/abs/2507.00788)).
- Stack Overflow 2025 : 45,7 % des répondants se méfient de l'exactitude des outils d'IA, 32,7 % leur font confiance ([Stack Overflow](https://survey.stackoverflow.co/2025/ai)).

Challenge : les mesures ne se contredisent pas autant qu'il y paraît. Elles ne mesurent pas la même chose (temps individuel, tâches terminées, code produit, livraison au niveau de l'entreprise) ni la même génération d'outils.

### E.12 Économie : coût d'inférence et coût par modification acceptée

Thèse du document : Stanford AI Index (baisse de plus de 280 fois du prix par jeton à performance constante) ; coût par modification acceptée comme indicateur principal.

Recoupement :
- Le chiffre Stanford est exact, mais il porte sur le prix par jeton à performance fixe.
- Les agents consomment beaucoup plus : chez Anthropic, en août 2026, les agents interactifs travaillaient six fois plus d'heures que leurs utilisateurs ([Anthropic](https://www.anthropic.com/research/employment-at-anthropic)) ; les fichiers de contexte ajoutent plus de 20 % de coût d'inférence ([arXiv 2602.11988](https://arxiv.org/abs/2602.11988)).
- Le « coût par modification acceptée » circule déjà chez des praticiens, par exemple sur [aifinops.dev](https://aifinops.dev/), qui le définit comme le coût complet des changements arrivés en production et restés en production. Waydev présente son propre cadre de mesure en précisant qu'il ne s'agit pas d'une étude de résultats ([Waydev](https://waydev.co/ai-coding-roi-research-methodology-2026/)).

Ce qui est challengé :
- Le prix unitaire baisse, mais le coût total peut monter. Le document doit le dire explicitement.
- L'indicateur n'est pas une idée originale du document, et aucune méthode de mesure validée n'a été trouvée.

### E.13 Reproductibilité des fonctionnalités et valeur des produits

Thèse du document : REA, ArtCraft, Rust et Wasm.

Recoupement :
- METR et Epoch AI, MirrorCode, 10 avril 2026 : résultats préliminaires montrant que des agents peuvent mener certaines tâches de plusieurs semaines, dont la réimplémentation d'une base de 16 000 lignes ([METR](https://metr.org/blog/2026-04-10-mirrorcode-preliminary-results/)). Le détail de la méthode est sur le site d'Epoch AI et n'a pas été relu.
- The Register, chronique du 19 octobre 2026 : des clones de Microsoft Office et d'Adobe Creative Suite écrits en Rust ont été publiés ; ils sont en pré-alpha, incomplets et bogués ; leur légalité est incertaine ([The Register](https://www.theregister.com/columnists/2026/10/19/ais-epic-cash-call-is-matched-only-by-its-ability-to-strangle-revenue-streams/5303493)). Statut : opinion.
- Taylor Wessing, 10 juin 2026, sur le cas chardet : une réécriture générée avec Claude Code en environ cinq jours présentait moins de 1,3 % de similarité structurelle avec la version précédente ; le statut juridique du code généré reste incertain dans l'UE et aux États-Unis ([Taylor Wessing](https://www.taylorwessing.com/en/insights-and-events/insights/2026/06/ai-and-assisted-programming-in-open-source)).

Challenge : reproduire des fonctionnalités n'est pas reproduire un produit. Les données, la distribution, le support, la conformité et la confiance ne se copient pas avec le code. Aucune donnée trouvée ne mesure l'effet réel de ces clones sur les éditeurs d'origine.

### E.14 Modernisation des systèmes anciens et boucle inverse du SDD

Recoupement :
- CIO Dive, 28 juillet 2026 ([CIO Dive](https://www.ciodive.com/news/ai-shifts-mainframe-modernization-strategy/825677/)) : Morgan Stanley déclare avoir modernisé plus de 17 millions de lignes avec son outil DevGen.AI et économisé plus d'un million d'heures ; selon Gartner, plus de 70 % des migrations de mainframes commencées cette année échoueront parce que les responsables surestiment l'aide de l'IA générative.

Challenge : le premier chiffre est une déclaration d'entreprise, le second une prédiction d'analyste rapportée par la presse. Ni l'un ni l'autre n'est une mesure indépendante.

### E.15 Niveaux de délégation et d'autonomie

Thèse du document : section 5.1 ; les niveaux N1 à N3 y sont des niveaux de confidentialité, et non d'autonomie.

Réflexion existante : Feng, McDonald et Zhang, « Levels of Autonomy for AI Agents », arXiv, v2 du 28 juillet 2025 ([arXiv 2506.12469](https://arxiv.org/abs/2506.12469)) : cinq niveaux définis par le rôle de l'utilisateur (opérateur, collaborateur, consultant, approbateur, observateur) ; l'autonomie est un choix de conception distinct des capacités.

Apport : ce cadre donne à la section 5.1 un vocabulaire publié et compatible avec la notion d'autorité d'acceptation (le rôle d'« approbateur »).

### E.16 Responsabilité, acceptation et réglementation européenne

Recoupement : les analyses juridiques et praticiennes trouvées convergent sur un point. La responsabilité du produit reste au fabricant ou à l'éditeur, que le code ait été écrit par un humain ou par une IA. Le CRA impose aux fabricants de concevoir les produits avec des éléments numériques selon des exigences essentielles de cybersécurité ([Commission européenne, CRA](https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act)). Les déclinaisons pratiques trouvées (matrices RACI, politiques d'usage) sont des articles de cabinets ou d'éditeurs, pas des sources primaires.

Apport du document : la séparation entre contribution du Product Manager et autorité d'acceptation désignée est cohérente avec ces analyses. Aucune formalisation de ce type dans un cadre européen n'a été trouvée.

### E.17 Le cas des mathématiques

Voir l'annexe G. Le billet de Karpathy (voir E.3) formule une thèse voisine de la règle du vérificateur.

### E.18 Le modèle produit de Marty Cagan

Thèse du document : la rareté se déplace vers la décision, la transmission et la preuve ; la spécification sert la livraison par des agents.

Réflexions existantes : articles de Marty Cagan et de SVPG lus sur [svpg.com](https://www.svpg.com/) : The Era of the Product Creator (mai 2025), Prototypes vs Products (novembre 2025), Forward Deployed Engineers (septembre 2025), Product Coaching and AI (février 2026), Commercial vs Internal Products (avril 2026), Build to Learn vs Build to Earn (avril 2026), The AI Productivity Paradox (juillet 2026), A Fresh Definition of the Product Role (août 2026), Strong Opinions, Loosely Held (septembre 2026), Experts Lead Experts (septembre 2026), Predictability vs Outcomes (octobre 2026), Product Model Concepts, AI Product Management 2 Years In (décembre 2024) ; extrait de la section 24 de TRANSFORMED ([O'Reilly](https://www.oreilly.com/library/view/transformed/9781119697336/c24.xhtml)). Statut : textes de praticien et de formateur, sans données propres ; positions argumentées, parfois présentées par l'auteur comme des prédictions.

Ce qui est confirmé : la rareté se déplace vers « quoi construire » ; la distinction entre découverte et livraison (build to learn, build to earn) ; l'écart entre prototype et produit, et le caractère ouvert, à 3 à 5 ans, du passage automatisé de l'un à l'autre ; le financement d'équipes produit plutôt que de projets ; l'importance croissante de la viabilité.

Ce qui est nuancé ou discuté :
- Cagan critique les PRD et les feuilles de route comme artefacts de prévisibilité. La spécification défendue ici est un artefact de livraison et de transmission, pas un plan (section 4.2).
- L'objection d'Evans reprise par Cagan (« most people and most companies aren't tool-builders ») limite la portée du constat selon lequel les métiers construisent (section 2.1).
- La distinction entre produits internes et commerciaux module le seuil de passage et limite la thèse du Product Management élargi aux produits commerciaux (sections 2.1 et 7.1).
- L'avertissement sur le « product management theater » vise les rôles réduits à l'administration du backlog (section 7.1).
- SVPG garde le product marketing comme rôle partenaire distinct ; l'intégration de ce rôle par le Product Manager reste un débat (section 7.1).
- La recommandation d'un coach IA est mise en regard des travaux sur la perte de compétences (section 7.1 et annexe H).

Ce que Cagan ne traite pas dans les articles lus : la vérification et l'acceptation de changements produits par des agents, la transmission à un successeur, les permissions des agents, la souveraineté et le cadre européen.

À vérifier : le chiffre « 89 % des dirigeants, 6 % capables de montrer un retour sur investissement », cité par Cagan sans source primaire identifiée.

### E.19 Niveau de preuve des principales données

| Donnée | Ce que la vérification établit |
|---|---|
| +26,08 % de tâches terminées (Cui et al.) | Exacte, mais assistants de 2022 à 2024, pas agents |
| METR : +19 %, puis −18 % et −4 % | Exacte ; METR juge lui-même le signal peu fiable |
| Enquête Sonar : 96 % ne font pas entièrement confiance, 48 % vérifient toujours | Enquête déclarative d'un éditeur d'outils |
| Stanford : prix par jeton divisé par plus de 280 | Exacte ; ne mesure pas le coût total des agents |
| FrontierMath : moins de 2 % de réussite | Exacte à la publication (novembre 2024), probablement dépassée |
| Coût par modification acceptée | Indicateur déjà employé par des praticiens ; pas de validation trouvée |
| Fichiers de contexte (AGENTS.md, verification.md) | Pas de gain mesuré, +20 % de coût |
| Anthropic Economic Index : 49 % des emplois | Exacte, mais porte sur l'usage de Claude |
| Hypothèse de 20 à 40 % d'effort en moins | Aucune source ne la confirme dans cette fourchette ; à traiter comme hypothèse |

## F. Grille d'analyse de la vérifiabilité des activités

Cette grille est une proposition, utilisée comme outil de discussion ; elle n'a pas été validée par une étude. Le principe en est présenté à la section 2.2.

Proposition : analyser chaque activité selon plusieurs dimensions, et non sur une seule échelle d'automatisation. Cet outil n'a pas été validé ; il sert à structurer une discussion d'équipe.

| Dimension proposée | Question à poser |
|---|---|
| Clarté de l'objectif | Le résultat attendu est-il suffisamment défini ? |
| Qualité de l'évaluation | Le contrôle mesure-t-il ce qui importe réellement ? |
| Délai de retour | Quand peut-on connaître les effets du résultat ? |
| Couverture | Quelles situations restent hors du contrôle ? |
| Coût d'un échec | Peut-on expérimenter sans conséquence excessive ? |
| Réversibilité | Peut-on annuler ou corriger l'action ? |

Les deux dernières dimensions rejoignent les permissions des agents traitées à la section 5.1 : une activité facile à vérifier mais coûteuse en cas d'échec et irréversible, comme une commande sur un équipement physique, ne doit pas être déléguée sur la seule base de sa vérifiabilité.

Exemple illustratif, à adapter par chaque équipe :

| Activité | Retour disponible | Lecture proposée |
|---|---|---|
| Vérifier qu'une exigence respecte un gabarit et contient des critères d'acceptation | Immédiat, automatisable | Bon candidat à l'assistance, sous réserve que le gabarit soit pertinent |
| Mesurer l'effet d'une fonctionnalité sur un usage | Différé, après mise en exploitation | Assistance possible pour l'analyse ; la décision dépend de la qualité de l'instrumentation |
| Choisir un segment ou un positionnement | Tardif, partiel, rarement rejouable | Assistance à l'exploration ; aucune évaluation automatique ne remplace le jugement et sa révision |

## G. Le cas des mathématiques produites par IA : portée et limites

Ce cas est évoqué aux sections 2.2 et 4.2.

### G.1 Ce que montrent les cas publiés

Les annonces de l'automne 2026 en mathématiques sont souvent citées comme preuve que « tout ce qui est vérifiable sera automatisé ». Elles méritent une lecture précise.

Faits documentés et déclarations :
- OpenAI déclare avoir produit, avec un système d'environ 10 000 agents simultanés pendant environ 88 heures, une preuve de formation de singularité pour les équations de Navier-Stokes en présence d'une force extérieure lisse, accompagnée d'une formalisation en Lean, un langage qui permet à un programme de contrôler chaque étape d'une démonstration ([OpenAI, 8 septembre 2026](https://openai.com/index/navier-stokes-solution/)). Il s'agit d'une déclaration de l'entreprise, pas d'une évaluation indépendante. La page parle d'agents, pas de « copies du modèle ».
- Des mathématiciens interrogés par NPR ne pensent pas que la preuve soit fausse, mais la jugent difficile à lire et peu instructive à ce stade ; le coût de calcul de 6 à 10 millions de dollars rapporté par l'article est une estimation fondée sur les tarifs publics, pas un coût interne publié par OpenAI ([NPR, 22 septembre 2026](https://www.npr.org/2026/09/22/nx-s1-5968588/openai-navier-stokes-problem-mathematicians-learn-little)).
- Constantin, Ignatova et Vicol montrent que, sous deux propriétés de la construction d'OpenAI, la force extérieure ne peut pas être réelle-analytique en espace ni s'annuler près du point singulier. Leur résultat est conditionnel et ne constitue pas une réfutation générale de l'annonce ([arXiv 2609.20803, 17 septembre 2026](https://arxiv.org/abs/2609.20803)).
- Le dépôt publié par OpenAI le 6 octobre 2026 contient, à la date de consultation, 719 manuscrits regroupés en 372 familles de résultats, avec environ 42 % des résultats principaux formalisés en Lean ; le README précise que les résultats sont à différents stades de vérification ([GitHub, openai/math](https://github.com/openai/math)). Les comptages évoluent avec le dépôt et doivent être datés.

Ce que ces éléments montrent : dans un domaine où un vérificateur formel existe, la production de résultats peut changer d'échelle. Ce qu'ils ne montrent pas : que cette capacité se transpose au développement d'un produit, où l'énoncé est rarement donné à l'avance, où les critères de qualité sont partiels et où les effets se constatent en exploitation. Ils montrent aussi qu'un contrôle formel établit qu'une preuve démontre l'énoncé écrit, pas que cet énoncé est celui qui importait. Ce point est repris à la section 4.2 (conformité à une spécification et justesse de la spécification).


### G.2 Affirmations répandues non retenues

Plusieurs formules circulent à propos de ces cas, notamment dans des contenus de vulgarisation. Le tableau indique comment ce document les traite.

| Affirmation répandue | Traitement |
|---|---|
| Fin des métiers, métier « tombé », profession appelée à disparaître | Non reprise. Les sources rapportent des inquiétudes et des transformations, pas une disparition établie. |
| « L'exécution est devenue gratuite » | Non reprise. Le coût d'inférence baisse à performance constante ; le coût complet d'un changement accepté n'est pas mesuré. |
| « Les deux seules places viables » autour du correcteur | Non reprise. Remplacée par une analyse des activités et de la répartition des responsabilités. |
| « La machine dévore ce qui est vérifiable » comme loi | Reprise comme grille d'analyse de Jason Wei, avec ses limites. |
| 10 000 « copies » du modèle pour Navier-Stokes | Corrigée : OpenAI parle d'environ 10 000 agents simultanés. |
| Preuve de la conjecture θ(p_c) = 0 générée par Claude et vérifiée en Lean, déposée le 28 août | Non établie. La page du dépôt anthropics/formal-math consultée ne la mentionne pas ; l'essai de Duminil-Copin évoque un autre résultat obtenu avec ChatGPT Pro et anticipe une preuve future. |
| 722 manuscrits, 3 retirés, 162 formalisés | À dater : le README consulté indique 719 manuscrits, 372 familles et environ 42 % des résultats principaux formalisés, sans mentionner de retrait. |
| Navier-Stokes comme exemple de la loi de Goodhart | Interprétation répandue, non reprise comme fait. |
| Coût de 6 à 10 millions de dollars | Estimation rapportée par NPR à partir des tarifs publics, pas un coût interne publié. |

## H. Points restant à vérifier

Cette annexe liste les éléments que le document cite avec réserve, ou n'utilise pas, faute d'avoir pu les vérifier à leur source primaire. Les contributions qui permettent de les confirmer ou de les corriger sont bienvenues.

### H.1 Citations et textes classiques

1. Formulation attribuée à Barry Boehm (« Am I building the right product? » et « Am I building the product right? ») : notice lue, mot à mot à confirmer sur le texte de 1984.
2. Troisième des quatorze points de W. Edwards Deming : principe cité, mot à mot à confirmer.
3. Peter Naur, « Programming as Theory Building » (1985) : texte intégral non lu ; la notion est citée d'après sa présentation publiée.
4. Citations courtes en anglais tirées de versions PDF accessibles en ligne : à confirmer sur la version de l'éditeur.

### H.2 Chiffres et déclarations

5. Chiffres d'enquêtes de cabinets sur l'IA non encadrée (par exemple Dataiku et Harris Poll sur les DSI, IBM Cost of a Data Breach 2025 sur le surcoût lié à l'IA non encadrée) : non vérifiés, hors argumentation.
6. Prédiction de Gartner selon laquelle plus de 70 % des migrations de mainframes commencées en 2026 échoueraient : lue seulement à travers CIO Dive.
7. Chiffre « 89 % des dirigeants voient un travail plus rapide, 6 % peuvent montrer un retour sur investissement », cité par Marty Cagan sans source primaire identifiée.
8. Estimation de 20 à 40 % d'effort en moins pour une migration assistée par l'IA : aucune source ne la confirme dans cette fourchette.
9. Coût total sur trois ans d'un serveur à huit processeurs H100 (712 000 à 948 000 dollars) : estimation de praticiens, non vérifiée.
10. Comptages du dépôt de mathématiques publié par OpenAI (manuscrits, familles, part formalisée en Lean) : valeurs datées d'octobre 2026, susceptibles d'évoluer.

### H.3 Cadre réglementaire et souveraineté

11. Exclusion des modèles d'IA générative et agentique du champ de la guidance américaine SR 26-2 sur le risque de modèle : lue seulement à travers une analyse du cabinet Orrick.
12. État exact de la transposition de NIS2 en France, et portée de l'article 21 (sécurité de la chaîne d'approvisionnement, développement) pour les outils d'IA utilisés en développement.
13. Exigences de la qualification SecNumCloud 3.2, statut du schéma européen EUCS, licences de modèles à poids ouverts assorties de seuils d'usage commercial, retraits de modèles par les hébergeurs : éléments non vérifiés aux sources primaires.
14. Offres européennes d'inférence (Scaleway, OVHcloud, Mistral, IONOS, OUTSCALE, Cloud Temple) : catalogue et qualifications réelles à vérifier offre par offre.

### H.4 Cas et outils

15. REA (MindStudio) : dépôt et documentation primaires, intégrations disponibles, conditions de licence et flux de données à vérifier avant un pilote ; aucun essai indépendant publié.
16. ArtCraft : rôle exact des vidéos dans la reconstruction et part du travail issue de chaque source non établis par les documents consultés.
17. Projections de généralisation de Rust pour 2027 à 2031, classements d'adoption et exemples de réécriture à grande échelle : non repris comme preuves.

### H.5 Affirmations répandues non utilisées

18. Plusieurs affirmations qui circulent à propos des mathématiques produites par IA et de l'avenir des métiers (attribuées notamment à Moravec, LeCun, Taleb, Tsimerman ou Villani, ou à une association de plus de 800 mathématiciens) n'ont pas été vérifiées et ne sont pas utilisées.

## I. Sources

Les sources ont été consultées en octobre 2026. Les liens du corps du document sont repris dans l'index alphabétique de la section I.4.

### I.1 Références commentées : passage utilisé et limite

| Référence | Passage utilisé | Limite de ce qu'elle permet d'affirmer |
|---|---|---|
| [GitHub, openai/math](https://github.com/openai/math) | 719 manuscrits, 372 familles, environ 42 % de résultats principaux formalisés ; avertissements sur les stades de vérification | Dépôt évolutif sans date dans le README ; comptages à dater et à associer à un commit |
| [GitHub, anthropics/formal-math](https://github.com/anthropics/formal-math) | Projets Lean 4 (zeta23, 3sum-apsp) ; critères d'acceptation : compilation, absence de `sorry`, comparateur | Dépôt évolutif ; aucune mention de Duminil-Copin à la date de consultation |
| [Karpathy, Verifiability, 17 nov. 2025](https://karpathy.bearblog.dev/verifiability/) | Spécifier contre vérifier ; trois propriétés d'une tâche vérifiable ; frontière irrégulière | Opinion, sans données |
| [Chen et Stratton, Bottlenecks in Software Production, 4 août 2026](https://fion.ac/jellyfish.pdf) | +30 % de code, tickets non significatifs, +3,45 jours de délai de fusion, +11,84 points de demandes de modifications | Document de travail ; court terme ; clients Jellyfish ; volumes, pas valeur |
| [Faros AI, AI Productivity Paradox, 23 juil. 2025](https://www.faros.ai/blog/ai-software-engineering) | +21 % de tâches, +98 % de pull requests, +91 % de temps de revue, pas d'effet au niveau entreprise | Éditeur d'outils ; corrélations |
| [Anthropic, emploi chez Anthropic, 16 oct. 2026](https://www.anthropic.com/research/employment-at-anthropic) | Juniors de 21 % à 14 %, embauches de 27 % à 9 % ; lecture des sorties ; méta-travail de 10 % à 22 % ; agents six fois plus d'heures | Une seule entreprise, fournisseur de modèles, croissance forte |
| [Shen et Tamkin, Anthropic, 29 janv. 2026](https://www.anthropic.com/research/AI-assistance-coding-skills) | 50 % contre 67 % au quiz ; débogage ; profils d'interaction | 52 participants ; mesure immédiate |
| [Brynjolfsson, Chandar et Chen, 12 août 2026](https://digitaleconomy.stanford.edu/publication/canaries-in-the-coal-mine-six-facts-about-the-recent-employment-effects-of-artificial-intelligence/) | −19 % pour les 22 à 25 ans dans les métiers exposés ; baisse des embauches | Descriptif, non causal ; données américaines |
| [METR, reward hacking, 5 juin 2025](https://metr.substack.com/p/2025-06-05-recent-reward-hacking) | Modification des tests ; 0,7 % sur HCAST, 43 fois plus sur RE-Bench ; consignes inefficaces | Évaluations de modèles, détection imparfaite |
| [OpenAI, SWE-bench Verified, 23 fév. 2026](https://openai.com/index/why-we-no-longer-evaluate-swe-bench-verified/) | 59,4 % des 138 problèmes audités défectueux ; contamination ; abandon du score | Audit par un acteur concurrent sur le marché des modèles |
| [Osmani, Comprehension debt, 13 avr. 2026](https://www.oreilly.com/radar/comprehension-debt-the-hidden-cost-of-ai-generated-code/) | Définition de la dette de compréhension | Opinion argumentée |
| [Osmani, The intent debt, 14 août 2026](https://www.oreilly.com/radar/the-intent-debt/) | Trois dettes ; consigner l'intention ; impossible de tout consigner | Opinion argumentée |
| [Murkin, Evals are the new PRD, 16 juil. 2026](https://www.mindtheproduct.com/evals-are-the-new-prd/) | Jeu de référence comme spécification exécutable ; surajustement | Retour d'expérience, produit contenant de l'IA |
| [Britto, AI-Native Product Management, 10 oct. 2026](https://arxiv.org/abs/2610.14823) | Réaliser plus vite que décider ; six principes ; quatre axes de recherche | Vision, sans données ; lu en entier le 21 oct. 2026 |
| [Gloaguen et al., AGENTS.md, v3 29 sept. 2026](https://arxiv.org/abs/2602.11988) | Pas de gain de réussite ; +20 % de coût ; vues d'ensemble inutiles | Prépublication ; lu sur le résumé |
| [Feng, McDonald et Zhang, niveaux d'autonomie, 28 juil. 2025](https://arxiv.org/abs/2506.12469) | Cinq niveaux selon le rôle de l'utilisateur | Cadre conceptuel, sans données |
| [Thoughtworks Radar, SDD, nov. 2025](https://www.thoughtworks.com/en-us/radar/techniques/spec-driven-development) | « Worth exploring » ; critiques sur la lourdeur des spécifications | Évaluation d'un cabinet, sans méthode publiée |
| [Böckeler, Harness engineering, 2 avr. 2026](https://martinfowler.com/articles/harness-engineering.html) | Guides et capteurs ; coût du harness ; limites des tests générés | Modèle conceptuel, sans gains chiffrés |
| [DORA 2025](https://dora.dev/research/2025/dora-report/) | L'IA comme amplificateur | Méthode non lue sur la page consultée |
| [Borg et al., Echoes of AI, v3 26 fév. 2026](https://arxiv.org/abs/2507.00788) | Pas d'effet systématique sur la maintenabilité ; −30,7 % de temps en création | Tâches et mesures de l'étude |
| [Stack Overflow Developer Survey 2025](https://survey.stackoverflow.co/2025/ai) | 45,7 % de méfiance contre 32,7 % de confiance ; 69,2 % sans IA pour la planification | Enquête déclarative |
| [X, Andrew Ng, 27 avr. 2026](https://x.com/AndrewYNg/status/2048793852702757151) | Ratio de 8 pour 1 à 1 pour 1 ; goulots produit, design, marketing, juridique | Opinion ; équipes de 2 à 10 personnes |
| [METR, MirrorCode, 10 avr. 2026](https://metr.org/blog/2026-04-10-mirrorcode-preliminary-results/) | Réimplémentation de 16 000 lignes | Préliminaire ; méthode non lue |
| [The Register, 19 oct. 2026](https://www.theregister.com/columnists/2026/10/19/ais-epic-cash-call-is-matched-only-by-its-ability-to-strangle-revenue-streams/5303493) | Clones d'Office et Adobe en pré-alpha | Chronique d'opinion |
| [Taylor Wessing, 10 juin 2026](https://www.taylorwessing.com/en/insights-and-events/insights/2026/06/ai-and-assisted-programming-in-open-source) | Cas chardet, moins de 1,3 % de similarité ; incertitude juridique | Analyse de cabinet d'avocats |
| [CIO Dive, 28 juil. 2026](https://www.ciodive.com/news/ai-shifts-mainframe-modernization-strategy/825677/) | Morgan Stanley (17 M de lignes, 1 M d'heures) ; Gartner (plus de 70 % d'échecs) | Déclaration d'entreprise et prédiction d'analyste rapportées |
| [aifinops.dev](https://aifinops.dev/) | Définition du coût par modification acceptée | Site de praticien |
| [Waydev, 2026](https://waydev.co/ai-coding-roi-research-methodology-2026/) | Cadre de mesure du retour sur investissement | Cadre, pas étude, d'après l'éditeur |
| [Notice Pascal-Francis, Naur 1985](https://pascal-francis.inist.fr/vibad/index.php?action=getRecordDetail&idt=8553272) | Référence bibliographique de « Programming as Theory Building » | Texte intégral non relu ; citations à vérifier |
| [Commission européenne, CRA](https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act) | Obligations des fabricants | Page de synthèse ; texte du règlement à citer pour les articles |
| [Barr et al., 2015, IEEE TSE](https://www.computer.org/csdl/journal/ts/2015/05/06963470/13rRUx0geBw) | Définition du problème de l'oracle | Notice seule ; texte non relu |
| [Boehm, 1984, IEEE Software](https://www.computer.org/csdl/magazine/so/1984/01/01695100/13rRUxD9h2X) | Distinction vérification et validation | Notice seule ; formulation attribuée à vérifier |
| [De Millo, Lipton et Perlis, 1979](https://www.cs.umd.edu/~gasarch/BLOGPAPERS/social.pdf) | Preuve comme processus social ; « Verifiability is not and cannot be a dominating concern in software design. » | Position contestée dans un débat |
| [Brandolini's law, Wikipédia](https://en.wikipedia.org/wiki/Brandolini's_law) | Asymétrie de la réfutation | Adage, source secondaire |
| [Brooks, 1987](https://www.cgl.ucsf.edu/Outreach/pc204/NoSilverBullet.html) | Complexité essentielle et accidentelle ; pas de gain d'un ordre de grandeur | Essai ; thèse discutée |
| [Zave et Jackson, 1997](https://cse.msu.edu/~chengb/RE-491/Papers/dark-corners-re-zave-jackson.pdf) | Exigences sur l'environnement ; propriétés indicatives et optatives | Cadre conceptuel |
| [Lehman, 1996](https://www.cs.kent.edu/~jmaletic/cs63902/Papers/Lehman96.pdf) | Type E ; changement continu ; rétroaction | Revue d'origine à compléter |
| [Hyrum Wright](https://www.hyrumslaw.com/) | Loi de Hyrum | Observation de praticien |
| [Krakovna et al., 2020, DeepMind](https://deepmind.google/discover/blog/specification-gaming-the-flip-side-of-ai-ingenuity/) | Définition du contournement de spécification ; environ 60 exemples | Billet de recherche |
| [Sharma et al., arXiv 2310.13548](https://arxiv.org/abs/2310.13548) | Complaisance de cinq assistants dans quatre tâches | Prépublication ; modèles de 2023 |
| [Bainbridge, 1983](https://ckrybus.com/static/papers/Bainbridge_1983_Automatica.pdf) | Ironies ; vigilance limitée à environ une demi-heure | Contrôle de procédés industriels |
| [Parasuraman et Manzey, 2010](https://pubmed.ncbi.nlm.nih.gov/21077562/) | Complaisance ; erreurs d'omission et de commission ; formation inefficace | Résumé seul |
| [Elish, 2019](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2757236) | Zone de déformation morale | Analyse qualitative d'accidents |
| [Green, 2022](https://www.benzevgreen.com/wp-content/uploads/2022/04/22-clsr.pdf) | 41 documents de politique ; limites de la supervision humaine | Secteur public |
| [Règlement IA, article 14](https://ai-act-service-desk.ec.europa.eu/en/ai-act/article-14) | Supervision effective ; pouvoir de ne pas suivre et d'interrompre ; biais d'automatisation | Systèmes à haut risque seulement |
| [SR 11-7, 2011](https://www.federalreserve.gov/boarddocs/srletters/2011/sr1107a1.pdf) | Contradiction effective | Remplacé en avril 2026 |
| [SR 26-2, 2026](https://www.federalreserve.gov/supervisionreg/srletters/SR2602.htm) | Remplacement de SR 11-7 et SR 21-8 ; approche fondée sur le risque | Lettre d'accompagnement seule |
| [Orrick, avril 2026](https://www.orrick.com/en/Insights/2026/04/Agencies-Overhaul-Model-Risk-Management-Guidance-for-Banks-Heres-What-Changed) | Trois conditions de la contradiction effective ; exclusion de l'IA générative et agentique | Analyse de cabinet ; à confirmer sur le texte |
| [Pidgeon, 2011, Nature](https://www.nature.com/articles/477404a) | Thèse de Perrow sur les accidents normaux | Présentation, pas le livre |
| [Budzyń et al., 2025, Lancet](https://www.thelancet.com/journals/langas/article/PIIS2468-1253(25)00133-5/abstract) | Taux de détection de 28,4 % à 22,4 % ; rapport de cotes 0,69 | Observationnel |
| [Bjork et Bjork, 2011](https://bjorklab.psych.ucla.edu/wp-content/uploads/sites/13/2016/04/EBjork_RBjork_2011.pdf) | Difficultés désirables | Apprentissage scolaire et en laboratoire |
| [Kremer, 1993](https://ideas.repec.org/a/oup/qjecon/v108y1993i3p551-575..html) | Modèle O-ring | Modèle théorique |
| [Autor, 2015](https://jenni.uchicago.edu/econ341/readings/Autor_2015_JEP_v29_n3.pdf) | Complémentarité ; paradoxe de Polanyi | Données américaines antérieures aux modèles génératifs |
| [Agrawal, Gans et Goldfarb, 2018](https://www.nber.org/papers/w24243) | Prédiction et jugement complémentaires | Modèle théorique |
| [Ford, Thoughtworks](https://www.thoughtworks.com/insights/articles/cheaper-code-wont-kill-software-development) | Paradoxe de Jevons appliqué au logiciel | Opinion ; date non indiquée |
| [Deming Institute](https://deming.org/explore/fourteen-points/) | Quatorze points, dont l'inspection | Mot à mot du troisième point à vérifier |

### I.2 Autres références lues, par thème

- **GitHub :** [Why AI is pushing developers toward typed languages](https://github.blog/ai-and-ml/llms/why-ai-is-pushing-developers-toward-typed-languages/). Typage comme contrat et garde-fou ; argument d'éditeur, lien d'adoption présenté comme corrélation, pas causalité démontrée.
- **Microsoft :** [Pragmatic Rust Guidelines, correctness](https://microsoft.github.io/rust-guidelines/guidelines/correctness/index.html). Encadrement et justification de `unsafe`, tests et distinction entre sûreté technique et opération dangereuse.
- **MDN :** [WebAssembly concepts](https://developer.mozilla.org/en-US/docs/WebAssembly/Guides/Concepts). Complémentarité avec JavaScript, compilation multi-langage, environnement sandboxé et intégration aux API web.
- **MDN :** [WebGPU API](https://developer.mozilla.org/en-US/docs/Web/API/WebGPU_API). Rendu et calcul GPU, disponibilité limitée signalée dans la page consultée ; aucune performance générale garantie.
- **Bytecode Alliance :** [Component Model Concepts](https://component-model.bytecodealliance.org/design/component-model-concepts.html). Composants, WIT, interfaces, worlds, plateformes hôtes et WASI.
- **Rust :** [Rust compiler performance survey 2025 results](https://blog.rust-lang.org/2025/09/10/rust-compiler-performance-survey-2025-results/). Variabilité des coûts de compilation ; périmètre particulier de la question sur les recompilations du projet le plus problématique.

- **PhotoCraft, source primaire :** [README du projet](https://github.com/storytold/photocraft). Réimplémentation revendiquée depuis des spécifications publiques et des comportements observés ; avertissement « early alpha » et distinction explicite entre menus raccordés et comportements validés.
- **PhotoCraft, instructions aux agents :** [AGENTS.md](https://github.com/storytold/photocraft/blob/main/AGENTS.md). Sources publiques et observation autorisées, copie de ressources propriétaires interdite, vérification visuelle des modifications ; pas de mention explicite des vidéos comme source de conception dans le contenu examiné.
- **FilmCraft, source primaire :** [README du projet](https://github.com/storytold/filmcraft). Distinction déclarée entre étendue fonctionnelle et aptitude au travail réel, lacunes documentées, moteur exposé à la CLI et à MCP ; fonctionnalités et estimations non testées indépendamment ici.
- **FilmCraft, instructions aux agents :** [AGENTS.md](https://github.com/storytold/filmcraft/blob/main/AGENTS.md). Interdiction explicite de lire ou désassembler les applications Adobe, observation par utilisation, captures de référence locales exclues des livrables.
- **ArtCraft, site officiel :** [Crafting Apps](https://getartcraft.com/apps). Catalogue et statuts « early alpha » ou « in development » des applications.
- **Gizmodo, octobre 2026 :** [Someone Vibe Coded a Free Knockoff of Adobe Creative Suite](https://gizmodo.com/someone-vibe-coded-a-free-knockoff-of-adobe-creative-suite-2000823322). Déclarations sur l'auteur et la réalisation avec Claude/Rust, essai journalistique limité de PhotoCraft avec des opérations utilisables et un comportement instable de Free Transform.

- **MindStudio, 11 octobre 2026 :** [Reverse Engineer Anything: What the Viral REA MCP Actually Does](https://www.mindstudio.ai/blog/reverse-engineer-anything-mcp). Article lu intégralement : présentation de REA comme couche d'orchestration MCP, boucle analyse/reconstruction/test, comparaison informelle avec et sans REA, limites du compte rendu et hypothèse de banalisation des interfaces légères. Source éditoriale d'un fournisseur ; ni documentation primaire du projet REA ni validation indépendante de ses capacités.

**Productivité et vérification :**
- METR, février 2026 : [We are Changing our Developer Productivity Experiment Design](https://metr.org/blog/2026-02-24-uplift-update/) : étude 2025 (temps supérieur de 19 %, IC +2 %/+39 %) ; étude 2026 (réductions brutes de 18 % et 4 %, non fiables, biais de sélection).
- SSRN, paper 4945566 : [The Effects of Generative AI on High-Skilled Work](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4945566) : 4 867 développeurs, 3 essais contrôlés, +26,08 % de tâches complétées (SE 10,3 %).
- Sonar, octobre 2026 : [Verification Gap in AI Coding](https://www.sonarsource.com/company/press-releases/sonar-data-reveals-critical-verification-gap-in-ai-coding/) : enquête déclarative, 1 100+ développeurs.
- Anthropic Economic Index, mars 2026 : [Learning curves](https://www.anthropic.com/research/economic-index-march-2026-report) : « About 49% of jobs have seen at least a quarter of their tasks performed using Claude ».

**SDD et agents :**
- Böckeler, site de Martin Fowler, 15 octobre 2025 : [Understanding Spec-Driven-Development: Kiro, spec-kit, and Tessl](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html) : trois approches (spec-first, spec-anchored, spec-as-source) ; SDD pas encore bien défini ; workflows élaborés = surcharge de revue possible.
- AGENTS.md : [site officiel](https://agents.md) : format Markdown ouvert, piloté par l'Agentic AI Foundation sous la Linux Foundation.
- Anthropic, septembre 2025 : [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) : contexte fini, gestion de tout le contexte (pas seulement le prompt), techniques de compaction.
- Cursor, 14 août 2026 : [Cursor is now a part of SpaceX](https://cursor.com/blog/joining-spacex) : acquisition confirmée.

**Citizen development et gouvernance :**
- CSA Research Note, juin 2026 : [The Vibe Coding Governance Gap](https://labs.cloudsecurityalliance.org/wp-content/uploads/2026/06/CSA_research_note_vibe_coding_ai_governance_gap_20260602-csa-styled.pdf) : vibe coding répandu en entreprise ; frameworks de sécurité IA (NIST AI RMF, OWASP LLM Top 10, CSA MAESTRO, AICM) manquent de guidance pour les citizen developers ; scan d'octobre 2025 sur 5 600 applications vibe-codées en production : aucune avec protection CSRF ou en-têtes de sécurité standard, toutes avec vulnérabilités SSRF.
- TechTarget : [Citizen developers move AI closer to the work](https://www.techtarget.com/enterprise-software/feature/Citizen-developers-move-AI-closer-to-the-work) : la barrière se déplace du code vers la description du problème ; les outils locaux doivent être repris par IT s'ils deviennent critiques.

**Product Management et organisation :**
- MTF Institute, 21 août 2026 : [AI Product Management: 100-Vacancy Study](https://mtfinstitute.com/insights/operating-shape-ai-product-management-100-vacancies-2026/) : rôle intégratif ; 100/100 codés pour stratégie produit IA et aisance technique ; résultat façonné par la règle d'éligibilité (exigeant une propriété matérielle explicite du produit IA), non généralisable à tous les rôles intitulés Product Manager.

**Cadre européen (vérifié à la source) :**
- Commission européenne : [AI Act](https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai) : calendrier complet vérifié.
- Commission européenne : [Cyber Resilience Act](https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act) : 10 décembre 2024, 11 septembre 2026, 11 décembre 2027.
- ANSSI : [Directive NIS 2](https://cyber.gouv.fr/reglementation/cybersecurite-systemes-dinformation/directives-nis-nis2-et-dispositif-saiv/directive-nis-2/) : la page décrit le processus de transposition sans permettre d'en établir l'état juridique exact ; ReCyF disponible depuis le 17 mars 2026.

**Modernisation legacy :**
- Amadeus, janvier 2020 : [Celebrating one year of running fully on open systems](https://amadeus.com/en/blog/articles/celebrating-one-year-fully-open-systems) : 2 000 personnes-années, 400+ ingénieurs au pic, TPF décommissionné juin 2017, dernier mainframe fin 2018.

- **Présentation grand public des cas mathématiques :** vidéo « Ils ont annihilé mon domaine : le métier qu'on croyait intouchable vient de tomber », chaîne IA et Stratégie ([YouTube](https://youtu.be/QzgsvzV7c8Y)). Exemple des affirmations examinées à l'annexe G ; pas une source factuelle.

### I.3 Références repérées, non examinées en détail

Ces références ont été repérées, mais leur contenu n'a pas été examiné en détail. Elles ne sont citées dans le document que comme tendance, pas comme preuve :
- Forasoft, TrueFoundry, Augment Code, Itential (SDD).
- Airfocus, KnowledgeHut, Product School (PM et IA).
- Security Boulevard, Moweb (strangler fig).
- Futurium, tech.eu, Euronews (souveraineté européenne).
- Expedient, Quandary CG, SC World (shadow AI).

- La conférence de Sean Grove (OpenAI) sur les spécifications comme « nouveau code ».
- L'article d'Ars Technica sur l'étude de Harvard.
- Les livres de Marty Cagan (INSPIRED, EMPOWERED, TRANSFORMED) et LOVED de Martina Lauchengco, dont seuls des articles de SVPG et un extrait de TRANSFORMED ont été lus.

### I.4 Index des sources citées dans le corps

- [agents.md](https://agents.md)
- [Agrawal, Gans et Goldfarb, NBER](https://www.nber.org/papers/w24243)
- [AI Act Service Desk](https://ai-act-service-desk.ec.europa.eu/en/ai-act/article-14)
- [aifinops.dev](https://aifinops.dev/)
- [Amadeus, janvier 2020](https://amadeus.com/en/blog/articles/celebrating-one-year-fully-open-systems)
- [ANSSI](https://cyber.gouv.fr/reglementation/cybersecurite-systemes-dinformation/directives-nis-nis2-et-dispositif-saiv/directive-nis-2/)
- [Anthropic, octobre 2026](https://www.anthropic.com/research/employment-at-anthropic)
- [ArtCraft](https://getartcraft.com/apps)
- [arXiv 2007.13422](https://ar5iv.labs.arxiv.org/html/2007.13422)
- [arXiv 2602.15761](https://arxiv.org/html/2602.15761v1)
- [Autor, 2015](https://jenni.uchicago.edu/econ341/readings/Autor_2015_JEP_v29_n3.pdf)
- [Bain](https://www.bain.com/insights/how-to-plan-and-budget-for-agile-at-scale/)
- [Bainbridge, 1983](https://ckrybus.com/static/papers/Bainbridge_1983_Automatica.pdf)
- [Barr et al., 2015](https://www.computer.org/csdl/journal/ts/2015/05/06963470/13rRUx0geBw)
- [Besker, Martini et Bosch, 2019](https://research.chalmers.se/publication/511450/file/511450_Fulltext.pdf)
- [Bjork et Bjork, 2011](https://bjorklab.psych.ucla.edu/wp-content/uploads/sites/13/2016/04/EBjork_RBjork_2011.pdf)
- [Boehm, 1984](https://www.computer.org/csdl/magazine/so/1984/01/01695100/13rRUxD9h2X)
- [Borg et al., arXiv 2507.00788](https://arxiv.org/abs/2507.00788)
- [Böckeler, avril 2026](https://martinfowler.com/articles/harness-engineering.html)
- [Böckeler, octobre 2025](https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html)
- [Brand, Israeli et Ngwe, HBS](https://www.hbs.edu/ris/Publication%20Files/23-062_1f58623a-ee21-44b9-a262-276047bc5543.pdf)
- [Britto, arXiv 2610.14823, 10 octobre 2026](https://arxiv.org/abs/2610.14823)
- [Brooks, 1987](https://www.cgl.ucsf.edu/Outreach/pc204/NoSilverBullet.html)
- [Budzyń et al., The Lancet Gastroenterology & Hepatology, 2025](https://www.thelancet.com/journals/langas/article/PIIS2468-1253(25)
- [Build to Learn vs Build to Earn](https://www.svpg.com/build-to-learn-vs-build-to-earn/)
- [Business & Information Systems Engineering, 2020](https://link.springer.com/article/10.1007/s12599-020-00635-2)
- [Business Insider](https://www.businessinsider.com/linkedin-product-manager-apm-full-stack-builder-2025-12)
- [Bytecode Alliance](https://component-model.bytecodealliance.org/design/component-model-concepts.html)
- [Cagan, A Fresh Definition of the Product Role, août 2026](https://www.svpg.com/a-fresh-definition-of-the-product-role/)
- [Cagan, Commercial vs Internal Products, avril 2026](https://www.svpg.com/commercial-vs-internal-products/)
- [Cagan, Experts Lead Experts, septembre 2026](https://www.svpg.com/experts-lead-experts/)
- [Cagan, Forward Deployed Engineers, septembre 2025](https://www.svpg.com/forward-deployed-engineers/)
- [Cagan, Strong Opinions, Loosely Held, septembre 2026](https://www.svpg.com/strong-opinions-loosely-held/)
- [Cagan, The AI Productivity Paradox, juillet 2026](https://www.svpg.com/the-ai-productivity-paradox/)
- [Cagan, The Era of the Product Creator, mai 2025](https://www.svpg.com/the-era-of-the-product-creator/)
- [CIO Dive, juillet 2026](https://www.ciodive.com/news/ai-shifts-mainframe-modernization-strategy/825677/)
- [Commission européenne](https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai)
- [Commission européenne](https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act)
- [CSA, juin 2026](https://labs.cloudsecurityalliance.org/wp-content/uploads/2026/06/CSA_research_note_vibe_coding_ai_governance_gap_20260602-csa-styled.pdf)
- [Cursor, août 2026](https://cursor.com/blog/joining-spacex)
- [De Millo, Lipton et Perlis, 1979](https://www.cs.umd.edu/~gasarch/BLOGPAPERS/social.pdf)
- [DeepTRACE](https://arxiv.org/html/2509.04499v1)
- [Deming Institute](https://deming.org/explore/fourteen-points/)
- [Duminil-Copin, août 2026](https://proofsandprompts.com/2026/08/30/care-for-a-little-more-ai/)
- [Elish, 2019](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2757236)
- [Faros AI, juillet 2025](https://www.faros.ai/blog/ai-software-engineering)
- [Federal Reserve, SR 11-7](https://www.federalreserve.gov/boarddocs/srletters/2011/sr1107a1.pdf)
- [Federal Reserve, SR 26-2](https://www.federalreserve.gov/supervisionreg/srletters/SR2602.htm)
- [Feng, McDonald et Zhang, arXiv 2506.12469](https://arxiv.org/abs/2506.12469)
- [FilmCraft](https://github.com/storytold/filmcraft)
- [Futurium, Commission européenne](https://futurium.ec.europa.eu/en/apply-ai-alliance/community-content/sovereign-infrastructure-sovereign-capability-europe-open-weight-ai-race)
- [GitHub](https://github.blog/ai-and-ml/llms/why-ai-is-pushing-developers-toward-typed-languages/)
- [Gizmodo](https://gizmodo.com/someone-vibe-coded-a-free-knockoff-of-adobe-creative-suite-2000823322)
- [Gloaguen et al., arXiv 2602.11988](https://arxiv.org/abs/2602.11988)
- [Google, arXiv 2504.09691](https://arxiv.org/abs/2504.09691)
- [Green, 2022](https://www.benzevgreen.com/wp-content/uploads/2022/04/22-clsr.pdf)
- [Hyrum Wright](https://www.hyrumslaw.com/)
- [instructions FilmCraft](https://github.com/storytold/filmcraft/blob/main/AGENTS.md)
- [Itamar Gilad](https://itamargilad.com/ai-pm-jobs/)
- [Journal of Marketing Analytics, 2026](https://link.springer.com/article/10.1057/s41270-026-00542-7)
- [Karpathy, 2025](https://karpathy.bearblog.dev/verifiability/)
- [Kiro](https://kiro.dev/docs/steering/)
- [Kiro](https://kiro.dev/blog/stop-repeating-yourself/)
- [Kopper et al., 2020](https://ideas.repec.org/a/spr/infsem/v18y2020i2d10.1007_s10257-020-00472-6.html)
- [Krakovna et al., 2020](https://deepmind.google/discover/blog/specification-gaming-the-flip-side-of-ai-ingenuity/)
- [Kremer, 1993](https://ideas.repec.org/a/oup/qjecon/v108y1993i3p551-575..html)
- [Lehman, 1996](https://www.cs.kent.edu/~jmaletic/cs63902/Papers/Lehman96.pdf)
- [Liu et al., 2025](https://link.springer.com/article/10.1007/s10515-025-00500-0)
- [LiveResearchBench](https://arxiv.org/html/2510.14240v5)
- [McKinsey](https://www.mckinsey.com.br/capabilities/tech-and-ai/our-insights/agile-funding-an-investment-management-approach-to-funding-outcomes)
- [MDN](https://developer.mozilla.org/en-US/docs/WebAssembly/Guides/Concepts)
- [MDN, WebGPU](https://developer.mozilla.org/en-US/docs/Web/API/WebGPU_API)
- [METR, avril 2026](https://metr.org/blog/2026-04-10-mirrorcode-preliminary-results/)
- [METR, février 2026](https://metr.org/blog/2026-02-24-uplift-update/)
- [METR, juin 2025](https://metr.substack.com/p/2025-06-05-recent-reward-hacking)
- [Microsoft, Pragmatic Rust Guidelines](https://microsoft.github.io/rust-guidelines/guidelines/correctness/index.html)
- [Mind the Product, compte rendu](https://www.mindtheproduct.com/transformed-moving-to-the-product-model-by-marty-cagan/)
- [MindStudio, octobre 2026](https://www.mindstudio.ai/blog/reverse-engineer-anything-mcp)
- [Murkin, 2026](https://www.mindtheproduct.com/evals-are-the-new-prd/)
- [Ng, avril 2026](https://x.com/AndrewYNg/status/2048793852702757151)
- [NIM, 2026](https://www.nim.org/en/publications/detail/leaving-insight-to-digital-twins)
- [notice Pascal-Francis](https://pascal-francis.inist.fr/vibad/index.php?action=getRecordDetail&idt=8553272)
- [OpenAI, février 2026](https://openai.com/index/why-we-no-longer-evaluate-swe-bench-verified/)
- [Orrick, avril 2026](https://www.orrick.com/en/Insights/2026/04/Agencies-Overhaul-Model-Risk-Management-Guidance-for-Banks-Heres-What-Changed)
- [Osmani, 2026](https://www.oreilly.com/radar/comprehension-debt-the-hidden-cost-of-ai-generated-code/)
- [Osmani, O'Reilly](https://www.oreilly.com/radar/the-intent-debt/)
- [Panko et Port, cité dans arXiv 1704.01130](https://arxiv.org/pdf/1704.01130)
- [Panko, 2007](https://panko.com/Publications/Overconfidence%20JOEUC%202007.doc)
- [Parasuraman et Manzey, 2010](https://pubmed.ncbi.nlm.nih.gov/21077562/)
- [PDF des auteurs, version du 4 août 2026](https://fion.ac/jellyfish.pdf)
- [Perrow, présenté dans Nature](https://www.nature.com/articles/477404a)
- [PhotoCraft](https://github.com/storytold/photocraft)
- [Pragmatic Marketing](https://mediafiles.pragmaticmarketing.com/strategic-role-of-product-management/strategic_role_product_management.pdf)
- [Predictability vs Outcomes, octobre 2026](https://www.svpg.com/predictability-vs-outcomes/)
- [Product Coaching and AI, février 2026](https://www.svpg.com/product-coaching-and-ai/)
- [Prototypes vs Products](https://www.svpg.com/prototypes-vs-products/)
- [Quanta Magazine, octobre 2026](https://www.quantamagazine.org/is-ai-the-end-of-math-as-we-know-it-20261005/)
- [Rust, enquête 2025](https://blog.rust-lang.org/2025/09/10/rust-compiler-performance-survey-2025-results/)
- [Sharma et al., arXiv 2310.13548](https://arxiv.org/abs/2310.13548)
- [Shen et Tamkin, Anthropic, janvier 2026](https://www.anthropic.com/research/AI-assistance-coding-skills)
- [Sonar, octobre 2026](https://www.sonarsource.com/company/press-releases/sonar-data-reveals-critical-verification-gap-in-ai-coding/)
- [Spec Kit](https://github.github.com/spec-kit/concepts/spec-persistence.html)
- [SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4945566)
- [Stanford Digital Economy Lab, août 2026](https://digitaleconomy.stanford.edu/publication/canaries-in-the-coal-mine-six-facts-about-the-recent-employment-effects-of-artificial-intelligence/)
- [Stanford HAI, AI Index 2025](https://hai.stanford.edu/ai-index/2025-ai-index-report/research-and-development)
- [SVPG](https://www.svpg.com/)
- [SVPG, Introducing LOVED](https://www.svpg.com/introducing-loved/)
- [SVPG, Product Model Concepts](https://www.svpg.com/product-model-concepts/)
- [Taylor Wessing, juin 2026](https://www.taylorwessing.com/en/insights-and-events/insights/2026/06/ai-and-assisted-programming-in-open-source)
- [TechCrunch, juin 2023](https://techcrunch.com/2023/06/27/whatsapp-business-crosses-200m-maus-introduces-personlized-messages-feature/)
- [The Register, 19 octobre 2026](https://www.theregister.com/columnists/2026/10/19/ais-epic-cash-call-is-matched-only-by-its-ability-to-strangle-revenue-streams/5303493)
- [Thoughtworks](https://www.thoughtworks.com/insights/articles/cheaper-code-wont-kill-software-development)
- [Thoughtworks Radar](https://www.thoughtworks.com/en-us/radar/techniques/spec-driven-development)
- [TRANSFORMED, section 24, O'Reilly](https://www.oreilly.com/library/view/transformed/9781119697336/c24.xhtml)
- [Waydev](https://waydev.co/ai-coding-roi-research-methodology-2026/)
- [Wei, 2025](https://www.jasonwei.net/blog/asymmetry-of-verification-and-verifiers-law)
- [Zave et Jackson, 1997](https://cse.msu.edu/~chengb/RE-491/Papers/dark-corners-re-zave-jackson.pdf)
