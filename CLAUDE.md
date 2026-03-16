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

## Graphiques Plotly — Style professionnel obligatoire

Référence : *Storytelling with Data* (Cole Nussbaumer Knaflic).

### Template à utiliser

Toujours commencer un notebook par cette cellule d'initialisation :

```python
import plotly.graph_objects as go
import plotly.io as pio

PALETTE = ["#0072B2", "#E69F00", "#009E73", "#CC79A7", "#D55E00", "#56B4E9", "#F0E442"]

pio.templates["formation"] = go.layout.Template(
    layout=go.Layout(
        font=dict(family="Inter, Arial, sans-serif", size=13, color="#333333"),
        title=dict(font=dict(size=18, color="#1a1a1a"), x=0.0, xanchor="left"),
        plot_bgcolor="white",
        paper_bgcolor="white",
        colorway=PALETTE,
        xaxis=dict(showgrid=False, showline=True, linewidth=1, linecolor="#333333", ticks="outside", zeroline=False),
        yaxis=dict(showgrid=True, gridwidth=0.5, gridcolor="#E8E8E8", showline=False, zeroline=False, ticks=""),
        legend=dict(orientation="h", yanchor="bottom", y=1.02, xanchor="left", x=0, borderwidth=0),
        margin=dict(l=60, r=30, t=80, b=50),
        hovermode="x unified",
    ),
)
pio.templates.default = "formation"
```

### Règles de style

- Fond blanc, pas de bordures ni d'ombres
- Gridlines Y uniquement, très légères (#E8E8E8), pas de gridlines X
- Palette Okabe-Ito (colorblind-safe) : jamais les couleurs par défaut de Plotly
- Titre à gauche, actif ("La consommation a baissé de 15%") pas générique ("Données")
- Légende horizontale au-dessus du graphique, sans cadre
- Labels directement sur les barres (`text_auto=True`, `textposition='outside'`)
- Axes en français avec unités
- Taille minimum : `width=800, height=500`
- Toujours `fig.show()` ET `fig.write_html("output/nom.html")`

### Règles par type de graphique

- **Barres** : trier par valeur (sauf ordre naturel), toujours partir de zéro, horizontal si noms longs
- **Lignes** : max 4-5 séries, au-delà tout en gris sauf la série clé
- **Scatter** : opacité 0.6-0.7, ligne de tendance en gris
- **Sunburst** : max 3 niveaux, cacher les labels trop petits

### Erreurs à ne jamais faire

- Camembert (pie chart) → barres
- Effets 3D → jamais
- Double axe Y → deux graphiques séparés
- Rouge et vert ensemble → daltonisme
- Trop de données dans un graphique → un graphique = un message
