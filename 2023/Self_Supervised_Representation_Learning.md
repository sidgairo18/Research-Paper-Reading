# Self-Supervised Representation Learning Methods for Vision

At a high level, existing solutions (for discriminative methods), typically employ a siamese style setup (with 2 networks) and its variations. Then they propose smart techniques to avoid the model/framework from collapsing into a non-trivial solution.

## SimCLRv1

## SimCLR v2

## MoCov1

This paper presents Momentum Contrast for unsupervised visual representation learning. The key idea is to have a siamese style backbone with an online encoder and a moving-averaged encoder. This is coupled with a dynamic dictionary with a queue and belongs to the contrastive style ssl methods. 
Peformance: With standard ResNet-50 achieves linear probe accuracy (training a linear classifier on top of frozen backbone encoder features) of 60.6% on ImageNet-1M (200 epochs, Batch size=256).

## MoCov2

This paper leverages the improvements from SimCLRv2. It adds an MLP projection head (2 layers: hidden layer 2048-d with ReLU) and additional data augmentation (+ blur augmentation, interestingly stronger color distortion doesn't add much value to the represenation quality) to improve performance. This requires much smaller batch sizes as compared to SimCLR.
**Performance**:  With standard ResNet-50, adding the proposed improvements + cosine learning rate schedule, the method achives linear probe accuracy of 67.5% on ImageNet-1M (when the model is trained for 200 epochs, Batch size=256).

## MoCov3

This paper extends the MoCov2 style framework to Vision Transformers.

## SwAV
This method proposes an optimized variant of deep clustering to learn self-supervised visual representations. This method (as compared to previous works), does not require using a large memory bank or a special momentum network. This work also proposees a new data augmentation strategy - *multi-crop* that uses a mix of views with different resolutions in place of two full-resolution views without increasing the memory or compute requirements.
**Performance**: With standard ResNet-50 the proposed method achieves a top-1 accuracy of 75.3% for linear probe training on ImageNet-1M (when the model is trained for 800 epochs, and Batch Size=4096).
With multi-crop + Batch Size=256 + 200 epochsthe method achives a top-1 accuracy of 72.0%.)

## SimSiam
This work proposes to use a simple siamese network architecture with a predictor MLP, where it shows that the model can learn useful visual representations without supervision, without using any of the following: (i) negative sample pairs, (ii) large batches, (iii) momentum encoders. They show that a stop-gradiant operation is essential to prevent the model from collapsing to a trivial solution.
**Performance**: with standard ResNet-50 the proposed method achieves top-1 accuracy of 71.3% for linear probe training on ImageNet-1M (when the model is trained for 800 epochs, and Batch Size-256).
For 200 epochs it achieves a top-1 accuracy of 70.0%, and with 100 epochs a top-1 accuracy of 68.1%.

## Boostrap your Own Latent (BYOL)
This work introduces a new framework for SSL learning, that also relies on two neural networks (similar to MoCov2) with an online network and a target network. The online network is used to predict the target network representation of the same image under a different augmented view. The target network is updated as a slow-moving average of the online network. A plus of this method is that it doesn't make use of any negative samples, as is typically the case for SimCLR and MoCo. 
**Performance**: with standard ResNet-50, the proposed method achieves a linear probe accuracy of 74.3% on ImageNet-1M (when the model is trained for 1000 epochs, Batch size=4096).
(It can also work with smaller batch sizes ~512 typically with only a small drop in performance.)

## Barlow Twins
This work proposes a new objective function that measures the cross-correlation matrix between the outputs of two identical  networks fed with distorted versions of a sample, and the model is optimized to make the output as close to an identity matrix as possible. This helps naturally avoid collapse. As a result of the objective function, the embedding vectors (output from the model) are similar for the two distorted version of the same sample, and minimizes the redundancy between the components of these vectors at the same time. This is inspired by neuroscientist H. Barlow's *redundancy-reduction principle* when applied to a pair of identical networks.
**Performance**: with standard ResNet-50, the proposed method achieves a linear probe accuracy of 73.2% on ImageNet-1M (when the model is trained for 1000 epochs, and Batch Size=2048).
(In the paper the authors also show that the method can also work with smaller batch sizes ~256 without a great drop in performance.)


## DINOv1

This paper studies the self-supervised learning properties that emerge when training Vision Transformers (ViTs) as compared to standard CNNs (like ResNets etc). This work leverages using student, teacher (where the teacher is an exponentially moving average of the student) distillation framework, along with multi-crop training augmentations and using small-patches for ViTs to learn visual representations in a self-supervised fashion.
**Performance**: With standard ResNet-50 (24M parameters), the method achieves linear probe accuracy of 75.3% on ImageNet-1M, and with ViT-S/8 (21M parameters) a linear probe accuracy of 77.0%.
