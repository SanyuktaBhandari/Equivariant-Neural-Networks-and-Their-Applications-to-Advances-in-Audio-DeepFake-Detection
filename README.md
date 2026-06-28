# Equivariant-Neural-Networks-and-Their-Applications-to-Advances-in-Audio-DeepFake-Detection

**Author:** Sanyukta Bhandari  
**Affiliation:** St. Xavier's College (Autonomous), Kolkata | TCG CREST  
**Supervisors:** Dr. Md. Sahidullah (TCG CREST) | Dr. Surupa Chakraborty Roy (St. Xavier's College)  
**Status:** MSc Dissertation — Under consideration for publication

---

## Overview

This repository contains the implementation and evaluation of group equivariant 
and steerable convolutional neural networks for audio deepfake detection, 
benchmarked on the ASVspoof 2019 Logical Access dataset.

The central question: can encoding rotational symmetry directly into a neural 
network architecture provide more robust deepfake detection than data augmentation 
alone — and with fewer parameters?

---

## Models

Four architectures are implemented and compared:

| Model | Architecture | Parameters | Augmentation |
|-------|-------------|------------|--------------|
| Model 1 | Vanilla CNN (Conv1D) | 657,282 | None |
| Model 2 | Vanilla CNN (Conv1D) | 657,282 | Tempo perturbation |
| Model 3 | C4-Equivariant G-CNN (e2cnn) | 565,218 | None |
| Model 4 | SO(2) Steerable CNN (escnn) | 42,164 | None |

---

## Key Results

- **Model 3 (G-CNN)** achieves **8.05% EER** on clean audio, outperforming 
both CNN baselines with 14% fewer parameters and no augmentation
- Under time-stretched audio at 0.77× (unseen during training), Model 3 
achieves **7.82% EER** — improving on its own clean performance
- Friedman test (χ²F ≈ 12.09, p ≈ 0.007) confirms statistically significant 
differences across all four models
- Model 4 (SO(2)) does not converge at this training scale, establishing 
a clear direction for future work

---

## Evaluation Conditions

Seven conditions evaluated across all four models:

| Condition | Description |
|-----------|-------------|
| (i) Original | Clean audio at 1.0× |
| (ii-a) Slow | Time-stretched to 0.77× |
| (ii-b) Fast | Time-compressed to 1.36× |
| (iii-a) Noise 20dB | Additive white Gaussian noise, mild |
| (iii-b) Noise 10dB | Additive white Gaussian noise, moderate |
| (iii-c) Noise 0dB | Additive white Gaussian noise, severe |
| (iv) Audio Dropout | Simulated packet loss |

---

## Dataset

This work uses the **ASVspoof 2019 Logical Access** dataset.  
Access must be requested through the official ASVspoof website:  
🔗 https://www.asvspoof.org/

The dataset and all derived files (including pre-generated mel spectrograms) 
are not included in this repository due to the dataset's access control 
requirements. Once you have obtained access, mel spectrograms can be 
generated using the preprocessing pipeline described in the notebook.

---

## Repository Structure

```text
audio-deepfake-equivariant/
├── README.md
├── LICENSE
├── requirements.txt
└── notebooks/
│   └── main_experiment.ipynb
```

---

## Dependencies

See `requirements.txt`. Key libraries:
- PyTorch + torchaudio
- e2cnn (C4 equivariant networks)
- escnn (SO(2) steerable networks)
- librosa (audio processing)

Install with:
```bash
pip install -r requirements.txt
```

---

## License

This work is licensed under **CC BY-NC-ND 4.0**.  
You may view and reference this work with attribution.  
Commercial use, modification, and redistribution are not permitted.  
The dataset and all derived data are excluded from this repository.  
See [LICENSE](LICENSE) for full details.

---

## Citation

If you reference this work, please cite:

Bhandari, S. (2025). Equivariant Neural Networks and Their Applications
to Advances in Audio Deepfake Detection. 
St. Xavier's College (Autonomous), Kolkata.

---

*This repository is associated with ongoing work that may be submitted 
for publication. Please do not reproduce or build upon this work 
without explicit written permission from the author.*
