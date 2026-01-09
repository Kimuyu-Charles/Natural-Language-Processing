# Natural Language Processing for Company & Industry Text Data

## Overview

This project applies **Natural Language Processing (NLP)** techniques to
company and industry text data. Starting from structured inputs (company
metadata, industry classifications and descriptions), it:

- cleans and normalises textual fields,
- converts text into numerical features (e.g. bag-of-words / TF-IDF style),
- explores term usage and similarity across companies and industries,
- and produces text-based features that can be fed into screening, clustering
  or risk-scoring models.

It is designed to sit on top of a **clean fundamentals layer**, such as the
one prepared in the _Company-Industry-Data-Pipeline project.

---

## Business Context & Motivation

For an **equity or credit analyst**, a lot of useful information is locked in
unstructured text:

- business descriptions,
- industry summaries,
- thematic tags,
- management commentary.

This project shows how to turn that text into **structured signals** that can
augment traditional quantitative metrics. It is aimed at questions like:

1. How similar are companies within and across industries based on their
   descriptions?
2. Can we create simple **text features** that help with screening or grouping
   companies?
3. How do company and industry descriptions differ in terms of key terms and
   themes?

---

## Data

The notebook expects company and industry data with at least:

- a **company identifier** (e.g. `company_id` or `company_name`),
- an **industry / sector identifier**,
- one or more **text fields**, for example:
  - `company_description`
  - `industry_description`

In practice, this can be:

- the same `companies_information.csv` and `industries_information.csv` used in
  the _Data Collection, Wrangling & Feature Engineering_ project,  
- or any similar files with company/industry text fields.

Place the CSV files under a `data/` directory (or adjust the paths in the
notebook).

---

## Approach

The main notebook (e.g. `Natural Language Processing.ipynb`) follows a
standard NLP workflow:

1. **Load & Inspect Data**
   - Load company and industry CSVs.
   - Inspect the distribution and completeness of text fields.

2. **Text Cleaning & Normalisation**
   - Lowercasing, trimming whitespace.
   - Removing punctuation, digits and other non-alphabetic characters.
   - Optionally remove stopwords and very short tokens.

3. **Tokenisation & Lemmas/Stems**
   - Split text into tokens.
   - Optionally apply stemming or lemmatisation to reduce words to a base form.

4. **Vectorisation (Text → Numbers)**
   - Build a **bag-of-words** and/or **TF-IDF** style representation of text.
   - Inspect common terms by industry or sector.
   - Optionally limit to a vocabulary size or minimum document frequency.

5. **Exploratory Analysis**
   - Compare term distributions across industries.
   - Compute simple similarity scores between companies based on their text
     vectors.
   - Identify clusters or outliers in the text space.

6. **Feature Export**
   - Combine text-derived features with structured company/industry data.
   - Output a feature table that can be used in downstream models or dashboards.

---

## Repository Structure

> This is the structure the project is moving towards. Your current layout may
> be a subset of this.

- `notebooks/`
  - `Natural Language Processing.ipynb` – main notebook with cleaning,
    feature extraction and analysis.
- `data/`
  - `companies_information.csv` – company-level data with descriptions.
  - `industries_information.csv` – industry-level data with descriptions.
- `README.md` – project overview and usage instructions.

---

## Tools & Libraries

- **Language:** Python 3.x  
- **Core libraries (typical):**
  - `pandas` – loading and joining structured data
  - `numpy` – numerical helpers
  - `matplotlib` / `seaborn` – visualisation
  - `scikit-learn` – vectorisation (e.g. `CountVectorizer`, `TfidfVectorizer`)
  - (Optionally) `nltk` or `spaCy` – tokenisation, stopwords, lemmatisation

- **Environment:** Jupyter Notebook

---

## How to Run

1. Clone the repository:

   ```bash
   git clone https://github.com/Kimuyu-Charles/Natural-Language-Processing.git
   cd Natural-Language-Processing
