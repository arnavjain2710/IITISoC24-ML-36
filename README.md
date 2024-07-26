# IITISoC24-ML-36

# Conversational Emotion Recognizer (PS-19 )
**Mentor:**
Arnav Jain
**Team Members:**
1) Vaidehi Bhat
2) Tanvi Agarwal

# Description of the PS:
The problem statement is to design an interface powered by AI that can detect the emotion in which a person is speaking and gives an output telling the mood of the
person in audio format. This problem statement, which is Emotion Recognition, represents only a section of the bigger domain Speech Recognition.
Its applications are diverse, ranging from customer calling service and support, mental health monitoring of patients, driver safety, personal AI powered assistants,
education and even gaming.

# The solution
**1) Dataset**
Four popular datasets, RAVDESS, TESS, CREMA-D and SAVEE were used for training. Only audio files corresponding to 6 emotions, anger, fear, sadness, happiness and disgust were used.
**2) Preprocessing and Data Loading**
All the datasets were accessed from kaggle and the file path was loaded into arrays. Mel spectrogram was created and converted to .png files and saved into training and validation directories.
**3) Model**
YOLO v8 with pretrained weights was used to classify these images into 6 categories corresponding to the 6 emotions. It turned out to be 80.2% accurate.
