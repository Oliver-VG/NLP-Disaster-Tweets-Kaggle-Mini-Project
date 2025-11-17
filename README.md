# NLP Disaster Tweets Kaggle Mini-Project

## Problem / Data

Mini-project for the Kaggle competition **"Natural Language Processing
with Disaster Tweets" (NLP Getting Started)**.

-   Competition overview:
    https://www.kaggle.com/c/nlp-getting-started/overview\
-   Goal: predict whether a given tweet is about a real disaster (1) or
    not (0).

Each sample in the dataset contains:

-   `id` -- a unique identifier for each tweet\
-   `text` -- the text of the tweet\
-   `location` -- the location the tweet was sent from (may be blank)\
-   `keyword` -- a particular keyword from the tweet (may be blank)\
-   `target` -- in `train.csv` only, 1 if the tweet is about a real
    disaster, 0 otherwise

**Prediction**

-   Predict 1 if the tweet is describing a real disaster, and 0
    otherwise.

**Evaluation**

-   Submissions are evaluated using **F1** between the predicted and
    expected answers.

------------------------------------------------------------------------

## Download Data (required)

Files needed:

-   `train.csv`\
-   `test.csv`\
-   `sample_submission.csv`

Download them from Kaggle:

-   Data download:
    https://www.kaggle.com/competitions/nlp-getting-started/data

Place the CSV files in the same directory as the notebook.

------------------------------------------------------------------------

## Download GloVe Twitter (required)

GloVe embeddings used in this project:

-   Download: https://nlp.stanford.edu/data/glove.twitter.27B.zip\
-   Zip size: \~3.6 GB

Steps:

1.  Extract the zip file.\
2.  Copy `glove.twitter.27B.200d.txt` (≈1.4 GB) into the directory of
    this notebook\
    (or adjust `GLOVE_PATH` in the Word Embedding section accordingly).

------------------------------------------------------------------------

## Plan

-   Download and extract the files from Kaggle\
-   Download, extract and copy GloVe\
-   Import libraries\
-   Load the data\
-   EDA\
-   Data preprocessing\
-   Tokenization\
-   Word embeddings (GloVe)\
-   Baseline LSTM model\
-   Tuned LSTM model (Hyperparameter Tuning)\
-   GRU model\
-   Stacked GRU model\
-   Model comparison\
-   Conclusions\
-   Discussion\
-   Link GitHub repository\
-   Citation\
-   AI Acknowledgement

------------------------------------------------------------------------

## Notebook Structure

The notebook covers:

-   Import Libraries\
-   Set configuration data

### Data

-   Load the data

### EDA

-   Missing values: `keyword` and `location` are optional fields in the
    original tweets, so missing values are expected noise rather than
    data errors.\
-   Sequence length / vocabulary:
    -   `MAX_VOCAB_SIZE = 20000`\
    -   `MAX_SEQUENCE_LENGTH = 50`\
    -   50 tokens is a safe sequence cap, and the vocabulary
        distribution confirms that the dataset is well covered by these
        settings.

### Text Pipeline

-   Data/Text preprocessing\
-   Tokenization and padding\
-   Word embedding (GloVe Twitter)\
-   Train/validation split

------------------------------------------------------------------------

## Q/A and Explanations

-   **Why using LSTM models:**
    -   They capture long-range dependencies effectively, which helps
        when tweets contain context spread across the sequence.
-   **Why using GRU models:**
    -   They train faster and use fewer parameters.\
    -   GRUs often generalize better on smaller datasets.\
    -   A Stacked GRU model adds a GRU layer for capturing deeper
        temporal patterns.
-   **Why using GloVe for Twitter:**
    -   These embeddings are trained on a massive corpus of real Twitter
        data and capture slang, abbreviations, and platform-specific
        language.
-   **Why retrain all models on full training data:**
    -   To let each model learn from the maximum available data,
        improving its final predictive performance.

------------------------------------------------------------------------

## Models

### Baseline LSTM Model

-   Build the LSTM model (baseline)\
-   Train the model\
-   Plot training curves\
-   Evaluate on validation set\
-   Retrain on full training data\
-   Predict on test set and create submission

**Kaggle Score LSTM Baseline**

-   Public Score: **0.80723**

------------------------------------------------------------------------

### Hyperparameter-Tuned LSTM Model

-   Learning rate set to `5e-5`\
-   Build the LSTM model (Hyperparameter Tuning)\
-   Train the model\
-   Plot training curves\
-   Evaluate on validation set\
-   Retrain on full training data\
-   Predict on test set and create submission

**Kaggle Score LSTM Tuned**

-   Public Score: **0.80968**

------------------------------------------------------------------------

### GRU Model

-   Build the GRU model\
-   Train the model\
-   Plot training curves\
-   Evaluate on validation set\
-   Retrain on full training data\
-   Predict on test set and create submission

**Kaggle Score GRU Model**

-   Public Score: **0.80110**

------------------------------------------------------------------------

### Stacked GRU Model

-   Build the Stacked GRU model\
-   Train the model\
-   Plot training curves\
-   Evaluate on validation set\
-   Retrain on full training data\
-   Predict on test set and create submission

**Kaggle Score Stacked GRU**

-   Public Score: **0.81918**

------------------------------------------------------------------------

## Model Comparison

Public leaderboard scores:

-   LSTM Baseline: **0.80723**\
-   LSTM Tuned: **0.80968**\
-   GRU Model: **0.80110**\
-   Stacked GRU Model: **0.81918**

------------------------------------------------------------------------

## Conclusions

-   The Stacked GRU model shows the best performance.\
-   LSTM with Hyperparameter Tuning is the second best model.\
-   All models used the same preprocessing pipeline, so the score
    differences mainly reflect architectural and hyperparameter
    choices.\
-   Overall, pretrained GloVe Twitter embeddings combined with recurrent
    architectures can achieve competitive performance on the Disaster
    Tweets task.

------------------------------------------------------------------------

## Discussion / Future Work

-   Further Hyperparameter Tuning with different Batch Sizes and more
    Epochs\
-   Use BiLSTM\
-   Use Transformers (BERT)\
-   Use other GloVe pretrained models from the downloaded zip-file

------------------------------------------------------------------------

## Link GitHub Repository

-   https://github.com/Oliver-VG/NLP-Disaster-Tweets-Kaggle-Mini-Project

------------------------------------------------------------------------

## Citation / References

-   Kaggle competition:
    https://www.kaggle.com/c/nlp-getting-started/overview

------------------------------------------------------------------------

## AI Acknowledgement

ChatGPT-5.1 (OpenAI, 2025) was used to assist in drafting parts of this
notebook, but no changes to the original ideas or analysis were made by
the model.
