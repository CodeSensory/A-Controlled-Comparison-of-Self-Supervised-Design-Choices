# A Controlled Comparison of Self-Supervised Design Choices with Limited Labels for Colon H&E Classification: NCT-CRC Training and CRC-VAL External Validation

Jaemin Hwang^a^, Meen Hye Lee^b^

^a^ Department of Computer Science, Kangwon National University, 150, Namwon-ro, Heungeop-myeon, Wonju-si, Gangwon-do, 26403, Rep. of KOREA  
^b^ Department of Nursing, Kangwon National University, 150, Namwon-ro, Heungeop-myeon, Wonju-si, Gangwon-do, 26403, Rep. of KOREA

Corresponding author: Jaemin Hwang, codesensory@gmail.com  
Co-author: Meen Hye Lee, leemh00@kangwon.ac.kr

## Abstract

### Background and Objectives

Patch-level classification of colorectal hematoxylin and eosin (H&E) histology is limited by the cost of expert labels and by color and stain shift between sites. We asked whether self-supervised pretraining followed by limited-label fine-tuning transfers to an external cohort, whether scheduled augmentation outperforms plain self-supervised learning when labels are scarce, and whether scheduling color emphasis adds a color-specific gain. We compare design choices under a fixed protocol rather than propose a new method.

### Methods

A ResNet-18 encoder was pretrained for 40 epochs with a SimCLR-style contrastive objective on NCT-CRC-HE-100K-NONORM and fine-tuned with 10%, 25%, or 100% of the training labels. Seven settings varied pretraining, augmentation schedule, color content of the schedule, fixed color emphasis, ImageNet initialization, and test-time intensity rescaling, each with three seeds (63 runs). Checkpoints were selected on a held-out NCT validation split only, and nine-class accuracy and macro-F1 were reported on the external CRC-VAL-HE-7K set. Seeds were summarized as mean ± population standard deviation, and paired differences were compared with the minimum detectable effect (α = 0.05, 80% power) without formal significance claims.

### Results

Nine-class accuracy and macro-F1 were the external metrics. Scheduled settings outperformed training from scratch at every label fraction and outperformed plain self-supervised learning at 10% and 25% labels (10%: accuracy 0.562 vs. 0.321, macro-F1 0.482 vs. 0.291; 25%, color-free schedule: accuracy 0.594 vs. 0.282). The color schedule and a matched color-free schedule differed by 0.026 in accuracy at 10% labels, and the color-free schedule was higher at 25%, so a color-specific gain was not supported. Color emphasis applied throughout pretraining was not beneficial at any fraction. Mean accuracy of the color schedule stayed near 0.56 as labels increased. ImageNet initialization exceeded the color schedule at 10% and 25% labels (0.674 and 0.604). Test-time rescaling gave the highest accuracy (0.717–0.828) but changes the evaluation input.

### Conclusions

Under this protocol, external accuracy depended more on initialization and the evaluation pipeline than on color scheduling. Scheduled augmentation is useful when labels are scarce, but color scheduling should not be presented as a color-specific remedy. Held-out validation accuracy did not predict external accuracy.
