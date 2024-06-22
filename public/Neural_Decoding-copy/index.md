# Neural Decoding of Smell With Generative AI


## Abstract

Olfaction (sense of smell) and related structural abnormalities in the olfactory bulbs are among the first observed symptoms corelated with Alzhiemer’s disease (Esiri and Wilcock 1984; Thomann et al. 2009). The functional relationship between olfaction and the olfactory bulbs is poorly understood (Weiss et al. 2020). In the area of visual decoding, advances in machine learning using  generative adversarial networks (GANs) have provided an unprecedented insight into neural decoding or the mapping of an individual brain’s responses and performance (Seeliger et al. 2018; Van Gerven et al. 2019) when compared to linear models (VanRullen and Reddy 2019). Working on a latent space of reduced dimensions from the neuroimaging data, GANs employ competing (artificial) neural networks – a generator to produce predictions and a discriminator to distinguish the ground truth – to ultimately converge on a model that has learned the mapping between the latent space (a reduced representation of neuroimages) and smell space (identity of odor and pleasantness rating).  It is a form of multi-voxel (3-D pixel) pattern analysis (MVPA).

I propose applying GANs to a publicly available dataset of neuroimages (fMRI) recorded in real-time after exposure to different smells (Weiss et al. 2019). This dataset is ideal for functional mapping as it includes individuals that pass standardized smell testing but inexplicably do not have any apparent olfactory bulbs. The guiding research question will be to explain how individuals without olfactory bulbs can smell. I hypothesize that there are different regions of interest (ROIs) for individuals without apparent olfactory bulbs and that neural decoding for individuals without olfactory bulbs will take more time than for others. Similar to a visual decoding task on gender by others (VanRullen and Reddy 2019), I will arrange the latent space for the neuroimages corresponding to different ROIs (such as occipital, temporal or frontoparietal lobes) and run a binary decoding task (pleasant vs unpleasant) after each odor stimulus. Understanding olfactory regions of interest is significant for radiologists in differentiating between olfactory symptoms caused by neurodegenerative diseases or other prevalent reasons such as aging (Zou et al. 2016).

## References

Esiri, M M, and G K Wilcock. 1984. “The Olfactory Bulbs in Alzheimer’s Disease.” Journal of Neurology, Neurosurgery, and Psychiatry 47 (1): 56–60.

Seeliger, K., U. Güçlü, L. Ambrogioni, Y. Güçlütürk, and M. A. J. van Gerven. 2018. “Generative Adversarial Networks for Reconstructing Natural Images from Brain Activity.” NeuroImage 181 (November):775–85. https://doi.org/10.1016/j.neuroimage.2018.07.043.

Thomann, Philipp A., Vasco Dos Santos, Pablo Toro, Peter Schönknecht, Marco Essig, and Johannes Schröder. 2009. “Reduced Olfactory Bulb and Tract Volume in Early Alzheimer’s Disease—A MRI Study.” Neurobiology of Aging 30 (5): 838–41. https://doi.org/10.1016/j.neurobiolaging.2007.08.001.

Van Gerven, Marcel A. J., Katja Seeliger, Umut Güçlü, and Yağmur Güçlütürk. 2019. “Current Advances in Neural Decoding.” In Explainable AI: Interpreting, Explaining and Visualizing Deep Learning, edited by Wojciech Samek, Grégoire Montavon, Andrea Vedaldi, Lars Kai Hansen, and Klaus-Robert Müller, 11700:379–94. Lecture Notes in Computer Science. Cham: Springer International Publishing. https://doi.org/10.1007/978-3-030-28954-6_21.

VanRullen, Rufin, and Leila Reddy. 2019. “Reconstructing Faces from fMRI Patterns Using Deep Generative Neural Networks.” Communications Biology 2 (1): 193. https://doi.org/10.1038/s42003-019-0438-y.

Weiss, Tali, Timna Soroka, Lior Gorodisky, Sagit Shushan, Kobi Snitz, Reut Weissgross, Edna Furman-Haran, Thijs Dhollander, and Noam Sobel. 2019. “Human Olfaction Without Apparent Olfactory Bulbs.” https://doi.org/10.18112/openneuro.ds002185.v1.1.0.

———. 2020. “Human Olfaction without Apparent Olfactory Bulbs.” Neuron 105 (1): 35-45.e5. https://doi.org/10.1016/j.neuron.2019.10.006.

Zou, Yong-ming, Da Lu, Li-ping Liu, Hui-hong Zhang, and Yu-ying Zhou. 2016. “Olfactory Dysfunction in Alzheimer’s Disease.” Neuropsychiatric Disease and Treatment 12 (April):869–75. https://doi.org/10.2147/NDT.S104886.




---

> Author:   
> URL: //localhost:1313/Neural_Decoding-copy/  

