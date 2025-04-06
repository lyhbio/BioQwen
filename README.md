# BioQwen

## Citation
If you use this method or code in your research, please cite the following paper:

Yinghong Li#,*, Yudong Yan#, Zhuohao Tong, Yu Wang, Yinqi Yang, Mingze Bai, Dan Pu, Jiazheng Xie, Chuan Liu, Bo Li*, Mingwei Liu, Kunxian Shu*. [Efficient fine-tuning of small-parameter large language models for biomedical bilingual multi-task applications](https://www.sciencedirect.com/science/article/abs/pii/S1568494625003953). Applied Soft Computing. 175:113084 (2025)

**BibTeX:**
```bibtex
@article{Li2025,
  author = {Li, Yinghong and Yan, Yudong and Tong, Zhuohao and Wang, Yu and Yang, Yinqi and Bai, Mingze and Pu, Dan and Xie, Jiazheng and Liu, Chuan and Li, Bo and Liu, Mingwei and Shu, Kunxian},
  title = {Efficient fine-tuning of small-parameter large language models for biomedical bilingual multi-task applications},
  journal = {Applied Soft Computing},
  year = {2025},
  volume = {175},
  pages = {113084},
  month = may,
  doi = {10.1016/j.asoc.2025.113084},
}
```

![Fig. 1](img/1.png)

## Prerequisites

- Python 3.10 or higher
- PyTorch
- bitsandbytes
- flash_atten
- datasets
- transformers
- peft
- trl

Install the required packages using:
```bash
pip install -r requirements.txt
```

## Directory Structure

```
.
├── app/
├── code/
│   ├── img/
│   └── notebook/
│       ├── BioQwen-manuscript.ipynb
│       └── README.md
├── result/
│   ├── ner/
│   │   ├── bc5cdr/
│   │   ├── cmeee/
│   │   └── ncbi/
│   └── qa/
│       ├── cmedqa2/
│       ├── icliniq/
│       └── webmedqa/
├── script/
│   ├── README.md
│   ├── script_stage1.py
│   └── script_stage2.py
├── README.md
└── requirements.txt
```

## Description of Contents

### app/

This directory contains the download link for the BioQwen mobile deployment APK file.

### code/

- **img/**: Contains image files related to the project.
- **notebook/**: Contains Jupyter notebooks for detailed exploration and documentation.
  - `BioQwen-manuscript.ipynb`: Notebook detailing the model training and inference process.
  - `README.md`: Documentation for the notebook.

### result/

- **ner/**: Results and outputs related to Named Entity Recognition tasks.
  - **bc5cdr/**: Results for the BC5CDR dataset.
  - **cmeee/**: Results for the CMEEE dataset.
  - **ncbi/**: Results for the NCBI-DISEASE dataset.
- **qa/**: Results and outputs related to Question Answering tasks.
  - **cmedqa2/**: Results for the cMedQA2 dataset.
  - **icliniq/**: Results for the iCliniq dataset.
  - **webmedqa/**: Results for the WebMedQA dataset.

### script/

- **README.md**: Documentation for the scripts.
- **script_stage1.py**: Script for Stage 1 training extracted from `BioQwen-manuscript.ipynb`.
- **script_stage2.py**: Script for Stage 2 training extracted from `BioQwen-manuscript.ipynb`.

### README.md

This file, providing an overview and instructions for the repository.

### requirements.txt

Here is a file listing all the dependencies required to run the scripts and notebooks in this repository. Please note that there might be some dependencies not listed here. Feel free to open an issue to provide feedback.

## Training

The training is performed in two stages using the scripts provided.

### Stage 1 Training OR Stage 2 Training

1. **Load and Filter Data:**
    - Load datasets from various sources.
    - Filter and preprocess the data.
    - Tokenize the data with language checks.

2. **Model Setup:**
    - Load the pre-trained model and tokenizer.
    - Configure BitsAndBytes for efficient training.
    - Prepare the model for QLoRA/LoRA training.

3. **Training Configuration:**
    - Define training arguments.
    - Create a Trainer instance and start training.

## Running the Training

### Single GPU

To run the training on a single GPU, use the `python` command:

```bash
python script/script_stage1.py
python script/script_stage2.py
```

### Multiple GPUs

To run the training on multiple GPUs, use the `torchrun` command:

```bash
torchrun --nproc_per_node=NUM_GPUS script/script_stage1.py
torchrun --nproc_per_node=NUM_GPUS script/script_stage2.py
```

Replace `NUM_GPUS` with the number of GPUs available on your machine.

## Contact

For any questions or further information, please submit an issue on this repository.
