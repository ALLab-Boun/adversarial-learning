# Do Adversarially Robust ImageNet Models Transfer Better?

| Date | Authors | Keywords | Paper Link | GitHub Link | Work Status |
|:----:|:-------:|:--------:|:----------:|:-----------:|:-----------:|
| 16 Jul 2020 | Hadi Salman et al. (MadryLab) | Transfer Learning | <https://arxiv.org/pdf/2007.08489.pdf> | <https://github.com/Microsoft/robust-models-transfer> | In Review |

### TL;DR

Robust models albeit having lower natural accuracy yield transfer learning gains over their naturally trained counterparts.

### Highlights

- **A large experimental study** consisting of 12 different dataset, different ResNet models in classification task.
    - Holds for both full-network fine tuning and penultimate classifier (fixed-feature) tuning.
- **4.2.** claims width of the network does not help in standard models (by using a prior work) but helps in robust models. Experiments show gains in both so claim is not fully analyzed.
- **4.3** shows that if you downscale other datasets to 32 x 32 (CIFAR size) and then upscale to ImageNet size, you get a similar epsilon-transfer curves in all dataset similar to CIFAR.
    - This is to prove that optimal epsilon choice for transfer learning depends on the granularity of the data which is approximated **very roughly** by the dimension.

### Objection

The most promising datasets which show robustness help transfer learning are CIFARs (others are rather marginal results). This is more evident in fixed-feature mode. However, CIFARs significantly upscaled (32x32 → 224x224 or 256x256). This creates a dataset with very high internal correlation which is unnatural to training domain of ImageNet.

1. The substantial improvement in CIFARs might be related with this upscaling issue rather than robust training. The stark difference between fixed-feature mode tuning in CIFARs point in this direction. Clearly, standard ImageNet feature extractor is not capable of dealing with such dataset (success rates are well below state-of-the art). We see that when we do full-network tuning the gap significantly lessens but still higher compared to other datasets (especially in CIFAR100). The authors need to delve into this issue and clarify upscaling effect on the experimentations.

2. In robust training setting and specifically in PGD adversarial training, network sees more samples due to the nature of the process. This alone might lead to improved feature representations. In this work, the authors didn't deal with specific effect of **robust** training which is having special adversarial samples rather than having larger training set. To more clearly study whether adversarial samples help transfer learning at all, one must experiment **standard training with random noise** and compare with robust training. In this current form, it is more likely to believe that increased training set resulted in marginal improvements provided by the paper.

3. Prior work claims robust training yield improved feature representations. How much of this "improvement" comes from enriching training set with more samples or from specific nature of the adversarial samples is unclear. This paper present us with marginal improvements in transfer learning when initial model is trained robustly. The cause of the improvement is not clear and can not be firmly tied to the nature of robust training (specifically to the usage of specifically crafted adversarial samples). However, the paper seems to demonstrate that if we have to upscale a dataset substantially robust training is useful in transfer learning (albeit we still be have to careful to distill the effect of increased training set and validate this claim).