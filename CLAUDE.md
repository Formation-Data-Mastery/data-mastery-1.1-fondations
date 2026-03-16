# Projet Data Mastery — Module 1

## Environnement

- Python géré avec uv (pas pip)
- Pour installer un package : `uv add nom-du-package`
- Pour exécuter du code : `uv run python script.py`
- IMPORTANT : ne JAMAIS utiliser pip, python -m pip, ou .venv/bin/pip — toujours uv add

## Contexte

Ce projet est un module de formation pour débutants. Les données sont dans `data/`. Les résultats (graphiques, notebooks) vont dans `output/` ou `notebooks/`.

## Conventions

- Commentaires en français, simples et pédagogiques
- Un concept par cellule dans les notebooks Jupyter
- Toujours expliquer le "pourquoi" avant le "comment"

## Graphiques

- Utiliser plotly express (`import plotly.express as px`) pour tous les graphiques
- Style par défaut de Plotly (pas de template personnalisé)
- Titre et axes en français
- Toujours `fig.show()` ET `fig.write_html("output/nom.html")`
