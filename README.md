# PatternMind 324111

**Team Members:**  
Giacomo Durante
Igor Pistilli
Francesco Saviotti

---

## 1. Introduction

This project studies **visual concept organization** in the PatternMind dataset (25,557 images across 233 categories). Rather than maximizing classification accuracy, our goal is to analyze **structure in visual feature space**, uncovering clusters, relationships, and macro-level visual themes.

Our pipeline:
1. Train a custom CNN to extract 256-dimensional embeddings  
2. Reduce dimensionality with PCA  
3. Discover macro-categories using hierarchical clustering  
4. Evaluate K-Means clustering at multiple granularities  

Supervised classifiers are used as baselines to contextualize representation quality.

---

## 2. Dataset Overview

The dataset exhibits strong class imbalance and wide visual diversity.

![Class distribution](images/class_distribution.png)

Random samples illustrate intra-class variability and inter-class overlap.

![Sample images](images/sample_images.png)

---

## 3. Feature Learning and Visualization

A custom CNN was trained from scratch to learn 256-dimensional visual embeddings. Despite modest classification accuracy, the learned features capture meaningful visual similarity.

A 2D PCA projection shows partial separation of related categories (e.g., aircraft, birds), with substantial overlap expected in fine-grained settings.

![PCA projection](images/pca_2d.png)

---

## 4. Hierarchical Clustering

Hierarchical clustering on category centroids reveals coherent **macro-categories** driven by visual similarity rather than predefined semantics.

![Hierarchical clustering](images/hierarchical_clustering.png)

Some clusters align with intuitive visual concepts (e.g., space objects, organic forms), while others highlight the CNN’s reliance on appearance over semantics.

---

## 5. Supervised Classification

To assess feature quality, several classifiers were trained on CNN embeddings. Logistic Regression with regularization performed best, outperforming more complex models.

![Classifier comparison](images/classifier_comparison.png)

This indicates that the CNN already performs the necessary non-linear transformations, making simple classifiers more effective.

---

## 6. K-Means Clustering Evaluation

K-Means clustering was evaluated against both fine-grained and macro-category labels. Results show reasonable performance for coarse organization but poor recovery of detailed categories.

![K-Means evaluation](images/kmeans_evaluation.png)

Unsupervised clustering captures broad structure but struggles with fine-grained distinctions.

---

## 7. Qualitative Nearest-Neighbor Analysis

Nearest-neighbor retrieval provides qualitative insight into the learned feature space. Queries often retrieve visually similar but semantically different images, illustrating both strengths and limitations of CNN embeddings.

![Nearest neighbors](images/nearest_neighbors.png)

---

## 8. Conclusions

This project demonstrates that **CNN features combined with hierarchical clustering can effectively organize large image collections without exhaustive labeling**. While fine-grained classification remains challenging, meaningful macro-level structure emerges clearly. Simple supervised models outperform more complex alternatives, and unsupervised methods are most useful for coarse organization.

**Future work** should focus on transfer learning and multimodal embeddings to improve feature separability and semantic alignment.
