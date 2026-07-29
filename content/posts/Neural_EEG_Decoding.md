---
title: Neural EEG Decoding
date: 2026-03-24T00:09:00-06:00
draft: false
projects: neuroimaging
featuredImage: /images/eeg_classification_flow.png
featuredImagePreview: /images/eeg_classification_flow_preview.png
---
## Neural EEG Decoding of Smell with Artificial Intelligence

Masters of Science in Data Science Thesis

School of Professional Studies, Northwestern University

**Abstract**

Although olfaction (sense of smell) and related structural abnormalities in the brain’s olfactory bulbs are among the first observed symptoms correlated with Alzheimer’s disease, the functional relationship between olfaction and regions of the brain is poorly understood. Understanding olfactory regions of interest is significant for radiologists in differentiating between olfactory symptoms caused by neurodegenerative diseases or other prevalent reasons such as aging.

Neural decoding, or the recognition of useful patterns in brain activity, can provide an unprecedented insight into our sensory experiences such as sight, sound, and smell. In the area of visual decoding, advances in machine learning with nonlinear methods using artificial neural networks have had superior results when compared to linear methods. This work applies a stacked convolutional neural network and long short-term memory (CNN-LSTM) architecture to electroencephalography (EEG) recordings to decode odor identity from the nonlinear spatiotemporal dynamics of brain activity.

Working with the publicly available Kato et al. (2022) EEG dataset of odorants, I demonstrate that the CNN-LSTM model achieves 59.3% ± 3.0% SD cross-validation accuracy (5-fold) on a positive–negative smell or citrus (Cit) versus cyclohexanone (Cyc) binary classification task. This compares to 54% reported for the cross-subject ridge-regression analysis over the matched post-odor window—an increase in accuracy of approximately 5 percentage points. Occlusion-based interpretability analyses reveal that the late-window (>1.0 s post-stimulus) temporal dynamics contribute most to discriminability, consistent with the original paper’s findings. Spatial occlusion topomaps uncover distinct electrode-importance profiles for the two odorants.

Supplementary code and data are available on GitHub at [asaraog/msdsthesis](https://github.com/asaraog/msdsthesis).

### Confusion matrix

Accuracy hides *where* a model is wrong. This is the pooled confusion matrix across all five folds, each trial predicted by a model that never saw its subject.

<style>
.cm-fig img.cm-dark { display: none; }
[data-theme="dark"] .cm-fig img.cm-light { display: none; }
[data-theme="dark"] .cm-fig img.cm-dark { display: block; }
.cm-fig img { max-width: 100%; height: auto; }
</style>
<div class="cm-fig">
<img class="cm-light" src="/images/eeg_confusion_light.png" alt="Confusion matrix for odor decoding from EEG. Citrus: 381 correct, 239 predicted as cyclohexanone. Cyclohexanone: 356 correct, 267 predicted as citrus. Pooled accuracy 59.3 percent.">
<img class="cm-dark" src="/images/eeg_confusion_dark.png" alt="Confusion matrix for odor decoding from EEG. Citrus: 381 correct, 239 predicted as cyclohexanone. Cyclohexanone: 356 correct, 267 predicted as citrus. Pooled accuracy 59.3 percent.">
</div>

### Precision and recall

| Class | Precision | Recall | F1 |
|---|---:|---:|---:|
| Citrus (Cit) | 0.588 | 0.615 | 0.601 |
| Cyclohexanone (Cyc) | 0.598 | 0.571 | 0.585 |

Per-fold accuracy was 61.9%, 59.0%, 57.9%, 54.9% and 62.2%, a mean of **59.2% ± 2.7%** with ROC AUC **0.617**, against the **54%** cross-subject baseline in Kato et al. (2022) and 50% chance on this balanced set.

The errors are near-symmetric, 239 citrus trials called cyclohexanone against 267 the other way, and precision is near-identical across the classes (0.588 and 0.598). The model is not collapsing onto one odor, which is the usual failure mode for a weak EEG classifier. The margin over chance is modest but every fold clears it.

## References

Kato, Mugihiko, Mitsuaki Okutsu, Hiroyuki Kanaya, Kohei Adachi, Kenichi Tomeoka, and Mariko Osaka. 2022. “Spatiotemporal Dynamics of Odor Representations in the Human Brain Revealed by EEG Decoding.” *Proceedings of the National Academy of Sciences* 119 (21): e2114966119. https://doi.org/10.1073/pnas.2114966119.
