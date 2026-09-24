# Data Science Fundamentals Assignment

This is the assignment repo for the Data Science course at Dlytica Academy. It covers the my first assignment related to
basics of Git/GitHub, NumPy, and pandas.

## Repo structure

```
.
├── README.md
├── requirements.txt
├── answers/
|   |── 01_git_theory.md     # part A - Basic Git(A1-A15)
│   ├── 02\_numpy.py         # Part B — NumPy (B1–B10)
│   └── 03\_pandas.ipynb     # Part C — pandas (C1–C12)
├── data/
│   ├── generate\_data.py    # Generates the dirty dataset used in Part C
│   └── scores\_raw.csv      # Generated dataset (seeded, reproducible)
└── outputs/
    └── summary.csv         # Exported from 03\_pandas.ipynb (C12a)
```

Part A (Git) is answered as written explanations rather than code, so it isn't a file here.

## Installation

```bash
python3 -m venv venv
source venv/bin/activate   # On Windows: venv\\Scripts\\activate

pip install -r requirements.txt
```

## To regenerate the dataset

```bash
cd data
python generate\_data.py
```

This uses a fixed random seed, so it reproduces the exact same dirty data every time
(24 inconsistent city spellings collapsing to 6, 6 duplicate rows, 4 missing `marks`,
10 missing `attendance\_percent`, and 2 impossible `marks` values above 100).

## To run the assignment files

```bash
jupyter notebook answers/02\_numpy.ipynb
jupyter notebook answers/03\_pandas.ipynb
```

