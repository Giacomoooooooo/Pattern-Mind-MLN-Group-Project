# PatternMind 324111

**Team Members:**  
name · name · name

---

## 1. Introduction

This project studies **visual concept organization** in the PatternMind dataset (25,557 images across 233 categories). Rather than maximizing classification accuracy, our goal is to analyze **structure in visual feature space**, uncovering clusters, relationships, and macro-level visual themes.

Our pipeline:
1. Train a custom CNN to extract 256-D embeddings  
2. Reduce dimensionality with PCA  
3. Discover macro-categories using hierarchical clustering  
4. Evaluate K-Means clustering at multiple granularities  

Supervised classifiers are used as baselines to contextualize representation quality.

---

## 2. Dataset Overview

The dataset contains strong class imbalance and wide visual diversity.

![Class distribution](figures/class_distribution.png)

Random samples illustrate intra-class variability and inter-class overlap.

![Sample images](figures/sample_images.png)

---

## 3. Feature Learning and Visualization

A custom CNN was trained from scratch to learn 256-dimensional visual embeddings. Despite modest accuracy, the learned features capture meaningful visual similarity.

A 2D PCA projection shows partial separation of related categories (e.g., aircraft, birds), with substantial overlap expected in fine-grained settings.

![PCA projection](figures/pca_2d.png)

---

## 4. Hierarchical Clustering

Hierarchical clustering on category centroids reveals coherent **macro-categories** driven by visual similarity rather than semantics.

![Hierarchical clustering](figures/hierarchical_clustering.png)

Some clusters align with intuitive concepts (e.g., space objects, organic forms), while others expose appearance-driven grouping.

---

## 5. Supervised Classification

To assess feature quality, several classifiers were trained on CNN embeddings. Logistic Regression with regularization performed best, outperforming more complex models.

![Classifier comparison](figures/classifier_comparison.png)

This suggests the CNN already performs the necessary non-linear transformations.

---

## 6. K-Means Clustering Evaluation

K-Means clustering was evaluated against both fine-grained and macro-category labels. Results show good performance for coarse organization but poor recovery of detailed classes.

![K-Means evaluation](figures/kmeans_evaluation.png)

Unsupervised clustering captures broad structure but struggles with fine distinctions.

---

## 7. Qualitative Nearest-Neighbor Analysis

Nearest-neighbor retrieval highlights how embeddings capture visual similarity. Queries often retrieve visually related but semantically distinct images, illustrating both strengths and limitations.

![Nearest neighbors](figures/nearest_neighbors.png)

---

## 8. Conclusions

CNN features combined with hierarchical clustering can effectively organize large image collections without exhaustive labeling. While fine-grained classification remains challenging, macro-level structure emerges clearly. Simple classifiers perform best, and unsupervised methods are most effective at coarse organization.

**Future work** should focus on transfer learning and multimodal embeddings to improve feature separability and semantic alignment.
