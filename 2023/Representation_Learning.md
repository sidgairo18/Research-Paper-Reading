# Representation Learning

## Matroyshka Representation Learning (NeurIPS 2022)

**Condensed Summary**: Rigid fixed-capacity representations can be either over or under-accomodating to the task at hand. Matroyshka Representation Learning encodes information at different granularities and allows a single embedding to adapt to the computational constraints of the downstream tasks. With no additional cost during inference and deployment. Improvements: (1) 14x smaller embedding size for ImageNet-1K classification with same accuracy, (2) upto 14x real-world speed-ups for large-scale image retrieval on ImageNet-1K and 4K, and (3) upto 2% accuracy improvements for long-tail few-shot classification.

### Notes

Learned representations are useful in real-world ML systems. Deployment of such representations has two steps: (1) an expensive but constant-cost forward pass to compute the reprsentation, and (2) using the representation for downstream applications. The 2nd step can be very expensive than the 1st step as representation dimensionality increases, dataset size (N) increases and label space (L) increases.

MRL learns representations of varying capacities within the same high-dimensional vector through explicit optimization of O(log(d)) lower-dimensional vectors in a nested fashion (which gives the name Matryoshka like the Russian doll). Advantage: MRL can be adapted to any existing representation pipeline and is easily extended to many standard tasks in computer vision and natural language processing).

MRL can be adapted across modalities like vision, vision + language, language, and to web-scale data.

#### Matryoshka Representation Learning (Sec 3)

For $d \in N$, consider a set $M \subset [d]$ of representation sizes. For a datapoint *x* in the input domain *X*, the goal is to learn a *d*-dimensional representation vector $z \in R^{d}$. 
