# Avian Sensitivity to Urban Dynamics — Delhi (2014–2025)

Spatio-temporal ML analysis decoding how Delhi's winter smog affects bird 
migration phenology across 11 migratory seasons (Oct–Mar).

## The problem

Delhi sits on the Central Asian Flyway — peak migration coincides exactly 
with peak winter smog. Do birds avoid pollution, or does migratory instinct 
override avoidance? And when sightings drop during smog, is that biology 
or just visibility bias?

## What we did

**Data:** 11 years of eBird citizen science checklists fused with daily 
PM2.5, PM10, AQI, and meteorological data for Delhi NCT.

**PCA:** Resolved multicollinearity in 7 weather features into 4 orthogonal 
components — isolating a "Smog Factor" (PC1: PM2.5 + PM10 + AQI) 
from a "Warmth Factor" (PC2: temperature), retaining 95% of variance.

**Model Arena:** Benchmarked Logistic Regression, Random Forest, Gradient 
Boosting, and a 3-layer Keras DNN on presence/absence prediction.

**Visibility control:** Used resident species (Black Kite) as a control group 
to distinguish visibility bias from true biological avoidance in migrant species.

**Visualization:** Built a pixel-perfect spatio-temporal animation engine 
(300×300 grid, ~90,000 predictions/frame) with cubic spline interpolation 
and GeoPandas inverted masking, strictly confined to Delhi's administrative boundary.

## Key results

| Model | ROC-AUC |
|-------|---------|
| Deep Neural Network (Keras) | 0.48 |
| **Random Forest (class-weighted)** | **0.97** |

Random Forest outperforms the DNN — ensemble methods handle tabular 
ecological data better than neural networks.

**Ecological Trap (Northern Shoveler):** Sightings rose 14.8% during peak 
smog. Migratory instinct overrides pollution avoidance — waterfowl are 
forced into toxic ancestral wetlands with no alternative wintering grounds.

## How to run

**Option A — Colab (recommended)**  
[Open notebook directly](https://colab.research.google.com/drive/1kLmQbsht4EvpCTRN_549i0zYePaT_5g7?usp=sharing)

**Option B — Local**

```bash
pip install -r requirements.txt
jupyter notebook avian_ecology.ipynb
```

Data is fetched via the eBird API and OpenAQ. See notebook for API setup.

## Repo structure

avian-urban-ecology-delhi/
├── avian_ecology.ipynb    # Full pipeline: data → PCA → models → maps
├── requirements.txt
└── README.md

