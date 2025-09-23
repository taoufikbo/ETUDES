---
title: Vendor Lock-in
author: Taoufik Bouazza
date: 2025
theme: serif
---

# 🚪 Vendor Lock-in  
### Comprendre et anticiper la dépendance aux fournisseurs IT

---

## Introduction

![Intro](images/intro.png)

## 🎯 Contexte : Une dépendance technologique croissante

Avec l’essor massif des **clouds publics** et la transformation des **solutions on-premises** vers des modèles de consommation à la demande, les entreprises font face à un risque accru de **vendor lock-in**.

---

### ⚠️ Enjeux majeurs

- 💸 **Changements tarifaires imprévus** (ex. VMware) → impact budgétaire critique  
- 🐌 **Pertes d’agilité** et **hausse des coûts** pour les applications sensibles  
- 🔒 **Dépendance accrue** via les **PaaS** → simplifient mais verrouillent  

---

## Quelques définitions  

## 📖 Définition et typologie du Vendor Lock-in

Le vendor lock-in désigne la situation où une entreprise devient dépendante d’un fournisseur technologique, rendant difficile, coûteux ou risqué le changement.

---

### Typologie (IEEE, 2015)

| **Type**                | **Description** |
|--------------------------|-----------------|
| 📂 **Lock-in des données** | Formats propriétaires, frais de sortie élevés |
| ⚙️ **Lock-in des applis**  | APIs/langages spécifiques → faible portabilité |
| 🖥 **Lock-in infra**       | Configs ou virtualisation propres au fournisseur |
| 🛠 **Lock-in services**    | Services managés intégrés difficilement migrables |

---

> *Source :* IEEE Xplore, *Vendor Lock-In in Cloud Computing: A Survey (2015)*  
> [Lien](https://ieeexplore.ieee.org/document/7009018)

---

## Et l’open source ?  

![Open Source](images/open_source.png)

L’open source est souvent vu comme un rempart. Pourtant, il existe des **verrouillages indirects** liés aux licences ou aux acteurs dominants.

---

### ⚠️ Trois formes possibles

1. **Désengagement d’un acteur clé**  
   Ex. *Cloud Foundry* → retrait de VMware  

2. **Changement de licence restrictif**  
   Ex. *Terraform* → BUSL → fork *OpenTofu*  

3. **Conflit d’intérêts**  
   Ex. *ElasticSearch* → SSPL → divergence avec *OpenSearch*  

---

### 📌 Leçon clé

✅ Vérifier la **communauté active**  
✅ Gouvernance **distribuée**  
✅ Éviter qu’un seul acteur impose la roadmap  

---

## Comprendre les modèles de licence

![Licence](images/licence.png)

Avant d’aller plus loin → analyser l’impact des modèles de licences (propriétaires, open source, OpenCore, SaaS…).

---

### Comparatif des licences

| Modèle | Exemple | Impact Lock-in |
|--------|---------|----------------|
| 🔒 **Propriétaire** | Windows, VMware | Très fort |
| 🐧 **Open Source** | Linux, K8s | Faible à modéré |
| ⚖️ **OpenCore** | Elastic, GitLab | Modéré à fort |
| 🎁 **Freemium** | MongoDB, Redis | Variable |
| ☁️ **SaaS** | Salesforce, GWS | Très fort |
| 💼 **Commercial OSS** | RHEL | Modéré |
| 🔀 **Licence duale** | MySQL, Qt | Variable |

---

> *Source :* German & Hassan (2009), *A Survey on Open Source Licensing Models and Their Implications*.  
> [Lien](https://ieeexplore.ieee.org/document/4803679)

---

## 💶 Viabilité économique

Avant tout engagement, vérifier :  
- solidité du modèle économique,  
- pérennité du fournisseur,  
- risques de rupture de service, hausses soudaines, ou abandon produit.

---

## Focus : Open Source vs OpenCore / Licences duales

### Historique  
- **Open Source** : années 80-90, mouvement du libre, OSI (1998).  
- **OpenCore** : années 2000, équilibre ouverture / revenus.  

---

### Différences clés

| Critère | Open Source pur | OpenCore / Dual |
|---------|----------------|-----------------|
| 🔓 Code source | Ouvert complet | Noyau ouvert + modules fermés |
| 💰 Éco modèle | Services/support | Fonctions avancées payantes |
| 🔧 Flexibilité | Très forte | Limitée |
| ⚠️ Risques | Dépend communauté | Verrouillage partiel |
| 👥 Communauté | Forte | Mixte |

---

## 🌐 L’écosystème CNCF

Créée en 2015 par la Linux Foundation après la libération de **Kubernetes**.  
Objectifs : standardiser, innover et promouvoir le **cloud-native**.

---

### Exemples

| Catégorie | Open Source pur | OpenCore |
|-----------|----------------|----------|
| Orchestration | Kubernetes | OpenShift |
| Base de données | Vitess | MongoDB |

---

## Retours d’expérience (Forrester, 2022)

### OpenCore :  
+ Réduction risques (41%)  
+ Efficacité (39%)  
+ Transition cloud (33%)  

### Open Source :  
+ Réduction coûts (45%)  
+ Pas de licences (41%)  
+ Code complet (40%)  
+ Communauté (40%)  

⚠️ Mais besoin d’accompagnement externe (sécurité, migration, expertise).

---

## Comparatif des plateformes Cloud (CaaS/PaaS)

![CaaS](images/caas.png)

_Tableau complet conservé tel quel_  

---

## Comparatif des plateformes Cloud (IaaS)

![IaaS](images/iaas.png)

_Tableau complet conservé tel quel_  

---

# ✅ Conclusion

- Le vendor lock-in est **inévitable mais maîtrisable**  
- La vigilance porte sur :  
  - licences,  
  - modèle économique,  
  - gouvernance,  
  - compétences internes.  

---

# 🙋 Q&A

![Questions](images/questions.png)


