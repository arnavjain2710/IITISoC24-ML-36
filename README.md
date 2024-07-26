# IITISoC24-ML-36

# Conversational Emotion Recognizer (PS-19 ) 
**Mentor:** <br />
Arnav Jain <br />

**Team Members:**
1) Vaidehi Bhat <br />
2) Tanvi Agarwal <br />

# Description of the PS:
The problem statement is to design an interface powered by AI that can detect the emotion in which a person is speaking and gives an output telling the mood of the
person in audio format. This problem statement, which is Emotion Recognition, represents only a section of the bigger domain Speech Recognition. <br />
Its applications are diverse, ranging from customer calling service and support, mental health monitoring of patients, driver safety, personal AI powered assistants,
education and even gaming. <br />

# The solution
**1) Dataset**
Four popular datasets, RAVDESS, TESS, CREMA-D and SAVEE were used for training. Only audio files corresponding to 6 emotions, anger, fear, sadness, happiness and disgust were used.<br />
**2) Preprocessing and Data Loading**
All the datasets were accessed from kaggle and the file path was loaded into arrays. Mel spectrogram was created and converted to .png files and saved into training and validation directories.<br />
**3) Model**
YOLO v8 with pretrained weights was used to classify these images into 6 categories corresponding to the 6 emotions. It turned out to be 80.2% accurate. <br />

# The complete flow of the conversational emotional recogniser
1) Recording the audio using the system microphone using the ffmpeg of python and saving it in .wav format. <br />
2) Resampling the audio to 16kHz as most of the pretrained models require that as their default sampling rate, taking out a melspectrogram and converting it into .png format. <br />
3) Feeding the image in the YOLO model, whose weights are saved in the 'best.pt' file which has to be uploaded before running the sequence. <br />
4) Saving the output emotion as a string in the variable called 'emotion'. <br />
5) Using openai/whisper-large-v3, which is a ASR Speech-to-Text we convert the audio into a 'text', and form a prompt comprising of 'text' and 'emotion'. <br />
6) Using Meta's Llama-3-8B-Instruct as our LLM, we give in the initial prompt, and start a dictionary of messages, which dynamically appends the user prompt and bot's response to form a dictionary, which is feeded every time into the LLM, to remember the context of the conversation. <br />
7) Using Coqui's tts_models/multilingual/multi-dataset/xtts_v2 we convert the bot's response to an audio and use the ipd.Audio library to play it, for the cloning we have two audios, one male and one female to select assitant's voice. <br />

