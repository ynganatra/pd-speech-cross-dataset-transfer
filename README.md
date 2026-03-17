# Limited Target Data Calibration Improves Cross-Dataset Transfer for Parkinson’s Disease Detection from Speech

This project studies how speech-based Parkinson’s Disease (PD) detection models perform within the same dataset and under cross-dataset zero-shot testing. It also evaluates whether adding a small, speaker-balanced portion of the target dataset during training improves cross-dataset performance, and whether fairness (difference in false negative rates between comparable demographic groups) depends on both training data and decision threshold selection.

The study focuses on cross-dataset transfer under combined differences in language, recording conditions, and speech tasks, rather than isolating any single factor.

This is a research project. The models and analyses are not intended for clinical diagnosis or medical decision-making. For any real-world use, additional clinical validation and ethical oversight would be required.

## What is in this repository
- `Yash_Ganatra_PD_Voice_Project.ipynb`  
  Main notebook with preprocessing, training, evaluation, and analysis steps.
- `model_card.md`  
  Plain-language summary of the model design and evaluation.
- `.gitignore`  
  Prevents large or private files (such as datasets and generated outputs) from being uploaded.

## Datasets (not included here)
This repository does not include speech datasets or audio clips. All data handling is kept separate from the code.

The study uses public datasets, including:
- NeuroVoz (Castilian Spanish)
- EWA-DB (Slovak)
- IPVS (Italian)
- MDVR-KCL (English-UK)
- English-US sustained “Ah” sounds

Please follow each dataset’s license and access requirements.

## Model setup (high level)
- Audio is standardized (mono, 16 kHz) and split by speaker to avoid overlap across train, validation, and test sets.
- A pretrained Wav2Vec2 model is used as a frozen feature extractor.
- Two small task-specific classification heads are trained:
  - one for sustained vowel clips  
  - one for read or continuous speech tasks

## How to run
1. Open `Yash_Ganatra_PD_Voice_Project.ipynb` in Google Colab or Jupyter.
2. Run the cells in sequence.
3. Update any local or Google Drive paths as needed.

Tip: Clear all outputs before uploading new notebook versions to keep file size manageable.

## Citation
If you use this code for a paper or school project, please cite the associated manuscript and the dataset sources referenced there.

## Related publication
This repository supports the research described in:

“Limited Target-Domain Calibration Improves Cross-Dataset Transfer for Speech-Based Parkinson’s Disease Detection”

The paper presents the experimental design and results. This repository provides the supporting code and analysis notebook.

## Contact
For questions, please open a GitHub Issue.

## License
This project is released under the MIT License. See the LICENSE file for details.
