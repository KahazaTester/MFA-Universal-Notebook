# MFA-Universal-Notebook
Huge thanks to PixPrucer and HAI-D for making the original notebook and script, I just updated it to the latest MFA version and added a menu to choose any compatible language!

Remember to cut up your samples in smaller bits before uploading them OR use the inbuilt slicer, MFA hates long samples!

Please refer to this:
https://github.com/openai/whisper

And this:
https://mfa-models.readthedocs.io/en/latest/

To check if this notebook will work for your language.

# Known issues
It really struggles with long silences, long notes and humming.

It's really dependent on Whisper's performance as well, which isn't always perfect: if you want a better base it's highly recommended to edit the transcriptions!

The pretrained dictionaries for MFA are often lackluster and/or inaccurate when transposed to singing, which affects the label quality (I've particularly noticed this with French).

It's possible to supplement the dictionaries with G2P models, but I haven't implemented that.

# Advantages over SOFA
The main advantage, of course, is much much wider language support compared to MFA.

The other advantage is that it tends to align much more precisely than SOFA does; whereas SOFA tries it's best to guess and is generally correct, MFA is very accurate when the aforementioned issues aren't present.

Of course, MFA's forte is speech, so it will also work very well for speech or rapping.

If you have a large enough dataset, it's possible to train your own MFA model without any labeled data: that is beyond the scope of this notebook, but if there's any interest I could try making a training notebook in the future.
