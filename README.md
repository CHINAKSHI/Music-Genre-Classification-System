# 🎵 Music Genre Classification & Analysis

This project focuses on audio feature extraction, exploratory data analysis (EDA), and machine learning-based classification of music genres using a dataset of 10 genres. Additionally, it includes a basic recommender system to suggest similar songs based on cosine similarity.

---

## 📁 Dataset

- Each audio file is 30 seconds long, sampled at 22,050 Hz.
- **Genres**: `blues`, `classical`, `country`, `disco`, `hiphop`, `jazz`, `metal`, `pop`, `reggae`, `rock`
- **Source**: [GTZAN Dataset](https://marsyas.info/downloads/datasets.html)

---

## 🧠 Features Extracted

We extracted a comprehensive set of audio features to capture time-domain, frequency-domain, and perceptual characteristics of music:

### 📊 Time Domain
- **Waveform**: Amplitude vs time visualization to observe overall dynamics.
- **Zero Crossing Rate (ZCR)**: Helps identify tonal vs percussive content.

### 🎶 Frequency Domain
- **Spectrogram & Mel-Spectrogram**: Frequency distribution over time.
- **MFCCs**: Capture timbre, useful for genre classification.
- **Chroma Features**: Highlight harmonic and melodic content.
- **Spectral Features**: Centroid, bandwidth, roll-off to describe brightness.
- **Tempo Estimation**: Useful for distinguishing fast-paced from slow-paced genres.

### 🎼 Harmonic Analysis
- **Harmonic-Percussive Source Separation (HPSS)**
- **Harmonics-to-Noise Ratio (HNR)** (Estimated)

---

## 🎨 Visualization Techniques

### 📉 Raw Audio Waveform (Sound Waves)
- **Purpose**: Visualize amplitude over time to understand energy dynamics.
- **How to Use**: Plot waveforms for different genres.
- **Key Observations**:
  - Sharp attacks in rock (e.g., drum hits).
  - Smooth, flowing waveforms in classical or jazz.

---

### 📊 Spectrogram
- **Purpose**: Displays the frequency content over time.
- **How to Use**: Use STFT or log-mel spectrograms.
- **Key Observations**:
  - Classical: Broad frequency coverage.
  - Rock/Metal: Dense, high-energy bands.

---

### 🌈 Mel-Spectrogram
- **Purpose**: Perceptually scaled frequency representation of the signal.
- **Usage**: Great for feeding into deep learning models.

---

### 🎙️ MFCCs (Mel-Frequency Cepstral Coefficients)
- **Purpose**: Capture timbre — a distinctive trait for genre classification.
- **How to Use**: Visualize MFCCs as heatmaps.
- **Key Observations**:
  - Rock: Sharper MFCCs due to percussive content.
  - Jazz/Classical: Smoother, complex patterns.

---

### 🎼 Chroma Features
- **Purpose**: Represent pitch classes (like piano keys).
- **How to Use**: Heatmap of pitch distribution over time.
- **Key Observations**:
  - Classical/Jazz: More harmonic diversity.
  - Pop/Rock: Repetitive chord progressions.

---

### 💡 Spectral Features
- **Includes**: Spectral centroid, bandwidth, and roll-off.
- **How to Use**: Use boxplots/scatter plots to compare across genres.
- **Key Observations**:
  - Pop/Electronic: Higher spectral centroid (brighter sound).
  - Jazz/Blues: Lower spectral centroid (darker sound).

---

### 🔁 Zero Crossing Rate (ZCR)
- **Purpose**: Measure signal noisiness or percussiveness.
- **Tonal Signals**: Lower ZCR (e.g., vocals, classical).
- **Non-Tonal Signals**: Higher ZCR (e.g., metal, drums).
- **Visualization**: Blue waveform with red dots at zero crossings; plot title showing total crossings.

---

## 🔉 Harmonic and Perceptual Features

### 🎶 Harmonics-to-Noise Ratio (HNR)
- **Purpose**: Distinguish harmonic vs. noise-like signals.
- **Applications**:
  - Genre classification
  - Speech analysis
  - Timbre recognition
  - Audio restoration

---

### 🎛️ HPSS (Harmonic-Percussive Source Separation)
- **Purpose**: Split audio into harmonic (steady) and percussive (transient) components.
- **Color Coding**:
  - Harmonic: Purple `#A300F9`
  - Percussive: Orange `#FFB100`

---

### ⏱️ Tempo Distribution
- **Purpose**: Analyze tempo patterns across genres.
- **How to Use**: Extract BPM and visualize using histograms or boxplots.

| Genre      | Tempo (BPM) |
|------------|-------------|
| Disco      | 117.45      |
| Metal      | 95.70       |
| Reggae     | 123.05      |
| Blues      | 123.05      |
| Rock       | 123.05      |
| Classical  | 95.70       |
| Jazz       | 123.05      |
| Hiphop     | 117.45      |
| Country    | 86.13       |
| Pop        | 89.10       |

---

## 📊 Exploratory Data Analysis (EDA)

### 📈 Class Distribution
- Plot a bar chart to check sample distribution across genres.
- **Solution for Imbalance**: Use data augmentation or weighted loss functions.

### 🧮 Dataset
- **Source**: `features_30_sec.csv`
- **Shape**: 1000 rows (10 genres × 100 samples) and 60 features.

### 🔥 EDA Techniques
- **Correlation Heatmap**: Explore inter-feature relationships.
- **Box Plots**: Analyze distribution of features per genre.

---

## 📉 Dimensionality Reduction

### ⚙️ PCA (Principal Component Analysis)
- **Purpose**: Reduce feature dimensionality while preserving variance.
- **Output**: Scatter plot of genres in reduced space.
- **Observation**: Natural clusters indicate strong features.

### 🌐 t-SNE or PCA Genre Clustering
- **How to Use**:
  - Extract features (MFCCs, tempo, etc.)
  - Apply PCA/t-SNE to reduce dimensions to 2D or 3D
  - Visualize song clusters
- **Insight**:
  - Overlapping clusters (e.g., pop-rock) → similar sounds
  - Clear clusters → good genre separation

---

## 🤖 Machine Learning Models

### 📂 Source: `features_3_sec.csv`
- Train a classifier to predict genre of unseen audio clips.

### 📊 Model Performance

| Model                                 | Accuracy   |
|--------------------------------------|------------|
| Naive Bayes                          | 51.95%     |
| Stochastic Gradient Descent          | 65.53%     |
| KNN                                  | 80.58%     |
| Decision Trees                       | 63.99%     |
| Random Forest                        | 81.42%     |
| Support Vector Machine (SVM)         | 75.41%     |
| Logistic Regression                  | 69.77%     |
| Neural Networks (MLP)                | 67.77%     |
| XGBoost                              | **90.09%** |
| XGBRFClassifier (Random Forest)      | 74.71%     |

- ✅ **Best Model**: XGBoost (`Accuracy: 90.09%`)

---

### 🧩 Confusion Matrix
- **Purpose**: Show genre-wise prediction accuracy and confusion.
- **How to Use**: Plot heatmap after predictions.
- **Key Observations**:
  - Confusion between similar genres (e.g., classical vs. jazz)
  - Guides model improvement areas

---

## 🎯 Recommender System

### 🔎 Cosine Similarity-based Recommender

```python
def find_similar_songs(name):
    series = sim_df_names[name].sort_values(ascending = False)
    series = series.drop(name)
    print(series.head(5))
