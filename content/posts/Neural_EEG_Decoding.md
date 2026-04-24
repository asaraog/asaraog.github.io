---
weight: 3
title: Neural EEG Decoding
date: 2026-03-24T00:09:00-06:00
draft: false
projects: neuroimaging
featuredImage: /images/eeg_task1_flow.png
featuredImagePreview: /images/eeg_task1_flow_preview.png
---
## Neural EEG Decoding of Smell with a CNN-LSTM

Masters of Science in Data Science Thesis

School of Professional Studies, Northwestern University

**Abstract**

Although olfaction (sense of smell) and related structural abnormalities in the brain’s olfactory bulbs are among the first observed symptoms correlated with Alzheimer’s disease, the functional relationship between olfaction and regions of the brain is poorly understood. Understanding olfactory regions of interest is significant for radiologists in differentiating between olfactory symptoms caused by neurodegenerative diseases or other prevalent reasons such as aging.

Neural decoding, or the recognition of useful patterns in brain activity, can provide an unprecedented insight into our sensory experiences such as sight, sound, and smell. In the area of visual decoding, advances in machine learning with nonlinear methods using artificial neural networks have had superior results when compared to linear methods. This work applies a stacked convolutional neural network and long short-term memory (CNN-LSTM) architecture to electroencephalography (EEG) recordings to decode odor identity from the nonlinear spatiotemporal dynamics of brain activity.

Working with the publicly available Kato et al. (2022) EEG dataset of odorants recorded via 64-channel BioSemi, I demonstrate that the CNN-LSTM model achieves 60% accuracy on a positive–negative smell or citrus (Cit) versus cyclohexanone (Cyc) binary classification task, compared to 54% reported for the cross-subject ridge-regression analysis over the matched post-odor window—an increase in accuracy of 6 percentage points. Occlusion-based interpretability analyses reveal that the late-window (>1.0 s post-stimulus) temporal dynamics contribute most to discriminability, consistent with the original paper’s findings. Spatial occlusion topomaps uncover distinct electrode-importance profiles for the two odorants.

Supplementary code and data are available on GitHub at [asaraog/msdsthesis](https://github.com/asaraog/msdsthesis).

## References

Kato, Mugihiko, Mitsuaki Okutsu, Hiroyuki Kanaya, Kohei Adachi, Kenichi Tomeoka, and Mariko Osaka. 2022. “Spatiotemporal Dynamics of Odor Representations in the Human Brain Revealed by EEG Decoding.” *Proceedings of the National Academy of Sciences* 119 (21): e2114966119. https://doi.org/10.1073/pnas.2114966119.
