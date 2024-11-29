---

# **MusicMood Classification Project**

## **Overview**
The **MusicMood Classification Project** is a machine learning application that categorizes songs into moods (e.g., Happy, Sad, Energetic, Calm) based on audio features. The project leverages **Apache Spark** for scalable data processing and employs a **Random Forest Classifier** for mood prediction. Audio attributes like danceability, energy, valence, loudness, and tempo are analyzed to determine a song's mood.

---

## **Features**
- Handles missing data and prepares a clean dataset for analysis.
- Implements rule-based mood classification using audio features.
- Uses a **Random Forest Classifier** for machine learning-based mood prediction.
- Recommends songs based on user-selected moods.
- Scalable and fault-tolerant through Spark's distributed computing capabilities.

---

## **Technologies Used**
- **Python**: Core programming language for implementation.
- **Apache Spark**: For distributed data processing and machine learning via MLlib.
- **Random Forest Classifier**: For supervised classification of song moods.
- **CSV File Format**: Dataset format for song attributes.

---

## **Project Workflow**

### **1. Data Loading and Preprocessing**
- The dataset (`data_moods.csv`) is loaded into a Spark DataFrame.
- Missing values are replaced with default values.
- Irrelevant columns are removed, and basic statistics such as correlations are calculated.

### **2. Feature Engineering**
- Mood classification rules are defined as follows:
  - **Happy**: High valence and danceability.
  - **Sad**: Low valence and high acousticness.
  - **Energetic**: High energy and tempo.
  - **Calm**: All other cases.
- The `mood` column is encoded into numeric values using `StringIndexer`.
- A feature vector is created using attributes like `danceability`, `energy`, and `tempo`.

### **3. Machine Learning**
- A **Random Forest Classifier** is trained on the labeled dataset.
- The dataset is split into training (80%) and testing (20%) subsets.
- Model performance is evaluated using **accuracy** as the primary metric.

### **4. Recommendations**
- Songs are filtered and recommended based on the user-specified mood.
- Results are sorted by their popularity score.

---

## **Dataset**
The dataset (`data_moods.csv`) includes the following attributes:
- **danceability**: Measures how suitable a track is for dancing.
- **energy**: Represents the intensity and activity of a track.
- **valence**: Describes the musical positivity of a track.
- **acousticness**: Measures the acoustic quality of a track.
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
1. Place your dataset (`data_moods.csv`) in the `data` folder or update the file path in the script.
2. Execute the script:
   - Using VS Code:
     ```bash
     code moodclassify.ipynb
     ```
   - Using Jupyter Notebook:
     ```bash
     pip install notebook
     cd /moodclassify.ipynb
     jupyter notebook
     ```

---

## **How to Recommend Songs**
To get song recommendations for a specific mood, use the `recommend_songs` function:
```python
# Example: Recommend Happy songs
happy_songs = recommend_songs("Happy", top_n=5)
happy_songs.show()
```

---

## **Evaluation**
The model is evaluated using the **MulticlassClassificationEvaluator** from Spark MLlib, focusing on:
- **Accuracy**: Proportion of correctly classified moods.  
  - Achieved accuracy: **97%**

---

## **Possible Extensions**
- Experiment with additional ML algorithms such as **Logistic Regression** or **Gradient Boosted Trees**.
- Integrate external APIs (e.g., Spotify) for richer and more diverse datasets.
- Develop a front-end interface to enable users to search and filter mood-based recommendations.

---
