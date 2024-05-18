
# Audio Video Captioning

## Description
This project explores five different models for audio-to-text conversion. The results obtained from these audio-to-text transcriptions are then utilized as input for large language models (LLMs) to perform grammar correction. Among the models evaluated, Whisper emerges as the top performer for accurate transcriptions. Subsequently, the transcribed text undergoes grammar correction using various LLMs, with the T5 model demonstrating superior performance in this task.

## Table of Contents
- Models
  - [Model 1: Wav2Vec2-base960h](#Model1-Wav2Vec2)
  - [Model 2: Wav2Vec2-large960h](#Model2-Wav2Vec2-Large960h)
  - [Model 3: Wav2Vec2-large960-lv60-self](#Model3-Wav2Vec2-Large960h-lv60-self)
  - [Model 4: Speech Recognition Model](#Model4-SpeechRecognition)
  - [Model 5: Whisper](#Model5-Whisper)
- LLM Models For Grammer Correction
  - [LLM Model 1: BERT Fine-tuned](#LLM-Model1-BERT-Finetuned)
  - [LLM Model 2: Venify T5](#LLM-Model2-Vennify-T5)
- [Combined Code: Transcription and GrammerCorrect](#own-audios-whisper-T5)
  
## Dataset

The dataset.zip file contains the following folders:

1. *Audio to Text Whisper Dataset*:
   - *Audio Files*: Contains 251 audio recordings.
   - *Transcriptions*: Contains audio file names and their respective transcriptions.

2. *Grammar Correction Dataset*:
   - *Grammer Dataset*: Contains original text transcriptions.
    
3. *Test Audios*:
   - Contains audio recordings created by the author.
   - These audios are utilized in the combined code, where the audio transcriptions are converted to text and subsequently corrected using the T5 LLM for grammar correction.
## Models

### Model 1: Wav2Vec2
- **Description**: This model converts audio to text. Two runs were performed to evaluate its performance.
- **Run 1**: Contains the model notebook and results in a CSV file.
- **Run 2**: Contains the model notebook and results in an Excel sheet which contains individual metrics for each audio too.
- **Model Details**: facebook/wav2vec2-base-960h.
  - **Input**: Audio files present in dataset/Audio-to-text-whisper-dataset/Audio Files
  - **Output**: Text transcriptions saved in
      - Model1-wav2vec2/Run1/wav2vec2-base-960h-results.csv
      - Model1-wav2vec2/Run2/wav2vec2-base960h-2ndtime.xlsx
  - **Time Taken for Model to Train**: 1 hour for 251 audio files
  - **Saved Model Weights**: The model is saved in the directory 'Model1-wav2vec2/saved-wav2vec2_model'
- **Metrics**:
  - **Accuracy**: 34.26%
  - **Precision**: 35.06%
  - **Recall**: 34.26%
  - **F1 Score**: 34.53%

### Model 2: Wav2Vec2-Large-960h
- **Description**: This model converts audio to text. One run was performed to evaluate its performance.
- Contains the model notebook and results in a CSV file.
- **Model Details**: facebook/wav2vec2-large-960h.
  - **Input**: Audio files present in dataset/Audio-to-text-whisper-dataset/Audio Files
  - **Output**: Text transcriptions saved in:
      - Model2-Wav2Vec2/wav2vec2-base-960h-results.csv
  - **Time Taken for Model to Train**: 1 hour for 251 audio files
  - **Saved Model Weights**: The model is saved in the directory 'Model2-Wav2Vec2-Large960h/saved-wav2vec2-large960h'
- **Metrics**:
  - **Accuracy**: 57.71%
  - **Precision**: 58.08%
  - **Recall**: 57.71%
  - **F1 Score**: 57.29%
  - **Word Error Rate[wer]**: 28.85%
  - **Character Error Rate[cer]**: 14.63%
### Model 3: Wav2Vec2-Large-960h-lv60-self
- **Description**: This model converts audio to text. One run was performed to evaluate its performance.
- Contains the model notebook and results in a CSV file.
- **Model Details**: facebook/wav2vec2-large-960h-lv60-self.
  - **Input**: Audio files present in dataset/Audio-to-text-whisper-dataset/Audio Files
  - **Output**: Text transcriptions saved in:
      - Model3-Wav2Vec2-Large960h-lv60-self/wav2vec2-large960h-lv60-self-results.csv
  - **Time Taken for Model to Train**: 1 hour for 251 audio files
  - **Saved Model Weights**: The model is saved in the directory 'Model3-Wav2Vec2-Large960h-lv60-self/Saved-Wav2Vec2-Large960h-lv60-self'
- **Metrics**:
  - **Accuracy**: 49.40%
  - **Precision**: 50.20%
  - **Recall**: 49.40%
  - **F1 Score**: 49.67%

### Model 4: SpeechRecognition
- **Description**: This model converts audio to text. One run was performed to evaluate its performance.
- Contains the model notebook and results in a CSV file.
- **Model Details**: one can use model by using command `pip install SpeechRecognition`
  - **Input**: Audio files present in dataset/Audio-to-text-whisper-dataset/Audio Files
  - **Output**: Text transcriptions are displayed in the respective notebook itself.
  - **Time Taken for Model to Train**: 2 hours for 251 audio files
- **Metrics**:
  - **Accuracy**: 50.81%
  - **Precision**: 96.00%
  - **Recall**: 51.00%
  - **F1 Score**: 66.00%
  
### Model 5: Whisper
- **Description**: This model converts audio to text. One run was performed to evaluate its performance.
- Contains the model notebook and results in a CSV file along with the individual metrics for each audio.
- **Model Details**: one can use model by using command `pip install -U openai-whisper`
  - **Input**: Audio files present in dataset/Audio-to-text-whisper-dataset/Audio Files
  - **Output**: Text transcriptions are saved to Model5-whisper/whisper-model-results-xlsx.
  - **Time Taken for Model to Train**: 2 hours for 251 audio files
- **Metrics**:
  - **Accuracy**: 93.40%
  - **Precision**: 94.05%
  - **Recall**: 93.40%
  - **F1 Score**: 93.39%
  - **Word Error Rate[wer]**: 14.00%
  - **Character Error Rate[cer]**: 9.00%

## LLM Models

### LLM Model 1: BERT Fine-tuned
- **Description**: Fine-tuned BERT model for grammar correction.
- **Input**: Sentences that have grammar mistakes.
- **Output**: Grammatically corrected sentences.
  - **Notebook**: Contains the model and results.
    - [Notebook](https://github.com/Yaswanth-B/AccessibleLLM/blob/main/Audio%20Video%20captioning/LLM-Model1-BERT-Finetuned/Fine-tuned-bertLLM.ipynb)

### LLM Model 2: Vennify T5
- **Description**: T5 model for grammar correction,fine-tuned on dataset available on huggingface.
  - **Notebook**: Contains the model and training details.
    - [Notebook](https://github.com/Yaswanth-B/AccessibleLLM/blob/main/Audio%20Video%20captioning/LLM-Model2-Vennify-T5/T5-Model.ipynb)
  - **Results**: Corrected sentences saved in a CSV file.
    - [Corrected Sentences CSV](https://github.com/Yaswanth-B/AccessibleLLM/blob/main/Audio%20Video%20captioning/LLM-Model2-Vennify-T5/T5-LLM-CORRECTED-SENTENCES.csv)
  - **Metrics**:
    - BLEU score : 0.79
   
## Combined Model
- **Notebook**: Converts audios to text using Whisper and immediately corrects them using T5.
  - [Combined Model Notebook](https://github.com/Yaswanth-B/AccessibleLLM/blob/main/Audio%20Video%20captioning/own-audios-whisper-T5.ipynb)


## Usage
1. Run the model notebooks to train and evaluate the models.
2. Use the provided Python scripts to test the models with your own audio and video files.
