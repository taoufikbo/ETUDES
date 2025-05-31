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

