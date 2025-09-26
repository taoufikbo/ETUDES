voila le contenu ## Introduction

## 🎯 Contexte : Une dépendance technologique croissante

Avec l’essor massif des **clouds publics** et la transformation des **solutions on-premises** vers des modèles de consommation à la demande, les entreprises font face à un risque accru de **vendor lock-in** — c’est-à-dire une dépendance difficilement réversible à un fournisseur unique.

### ⚠️ Enjeux majeurs

- **Changements tarifaires imprévus** (ex. VMware) peuvent avoir un **impact budgétaire critique**
- **Pertes d’agilité** et **hausse des coûts** pour les applications métier sensibles
- **Dépendance accrue** via les **PaaS**, qui simplifient le développement mais verrouillent les choix techniques

## Quelques definitions : 
## Définition et typologie du Vendor Lock-in

Le vendor lock-in désigne la situation où une entreprise devient dépendante d’un fournisseur technologique, rendant difficile, coûteux ou risqué le changement de prestataire ou de solution.

### Typologie du Vendor Lock-in selon l’article IEEE (2015)

L’article *Vendor Lock-In in Cloud Computing: A Survey* (2015) identifie quatre principaux types de verrouillage dans le contexte du cloud computing :
## Typologie du Vendor Lock-in (IEEE, 2015)

| **Type de Lock-in**          | **Description**                                                                                                                                     |
|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Lock-in des données**     | Difficulté à migrer ou exporter les données en raison de formats propriétaires ou de frais de sortie élevés.                                        |
| **Lock-in des applications**| Dépendance aux APIs, langages ou outils spécifiques d’un fournisseur, compliquant la portabilité des applications.                                  |
| **Lock-in des infrastructures** | Usage de technologies matérielles, de virtualisation ou de configurations propres au fournisseur, rendant complexe le changement d’infrastructure. |
| **Lock-in des services**    | Forte dépendance aux services managés intégrés (bases de données, monitoring, sécurité), difficilement transposables chez un autre fournisseur.      |

---


> *Source : IEEE Xplore, Vendor Lock-In in Cloud Computing: A Survey (2015)*  
> [https://ieeexplore.ieee.org/document/7009018](https://ieeexplore.ieee.org/document/7009018)

## Et l'opensource ? : une forme de lock souvent sous-estimée

L’open source est souvent perçu comme un rempart contre le vendor lock-in. Pourtant, plusieurs formes de **verrouillage indirect** peuvent exister, notamment liées à la fragilité de l’écosystème ou aux décisions d’acteurs dominants.

---

### ⚠️ Trois formes de verrouillage possibles

#### 1. Désengagement d’un acteur clé
- **Exemple** : *Cloud Foundry* (Pivotal/VMware)
- **Problème** : Retrait de VMware → affaiblissement de l’écosystème
- **Conséquences** : perte de support, arrêt des développements, migration coûteuse

#### 2. Changement de licence restrictif
- **Exemple** : *Terraform* (HashiCorp) → passage en BUSL
- **Problème** : Usage commercial restreint
- **Conséquences** : Fork communautaire (*OpenTofu*), incertitudes pour les utilisateurs

#### 3. Verrouillage par conflit d’intérêts
- **Exemple** : *ElasticSearch* → passage à SSPL
- **Problème** : Tension avec AWS, modèle fermé
- **Conséquences** : Perte du statut open source, divergence de l’écosystème (ex. OpenSearch)

---

### 📌 Leçon clé

Un projet open source n’est pas automatiquement synonyme de pérennité.  
Pour limiter le risque de verrouillage, il faut s’assurer que :
- ✅ La communauté est **active et diversifiée**  
- ✅ La **gouvernance est distribuée**  
- ✅ Aucun acteur unique ne peut imposer seul des **changements de licence ou de roadmap**

---

## Comprendre les modèles de licence avant d'aller plus loin

Avant d’aller plus loin dans l’étude du vendor lock-in, il est important de comprendre les différents **modèles de licence** utilisés par les acteurs IT, qu’ils soient propriétaires, open source ou hybrides. Ces modèles influencent fortement la flexibilité, la pérennité et les risques de dépendance aux fournisseurs.

| Modèle de licence       | Description                                                                                       | Exemple d’utilisation                         | Impact potentiel sur le vendor lock-in           |
|-------------------------|-------------------------------------------------------------------------------------------------|-----------------------------------------------|--------------------------------------------------|
| **Propriétaire**        | Licence fermée, code source non accessible, usage soumis à un contrat strict et souvent coûteux. | Microsoft Windows, VMware vSphere              | Fort, verrouillage élevé à cause des coûts et restrictions |
| **Open Source**         | Code source accessible librement, souvent sous licences permissives (MIT, Apache) ou copyleft (GPL). | Linux, Kubernetes                   | Faible à modéré, possibilité de fork et migration, mais dépend de la communauté et du support |
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

## Viabilité économique des différents modèles de licence qui faut prendre en compte pour les plateformes et projets critiques 

Comme dans toutes les strategies de sourcing Il est essentiel **avant de s’engager dans une solution** technologique, de s’assurer de la viabilité du business model du fournisseur selon le modèle de licence proposé. En effet, la pérennité financière du fournisseur impacte directement la continuité des services, la maintenance, la mise à jour des logiciels, et la disponibilité du support. 

Un fournisseur dont le modèle économique est fragile ou non durable peut entraîner des risques importants : interruption de service, augmentation soudaine des coûts, changement unilatéral des conditions contractuelles, voire abandon du produit. Ainsi, comprendre la robustesse économique derrière le modèle de licence permet de mieux anticiper ces risques et de sécuriser les investissements sur le long terme.

## Focus : Open Source vs OpenCore et licences duales

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
## Intégration des solutions open source vs OpenCore : retour d’expérience utilisateur

### Résultats d’une étude comparative

Une étude menée par Forrester Consulting pour Instaclustr en 2022, basée sur les réponses de 322 décideurs en développement applicatif, met en lumière les différences perçues et réelles entre les modèles **open source** (FOSS) et **OpenCore** du point de vue des utilisateurs finaux :contentReference[oaicite:4]{index=4}.

#### Avantages perçus du modèle OpenCore

Les répondants utilisant des solutions OpenCore ont identifié les avantages suivants :

- **Réduction des risques** : 41%
- **Efficacité accrue** : 39%
- **Facilité de transition vers le cloud** : 33%

Cependant, ces avantages sont également attribués aux solutions open source matures, remettant en question la supériorité perçue du modèle OpenCore.

#### Obstacles à l'adoption de l'open source

Parmi les organisations utilisant des solutions OpenCore, les principaux freins à l'adoption de l'open source sont :

- **Stratégie incohérente entre les départements** : 39%
- **Manque de support complet** : 31%
- **Absence de compétences internes en open source** : 29%
- **Verrouillage des licences existantes** : 29%

Ces obstacles soulignent la nécessité d'un accompagnement spécialisé pour réussir la transition vers des solutions open source.

#### Avantages reconnus des solutions open source

Les organisations ayant adopté des solutions open source mettent en avant :

- **Réduction des coûts** : 45%
- **Élimination des frais de licence** : 41%
- **Accès complet au code source** : 40%
- **Force de la communauté** : 40%

Ces avantages contribuent à une plus grande flexibilité et à une meilleure adaptabilité des solutions open source.

#### Besoin d'accompagnement externe

Malgré les avantages, 84% des organisations utilisant des solutions open source expriment le besoin de recourir à des services managés ou à des consultants pour :

- **Sécurité** : 68%
- **Scalabilité** : 66%
- **Assistance à la migration** : 66%
- **Expertise globale en open source** : 65%

Cela souligne l'importance d'un support externe pour maximiser les bénéfices des solutions open source.

### Synthése 

| **Thème**                                              | **Détails / Données**                                                                                                                                                                          |
| ------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Avantages perçus du modèle OpenCore**                | - Réduction des risques : 41%  <br> - Efficacité accrue : 39%  <br> - Facilité de transition vers le cloud : 33%                                                                               |
| **Obstacles à l’adoption de l’open source**            | - Stratégie incohérente entre départements : 39%  <br> - Manque de support complet : 31%  <br> - Absence de compétences internes : 29%  <br> - Verrouillage des licences existantes : 29%      |
| **Avantages reconnus des solutions open source**       | - Réduction des coûts : 45%  <br> - Élimination des frais de licence : 41%  <br> - Accès complet au code source : 40%  <br> - Force de la communauté : 40%                                     |
| **Besoin d’accompagnement externe pour l’open source** | 84% des organisations déclarent un besoin d’accompagnement pour :  <br> - Sécurité : 68%  <br> - Scalabilité : 66%  <br> - Assistance à la migration : 66%  <br> - Expertise open source : 65% |


### Implications pour les utilisateurs finaux

Les données indiquent que, bien que les solutions open source offrent des avantages significatifs en termes de coût, de flexibilité et d'innovation, leur adoption réussie dépend fortement de la stratégie organisationnelle, des compétences internes et du support externe disponible. Les solutions OpenCore, bien qu'offrant une certaine commodité, peuvent entraîner des coûts plus élevés et un risque de verrouillage fournisseur.

---

**Références :**

- Forrester Consulting & Instaclustr, *The Advantages of Using Free And Open-Source Software Vs. Open-Core Software*, 2022. :contentReference[oaicite:5]{index=5}

# Comparatif des plateformes Cloud (CaaS/PaaS)

| Critère                                | OpenShift (Red Hat)                          | Kubernetes Vanilla                  | VMware Tanzu / vSphere             | SUSE Rancher / RKE2                       | Cloud Foundry                        |
|----------------------------------------|----------------------------------------------|-------------------------------------|------------------------------------|-------------------------------------------|--------------------------------------|
| **Modèle de licence**                  | Commercial (par node)                         | Open source (gratuit)               | Commercial (CPU/vCPU)              | Open source + support                     | Open source + support               |
| **Richesse fonctionnelle entreprise**  | Très riche (CI/CD, GitOps, ACM, ACS, ODF...) | Basique, à construire               | Riche avec stack VMware (NSX, Harbor) | Complète (GUI, Fleet, CAPI...)            | Riche mais rigide (12-factor apps)  |
| **Portabilité des workloads**          | Bonne : compatible K8s, mais dépend des CRDs et Operators OpenShift spécifiques. Support d'OpenShift Service Mesh, ODF, etc. Moins portable sur clusters génériques K8s. | Excellente : 100 % natif Kubernetes, sans dépendance à un fournisseur. Compatible multi-cloud et edge. | Moyenne : les Tanzu CRDs, NSX-T et services VMware réduisent la portabilité vers des environnements hors vSphere. | Très bonne : Rancher orchestre des clusters hétérogènes (on-prem, cloud, edge). RKE2 est compatible K8s standard, pas de vendor lock-in fort. | Faible : déploiement lié à la plateforme Cloud Foundry. Stack rigide, difficulté à migrer vers K8s natif sans refactorisation. |
| **Risque de lock-in (LCM, CI/CD, sécurité)** | Élevé : gestion centralisée via RH Operators, ACM, Pipelines, Console intégrée. | Faible : outils au choix (ArgoCD, Flux, Jenkins...). Aucune dépendance forte. | Élevé : CLI Tanzu, NSX, LCM propriétaire. Difficulté à s’extraire de l’écosystème. | Faible à modéré : Fleet et Rancher GUI facilitent la gestion, mais peuvent devenir centraux dans l’organisation. | Très élevé : BOSH, Diego, UAA sont très spécifiques. Migration complexe. |
| **Disponibilité des compétences**      | Bonne : écosystème Red Hat mature, certifications bien reconnues. | Très large : forte communauté, documentations, formations en masse. | Moyenne : nécessite des compétences K8s **et** VMware. | Bonne, en croissance : adoption croissante dans les secteurs publics et edge. | Faible : désintérêt croissant, moins de formations disponibles. |
| **Adoption marché (entreprises & Telco)** | Très forte : telcos (Orange, Vodafone,Nokia ,Mavenir...), industries, secteurs publics. | Universelle : hyperscalers, startups, industries, institutions. | Bonne : adoption dans les entreprises déjà VMware-centric. | Croissante : souveraineté, edge computing, clusters embarqués. | En déclin : utilisé dans certains systèmes legacy ou très spécifiques. |
| **Pérennité / Roadmap**                | Très forte : soutenu par IBM/Red Hat, feuille de route solide. | Très forte : CNCF, soutenu par tous les hyperscalers. | Moyenne : incertitudes après le rachat par Broadcom. | Bonne : SUSE investit fortement dans Rancher, RKE2, NeuVector. | Faible : projets peu actifs, roadmap floue. |
| **Participation open source**          | Très élevée : Tekton, Istio, OKD, core K8s contributor. | Forte : projets menés par Google, Red Hat, AWS, etc. | Moyenne : contributions à Velero, Harbor. | Élevée : Rancher Labs, K3s, RKE2, NeuVector. | Faible : héritage fort, mais contributions en baisse. |

Ajout du Radar 


### Comparatif des plateformes Cloud (IaaS)

| Critère | KubeVirt (standalone) | OpenShift Virtualization | OpenStack (com.) | OpenStack Red Hat | VMware vSphere | KubeVirt SUSE Harvester | Proxmox VE | CloudStack (Apache) |
|---------|----------------------|-------------------------|------------------|-------------------|---------------|-------------------------|------------|---------------------|
| **Modèle de licence** | Open source (Apache) | Commercial via OpenShift | Open source | Commercial RHOSP | Commercial | Open source + support | Open source GPL | Open source (Apache) |
| **Richesse fonctionnelle** | Moyenne (VMs dans K8s) | Très riche (SDN, CSI, RH integrations) | Riche | Très riche | Très riche | Bonne (Fleet, GUI) | Moyenne | Riche (réseau, stockage) |
| **Portabilité workloads** | Bonne | Bonne (OVF/virtIO/CDI) | Bonne | Moyenne | Moyenne-faible | Bonne | Moyenne | Bonne |
| **Vendor lock-in - Portabilité** | Faible | Moyenne (CDI, CRDs RH) | Faible | Moyen | Fort | Faible à modéré | Faible | Faible |
| **Vendor lock-in - LCM/gestion** | Faible | Fort (via OCP stack) | Faible | Fort (RH tools) | Très fort | Modéré | Faible | Faible à modéré |
| **Disponibilité compétences** | Moyenne | Moyenne à bonne (RH cert.) | Bonne | Moyenne | Très bonne | En croissance | Bonne | Moyenne |
| **Adoption marché** | En hausse | Forte chez Telcos | Moyenne | Forte (Telcos) | Très forte | Croissante | Moyenne | Moyenne |
| **Pérennité / Roadmap** | Forte (CNCF) | Très forte (IBM/Red Hat) | Bonne | Bonne | Incertaine | Bonne | Bonne | Moyenne |
| **Participation open source** | Élevée (CNCF) | Très forte (KubeVirt, CDI, Tekton…) | Élevée | Très élevée | Moyenne | Bonne (SUSE, CNCF) | Moyenne | Élevée (Apache) |
