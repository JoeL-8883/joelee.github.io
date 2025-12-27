---
layout: page
title: Generating Emotionally Expressive Motion by Fine-Tuning Full-Body Motion Synthesis Models
description:
img: assets/dataset_samples.jpg
importance: 1
category: 2025
related_publications: true
---

This was my final year honours dissertation, supervised by Dr. Edmond Ho at the University of Glasgow.

**Abstract:** Current research on full-body generative motion models primarily focus on improving motion quality and diversity. Much of this research neglects the emotional expression of generated motion despite its importance. In this work, we explore the less-explored domain of emotional motion synthesis. In particular, and in contrast to traditional style transfer approaches, we investigate the impact of fine-tuning text-to-motion models with emotion-focused motion datasets. By fine-tuning state of the art generative motion models, we leverage the model's rich pre-trained knowledge of motion and language, and enhance it to produce emotionally rich motion. To this end, we retarget a previously overlooked emotion-focused motion dataset, the Emotional Body Expression in Daily Actions (Emilya) dataset, and integrate Emilya into the Emotional-T2M dataset to construct the Emilya+EmotionalT2M dataset which is compatible with other motion generation models. To the best of my knowledge, this is the largest emotion-focused motion dataset, and this work is the first to fine-tune full-body motion models using an exclusively emotion-focused motion dataset. Quantitative and qualitative analyses revealed that fine-uning masked motion models was ineffective, whereas fine-tuned motion diffusion models -- particularly those with fewer diffusion steps achieved competitve performance.

**Masked Motion Model**

The Generative Masked Motion Model (MMM) proposed by {% cite pinyoanuntapong2024mmm %}, predicts masked motion sequences in the form of motion and text tokens. A transformer is used to decode tokens in parallel, and a vector quantied variational autoencoder encodes motion and text data. We fine-tune the transformer, which effectively captures spatio-temporal dependencies thanks to its self-attention mechanism.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/MMM.png" title="Generative Masked Motion Model Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    MMM Architecture.
</div>

**Motion Diffusion Model**

We also fine-tuned the Human Motion Diffusion Model (MDM) proposed by {% cite tevet2022human %}. Diffusion demonstrated great success in the image and video generation domain, and has recently been explored in motion generation. Diffuson models have demonstrated strong condiitonally capabilities, and have previously been used to fine-tune motion models. By using fewer denoising steps, on-demand motion generation is possible. 

**Fine-Tuning**

Both models were fine-tuned using the Emotional Body Expression in Daily Actions Database (EMILYA) {% cite fourati2014emilya %} which we re-targeted to fit the SMPL skeletal model used in most motion generation models. Code to retarget EMILYA can be found [here](https://github.com/JoeL-8883/retarget-emilya). This EMILYA dataset was combined with existing emotion focused motion data, creating a sufficiently large dataset for effective fine-tuning.

**Results**

MMM synthesised static motion after fine-tuning. We speculate it could be from codebook collapse after fine-tuning. Unfortunately, I did not have the time to remedy this issue.

MDM successfully generated emotionally expressive motion when prompted accordingly. 
