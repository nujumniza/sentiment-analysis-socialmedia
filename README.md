# Social Media Sentiment Analysis: A Comparative Study of Classical Machine Learning and Pretrained Transformer Models

A single, reproducible Google Colab notebook that compares a **classical TF-IDF pipeline** (class-weighted Logistic Regression + Linear SVM) with the **pretrained `cardiffnlp/twitter-roberta-base-sentiment-latest` transformer** on the **Twitter US Airline Sentiment** dataset — one shared held-out test set, identical metrics, zero tuning on test data.

This is a portfolio/educational project for PhD applications in CS & AI. It is a **new implementation** inspired by the author's MSc dissertation topic ("Sentiment Analysis in Social Media"); it does not reproduce that dissertation's data, methodology or findings, and it makes **no claim of novelty**.

---

## What the notebook does

| | |
|---|---|
| **Dataset** | [Twitter US Airline Sentiment](https://www.kaggle.com/datasets/crowdflower/twitter-airline-sentiment) — 14,640 crowd-labelled English tweets (Feb 2015), three classes: negative / neutral / positive |
| **Model A** | TF-IDF (1–2 grams, fit on train only) → Logistic Regression (`C` tuned on validation) and Linear SVM, both class-weighted |
| **Model B** | `cardiffnlp/twitter-roberta-base-sentiment-latest` — pretrained on ~124M tweets (2018–2021), fine-tuned on TweetEval sentiment, used **out of the box** (no fine-tuning) |
| **Protocol** | Stratified 70/15/15 split (seed 42); validation used only to pick `C`; the test set is scored **exactly once**, by every model, on the same examples |
| **Metrics** | Accuracy, macro precision/recall/F1, per-class scores, confusion matrices, inference time and hardware record |
| **Analysis** | Class-balance and text-length figures, error-analysis tables (most confidently wrong predictions), confidence analysis (clearly labelled *uncalibrated*) |
| **Outputs** | `results/` with metrics CSVs, PNG figures, classification reports, an anonymised `error_analysis.csv`, an environment report, and a ZIP archive |

The notebook follows a full research write-up in 14 markdown sections: abstract & objectives, research questions (RQ1–RQ3), background, dataset & ethics, experimental design, preprocessing, model implementation, evaluation metrics, results, error analysis, discussion, limitations & threats to validity, conclusion, and references.

## Quickstart (Google Colab)

1. Open [colab.research.google.com](https://colab.research.google.com/) and upload `sentiment_analysis_social_media.ipynb`.
2. Pick a GPU runtime if you want the transformer fast (*Runtime → Change runtime type → T4 GPU*); the notebook **automatically falls back to CPU** otherwise.
3. **Runtime → Run all.** The dataset downloads automatically via `kagglehub` — the dataset is public, so **no Kaggle credentials are needed** (configured credentials are used automatically if present).

Typical wall-clock: ~10–20 min on GPU, ~30–60 min on CPU. Actual runtime depends on hardware, dataset downloads and package versions. If the automatic download is blocked, the notebook stops with **manual-upload instructions** (download the CSV from the Kaggle page and drop it into the runtime) — it never silently substitutes a different dataset.

## Dataset licence and restrictions (verified)

The Kaggle dataset page states the dataset is licensed **CC BY-NC-SA 4.0**: **non-commercial** use, **attribution**, **share-alike**. Consequences honoured by this repository:

- The CSV is **not redistributed** here — it is downloaded from Kaggle or uploaded by the reader.
- The project is for research/education; commercial use of the data is not permitted under this licence.
- Exports produced by the notebook anonymise `@handles` (`@user`) and URLs (`http`).

See `CITATION.md` for how to cite the dataset, the model and the underlying papers.

## Repository contents

| File | Purpose |
|---|---|
| `sentiment_analysis_social_media.ipynb` | The clean notebook — upload to Colab and run all |
| `sentiment_analysis_social_media_executed_run.ipynb` | The same notebook after one **real verification run** (CPU-only Linux container, seed 42), shipped with its genuine outputs for provenance |
| `requirements.txt` | Dependency floor pins, with the exact versions verified in the shipped run |
| `CITATION.md` | BibTeX for the dataset, model and papers |
| `README.md` | This file |

## Reproducibility

- Fixed seed (42) for the split and all models; transformer inference runs deterministically in eval mode.
- Library versions, hardware, dataset checksum (sha256), split sizes, model identifier and label mapping are recorded at run time in `results/environment_report.csv`.
- All learned preprocessing is fit on the training split only; the test split is used once.
- No results are hard-coded anywhere in the notebook — every number is computed live.

## Verification statement

The notebook was **executed end-to-end** (the `kagglehub` download path included) on a CPU-only Linux container; the executed copy shipped above contains that run's real outputs. The **manual-upload fallback branch** of the data loader was not exercised in that run (the automatic download worked) — it is generated code, clearly labelled as such. Timing and metric values in the executed copy are specific to that hardware and must not be quoted as general results; re-run the notebook to produce your own.

## Limitations

One dataset, one platform (Twitter), one language, one month (February 2015), one domain (US airlines); three-class crowd labels with unused annotator-confidence; a single split without confidence intervals; uncalibrated confidences; a preprocessing asymmetry between the models (each receives its documented, correctly configured input). **Nothing here generalises to other platforms, topics or eras.** Full discussion in §12 of the notebook.

## Licence note

**No code licence has been chosen yet** — deliberately. The author has not selected a licence for this repository, and no `LICENSE` file is included until they choose one and understand its terms. The *dataset* carries its own licence (CC BY-NC-SA 4.0), independent of any code licence.
