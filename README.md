# GenerativeAI-StyleTransfer
# CycleGAN with Enhanced Detail Capture

This repository contains the implementation of a CycleGAN for image-to-image translation tasks, enhanced with a deeper generator network for improved detail capture. The project demonstrates significant improvements in translation quality through the integration of a pretrained model and a deeper generator network.

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Pretrained Model](#pretrained-model)
- [Deeper Generator Network](#deeper-generator-network)
- [Improvements](#improvements)
- [Installation](#installation)
- [Usage](#usage)
- [Evaluation](#evaluation)
- [Results](#results)
- [Contributing](#contributing)

## Introduction
CycleGANs are powerful models for unpaired image-to-image translation tasks. This project aims to enhance the standard CycleGAN architecture by integrating a pretrained model and a deeper generator network, leading to improved image quality and finer details in the generated images.

## Features
- CycleGAN architecture for unpaired image-to-image translation
- Integration of a pretrained model
- Deeper generator network for better detail capture
- Significant improvement in MiFID score

## Pretrained Model
We use a pretrained CycleGAN model that is not overly complex, trained to get a general idea of the images. This pretrained model helps in achieving faster convergence and better initial results.

## Deeper Generator Network
To further enhance the detail capture capability of the generator, we introduced a deeper generator network. The deeper network includes additional layers and a more complex architecture, allowing it to learn finer details in the images while keeping the discriminator unchanged.

## Improvements
The integration of the pretrained model with the deeper generator network led to a significant reduction in the MiFID score from 202.53147 to 93.81957, indicating a substantial improvement in the quality of the generated images.
![Sample Results](im_o.png)

## Installation
To get started, clone the repository and install the required dependencies:

```bash
git clone https://github.com/yourusername/cyclegan-enhanced.git
cd cyclegan-enhanced
pip install -r requirements.txt
```

## Usage
1. Prepare your dataset and organize it into appropriate folders.
2. Train the CycleGAN model:
3. Evaluate the model:
4. Explore the extra approches i used or create new ones. 


## Evaluation
### MiFID
Submissions are evaluated on MiFID (Memorization-informed Fréchet Inception Distance), which is a modification of Fréchet Inception Distance (FID). The smaller the MiFID, the better your generated images are.

### What is FID?
FID, along with Inception Score (IS), are both commonly used in recent publications as the standard for evaluation methods of GANs. In FID, the Inception network is used to extract features from an intermediate layer. The data distribution for these features is modeled using a multivariate Gaussian distribution with mean μ and covariance Σ. The FID between the real images and generated images is computed as:

\[ \text{FID} = \left\| \mu_{\text{real}} - \mu_{\text{gen}} \right\|^2 + \text{Tr} \left( \Sigma_{\text{real}} + \Sigma_{\text{gen}} - 2 \left( \Sigma_{\text{real}} \Sigma_{\text{gen}} \right)^{\frac{1}{2}} \right) \]

### What is MiFID (Memorization-informed FID)?
MiFID takes training sample memorization into account in addition to FID. The memorization distance is defined as the minimum cosine distance of all training samples in the feature space, averaged across all user-generated image samples. This distance is thresholded and assigned to 1.0 if the distance exceeds a pre-defined epsilon. 

In mathematical form:

\[ d_{\text{mem}} = \frac{1}{N} \sum_{i=1}^N \min_{j} \left( 1 - \cos(\mathbf{z}_{\text{gen}_i}, \mathbf{z}_{\text{real}_j}) \right) \]

where \( \mathbf{z}_{\text{gen}} \) and \( \mathbf{z}_{\text{real}} \) represent the generated/real images in feature space. The final MiFID is:

\[ \text{MiFID} = \text{FID} \cdot \max(1, d_{\text{mem}} - \epsilon) \]

## Results
Here are some sample results comparing the original CycleGAN and the enhanced CycleGAN with the deeper generator network.

![Sample Results](results/sample_results.png)

## Contributing
Contributions are welcome! Please submit a pull request or open an issue to discuss any changes.
