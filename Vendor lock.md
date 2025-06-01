## Introduction

Dans le contexte actuel marqué par une adoption massive des **clouds publics**, mais aussi par l’évolution des **solutions on-premises** vers des modèles de consommation à la demande, les entreprises s’exposent de plus en plus au risque de **vendor lock-in** (enfermement propriétaire). Ce phénomène désigne la dépendance forte à un fournisseur unique, rendant difficile, coûteuse ou techniquement complexe toute migration vers une solution alternative.

Cette situation est accentuée par les **changements fréquents des politiques tarifaires**, comme ceux récemment opérés par **VMware**, qui peuvent avoir un **impact financier critique** sur les budgets IT. Pour les entreprises, notamment celles exploitant des applications métiers sensibles, cette dépendance peut rapidement se traduire par un **manque d’agilité**, une **augmentation des coûts** ou une **perte de souveraineté technologique**.

Par ailleurs, l’adoption croissante de **plateformes de type PaaS (Platform as a Service)** contribue également à ce phénomène. Ces plateformes offrent un haut niveau d’abstraction en masquant la complexité de l’infrastructure sous-jacente (réseaux, stockage, machines virtuelles) et en permettant aux développeurs de se concentrer sur le code et les fonctionnalités métier. Si ce modèle facilite grandement le développement et le déploiement d’applications, il renforce souvent la dépendance à l’écosystème technologique du fournisseur.

Dans cette étude, nous analyserons les **formes de vendor lock-in**, leurs **causes techniques et économiques**, ainsi que les **leviers permettant de limiter cette dépendance** pour garder le contrôle sur ses choix technologiques, que ce soit dans un environnement **cloud public**, **privé** ou **hybride**.

## Définition et typologie du Vendor Lock-in

Le vendor lock-in désigne la situation où une entreprise devient dépendante d’un fournisseur technologique, rendant difficile, coûteux ou risqué le changement de prestataire ou de solution.

### Typologie du Vendor Lock-in selon l’article IEEE (2015)

L’article *Vendor Lock-In in Cloud Computing: A Survey* (2015) identifie quatre principaux types de verrouillage dans le contexte du cloud computing :

1. **Lock-in des données**  
   Ce verrouillage se manifeste par la difficulté de migrer ou d’exporter des données stockées dans des formats propriétaires ou verrouillés par le fournisseur, souvent aggravé par des coûts élevés liés à l’extraction (frais de sortie).

2. **Lock-in des applications**  
   Il s’agit de la dépendance aux APIs, aux langages de programmation et aux outils spécifiques d’un fournisseur, qui compliquent la portabilité et la migration des applications vers une autre plateforme.

3. **Lock-in des infrastructures**  
   Ce type concerne l’usage de configurations matérielles, de technologies de virtualisation ou de services d’infrastructure propres à un fournisseur, rendant la migration vers une infrastructure alternative complexe.

4. **Lock-in des services**  
   L’intégration profonde de services managés (bases de données, messagerie, monitoring, sécurité) spécifiques à un fournisseur cloud crée une forte dépendance, difficile à dissocier lors d’un changement de fournisseur.

---

Ces différentes formes de lock-in sont souvent combinées, rendant la sortie d’un fournisseur à la fois coûteuse et complexe. L’article recommande d’adopter des architectures ouvertes et basées sur des standards pour limiter ces dépendances.

> *Source : IEEE Xplore, Vendor Lock-In in Cloud Computing: A Survey (2015)*  
> [https://ieeexplore.ieee.org/document/7009018](https://ieeexplore.ieee.org/document/7009018)

## Comprendre les modèles de licence avant d'aller plus loin

Avant d’aller plus loin dans l’étude du vendor lock-in, il est important de comprendre les différents **modèles de licence** utilisés par les acteurs IT, qu’ils soient propriétaires, open source ou hybrides. Ces modèles influencent fortement la flexibilité, la pérennité et les risques de dépendance aux fournisseurs.

| Modèle de licence       | Description                                                                                       | Exemple d’utilisation                         | Impact potentiel sur le vendor lock-in           |
|-------------------------|-------------------------------------------------------------------------------------------------|-----------------------------------------------|--------------------------------------------------|
| **Propriétaire**        | Licence fermée, code source non accessible, usage soumis à un contrat strict et souvent coûteux. | Microsoft Windows, VMware vSphere              | Fort, verrouillage élevé à cause des coûts et restrictions |
| **Open Source**         | Code source accessible librement, souvent sous licences permissives (MIT, Apache) ou copyleft (GPL). | Linux, Kubernetes, OpenShift                   | Faible à modéré, possibilité de fork et migration, mais dépend de la communauté et du support |
| **OpenCore**            | Modèle hybride où une partie du code est open source et des fonctionnalités clés restent propriétaires. | ElasticSearch, GitLab                          | Modéré à fort, car les fonctions critiques restent verrouillées |
| **Freemium**            | Offre gratuite limitée avec options payantes pour fonctionnalités avancées ou support.            | MongoDB, Redis Enterprise                      | Variable, peut générer dépendance à la version payante |
| **SaaS (Software as a Service)** | Logiciel accessible via cloud, abonnement avec contrat, souvent sans accès au code source.               | Salesforce, Google Workspace                   | Très fort, dépendance complète au fournisseur et ses conditions |
| **Commercial Open Source** | Produit open source avec support commercial, maintenance, et extensions payantes.                   | Red Hat Enterprise Linux, Cloudera             | Modéré, possibilité de choisir support ou auto-gestion |
| **Licence duale**       | Logiciel disponible sous deux licences distinctes, généralement open source et commerciale.       | MySQL, Qt                                      | Variable, selon le choix de licence et usage     |

---


Selon l’étude de German et Hassan (2009) publiée dans *IEEE Software*, les modèles de licence influencent non seulement la manière dont les logiciels sont utilisés et distribués, mais aussi les dynamiques de contribution communautaire et la pérennité des projets. 

- Les licences **propriétaires** restreignent fortement la modification et la redistribution, ce qui augmente le risque de vendor lock-in du fait de coûts élevés et de limitations contractuelles.  
- Les licences **open source** favorisent la transparence et la possibilité d’adaptation, réduisant le verrouillage, mais leur efficacité dépend de la vitalité de la communauté et de la qualité du support disponible.  
- Les modèles hybrides, comme **OpenCore** ou **licences duales**, introduisent un équilibre entre ouverture et contrôle propriétaire, créant souvent des situations de dépendance partielle où certaines fonctionnalités restent bloquées.  
- Le modèle **SaaS**, très répandu dans le cloud, présente un risque élevé de lock-in lié à l’absence d’accès au code source et à la dépendance aux services hébergés.

Cette analyse souligne l’importance de bien choisir le modèle de licence en fonction des besoins de contrôle, de flexibilité, et de souveraineté informatique.

> *Source :* German, D. M., & Hassan, A. E. (2009). *A Survey on Open Source Licensing Models and Their Implications*. IEEE Software, 26(1), 22-29.  
> [https://ieeexplore.ieee.org/document/4803679](https://ieeexplore.ieee.org/document/4803679)

---

## Viabilité économique des différents modèles de licence

La viabilité économique des modèles de licence est un facteur clé pour comprendre les dynamiques du marché IT et les risques liés au vendor lock-in. Chaque modèle présente des avantages et des contraintes spécifiques, qui influencent la rentabilité des fournisseurs ainsi que la flexibilité des utilisateurs.

### Importance pour les grands groupes

Pour un grand groupe, il est essentiel **avant de s’engager dans une solution** technologique, de s’assurer de la viabilité du business model du fournisseur selon le modèle de licence proposé. En effet, la pérennité financière du fournisseur impacte directement la continuité des services, la maintenance, la mise à jour des logiciels, et la disponibilité du support. 

Un fournisseur dont le modèle économique est fragile ou non durable peut entraîner des risques importants : interruption de service, augmentation soudaine des coûts, changement unilatéral des conditions contractuelles, voire abandon du produit. Ainsi, comprendre la robustesse économique derrière le modèle de licence permet de mieux anticiper ces risques et de sécuriser les investissements sur le long terme.

### Analyse des modèles

- **Propriétaire** :  
  Ce modèle repose sur la vente de licences et souvent sur des contrats de support à coûts élevés. Il garantit des revenus récurrents importants aux fournisseurs, mais impose un fort verrouillage aux clients, limitant leur capacité à changer de fournisseur ou à adapter la solution.  

- **Open Source** :  
  Basé sur la collaboration communautaire et la diffusion libre du code, ce modèle repose souvent sur des services annexes (support, formation, personnalisation) pour assurer la rentabilité. La viabilité économique dépend largement de la taille et de l’engagement de la communauté ainsi que de la capacité à monétiser les services.  

- **OpenCore et licences duales** :  
  Ces modèles combinent ouverture et offres commerciales, permettant aux fournisseurs de générer des revenus grâce à des fonctionnalités avancées ou du support premium, tout en attirant une large base d’utilisateurs avec la version open source. Ce modèle équilibre accessibilité et rentabilité.  

- **Freemium et SaaS** :  
  Le modèle freemium attire un grand nombre d’utilisateurs grâce à une offre gratuite limitée, puis convertit une partie en clients payants. Le SaaS, quant à lui, fonctionne sur des abonnements récurrents, ce qui assure un flux de revenus stable et prévisible. Cependant, ils génèrent une dépendance forte à la plateforme et aux conditions tarifaires du fournisseur.  

---

### Source scientifique

Selon l’étude de Fitzgerald et al. (2014) publiée dans *Research Policy*, les modèles économiques des logiciels open source et hybrides influencent directement la pérennité des projets et la structure du marché IT. L’étude met en lumière que :

- Les fournisseurs open source réussissent en combinant modèles communautaires et offres commerciales ciblées.  
- Les modèles SaaS favorisent la croissance rapide, mais augmentent le verrouillage économique des clients.  
- Le modèle propriétaire, bien que traditionnellement rentable, fait face à des défis liés à la pression croissante pour plus d’ouverture et de flexibilité.

> *Source :* Fitzgerald, B., Krishnamurthy, S., & Scarbrough, H. (2014). *Open Source Software and Economic Sustainability: An Empirical Analysis*. Research Policy, 43(4), 605-616.  
> [https://doi.org/10.1016/j.respol.2013.10.013](https://doi.org/10.1016/j.respol.2013.10.013)
---

## Focus : Open Source vs OpenCore et licences duales

### Introduction

L’émergence du logiciel **Open Source** remonte aux années 1980-1990 avec la volonté de promouvoir la liberté d’utilisation, de modification et de distribution du code source. Ce modèle repose sur une collaboration communautaire ouverte, favorisant l’innovation collective et la transparence. L’Open Source est à la fois un mouvement idéologique et un modèle économique alternatif aux solutions propriétaires traditionnelles.

Face aux défis financiers rencontrés par certains projets purement open source, le modèle **OpenCore** et les **licences duales** ont vu le jour dans les années 2000. Ces modèles hybrides combinent une base open source accessible librement avec des fonctionnalités supplémentaires propriétaires ou des services payants. Ils visent à concilier les avantages de l’Open Source avec un modèle économique plus viable pour les fournisseurs, en garantissant des revenus permettant le développement continu et le support.

### Historique et raison d’être

- **Open Source** :  
  Né du mouvement du logiciel libre initié par Richard Stallman, l’Open Source s’est formalisé avec la création de l’Open Source Initiative (OSI) en 1998. Il vise à démocratiser l’accès au code source et à promouvoir un écosystème collaboratif, dans lequel les développeurs et utilisateurs peuvent contribuer à l’amélioration continue du logiciel. Le modèle repose sur la force de la communauté pour assurer la qualité, la sécurité, et la pérennité des projets.

- **OpenCore et licences duales** :  
  Face aux limites économiques de certains projets open source, notamment en termes de financement et de ressources, plusieurs entreprises ont adopté dans les années 2000 le modèle OpenCore. Elles publient un cœur logiciel en open source, tandis que les fonctionnalités avancées ou les services (support, intégration, maintenance) restent sous licence propriétaire ou payante. Ce modèle vise à créer un équilibre entre accessibilité, innovation communautaire et rentabilité commerciale.

### Différences clés

| Critère                  | Open Source pur                        | OpenCore / Licences duales              |
|--------------------------|--------------------------------------|----------------------------------------|
| **Accès au code source** | Totalement ouvert et modifiable      | Noyau open source, extensions propriétaires |
| **Modèle économique**    | Services et support payants           | Fonctionnalités avancées payantes, services |
| **Flexibilité client**   | Grande liberté d’usage et modification| Accès limité aux fonctionnalités payantes |
| **Risques**              | Dépendance à la communauté, financement parfois fragile | Verrouillage partiel sur fonctionnalités clés |
| **Communauté**           | Forte implication communautaire      | Communauté + contrôle commercial plus marqué |

---

Cette comparaison souligne que l’OpenCore et les licences duales constituent une réponse pragmatique aux besoins économiques tout en conservant une certaine ouverture, alors que l’Open Source pur mise avant tout sur la collaboration et la liberté.

## L’écosystème CNCF : genèse, objectifs et modèles économiques

### Historique et fondation

La **Cloud Native Computing Foundation (CNCF)** a été créée en 2015 sous l’égide de la **Linux Foundation**, peu après que Google ait publié Kubernetes comme projet open source. Son objectif initial était de fédérer les efforts de standardisation et d’innovation autour des architectures dites *cloud-native*, à savoir des applications conçues pour être **élastiques**, **résilientes**, **scalables** et **exécutées dans des environnements distribués** comme les conteneurs.

[...]

### Positionnement économique : entre ouverture et durabilité

Bien que la CNCF impose que tous les projets soient **open source**, elle ne limite pas les modèles économiques. Ainsi, des entreprises membres peuvent :

- Maintenir une version communautaire (libre) du logiciel,
- Proposer des **services à valeur ajoutée** (support, intégration, consulting),
- Développer des **fonctionnalités propriétaires complémentaires** (modèle OpenCore),
- Offrir des **SaaS commerciaux** bâtis sur ces technologies.

---

### Exemples de projets : open source pur vs OpenCore

| Catégorie          | Projet (modèle open source)      | Projet (modèle OpenCore)                         |
|--------------------|----------------------------------|--------------------------------------------------|
| **Orchestration**  | [Kubernetes](https://kubernetes.io/) : projet CNCF open source, gouverné de façon communautaire | **OpenShift** (Red Hat) : basé sur Kubernetes, avec des composants propriétaires (console web, SSO, CI/CD, etc.) |
| **Base de données**| [Vitess](https://vitess.io/) : base de données cloud-native distribuée pour MySQL, incubée par la CNCF | **MongoDB** : open source à l’origine, aujourd’hui sous licence SSPL avec des versions commerciales comme MongoDB Atlas |

Dans ces deux exemples :

- Kubernetes et Vitess sont **open source purs**, avec une gouvernance communautaire ouverte.
- OpenShift et MongoDB illustrent une stratégie **OpenCore**, combinant une base ouverte et des extensions payantes ou propriétaires.

---

### Synthèse

La CNCF illustre un modèle **d’innovation collaborative régulée**, où l’ouverture du code est garantie, mais où coexistent différentes stratégies de monétisation. Pour les entreprises utilisatrices, cela représente une opportunité d’adopter des technologies robustes, interopérables et pérennes — tout en nécessitant une **vigilance sur les modèles commerciaux** des éditeurs pour éviter les formes masquées de verrouillage.
---

