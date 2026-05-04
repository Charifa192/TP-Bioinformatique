# TP Fluxomique — Analyse des Flux Métaboliques

> Module : Omics 1 — Bioinformatique  
> Outil principal : [Escher](https://escher.github.io) (visualisation de flux) + FBA (Flux Balance Analysis)  
> Organisme modèle : *Escherichia coli* (modèle `e_coli_core`)

---

##  Objectifs pédagogiques

- Comprendre la **Flux Balance Analysis (FBA)** comme outil de simulation du métabolisme
- Lire et interpréter une **flux map** (carte métabolique interactive)
- Analyser les différences entre métabolisme **aérobie et anaérobie**
- Identifier les **gènes essentiels** (knockouts létaux) comme cibles thérapeutiques
- Simuler la **production d'un métabolite d'intérêt** (éthanol)
- Relier les données de simulation à un contexte industriel réel

---

##  Outils utilisés

| Outil | Usage |
|-------|-------|
| **Escher** | Visualisation de la carte métabolique d'*E. coli* |
| **FBA (Flux Balance Analysis)** | Simulation de la distribution des flux à l'état stationnaire |
| Navigateur web | Interface graphique interactive |

---

##  Structure du TP

### Tutoriel — Prise en main d'Escher
- Navigation sur la carte métabolique (glycolyse, TCA, voies annexes)
- Lecture des flux (mmol/gDW/h), identification des métabolites et réactions

### Mission 1 — Bilan carbone
- Vérification de la conservation de la masse (glucose → biomasse + CO₂ + sous-produits)
- Calcul des bilans entrée/sortie de carbone

### Mission 2 — Aérobie vs Anaérobie
- Simulation du passage en conditions anaérobies (knockout `EX_o2_e`)
- Observation de l'**overflow métabolique** (acétate, éthanol, formate)
- Comparaison des taux de croissance et des sous-produits

### Mission 3 — Gènes essentiels & Cibles thérapeutiques
- Knockouts unitaires sur des réactions clés (ATPS4r, PFK, CS…)
- Identification des réactions létales (croissance → 0)
- Lien avec l'**effet Warburg** en oncologie

### Mission 4 — Produire de l'éthanol
- Changement d'objectif FBA : maximiser `EX_etoh_e` au lieu de la biomasse
- Analyse du **dilemme croissance vs production**
- Stratégie industrielle en deux phases (fed-batch)

### Mission 5 — Diagnostic industriel (Lot B-2024-47)
- Simulation d'une aération réduite de moitié (Lower Bound `EX_o2_e` = −10)
- Identification de l'overflow métabolique comme cause de perte de rendement
- Rédaction d'un rapport de diagnostic qualité

---

##  Concepts clés

- **FBA (Flux Balance Analysis)** : méthode d'optimisation qui prédit la distribution des flux métaboliques à l'état stationnaire, sous contrainte de conservation de la masse (bilan de stœchiométrie).
- **Flux map** : représentation graphique du réseau métabolique avec l'épaisseur et la couleur des flèches proportionnelles aux flux.
- **Knockout** : suppression d'une réaction (simulant la délétion du gène correspondant) pour observer l'effet sur la croissance ou la production.
- **Overflow métabolique** : quand la chaîne respiratoire est saturée (manque d'O₂), le carbone excédentaire est dévié vers des sous-produits (acétate, éthanol).
- **Effet Warburg** : les cellules cancéreuses dépendent fortement de la glycolyse même en présence d'oxygène → les enzymes glycolytiques sont des cibles thérapeutiques.

---

##  Fichiers

```
TP_Fluxomique/
├── README.md          # Ce fichier
└── reponses.md        # Mes réponses aux questions du TP
```
