
README.txt
==========

1. Description of Each Directory and File
-----------------------------------------

/quran-qa-2023-main/
│
├── README.md                         # Original documentation
├── requirements.txt                  # Required Python packages
├── LICENSE                           # Project license
├── HowToCite_TaskA.bib               # Citation reference for Task A
├── HowToCite_TaskB.bib               # Citation reference for Task B
│
├── .idea/                            # PyCharm configuration (ignore)
│
├── Task-A/
│   ├── README.md
│   ├── code/
│   │   ├── BM25_baseline.ipynb       # BM25 baseline for passage retrieval
│   │   ├── QQA23_TaskA_eval.py       # Official evaluation script
│   │   ├── QQA23_TaskA_submission_checker.py  # Submission format checker
│   │   ├── bi_encoder.ipynb          # ✅ Custom Bi-Encoder model (created by us)
│   │   ├── filtered_run.txt
│   │   └── .ipynb_checkpoints/
│   └── .gitkeep
│
└── Task-B/
    ├── arabert_baseline.ipynb        # ✅ Custom AraBERT-based QA model (created by us)
    └── ...                           # Other MRC-related scripts


2. Code Attribution
--------------------

✅ Our Custom Code:

- Task-A/code/bi_encoder.ipynb: Passage retrieval using SentenceTransformer with AraBERT.
- Task-B/arabert_baseline.ipynb: Machine Reading Comprehension (MRC) model based on AraBERT.

🧩 Provided by Organizers:

- BM25_baseline.ipynb
- QQA23_TaskA_eval.py
- QQA23_TaskA_submission_checker.py
- Dataset files


3. User Manual – Step-by-Step Instructions
------------------------------------------

Task A: Passage Retrieval
--------------------------

Step 1: Install dependencies

    pip install -r requirements.txt
    # or manually:
    pip install pandas tqdm sentence-transformers

Step 2: Prepare input files

Place these in a `data/` folder:
- QQA23_TaskA_ayatec_v1.2_dev.tsv
- QQA23_TaskA_QPC_v1.1.tsv
- QQA23_TaskA_ayatec_v1.2_qrels_dev.gold

Step 3: Run the bi-encoder

Open and execute:
    Task-A/code/bi_encoder.ipynb

This notebook:
- Embeds questions/passages
- Computes similarities
- Outputs a ranked run file

Step 4: Evaluate the run

    python Task-A/code/QQA23_TaskA_eval.py         --qrels QQA23_TaskA_ayatec_v1.2_qrels_dev.gold         --run path/to/run.txt


Task B: Machine Reading Comprehension (AraBERT)
------------------------------------------------

Step 1: Install required packages

    pip install transformers datasets evaluate

Step 2: Run the notebook

Open and execute:
    Task-B/arabert_baseline.ipynb

This notebook:
- Loads MRC dataset and fine-tunes AraBERT
- Predicts answers
- Reports pAP, F1, and EM

Note: Using GPU is recommended for training.
