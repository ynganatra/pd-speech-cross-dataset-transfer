# Model Card (Research Only): Speech-Based PD Classifier (Model Family)

## What this is
This project does not define a single “final” model. It evaluates a family of models that share a common design but differ in training setup (monolingual training, cross-dataset zero-shot testing, and limited target-data calibration).

This model card describes the experimental system evaluated in the associated research study.

## Intended use
Research on:
- cross-dataset testing under differences in language, recording conditions, and speech tasks
- how limited target training data affects transfer performance
- fairness analysis using sex-stratified false negative rates (FNR)
- task comparisons (vowel vs read or continuous speech)

Not intended for:
- clinical diagnosis
- real-world medical screening
- treatment decisions, patient advice, or any high-stakes use

## Inputs and outputs
**Input:** short speech clips that have been preprocessed and labeled for research (PD vs healthy control)  
**Output:** a probability score for PD vs healthy control at the clip level

## Model design (simple description)
- A pretrained Wav2Vec2 speech model is used as a frozen feature extractor (backbone weights are not updated during training)
- Two small task-specific classification heads are trained:
  - one head for sustained vowel clips  
  - one head for read or continuous speech clips
- This design allows the model to account for differences across speech tasks

## Data used (not included in this repository)
The study uses public speech datasets collected under different languages, accents, recording conditions, and speech tasks. The datasets are not included in this repository.

## How it is evaluated
Common evaluation steps include:
- AUROC as the primary performance metric
- decision thresholds selected using validation data (for example, Youden J)
- fairness analysis based on differences in false negative rates between female and male speakers
- additional analyses such as target-data inclusion steps, task-head routing checks, and score distribution plots

## Key limitations
- Performance can vary across datasets due to combined differences in language, recording conditions, and speech tasks
- The study does not isolate the individual sources of these differences
- Subgroup metrics can be unstable when subgroup sample sizes are small
- The model was evaluated as part of a single defined modeling pipeline and was not compared with alternative model families or domain adaptation approaches
- This work is research-only and has not been clinically validated

## Safety note
This model family is intended for research use only. Any real-world use would require clinical validation, privacy safeguards, and appropriate ethical oversight.
