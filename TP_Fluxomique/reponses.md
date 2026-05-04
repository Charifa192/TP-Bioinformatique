# Réponses — TP Fluxomique

---

## Tutoriel — Valeurs de référence (WT aérobie)

| Réaction | Nom | Valeur |
|----------|-----|--------|
| GLCpts | Transport glucose | 10.0 |
| PFK | Phosphofructokinase | 7.48 |
| CS | Citrate synthase | 6.01 |
| ATPS4r | ATP synthase | 45.5 |

> **Interprétation :** GLCpts = 10.0 est la borne par défaut du glucose. PFK = 7.48 signifie que ~75% du glucose passe par la glycolyse, les ~25% restants vont vers la PPP. CS = 6.01 représente la porte d'entrée du cycle de Krebs. ATPS4r = 45.5 est le flux le plus élevé de la carte — la respiration produit massivement de l'ATP (18× plus que la fermentation).

> **Taux de croissance WT :** 0.874 h⁻¹ → temps de doublement = ln(2) ÷ 0.874 ≈ **48 minutes** en conditions optimales.

---

## Mission 1 — Bilan carbone

### Flux d'échange relevés

| Réaction | Molécule | Valeur (mmol/gDW/h) |
|----------|----------|----------------------|
| EX_glc_e | Glucose | −10.0 (consommé) |
| EX_o2_e | O₂ | −21.8 (consommé) |
| EX_co2_e | CO₂ | +22.8 (produit) |
| EX_ac_e | Acétate | 0.00 |
| EX_etoh_e | Éthanol | 0.00 |

### Q1.1 — L'acétate et l'éthanol sont-ils produits en aérobie ?

**Non**, EX_ac_e = 0.00 et EX_etoh_e = 0.00. Aucun sous-produit de fermentation n'est sécrété.

Cela signifie que le métabolisme est **très efficace** en conditions aérobies optimales : tout le carbone du glucose va soit vers la **respiration** (CO₂ = énergie), soit vers la **biomasse** (nouvelles cellules). Il n'y a aucun gaspillage. C'est la situation idéale pour un bioréacteur.

### Q1.2 — Bilan carbone

```
Carbone entrant     = 10 × 6 = 60 mmol C/h
Carbone en CO₂      = 22.8 × 1 = 22.8 mmol C/h  → brûlé par la respiration pour l'ATP
Carbone en biomasse = 60 − 22.8 = 37.2 mmol C/h  → incorporé dans protéines, ADN, membranes

Répartition :
  → ~38% énergie (CO₂)
  → ~62% biomasse
```

C'est un rendement élevé. En comparaison, les cellules cancéreuses gaspillent souvent >80% du glucose en lactate (effet Warburg).

---

## Mission 2 — Aérobie vs Anaérobie (Knockout EX_o2_e)

### Tableau comparatif

| Paramètre | Avant (aérobie) | Après KO O₂ (anaérobie) |
|-----------|----------------|--------------------------|
| Croissance (h⁻¹) | 0.874 | ~0.21 |
| Éthanol (EX_etoh_e) | 0.00 | ~16 mmol/h |
| Acétate (EX_ac_e) | 0.00 | ~8 mmol/h |
| ATPS4r | 45.5 | 0 |

### Q2.1 — Chute de croissance en %

```
Perte = (0.874 − 0.21) ÷ 0.874 × 100 ≈ 76%
```

Sans respiration, la cellule produit beaucoup moins d'ATP → elle croît beaucoup plus lentement.

### Q2.2 — Nouveaux produits de fermentation

**Éthanol** (~16 mmol/h) et **acétate** (~8 mmol/h) apparaissent — ils étaient à 0 en aérobie.

La cellule les produit pour **régénérer le NAD⁺** nécessaire à la glycolyse, puisque la chaîne respiratoire est bloquée sans O₂. L'ATP synthase (ATPS4r) tombe à **0**, confirmant que la respiration est totalement arrêtée. C'est l'**overflow métabolique**.

### Q2.3 — Conséquence et recommandation (point de vue ingénieur)

**Conséquence :** la production chute de ~76%, l'éthanol et l'acétate s'accumulent et peuvent **inhiber** les cellules, aggravant le problème.

**Recommandation :** installer un **système de secours d'aération**, surveiller l'O₂ dissous en continu avec un capteur, et déclencher une alarme automatique si le niveau descend sous un seuil critique.

---

## Mission 3 — Gènes essentiels & Cibles thérapeutiques

### Tableau des knockouts

| Réaction | Voie | Croissance après KO | Essentielle ? |
|----------|------|---------------------|---------------|
| PFK | Glycolyse | Réduite mais positive | Non (dispensable) |
| CS | TCA | Réduite | Non (dispensable) |
| G6PDH2r | PPP | Peu affectée | Non (dispensable) |
| ATPS4r | ATP synthase | ~0.2 (quasi-nulle) | Quasi-essentielle |
| PYK | Pyruvate kinase | Réduite mais positive | Non (dispensable) |

### Q3.1 — Classification et explication biologique

- **PFK** (glycolyse) : **dispensable** — le glucose est rerouté vers la PPP, qui le renvoie ensuite dans la glycolyse en aval de PFK. La cellule « contourne » l'obstacle.
- **CS** (TCA) : **dispensable** — la glycolyse seule peut générer de l'ATP, moins efficacement.
- **G6PDH2r** (PPP) : **dispensable** — les précurseurs fournis par la PPP peuvent être obtenus par d'autres voies.
- **ATPS4r** (ATP synthase) : **quasi-essentielle** — la croissance chute très fortement (~0.2). Sans elle, la cellule bascule en fermentation, beaucoup moins rentable.
- **PYK** (pyruvate kinase) : **dispensable** — le pyruvate peut être produit par d'autres réactions (PPS, ou via le PEP directement).

### Q3.2 — Cibles thérapeutiques en oncologie

**ATPS4r** est la cible la plus évidente — bloquer l'ATP synthase priverait la cellule de sa principale source d'énergie.

En oncologie, les enzymes de la **glycolyse** (PFK, PYK) sont intensément étudiées car les cellules cancéreuses en dépendent fortement (**effet Warburg**). Des inhibiteurs de PFK et de la lactate déshydrogénase sont actuellement en essais cliniques.

---

## Mission 4 — Produire de l'éthanol

### Tableau comparatif des objectifs FBA

| Paramètre | Max. croissance | Max. éthanol |
|-----------|----------------|--------------|
| Éthanol produit | 0.00 | ~20 mmol/h |
| Biomasse | 0.874 | 0 |
| Flux TCA (CS) | 6.01 | 0 |

### Q4.1 — Dilemme croissance vs production

La biomasse tombe à **0**. Tout le carbone va vers l'éthanol (~20 mmol/h). Le TCA est aussi à 0 (pas besoin du cycle de Krebs pour fermenter).

C'est le **dilemme fondamental croissance vs production** : en industrie, on résout cela avec une stratégie en **deux phases** :
- **Phase 1** : croissance rapide (multiplier les cellules)
- **Phase 2** : induction de la production (rediriger le carbone vers le produit)

C'est le principe du **fed-batch**.

---

## Mission 5 — Diagnostic du Lot B-2024-47

### Q5.1 — Taux de croissance avec O₂ réduit (Lower Bound EX_o2_e = −10)

```
Croissance ≈ 0.65 h⁻¹
Perte = (0.874 − 0.65) ÷ 0.874 × 100 ≈ 26%
```

C'est cohérent avec les 30% de baisse observés sur le lot B-2024-47.

### Q5.2 — Sous-produits indésirables

Oui, de l'**acétate** apparaît. C'est l'**overflow métabolique** : avec seulement la moitié de l'O₂, la chaîne respiratoire ne peut pas traiter tout le NADH produit. Le carbone excédentaire est dévié vers l'acétate = du **carbone gaspillé**.

### Q5.3 — Rapport de diagnostic Lot B-2024-47

**1. Observation :** rendement du lot B-2024-47 inférieur de ~30% aux lots de référence.

**2. Cause probable :** défaillance du compresseur d'air, réduisant l'apport en O₂ d'environ 50%.

**3. Mécanisme :** la limitation en O₂ provoque un overflow métabolique. La chaîne respiratoire sature et le carbone excédentaire est dévié vers la production d'acétate, qui gaspille du substrat et peut inhiber la croissance cellulaire.

**4. Recommandation :**
- (a) Vérifier et réparer le compresseur immédiatement.
- (b) Installer un capteur d'O₂ dissous avec alarme automatique (seuil : 30% de saturation).
- (c) Ajouter un capteur d'acétate en ligne pour détecter l'overflow précocement.
- (d) Prévoir un compresseur de secours.

---

## Synthèse — Compétences acquises

| Mission | Compétence | Concept clé |
|---------|-----------|-------------|
| Tutoriel | Naviguer dans un flux map | Réactions, métabolites, flux |
| M1 | Bilan carbone | Conservation de la masse |
| M2 | Aérobie vs anaérobie | Respiration vs fermentation, overflow |
| M3 | Gènes essentiels | Knockouts, cibles thérapeutiques |
| M4 | Optimiser la production | Dilemme croissance/production, fed-batch |
| M5 | Diagnostic industriel | Overflow, rapport qualité |
