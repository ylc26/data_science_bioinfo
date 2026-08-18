# Fragmentation des populations — simulation et analyse de données

Projet de bio-informatique étudiant l’effet de la taille et de la fragmentation d’une population sur sa dynamique génétique. Des simulations évolutives sont produites avec SLiM, puis analysées dans un notebook Python avec Pandas, Matplotlib et SciPy.

## Problématique

Une population fragmentée en petits groupes est davantage exposée à la dérive génétique et à l’accumulation de mutations délétères. Le projet compare cinq configurations sur 2 000 générations afin d’étudier la fitness, la charge génétique et le risque d’extinction.

## Scénarios étudiés

| Scénario | Structure initiale | Migration |
|---|---:|---:|
| A | 1 population de 10 000 individus | Non |
| B | 1 population de 1 000 individus | Non |
| C | 2 sous-populations de 500 individus | Non |
| D | 5 sous-populations de 200 individus | Non |
| E | 10 sous-populations de 100 individus | Oui, taux de 1 % |

Chaque archive fournie contient 100 répétitions de simulation.

## Indicateurs analysés

- taille moyenne de la population ;
- fitness moyenne et variabilité ;
- mutations délétères et bénéfiques ;
- charge génétique nette ;
- taux d’extinction ;
- tendance de la fitness à long terme.

## Structure du dépôt

```text
.
├── data/
│   └── scenarios/                         # Résultats SLiM compressés, scénarios A à E
├── docs/
│   └── rapport_projet_bioinformatique.pdf # Rapport universitaire
├── notebooks/
│   └── analysis_fragmentation_population.ipynb
├── simulation/
│   └── fragmentation_population.slim     # Modèle évolutif SLiM
├── .gitignore
├── requirements.txt
└── README.md
```

## Installation de l’environnement Python

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter notebook notebooks/analysis_fragmentation_population.ipynb
```

Sous Windows, activez l’environnement avec `.venv\\Scripts\\activate`.

Le notebook détecte automatiquement les données lorsque Jupyter est lancé depuis la racine du dépôt ou depuis `notebooks/`.

## Relancer une simulation SLiM

Après installation de SLiM, l’exemple suivant lance la première répétition du scénario A et écrit le CSV dans le dossier courant :

```bash
slim -d scenario='"A"' -d rep=1 simulation/fragmentation_population.slim
```

Le paramètre `outdir` peut être fourni pour choisir un autre dossier de sortie.

## Principaux résultats observés

- le scénario A conserve la fitness moyenne la plus élevée ;
- les populations très fragmentées accumulent davantage de mutations délétères ;
- le scénario D présente le compromis le plus défavorable ;
- la migration du scénario E atténue une partie des effets de la fragmentation sans les supprimer.

Ces résultats proviennent d’un modèle simplifié et ne constituent pas une prédiction biologique réelle.

## Contexte

Projet collectif réalisé en Licence 3 Informatique, option bio-informatique, à l’Université Paris-Saclay durant l’année universitaire 2025-2026.
