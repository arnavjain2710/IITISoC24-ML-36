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

# Contents of the Git Repo, documentation of efforts and experiments made so far
1) The directory 'Lit_Review' consists of all the research papers, articles and online resources used. <br />
2) The directory 'Run it on your own ' consists of all the necessary files needed to run it on your own system, the colab file should be run in colab environment, and the audio files and the pretrained modle weights 'best.pt' must be uploaded before. This code runs on YOLO and is the best functional pipeline. <br />
3) The file 'copy_of_iitisoc_dataloading' contains models built from scratch, includes dataloading, preprocessing, feature extraction codes and experimentation of various models to acheive audio emotion classfication. <br />
4) file 'copy_of_no_fine_tuning' consists of sewing together different pretrained, and not fine tuned models to achieve the end goal. it uses speech brain's pretrained model for audio emotion classfication. <br />
5) 'finetuning_wav2vec2_lg_xlsr' is an attempt to finetune the wav2vec2 model, but it was ram intensive and hence incomplete. <br />
6) 'fintetune_classification_emo' we fine tune wav2vec2 on our own dataset for emotion classfication. <br />
7) 'Gradio_model_deploy' is an attempt to deploy the fine tuned wav2vec2 on Gradio, but due to microphone access issues wasn't able to. <br />
8) 'My own fine tuned model' is a functional pipeline that can be run, and runs on the fine tuned version of wav2vec2. <br />
9) 'RAVDESS copy of dataloading' is an implementation of YOLO on a smaller subsection of the data, to monitor the performance. <br />
10) 'modified feature definitions' was a trial of running the conventional ML models (CNN RNN LSTMS) on changed feature definitions. <br />
11) 'pretrained_YOLO_ravdess_copy_of_IITISOC'  is an implementation of YOLO, but htis time using fixed weights, on a smaller subsection of the data, to monitor the performance. <br />
12) 'generate corresponding video from audio' is a mix of various pretrained models, that can be joined with my model, to generate corresponding video from the audio generated. **This is something the PS didn't ask for, just an extra effort,** not integrated with the complete code yet. But all the inputs it needs are present as the outputs of Run it on your own/IITISOC Demo file. <br/>


# How to run my file:
1) Open the file  Run it on your own/IITISOC Demo in Google Colab, upload best.pt, mixofemotions.wav(for female voice output) or male_voice(for male voice output) in the /content directory. <br/>
2) Install pip dependencies of first cell, restart the session. <br/>
3) Run the function definitions. <br/>
4) Install TTS, **DO NOT RESTART SESSSION AFTER THIS** <br/>
5) Run the setup of TTS <br/>
6) The cell marked 'this cell can be run again and again' has to be pressed each time you want to record an audio to continue the conversation. <br/>
7) To clear context and start a fresh conversation, run the last cell. <br/>
