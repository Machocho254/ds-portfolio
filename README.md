# ds-portfolio
# 🗳️ Kenya 2022 Election — Media Sentiment & Topic Analysis

> Analysing how 1,001 global news sources covered Kenya's 2022 General Election
> using NLP, sentiment analysis, and topic modeling.

---

## 📌 Project Overview

The 2022 Kenyan General Election was one of East Africa's most closely watched
democratic events — a tight race between William Ruto and Raila Odinga, set
against a backdrop of ethnic tensions, security fears, and disputed results.

This project uses **GDELT** (Global Database of Events, Language and Tone) to
analyse how international and local media covered the election across 5 critical
days (August 7–11, 2022), including election day itself (August 9, 2022).

Rather than relying on social media data (which is increasingly restricted),
this project uses a more credible and reproducible data source — global news
event data — making the findings more defensible and publishable.

---

## 📊 Key Findings

### 1. International Coverage Was The Only Positive Theme
Of 15 major topics discovered through topic modeling, **international coverage
was the only one with a positive average tone (+0.8)**. All 14 domestic topics
were negative — reflecting deep public distrust in the election process,
consistent with the atmosphere on the ground during that period.

### 2. Marsabit Violence Dominated the Negative Narrative
The **Marsabit Violence & Police** topic had the most negative average tone
(-4.5) of any theme — reflecting deadly clashes in Marsabit County on election
day that received significant negative coverage globally.

### 3. Odinga's Sentiment Rose Sharply on Election Day — Then Collapsed
Odinga's media tone rose from -1.8 (Aug 7) to a peak of +1.15 on Aug 10 — the
day after voting — reflecting widespread expectation of his victory. It then
dropped sharply on Aug 11 (-0.07) when Ruto was announced the winner,
illustrating how quickly media narratives can reverse.

### 4. Media Sentiment Did Not Predict the Winner
Ruto (tagged as "Deputy" in GDELT) had **consistently more negative coverage**
than Odinga throughout the election week, yet won the presidency. This
disconnect between media tone and electoral outcome is one of the most
important findings of this analysis.

### 5. Kenyatta's Betrayal Narrative Grew Increasingly Negative
Sitting President Uhuru Kenyatta, who broke from his deputy Ruto to back
opposition candidate Odinga, saw his media tone decline steadily from +0.39
(Aug 7) to -1.69 (Aug 11) — reflecting growing negative coverage of his
politically unusual position.

---

## 📈 Visualisations

| Chart | Description |
|---|---|
| `chart1_sentiment_by_candidate.html` | Sentiment distribution (%) by political figure |
| `chart2_sentiment_over_time.html` | Average media tone per candidate across election week |
| `chart3_topic_distribution.html` | Volume of news events by discovered theme |
| `chart4_sentiment_by_topic.html` | Average sentiment score per topic |

---

## 🗂️ Dataset

| Property | Value |
|---|---|
| Source | GDELT Global Database of Events, Language and Tone |
| Date Range | August 7–11, 2022 |
| Total Events | 4,106 Kenya-specific news events |
| Raw Records | 487,719 (filtered from global dataset) |
| Countries of Coverage | 57 countries |
| Unique News Sources | 1,001 |
| Sentiment Method | GDELT AvgTone score (built-in, per-article) |

---

## 🛠️ Methods & Tools

**Data Collection**
- GDELT daily export files downloaded directly via URL (no API key needed)
- Filtered to Kenya-specific events using country codes (KEN / KE)

**Sentiment Analysis**
- Used GDELT's built-in `AvgTone` metric (ranges from -100 to +100)
- Classified as Negative (<-2), Neutral (-2 to +2), or Positive (>+2)
- Negative: 37.7% · Neutral: 47.1% · Positive: 15.3%

**Topic Modeling**
- BERTopic with transformer embeddings (all-MiniLM-L6-v2)
- Reduced to 15 interpretable themes via hierarchical topic reduction
- CountVectorizer with bigram support for phrase detection

**Candidate Tagging**
- GDELT uses role-based actor codes rather than personal names
- Ruto identified via "DEPUTY" tag (his title as Deputy President at the time)
- Kenyatta identified via "PRESIDENT" and "KENYATTA" tags

**Visualisation**
- Plotly Express — interactive HTML charts

---

## 💡 Limitations & Future Work

- **No full article text** — GDELT provides metadata and tone scores but not
  full article content, limiting the depth of topic modeling
- **Role-based actor tagging** introduces ambiguity (e.g. "DEPUTY" could
  refer to other deputy officials)
- **Future work**: Combine with Twitter/X data for public sentiment comparison
  vs. media sentiment — the gap between the two would be an interesting study
- **Future work**: Extend analysis to the disputed results period
  (August 15–September 5, 2022) when Odinga challenged the results in court

---

## 📁 Repository Structure

```
project-1-kenya-election-nlp/
│
├── kenya_election_nlp_analysis.ipynb   # Main Colab notebook
├── kenya_election_2022_cleaned.csv     # Cleaned Kenya events dataset
├── kenya_election_2022_topics.csv      # Dataset with topic labels
│
├── charts/
│   ├── chart1_sentiment_by_candidate.html
│   ├── chart2_sentiment_over_time.html
│   ├── chart3_topic_distribution.html
│   └── chart4_sentiment_by_topic.html
│
└── README.md
```

---

## 🚀 How to Reproduce

1. Open the notebook in Google Colab
2. Run all cells in order — no API keys or accounts required
3. GDELT data downloads automatically from public URLs
4. All outputs save to Google Drive

```python
# The only install needed
!pip install bertopic plotly -q
```

---

## 🌍 Why This Project Matters

Most NLP portfolio projects use generic Western datasets. This project
demonstrates that rich, reproducible political media analysis is possible
using African data — and surfaces findings that are historically accurate,
locally relevant, and globally interesting.

The disconnect between media sentiment and electoral outcomes in Kenya 2022
is a finding with real implications for how we interpret media coverage of
African elections.

---

*Built as part of a data science portfolio focused on NLP and LLM applications
for qualitative data analysis in East Africa.*
