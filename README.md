# **MusicMood Classification Project**

## **Overview**
The **MusicMood Classification Project** is a machine learning application that categorizes songs into moods (e.g., Happy, Sad, Energetic, Calm) based on audio features. The project utilizes **Apache Spark** for scalable data processing and a **Random Forest Classifier** for mood prediction. The dataset contains various audio attributes like danceability, energy, valence, loudness, and tempo, which are analyzed to determine the mood of songs.

---

## **Features**
- Handles missing data and prepares a clean dataset for analysis.
- Implements rule-based mood classification using audio features.
- Uses **Random Forest Classifier** for machine learning-based mood prediction.
- Recommends songs based on a user-selected mood.
- Scalable and fault-tolerant using Spark's distributed computing.

---

## **Technologies Used**
- **Python**: Core programming language for implementation.
- **Apache Spark**: For distributed data processing and MLlib for machine learning.
- **Random Forest Classifier**: For supervised classification of song moods.
- **CSV File Format**: Dataset format for song attributes.

---

## **Project Workflow**

### **1. Data Loading and Preprocessing**
- Dataset (`data_moods.csv`) is loaded into a Spark DataFrame.
- Missing values are handled by replacing them with default values.
- Irrelevant columns are dropped, and basic statistics like correlation are calculated.

### **2. Feature Engineering**
- Moods are assigned based on the following rules:
  - **Happy**: High valence and danceability.
  - **Sad**: Low valence and high acousticness.
  - **Energetic**: High energy and tempo.
  - **Calm**: All other cases.
- The `mood` column is encoded into numeric values using `StringIndexer`.
- A feature vector is prepared with key attributes like `danceability`, `energy`, and `tempo`.

### **3. Machine Learning**
- A **Random Forest Classifier** is trained using the labeled dataset.
- Data is split into training (80%) and testing (20%) subsets.
- Model performance is evaluated using **accuracy** as the metric.

### **4. Recommendations**
- Songs are filtered and recommended based on the user-specified mood.
- Results are sorted by popularity.

---

## **Dataset**
The dataset (`data_moods.csv`) contains the following attributes:
- **danceability**: Measures how suitable a track is for dancing.
- **energy**: Represents the intensity and activity of a track.
- **valence**: Describes the musical positivity of a track.
- **acousticness**: Measures whether a track is acoustic.
- **tempo**: The speed of a song in beats per minute.
- **loudness**: The overall loudness of a track in decibels.
- **popularity**: Popularity of the track, used for recommendations.

---

## **Installation and Usage**

### **1. Prerequisites**
- Python 3.7+
- Apache Spark
- Java Development Kit (JDK) 8+
- Dataset (`data_moods.csv`)

### **2. Installation**
1. Clone the repository:
   ```bash
   git clone https://github.com/sanskreate/musicmood.git
   cd musicmood
   ```
2. Install dependencies:
   ```bash
   pip install pyspark
   ```

### **3. Run the Project**
1. Place your dataset (`data_moods.csv`) in the `data` folder or update the path in the script.
2. Execute the script:
  i) VS code:
     ```bash
     code moodclassify.ipynb
     ```
  ii) Jupyter Notebook:
     ```bash
     pip install notebook
     cd /moodclassify.ipynb
     jupyter notebook
     ```

---

## **How to Recommend Songs**
To get song recommendations for a specific mood, call the `recommend_songs` function:
```python
# Recommend Happy songs
happy_songs = recommend_songs("Happy", top_n=5)
happy_songs.show()
```

---

## **Evaluation**
The model is evaluated using the **MulticlassClassificationEvaluator** in Spark MLlib, focusing on:
- **Accuracy**: Measures the proportion of correctly classified moods. The measured accuracy is 95%.

---

## **Possible Extensions**
- Explore additional ML algorithms like **Logistic Regression** or **Gradient Boosted Trees**.
- Integrate external APIs (e.g., Spotify) for richer datasets.
- Develop a front-end interface for mood-based song recommendations.

---

## **License**
This project is licensed under the MIT License. See `LICENSE` for more details.

---
