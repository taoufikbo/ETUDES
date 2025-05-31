## Introduction

Dans le contexte actuel marqué par une adoption massive des **clouds publics**, mais aussi par l’évolution des **solutions on-premises** vers des modèles de consommation à la demande, les entreprises s’exposent de plus en plus au risque de **vendor lock-in** (enfermement propriétaire). Ce phénomène désigne la dépendance forte à un fournisseur unique, rendant difficile, coûteuse ou techniquement complexe toute migration vers une solution alternative.

Cette situation est accentuée par les **changements fréquents des politiques tarifaires**, comme ceux récemment opérés par **VMware**, qui peuvent avoir un **impact financier critique** sur les budgets IT. Pour les entreprises, notamment celles exploitant des applications métiers sensibles, cette dépendance peut rapidement se traduire par un **manque d’agilité**, une **augmentation des coûts** ou une **perte de souveraineté technologique**.

Par ailleurs, l’adoption croissante de **plateformes de type PaaS (Platform as a Service)** contribue également à ce phénomène. Ces plateformes offrent un haut niveau d’abstraction en masquant la complexité de l’infrastructure sous-jacente (réseaux, stockage, machines virtuelles) et en permettant aux développeurs de se concentrer sur le code et les fonctionnalités métier. Si ce modèle facilite grandement le développement et le déploiement d’applications, il renforce souvent la dépendance à l’écosystème technologique du fournisseur.

Dans cette étude, nous analyserons les **formes de vendor lock-in**, leurs **causes techniques et économiques**, ainsi que les **leviers permettant de limiter cette dépendance** pour garder le contrôle sur ses choix technologiques, que ce soit dans un environnement **cloud public**, **privé** ou **hybride**.

## Définition du Vendor Lock-in

Le **vendor lock-in**, ou enfermement propriétaire, désigne une situation dans laquelle une entreprise devient fortement dépendante d’un fournisseur particulier pour un produit ou un service, au point qu’elle ne peut pas en changer sans subir des coûts significatifs, des pertes de données, ou des interruptions de service.

Selon le **NIST (National Institute of Standards and Technology)**, le vendor lock-in est un risque inhérent à l’utilisation des services cloud, notamment lorsque les solutions utilisées ne respectent pas des standards ouverts ou ne permettent pas l’interopérabilité avec d’autres systèmes. Ce phénomène complique la migration vers d'autres prestataires ou le rapatriement des charges de travail en interne.

> *Source : NIST Special Publication 800-146 – Cloud Computing Synopsis and Recommendations*

De manière complémentaire, **Jean-Christophe Viseur** (2014) étend la notion de verrouillage en insistant sur ses **dimensions multiples**, qui vont au-delà des simples considérations techniques. Il identifie ainsi **plusieurs niveaux de lock-in**, chacun pouvant être un frein à la réversibilité des systèmes d'information.

### Les niveaux de Vendor Lock-in selon J.-C. Viseur

1. **Verrouillage technologique** :  
   Résulte de l’utilisation de technologies propriétaires ou non standardisées, rendant difficile l’interopérabilité ou la migration.

2. **Verrouillage juridique** :  
   Découle de clauses contractuelles restrictives, d’accords de licences, ou d'engagements de durée qui limitent la liberté de changement de fournisseur.

3. **Verrouillage organisationnel** :  
   Apparaît lorsque les processus internes de l’entreprise sont profondément intégrés à une solution spécifique, rendant complexe le changement sans transformation structurelle.

4. **Verrouillage cognitif** :  
   Reflète la dépendance aux compétences internes ou à la culture d’un écosystème technologique donné, rendant psychologiquement ou culturellement difficile toute remise en question.

5. **Verrouillage économique** :  
   Lié aux investissements financiers déjà réalisés (capex, formation, intégration), qui rendent toute migration économiquement non rentable à court terme.

> *Source : Viseur, J.-C. (2014). « Les enjeux du verrouillage technologique dans le cloud computing », CREIS-Terminal, n°115-116.*  
> [https://www.lecreis.org/creis/wp-content/uploads/Viseur-CREIS-TERMINAL_2014.pdf](https://www.lecreis.org/creis/wp-content/uploads/Viseur-CREIS-TERMINAL_2014.pdf)

Ces différentes formes de verrouillage peuvent se cumuler et former un **système de dépendance complexe**, qu’il est nécessaire d’analyser en profondeur pour anticiper les risques et prendre des décisions éclairées.


