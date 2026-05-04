# TP2 — Ingénierie Métabolique

> Module : Omics 1  Bioinformatique  
> Outil principal : [Escher](https://escher.github.io) + FBA (Flux Balance Analysis)  
> Organisme modèle : *Escherichia coli* (modèle `e_coli_core`)  
> Prérequis : TP Fluxomique

---

## 🎯 Objectifs pédagogiques

- Appliquer le cycle **Design-Build-Test-Learn** de l'ingénierie métabolique
- Optimiser une souche pour la **production d'un métabolite d'intérêt** (éthanol, succinate, acétate)
- Comprendre les **knockouts stratégiques** : éliminer les voies concurrentes sans tuer la cellule
- Identifier des **létalités synthétiques** (double knockouts) comme outil en oncologie
- Analyser l'**overflow métabolique** et le seuil critique de glucose
- Relier la simulation FBA au processus industriel de scale-up

---

## 🧰 Outils utilisés

| Outil | Usage |
|-------|-------|
| **Escher** | Visualisation et manipulation de la carte métabolique |
| **FBA** | Simulation des flux après modifications génétiques |
| **Escher FBA — mode knockout** | Suppression de réactions pour simuler des délétions géniques |

---

## 📋 Structure du TP

### Rappels — Valeurs de référence (WT)
- Baseline du métabolisme sauvage en conditions aérobies
- Valeurs de référence pour toutes les comparaisons suivantes

### Mission 1 — Produire un métabolite cible
- Combinaison conditions anaérobies + objectif Maximize
- Stratégie : anaérobie (knockout `EX_o2_e`) + maximiser un export (`EX_etoh_e`, `EX_succ_e`…)

### Mission 2 — Knockouts stratégiques
- Suppression des voies concurrentes (acétate, formate) pour concentrer le flux vers l'éthanol
- Analyse du meilleur compromis **éthanol produit / croissance maintenue**
- Réactions testées : ACKr, PFL, PTAr

### Mission 3 — Double knockout & Létalité synthétique
- Recherche de combinaisons de 2 knockouts simultanés maximisant la perte de croissance
- Concept de **létalité synthétique** : deux voies qui se compensent mutuellement
- Application en oncologie : cibler deux gènes redondants dans les cellules cancéreuses

### Mission 4 — Overflow métabolique & Fed-batch
- Simulation de l'augmentation progressive de l'apport en glucose
- Identification du **seuil d'overflow** (apparition d'acétate)
- Stratégie **fed-batch** pour maintenir le glucose sous le seuil critique

### Mission 5 — Conception libre de souche
- Choix d'un produit biotechnologique (biocarburant, bioplastique, molécule d'intérêt)
- Application du cycle **Design-Build-Test-Learn**
- Rédaction d'un mini-rapport de conception incluant rendement carbone et faisabilité industrielle

---

## 💡 Concepts clés

- **Ingénierie métabolique** : modification rationnelle du métabolisme cellulaire pour optimiser la production d'un composé d'intérêt.
- **Knockout stratégique** : suppression d'une voie *concurrente* (qui détourne le carbone du produit cible) sans couper une voie *essentielle* à la survie.
- **Létalité synthétique** : deux gènes non essentiels individuellement, mais dont la double délétion est létale. Exemple : PFK + G6PDH2r bloquent toute entrée du glucose.
- **Overflow métabolique** : au-delà d'un seuil de glucose, la chaîne respiratoire sature et le carbone excédentaire déborde vers l'acétate → carbone gaspillé.
- **Fed-batch** : stratégie industrielle qui alimente le bioréacteur en glucose à débit contrôlé pour rester sous le seuil d'overflow.
- **¹³C-MFA** : méthode de mesure des flux réels in vivo grâce à des traceurs isotopiques — permet de valider les prédictions FBA.
- **Cycle Design-Build-Test-Learn** : cadre de l'ingénierie des systèmes biologiques. La FBA correspond à l'étape "Design".

---

##  Fichiers

```
TP2_Ingenierie_Metabolique/
├── README.md          # Ce fichier
└── reponses.md        # Mes réponses aux questions du TP
```
