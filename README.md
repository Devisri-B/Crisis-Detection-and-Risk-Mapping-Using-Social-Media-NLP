# Crisis Detection and Risk Mapping Using Social Media & NLP

## Project Description

### Purpose

In times of crisis, real-time information is crucial. This project aims to leverage social media data—specifically posts related to crises—to:

- **Detect potential crisis events** (natural disasters, political unrest, violence)
- **Analyze the severity and public sentiment**
- **Visualize the risk level across different geographical locations**

The goal is to support **early warning systems**, media coverage, and disaster response planning by understanding where and how people are affected or expressing concern.

---

###  Background

Social media platforms like **Reddit** have become modern sensors for crisis reporting. People share their experiences, warnings, and reactions in real-time. However, this data is noisy, unstructured, and massive in scale.

This project applies **Natural Language Processing (NLP)**, **Machine Learning**, and **Geospatial Visualization** to mine meaningful patterns from that raw data and map it interactively.

---

###  Approach

The pipeline includes:

1. **Data Extraction**
   - Using the `praw` API, Reddit posts related to predefined crisis keywords are collected.
   - Extracted data is stored in a csv file for offline analysis.

2. **Text Preprocessing**
   - Cleaning includes removal of emojis, URLs, HTML tags, stopwords, and expanding contractions.
   - Tokenization and lemmatization standardize the text for analysis.

3. **Sentiment Analysis**
   - Using TextBlob to compute **polarity** scores indicating positive, negative, or neutral tone.
   - Sentiment informs the potential psychological impact or urgency.

4. **Risk Classification**
   - Rule-based labels + Random Forest classifier used to categorize locations into:
     - **High Concern**
     - **Moderate Concern**
     - **Low Concern**
   - Classification depends on sentiment, word frequencies, and post metadata.
5. **Clustering** (Optional Insight Layer)
    - After text cleaning and sentiment analysis, KMeans clustering is applied on TF-IDF vectorized text data to group posts by thematic similarity. This helps identify emerging topics or thematic zones even if the location or risk level isn’t immediately known.

6. **Geolocation**
   - Textual location info is translated into coordinates using GeoPy.
   - Only posts with mappable locations are visualized.

7. **Visualization**
   - Interactive maps using **Folium** to communicate results clearly:
     - A **Heatmap** to show intensity (tweet/post density)
     - A **Marker Map** with risk level popups per location

---

##  Key Tasks & Methodology

| Stage              | Tools/Libraries       | Description |
|--------------------|------------------------|-------------|
| Data Extraction     | `praw`, `pandas`       | Collect Reddit posts |
| Cleaning & NLP      | `nltk`, `spacy`, `re`, `contractions` | Clean and normalize text |
| Sentiment Analysis  | `TextBlob`             | Assign polarity scores |
| Risk Classification | `sklearn`, `RandomForestClassifier` | Categorize risk level |
| Clustering  | `sklearn`, `KMeans`, `TfidfVectorizer` | Group similar posts based on textual patterns |
| Geolocation         | `geopy`                | Convert location to lat/lon |
| Visualization       | `folium`, `markercluster`, `heatmap` | Map creation |

---

##  Project Outputs

###  Marker Cluster Map — Visualizing Risk Levels by Location

Each marker shows the **location** and the **assigned risk level**. Colors and clustering help explore high-concern areas easily.

👉 [View Map](/Images/crisis_marker_map.html)


###  Heatmap — Visualizing Density of Concerned Posts

The heatmap highlights the **volume of crisis-related posts** per region. Brighter areas represent more public concern or attention.

👉 [View Heatmap](/Images/crisis_locations_heatmap.html)


---

##  How to Run

### 1. Clone this repository
```bash
git clone https://github.com/yourusername/crisis-risk-mapping.git
cd crisis-risk-mapping

