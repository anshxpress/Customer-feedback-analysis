# Customer Feedback Analysis

A lightweight, exploratory sentiment analysis project on customer/movie reviews collected from multiple sources and locations. The notebook loads a Kaggle dataset, cleans and structures the raw text, explores the data, and visualizes sentiment distributions by source and location. Tokenization is demonstrated to prepare for further NLP tasks.

Open the companion notebook on Kaggle:

[Open in Kaggle](https://www.kaggle.com/code/anshxpress/customer-feedback-analysis?scriptVersionId=156964231)

## Project Goals
- Understand the dataset of user reviews and associated metadata (sentiment, source, date, user, location, confidence)
- Clean and reshape raw text into structured columns
- Explore missing values and perform simple cleaning
- Visualize review sources, sentiment distribution, and sentiment by location
- Prepare text (tokenization) for downstream NLP tasks

## Repository Contents
- `customer-feedback-analysis.ipynb`: Main analysis notebook
- `README.md`: Project overview, setup, and usage

## Dataset
- Expected path on Kaggle: `/kaggle/input/customer-feedback-dataset/sentiment-analysis.csv`
- The raw file is read twice in the notebook: first to preview, then again (without header) to treat the entire first column as raw `comments` for parsing into fields.

If you are running locally, download the dataset from Kaggle and place it in a local `data/` folder, then update the notebook path accordingly (e.g., `data/sentiment-analysis.csv`).

## Methods Overview (what the notebook does)
1. Load data from CSV
2. Reset index and basic renaming for clarity
3. Reload without header and focus on the single `comments` column
4. Text normalization: lowercasing and trimming whitespace
5. Split `comments` by comma into structured columns:
   - `review`, `sentiment`, `source`, `date`, `user`, `location`, `confidence`
6. Remove header-like first row and handle missing values
7. Exploratory analysis:
   - Value counts for `source`
   - Character length feature for `review`
   - Sentiment distribution (pie chart)
   - Location distribution (bar chart)
   - Sentiment by location (grouped bar chart)
8. Tokenization of `review` using NLTK `word_tokenize`

## Requirements
- Python 3.8+
- pandas, numpy, seaborn, matplotlib, nltk

Install dependencies:

```bash
pip install pandas numpy seaborn matplotlib nltk
```

For NLTK tokenization, you may need to download punkt once:

```python
import nltk
nltk.download('punkt')
```

## How to Run
### Option 1: Run on Kaggle (recommended)
- Open the Kaggle notebook via the link above
- Ensure the dataset `customer-feedback-dataset` is added to the notebook session
- Run all cells in order

### Option 2: Run locally
1. Clone this repository
2. Download the dataset from Kaggle and place it at `data/sentiment-analysis.csv`
3. Open `customer-feedback-analysis.ipynb` in Jupyter or VS Code
4. Update file paths in the notebook from `/kaggle/input/...` to `data/sentiment-analysis.csv`
5. Run cells top-to-bottom

## Outputs & Visualizations
The notebook generates plots for:
- Review sources (bar chart)
- Sentiment distribution (pie chart)
- Location distribution (bar chart)
- Sentiment by location (grouped bar chart)

It also creates helper columns like `char_length` and `tokenized_word` to support later NLP tasks.

## Notes & Next Steps
- Current parsing assumes fields are reliably comma-delimited; if commas appear within text fields, consider using a robust CSV with proper quoting or a different delimiter.
- Add stronger preprocessing (stopword removal, lemmatization), model-based sentiment classification, and evaluation in future iterations.

## License
This project is for educational purposes. Please ensure you respect the dataset's license and Kaggle terms when using the data.
