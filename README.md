# Antimicrobial activity prediction against Neisseria gonorrhoeae from public ChEMBL data

Bioactivity prediction of growth inhibition in Neisseria gonorrhoeae, trained as binary (active/inactive) classifiers from publicly available data in ChEMBL. Independent models are trained on multiple bioactivity datasets, corresponding to dose-response (MIC) assays. A ranking score is provided for each model alongside a combined consensus score.

This model was incorporated on 2026-05-19.Last packaged on 2026-05-21.

## Information
### Identifiers
- **Ersilia Identifier:** `eos5qya`
- **Slug:** `antimicrobial-activity-ngonorrhoeae`

### Domain
- **Task:** `Annotation`
- **Subtask:** `Activity prediction`
- **Biomedical Area:** `Gonorrhea`
- **Target Organism:** `Neisseria gonorrhoeae`
- **Tags:** `Gram-negative bacteria`, `Antimicrobial activity`, `ChEMBL`

### Input
- **Input:** `Compound`
- **Input Dimension:** `1`

### Output
- **Output Dimension:** `6`
- **Output Consistency:** `Fixed`
- **Interpretation:** Probability of antimicrobial activity against Neisseria gonorrhoeae from 5 ChEMBL-trained sub-models, plus a quality-weighted consensus score.

Below are the **Output Columns** of the model:
| Name | Type | Direction | Description |
|------|------|-----------|-------------|
| consensus_score | float | high | Tanh-transformed quality-weighted consensus probability across the 5 sub-models. Recommended threshold: 0.887. |
| merged_mic_decoys | float | high | Probability from sub-model trained on MIC measurements merged across 7 ChEMBL assays (cutoff 10 uM; n=570 incl. decoys). Recommended threshold: 0.861. |
| general_dose_response_decoys | float | high | Probability from sub-model trained on dose-response measurements aggregated across 3 ChEMBL assays (n=2620). Recommended threshold: 0.841. |
| general_mic90_decoys | float | high | Probability from sub-model trained on MIC90 measurements aggregated across 12 ChEMBL assays (cutoff 10 uM; n=560 incl. decoys). Recommended threshold: 0.87. |
| general_mic50_decoys | float | high | Probability from sub-model trained on MIC50 measurements aggregated across 8 ChEMBL assays (cutoff 10 uM; n=530 incl. decoys). Recommended threshold: 0.873. |
| general_mic | float | high | Probability from sub-model trained on MIC measurements aggregated across 338 ChEMBL assays (cutoff 10 uM; n=446). Recommended threshold: 0.493. |


### Source and Deployment
- **Source:** `Local`
- **Source Type:** `Internal`
- **DockerHub**: [https://hub.docker.com/r/ersiliaos/eos5qya](https://hub.docker.com/r/ersiliaos/eos5qya)
- **Docker Architecture:** `AMD64`, `ARM64`
- **S3 Storage**: [https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos5qya.zip](https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos5qya.zip)

### Resource Consumption
- **Model Size (Mb):** `30`
- **Environment Size (Mb):** `1888`
- **Image Size (Mb):** `2068.95`

**Computational Performance (seconds):**
- 10 inputs: `35.95`
- 100 inputs: `31.53`
- 10000 inputs: `564.31`

### References
- **Source Code**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication Type:** `Other`
- **Publication Year:** `2026`
- **Ersilia Contributor:** [arnaucoma24](https://github.com/arnaucoma24)

### License
This package is licensed under a [GPL-3.0](https://github.com/ersilia-os/ersilia/blob/master/LICENSE) license. The model contained within this package is licensed under a [GPL-3.0-or-later](LICENSE) license.

**Notice**: Ersilia grants access to models _as is_, directly from the original authors, please refer to the original code repository and/or publication if you use the model in your research.


## Use
To use this model locally, you need to have the [Ersilia CLI](https://github.com/ersilia-os/ersilia) installed.
The model can be **fetched** using the following command:
```bash
# fetch model from the Ersilia Model Hub
ersilia fetch eos5qya
```
Then, you can **serve**, **run** and **close** the model as follows:
```bash
# serve the model
ersilia serve eos5qya
# generate an example file
ersilia example -n 3 -f my_input.csv
# run the model
ersilia run -i my_input.csv -o my_output.csv
# close the model
ersilia close
```

## About Ersilia
The [Ersilia Open Source Initiative](https://ersilia.io) is a tech non-profit organization fueling sustainable research in the Global South.
Please [cite](https://github.com/ersilia-os/ersilia/blob/master/CITATION.cff) the Ersilia Model Hub if you've found this model to be useful. Always [let us know](https://github.com/ersilia-os/ersilia/issues) if you experience any issues while trying to run it.
If you want to contribute to our mission, consider [donating](https://www.ersilia.io/donate) to Ersilia!
