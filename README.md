# MFA-Universal-Notebook
Huge thanks to PixPrucer and HAI-D for making the original notebook and script, I just updated it to the latest MFA version and added a menu to choose any compatible language.

Remember to cut up your samples in smaller bits before uploading them OR use the inbuilt slicer, MFA hates long samples!

Please refer to this:
https://github.com/openai/whisper

And this:
https://mfa-models.readthedocs.io/en/latest/

To check if this notebook will work for your language.

# How to use
Click on MFA_Notebook.ipynb to open the notebook, then on ![image](https://github.com/user-attachments/assets/d77dc07d-0251-49d7-93c0-3a45d94db28a)

You will be redirected to Google Colab (you will need a Google account to use it).

*Before proceeding, it is highly recommended you use Google Drive to store your files.*

Upload your dataset to Drive in a .zip file containing nothing but your .wav files.

Afterwards, follow the notebook steps, pointing to /content/drive/MyDrive/nameofzipfile.zip. If your samples are longer than approx. 30 seconds, you should check 'slice_samples', otherwise leave it unchecked.
If you already have text transcriptions for your dataset, then you can skip all the Whisper related steps and just upload your transcriptions in zip file on Drive and use the "(Optional) Unzip edited transcriptions" button.

Whisper is used to generate transcriptions automatically for your dataset: install it and run the 'Whisper inference' step (please note the transcriptions aren't always accurate and it's generally best to edit them before starting the aligning process).

For the MFA steps, make sure to follow the instructions on the notebook and choose the acoustic and dictionary models of your liking on the MFA website. You will find the name of your models by choosing the language you prefer, then scrolling down on the model's page to 'Installation'.

![image](https://github.com/user-attachments/assets/1a5ebdfa-6907-4ed7-be21-71d54318a08d)

In this case, the name to put in will be 'spanish_mfa' (acoustic model).

The next step will be to convert the TextGrid files MFA outputs into monophonic HTS .lab files that DiffSinger can utilize. You can do so by following the next steps, but be mindful of the converter you choose.
If your language is already in the dropdown menu, then you're all set! Otherwise, you'll have to make your own custom converter; that is because most MFA models are set up to use some form of IPA in their alignment, which does not work for DiffSinger.

To make your own custom converter, please check the MFA page for the dictionary model you're using for a list of all the phonemes present in said model. You will then make a file called 'custom_converter.txt' and it will be structured as follows:

phonemetobereplaced,replacementphoneme

For example, if you wanna make a converter that turns all characters lowercase, it will be like this:

A,a<br>B,b<br>C,c<br>etc...

Lastly, there's an additional step for added compatibility specifically for Italian, otherwise you can just skip to the 'Zip output' step. If you've previously used the 'slice_samples' option, you should also check the 'save_samples' option.
Choose the path you most prefer (I personally recommend something like /content/drive/MyDrive/MFA_output) and make sure there's no '/' at the end! There you will find zip files containing your samples and labels.

Currently there's no step for saving TextGrid labels as opposed to HTS labels, as this is meant for DiffSinger users, but feel free to make your own.

# Known issues
It really struggles with long silences, long notes and humming.

It's really dependent on Whisper's performance as well, which isn't always perfect: if you want a better base it's highly recommended to edit the transcriptions!

The pretrained dictionaries for MFA are often lackluster and/or inaccurate when transposed to singing, which affects the label quality (I've particularly noticed this with French).

It's possible to supplement the dictionaries with G2P models, but I haven't implemented that.

# Advantages over SOFA
The main advantage is much much wider language support compared to MFA.

The other advantage is that it tends to align much more precisely than SOFA does; whereas SOFA tries it's best to guess and is approximately correct, MFA is very accurate when the aforementioned issues aren't present.

MFA's forte is speech, so it will also work very well for speech or rapping.

If you have a large enough dataset, it's possible to train your own MFA model without any labeled data: that is beyond the scope of this notebook, but if there's any interest I could try making a training notebook in the future.
