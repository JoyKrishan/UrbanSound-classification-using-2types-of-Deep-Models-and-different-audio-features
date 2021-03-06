
### Research Topic:
[Urban Sound Classification Using Convolutional Neural Network and Long Short Term Memory Based on Multiple Features](https://www.researchgate.net/publication/346659500_Urban_Sound_Classification_Using_Convolutional_Neural_Network_and_Long_Short_Term_Memory_Based_on_Multiple_Features)

### Dataset: 
[Urban Sound Classification](https://urbansounddataset.weebly.com/urbansound8k.html). For detailed explaination about the dataset and the methods used to clean and compile it please read this [paper](http://www.justinsalamon.com/uploads/4/3/9/4/4394963/salamon_urbansound_acmmm14.pdf).

### Audio features(Spectral features) extracted:
[MFCC](https://librosa.org/doc/latest/generated/librosa.feature.mfcc.html#librosa.feature.mfcc), 
[Mel Spectrogram](https://librosa.org/doc/latest/generated/librosa.feature.melspectrogram.html#librosa.feature.melspectrogram), 
[Chroma STFT](https://librosa.org/doc/latest/generated/librosa.feature.chroma_stft.html#librosa.feature.chroma_stft), [Chroma CQT](https://librosa.org/doc/latest/generated/librosa.feature.chroma_cqt.html#librosa.feature.chroma_cqt), 
[Chroma Cens](https://librosa.org/doc/latest/generated/librosa.feature.chroma_cens.html#librosa.feature.chroma_cens), [Spectral Contrast](https://librosa.org/doc/latest/generated/librosa.feature.spectral_contrast.html#librosa.feature.spectral_contrast),
[Tonnetz](https://librosa.org/doc/latest/generated/librosa.feature.tonnetz.html#librosa.feature.tonnetz).
<p float="left">
  <img src="https://github.com/JoyKrishan/UrbanSound-classification-using-2types-of-Deep-Models-and-different-audio-features/blob/master/images/Mfccfeaturedetailed.PNG" width="400" alt="MFCC of Dog Bark" />
  <img src="https://github.com/JoyKrishan/UrbanSound-classification-using-2types-of-Deep-Models-and-different-audio-features/blob/master/images/melspectrogram.PNG" width="400" alt="Mel Spectogram of Dog Bark" /> 
</p>

<p float="left">
  <img src="https://github.com/JoyKrishan/UrbanSound-classification-using-2types-of-Deep-Models-and-different-audio-features/blob/master/images/chroma_stft.PNG" width="400" alt="Chroma STFT of Dog Bark"/>
  <img src="https://github.com/JoyKrishan/UrbanSound-classification-using-2types-of-Deep-Models-and-different-audio-features/blob/master/images/chromacqt.PNG" width="400" alt="Chroma CQT of Dog Bark"/> 
</p>

<p float="left">
  <img src="https://github.com/JoyKrishan/UrbanSound-classification-using-2types-of-Deep-Models-and-different-audio-features/blob/master/images/cens.PNG" width="400" alt="Chroma Cens of Dog Bark"/>
  <img src="https://github.com/JoyKrishan/UrbanSound-classification-using-2types-of-Deep-Models-and-different-audio-features/blob/master/images/spectral.PNG" width="400" alt="Spectral Contrast of Dog Bark"/> 
</p>

<p float="left">
  <img src="https://github.com/JoyKrishan/UrbanSound-classification-using-2types-of-Deep-Models-and-different-audio-features/blob/master/images/tonnetz.PNG" width="400" alt="Chroma Cens of Dog Bark"/></p>


### Models Used:
* A CNN model with layers of **CONV2D ---> MAXPOOL ---> CONV2D ---> MAXPOOL ---> DENSE ---> DENSE ---> SOFTMAX**.The first layer of Conv2d uses 64 filters with the dimension of (5\*1\*1) which is placed on the input shape of (20\*5\*1). After that a maxpool layer is applied followed by another CONV2D layer and so on. Finally a softmax layer is used at the end to classify between the 10 classes. We have used the adam optimizer which is the most optimized algorithm to calculate the cost.

<!--<p float="left">
  <img src="https://github.com/JoyKrishan/UrbanSound-classification-using-2types-of-Deep-Models-and-different-audio-features/blob/master/images/img16CNN%20Final%20Model.jpg", width="700" alt="CNN model"/>
  </p>-->

* A LSTM model with layers of 2 LSTM blocks, 2 time distributed dense layers and finally a output layer for classification.
**LSTM ---> LSTM ---> DENSE ---> DENSE ---> SOFTMAX**. The first and the second lstm layer contains 128 blocks which returns 128 yHat values from the given x values. The values from the LSTM layes are passed onto Dense layer and then to the output layer. Here we use an adam optimizer so that the model converges faster.
<!--<p float="left">
  <img src="https://github.com/JoyKrishan/UrbanSound-classification-using-2types-of-Deep-Models-and-different-audio-features/blob/master/images/ModelLSTM.jpg", width="700" alt="LSTM model"/>
  </p>-->

### Augmentation
* Time Stretch : In this technique, we slow down or speed up the sound clips with a rate of 0.9 and 1.1.  In this way, we couldgenerate more 17464 new audio clips for our augmented dataset.

![Time Stretch](https://github.com/JoyKrishan/UrbanSound-classification-using-2types-of-Deep-Models-and-different-audio-features/blob/master/images/Time%20Stretch.PNG)

* Pitch Shift : The factors of {-2, +2} are used to raise and lower the pitch (in semitones) of an audio sample in the dataset through which we could create 17464 samples using pitch shift.

![Pitch Shift](https://github.com/JoyKrishan/UrbanSound-classification-using-2types-of-Deep-Models-and-different-audio-features/blob/master/images/pitch_shift.PNG)

* Pitch Shift along with Time Stretch : In this augmentation step, a sound clip is manipulated using both pitch shift and time stress to generate a total of 34928 novel audio clips.

![Pitch Shift and Time Stretch](https://github.com/JoyKrishan/UrbanSound-classification-using-2types-of-Deep-Models-and-different-audio-features/blob/master/images/Time%20stretech%20and%20Pitch.PNG)

### Results

The table below shows the max accuracy of the models on different types of features used. 

| Model | Accuracy |
| ------ | :-----: |
| CNN   | 96.5% |
| LSTM  | 98.81% |

### Fundamental Libraries required before implementation
Librosa and ffmpeg 
```
pip install librosa 
pip install ffmpeg
```
### For more information - [Click here to view our paper published in IEEE](https://ieeexplore.ieee.org/document/9268723/references#references) 
**Cite this paper if you use the code and information from the paper** :smiley:
