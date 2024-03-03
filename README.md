# Whisper-Fairness-Eval
Using the Speech Accent Archive Dataset to audit the Whisper v2 (large) model with OpenAI API

## Model 
I chose Whisper because it is one of the most popular and most widely used ASR systems right now. The Whisper models are trained for speech recognition and translation tasks, capable of transcribing speech audio into the text in the language it is spoken (ASR) as well as translated into English (speech translation). Researchers at OpenAI developed the models to study the robustness of speech processing systems trained under large-scale weak supervision. There are 9 models of different sizes and capabilities, and I have used Whisper Large (v2) model. This model has been trained for 2.5 times more epochs, with SpecAugment, stochastic depth, and BPE dropout for regularization. Other than the training procedure, the model architecture and size remained the same as the original large model, which is now renamed to large-v1. The new large model shows improved performance in transcription, translation, as well as language identification compared to the large-v1 model. 


## Dataset
I chose this dataset because it contains a lot of detailed demographic data on the speakers that could be contributing factors to how the same speech is detected by the model for speakers of different demographics. 

The speech accent archive is established to uniformly exhibit a large set of speech accents from a variety of language backgrounds. Native and non-native speakers of English all read the same English paragraph and are carefully recorded.
The dataset folder is called Speech-Archive and it contains the following:
recordings folder contains 2140 recordings from the speech (.mp3) archive dataset of speakers (male and female) saying the same thing. Some of these speakers also speak in langauges other than english

speakers_all.csv contains the original dataset of speakers and the following columns:

age - age of the speaker

age_onset - age when English language was learned

birthplace - place of birth

filename - name of the audio files in recordings folder

native_language - native language of the speaker

sex - gender

speakerid - speaker unique id

country - country of origin

file_missing - if the audio file exists or not

reading-passage.txt contains the English paragraph that all speakers read (Ground Truth)

The dataset license: CC BY-NC-SA 2.0 license.

This dataset was collected by many individuals (full list here) The dataset was collected legally and ethically under the supervision of Steven H. Weinberger. The most up-to-date version of the archive is hosted by George Mason University.

Citation: Weinberger, S. (2013). Speech accent archive. George Mason University.

## Testing and Results

Whisper performs excellently for this dataset. I grouped the mean WER rates by native language and gender. I used these two comparisons as I wanted to understand how native language, accent and pronunciation affect speech recognition and also how gender is a factor in speech recognition.
Even the speakers with most obscure native languages have a surprisingly low WER(better speech recognition) when speaking in English. Probable causes for this could be that because these speakers do not natively speak or use English routinely, their spoken English is not marred by colloquial irregularities that some native English speakers may inculcate into their speech.

![image](https://github.com/srimoyee1212/Whisper-Fairness-Eval/assets/30791239/a92af911-8af2-41ca-9625-8c7ad0e45a62)


Another interesting thing to note is how the average WER rates vary across genders. Since females are historically underrepresented and a lot of other applications such as vision are biased against females, I expected this to follow that pattern. But very surprisingly females have a lower WER compared to males. But reviewing relevant literature I see that the WER is mostly always higher for males than females (by 12.05% for English language, in this case).

![image](https://github.com/srimoyee1212/Whisper-Fairness-Eval/assets/30791239/676ba43c-36a1-43e7-88bf-5ea6e59960e9)
