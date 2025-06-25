
# Étude sur le déploiement CaaS pour ZOR5G

**Créé par** : Taoufik BOUAZZA  
**Dernière modification** : hier, à 3:26 PM

---

## Contexte et Besoin

Plusieurs clients ZOR5G nécessitent de petits CaaS pour fonctionner dans différentes zones avec des chaînes de soutien variées.  
Ces CaaS sont classifiés selon la règle MIRE (cf. Règles de sécurité à appliquer aux clusters Kubernetes - DRAFT - Infras Réseaux - Confluence for Orange).  
Ils ne peuvent pas être mutualisés entre deux chaînes de soutien ou zones de sécurité différentes.

---

## Liste des besoins référencés

| Projet                  | Classification | Chaîne de soutien | Zone ZORG | Nombre d'instances | TOTAL VCPU MASTER | Total VCPU WORKER | Criticité | Contrainte Distribution K8S | Détails                                              |
|-------------------------|------------------|-------------------|------------|---------------------|-------------------|-------------------|-----------|------------------------------|------------------------------------------------------|
| SAS (Identools)         | MIRE             | S.A.S             | BLEU       | 1 Qualif, 1 Preprod, 2 Prod | 32 vCPU          |                   | Haute     | OUI                          | NON                                                  |
| Orchestration (GitOps)   | MIRE             | Orchestration     | ROUGE      | 1 Qualif, 6 Preprod, 12 Prod | Min 72, max 144 VCPU |               | ?         | NON                          | HLD%3A Expression de besoin GitOps pour le CaaS     |
| CICD (Runner)           | MIRE             | CICD              | ROUGE      | ?                   | ?                 |                   | Basse     | ?                            | NON                                                  |
| ESSVT                   | ?                | ?                 | ?          | 1 Preprod           | ?                 |                   | Basse     | NON                          |                                                      |

---

## Scénarios envisagés

| Produit             | Compatibilité VMware | Coût licence annuel | Coût d'industrialisation | Modèle opérationnel | Commentaires                                              |
|---------------------|------------------------|----------------------|--------------------------|---------------------|-----------------------------------------------------------|
| PRODUIT OTC        | NON                    | 800 €/serveur        | N/A                      | Pas de modèle sous VMware |                                                       |
| SUSE               | OUI                    | 600 €/serveur        | 2 ETP pour 6 mois + formation |                     |                                                           |
| OPENSHIFT          | OUI                    | ~1700 / 4 VCPU       | ACM disponible, mutualisation MRF |                     |                                                           |
| OPENSHIFT bare metal | NA                   | 5000 / max 64 cores par node |                      |                     | Note : L'utilisation d'OpenShift VM n'est pas viable en l'état, en raison de limitations de cores par socket. Licences pour OpenShift Virtualisation sont identiques si déployé sur VM ou directement en CaaS. Rancher nécessite uniquement des licences pour la production. RHEL gratuit sur OpenShift. Tarif négocié : 3000 € pour MRF. |

---

## Coûts

### Suse

| Ligne | Description                     | Type             | Prix par serveur | Détails                                              |
|--------|---------------------------------|------------------|------------------|------------------------------------------------------|
| 1      | Suse edge for telco suite      | Baremetal (2 sockets) | 1625 €           |                                                      |
|        |                                 | VM (4 vCPU)      | 400 €            |                                                      |
| 2      | Suse Edge for telco core       | Baremetal        | 525 €            |                                                      |
|        |                                 | VM (4 vCPU)      | 125 €            | En mode VM au-delà de 16 VCPU (prix fixe 4x 4 vCPU)  |

**Vue fonctionnelle** : entre Suse Rancher Prime - Telco Core et Telco Suite - Rancher Suite

**Coût Rancher sur VM** :  
16 VCPU + 36 GB RAM  
**Total** : 16 * 162 € + 600 € (licence) = **3 192 €**

---

### Red Hat (bare metal)

| Description | Coût par cœur | Détails |
|--------------|--------------|---------|
| 16 cœurs    | 312,5 €     | 5000 € / 16 cœurs = 312,5 € par cœur |
| Hors stockage | 78,125 € par cœur | |

| VCPU | Coût |
|-------|-------|
| 16    | 466 € |

---

### VMware

| Contrat | Coût / core / an |
|---------|------------------|
| VVF     | 126 €            |
| VCF     | 162 €            |

---

## Scénarios de déploiement

| Scenario | Description | Coût | Fonctionnalités |
|----------|--------------|-------|-----------------|
| Rancher sur VM VMware | | | |
| OpenShift bare metal avec Virtualisation | | | |
| OpenShift sur VM | | | |
| Libvirt sur OTC (Non retenu) | | | |

---

## Classification MIRE et Mutualisation

| Niveau | Description | Mutualisation autorisée | Commentaires |
|---------|--------------|-------------------------|--------------|
| M       | Cluster suivant recommandations | Mutualisation autorisée | |
| MI      | Cluster suivant recommandations | Mutualisation autorisée | |
| MIR     | Cluster suivant recommandations | Mutualisation autorisée | |
| MIRE    | Mutualisation limitée | Autorisée uniquement entre applications de même chaîne/support | Les outils CICD, GitOps ou d’identité sont de catégorie Élevée. |

---

*Fin de l'étude.*

| Projet                         | Classification | Chaîne de soutien | Zone ZORG | Nombre d'instances             | Bi-site | TOTAL VCPU MASTER | Total VCPU WORKER | Criticité | Détails                     |
|--------------------------------|------------------|-------------------|------------|-------------------------------|---------|-------------------|-------------------|-----------|------------------------------|
| SAS (Outils dont Identools)    | MIRE             | S.A.S             | BLEU       | 1 Qualif, 1 Preprod, 2 Prod   | OUI     | 32 vCPU           |                   | Haute     | À étudier                   |
| Orchestration (GitOps)          | MIRE             | Orchestration     | ROUGE      | 2 Qualif, 6 Preprod, 12 Prod  | OUI     | Min 64, max 124 VCPU |               |           | À étudier                   |
| CICD                          | MIRE             | ?                 | ?          | 1 Preprod                     | ?       | Min 32, Max 64   |                   |           |                              |
| Runner                        | ESSVT            | ?                 | ?          | 1 Preprod                     | ?       | Min 60, Max 100 VCPU |               |           | Étude en cours (BM vs VM)   |
| Outils de test                |                  |                   |            |                               |         |                   |                   |           |                              |

```
