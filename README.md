# Assignment-Learning-Probability-Density-Functions-using-data-only

This project focuses on learning an unknown probability density function (PDF) of a transformed random variable using only data samples. A Generative Adversarial Network (GAN) is employed to model the distribution without assuming any parametric form.

---

## Dataset Description

The India Air Quality Dataset is used in this study.  
The NO₂ (Nitrogen Dioxide) concentration feature is selected.

Preprocessing steps:
- Removal of missing values
- Conversion to numerical format

---

## Transformation Parameters

The transformation applied to each sample is:

z = x + aᵣ sin(bᵣ x)

For roll number **102303792**:

aᵣ = 1.5  
bᵣ = 0.9  

Final equation:

z = x + 1.5 sin(0.9x)

---


## GAN Architecture Description

The GAN consists of two neural networks trained in an adversarial manner:

### Generator (G)

The generator learns to map random noise samples drawn from a standard normal distribution N(0,1) into synthetic samples of the transformed variable z. Its purpose is to approximate the unknown data distribution.

Architecture:
- Input layer: 1-dimensional noise vector  
- Hidden layer 1: 32 neurons with ReLU activation  
- Hidden layer 2: 32 neurons with ReLU activation  
- Output layer: 1 neuron producing generated z value  

---

### Discriminator (D)

The discriminator acts as a binary classifier that distinguishes between real transformed samples and generator-produced samples. It guides the generator to produce realistic outputs.

Architecture:
- Input layer: 1-dimensional z value  
- Hidden layer 1: 32 neurons with ReLU activation  
- Hidden layer 2: 32 neurons with ReLU activation  
- Output layer: 1 neuron with Sigmoid activation (real/fake probability)

---

## Training Configuration

| Parameter | Value |
|----------|------|
| Epochs | 400 |
| Batch size | 128 |
| Optimizer | Adam |
| Loss Function | Binary Cross Entropy |

---

## PDF Estimation

After training the GAN:

- 8000 synthetic samples were generated  
- Kernel Density Estimation (KDE) was applied  
- A smooth probability density function p(z) was obtained  

The resulting PDF plot is available in:
results/gan_pdf.png

---

## Observations

### Mode Coverage

The generator successfully captures the dominant probability peak of the transformed distribution. Major high-density regions are well represented, indicating effective learning of the real data structure.

---

### Training Stability

The adversarial training process remained stable throughout the epochs. No significant oscillations or mode collapse were observed due to normalization and low-dimensional input structure.

---

### Quality of Generated Distribution

The KDE-estimated PDF from GAN samples closely matches the empirical distribution of the transformed data. Both sharp density peaks and long-tailed behavior are well approximated, demonstrating high-quality sample generation.

---

## Conclusion

This project demonstrates that Generative Adversarial Networks can accurately learn unknown probability density functions using only data samples. Without any parametric assumptions, the GAN effectively models complex nonlinear distributions with stable training and realistic outputs.

---

## Author

Mehak  
Roll Number: 102303792

COE,TIET


