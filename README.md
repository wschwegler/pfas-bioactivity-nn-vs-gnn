# Comparing a Neural Network and a Graph Neural Network for Predicting PFAS Bioactivity

**Author:** Wilson Schwegler  
**Advisor:** Justin Li, Department Chair, Computer Science, Occidental College  
**Affiliation:** Occidental College (Senior Comprehensive Project)  
**Paper:** *Comparing a Neural Network and a Graph Neural Network for Predicting PFAS Bioactivity*

## Project Overview

Per- and polyfluoroalkyl substances (PFAS) are widely used industrial chemicals known for their environmental persistence and potential health risks. Identifying bioactive PFAS compounds is a critical step in prioritizing regulatory action and guiding safer material design, but experimental screening is costly and time-intensive.

This project investigates whether explicitly modeling molecular structure using a **Graph Neural Network (GNN)** provides meaningful advantages over a traditional **feed-forward Neural Network (NN)** when predicting PFAS bioactivity. Rather than focusing on a single headline metric, this work emphasizes how **model performance depends on evaluation priorities**, particularly the trade-off between precision and recall under severe class imbalance.

---

## Research Questions

This project is guided by the following questions:

- When is a fingerprint-based neural network sufficient for predicting PFAS bioactivity?
- Under what conditions does a graph-based model that encodes molecular structure outperform a traditional NN?
- How do conclusions change when evaluation prioritizes recall over precision, as is common in chemical screening tasks?
- Can differences in model performance be explained by underlying structure–property relationships in the data?

---

## Methods Summary

The models were trained and evaluated on a PFAS bioactivity dataset originally constructed by Cheng and Ng, consisting of over 62,000 molecules evaluated across 26 bioassays.

Two modeling approaches were compared:

- **Neural Network (NN):**  
  A feed-forward neural network trained on fixed-length Morgan fingerprints generated from SMILES strings. This approach treats molecules as high-dimensional vectors and does not explicitly encode molecular topology.

- **Graph Neural Network (GNN):**  
  A graph-based model built on an equivariant message-passing architecture (NequIP), where atoms are represented as nodes and bonds as edges. This formulation allows the model to directly leverage molecular structure and spatial relationships.

Severe class imbalance was addressed through class weighting. Model evaluation focused on **F-β scores** to explicitly control the relative importance of precision versus recall.

---

## Evaluation Philosophy

Standard metrics such as accuracy and F1-score can be misleading in highly imbalanced bioactivity datasets, where predicting most compounds as inactive yields deceptively strong performance.

To better reflect the goals of chemical screening, this project evaluates models across multiple **β values** in the F-β metric:

- Lower β values emphasize precision and penalize false positives.
- Higher β values emphasize recall and penalize false negatives.

This framing allows model selection to be aligned with downstream risk tolerance rather than a single aggregate score.

---

## Key Findings

- The **Neural Network** performs better when precision is prioritized, reflecting a tendency to conservatively predict inactivity.
- The **Graph Neural Network** consistently outperforms the NN in recall-heavy regimes, identifying a larger fraction of bioactive compounds.
- Dimensionality reduction via PCA reveals that GNN advantages are strongest for bioassays exhibiting clear structure–property clustering, suggesting that explicit structural modeling is most beneficial when such relationships exist.

Overall, the results indicate that neither model is universally superior; instead, **model choice should be driven by the intended application and evaluation priorities**.

---

## Repository Structure

