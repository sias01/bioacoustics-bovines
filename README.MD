# Bio Acoustics based Cattle Monitoring Platform

Bio Acoustics is a field of research that deals with analyzing the vocalizations of animals to predict potential diseases and make educated decisions about wellness of animals

This project aims to use BioAcoustics to learn the patterns of vocalizations of cows and hens for early stage detection of respiratory diseases like Bovine Respiratory Disease (BVT) and Avenian Infulenza.







## Aim 

- The farmers who are on-board this platform will also recieve regular monitoring data and warnings about their cattle incase of a detection of diesease based on vocalization of their cattle.

- Through this project the creators also aim to create a platform for bio-acoustics researchers to bring their research closer to users as well as create a data ingestion platform to in-turn support research with more data.
## Idea Description

- The idea revolves around a low-cost computer mounted to the cattle to analyze their vocalizations at regular intervals and notify the user of any anamolies in the cattle and how severe it is

- Employs the use of a computer like Raspberry Pi() to run the inference in-field which is mounted to the cattle and can record vocalizations using specialized microphones

- It uses a VGG based CNN network to analyze the spectograms generated by the the audio to segregate the different classes of vocalizations of cattle

- The 4G/LTE enabled RaspberryPi can then run the inference and send SMS based alerts to the user as well as update the cloud database at regular intervals to maintain a history for further pattern analysis

- The companion app written in Flutter allows users to register their cattle with deviceId and phone number to start monitoring their cattle as well as to get detailed history of their cattle behaviour along with vocalization recordings in abnormal situations

- The optional backend can facilitate the inference of the vocalizations and SMS service if the inference device is underpowered

- The backend is powered by Firebase in the form of FireBase Auth,Cloud Messaging for Push Notifications and Firebase Storage for anamaly vocal storage and Firestore Database for fast writes

- The frontend was written in Flutter and connected to firebase using Flutter Fire packages
## System Overview

<p align="center" width="100%">
  <img src="https://github.com/srikharshashi/cattle-monioring-bioacoustics/assets/37980605/ee87cf4b-d07b-4ee9-8f7b-b6a4cd8ad86c" />
</p>


## WorkFlow

<p align="center" width="100%">
  <img src="https://github.com/srikharshashi/cattle-monioring-bioacoustics/assets/37980605/64494755-ba63-407d-8f38-a99ad19451ba" />
</p>


## Audio Processing

- A noise model was created from the background noises then used to filter out any noises in the recordings before it was processed by the deep learning model


<p align="center" width="100%" >
  <img src="https://github.com/srikharshashi/cattle-monioring-bioacoustics/assets/37980605/65c82b9a-79e0-440b-946b-0485bef21a67" />
</p>

- Received audio from the microphone is converted into its digital form, the digital representation consists of series of samples, which are essentially numerical that represent the amplitude value of the sound wave at different points of time.

- The digital form of the received audio is used to convert the audio into mel spectrogram, spectorgram is a visual representation of the audio and mel spectrogram is the variant of spectrogram that uses mel-scale for the frequency axis instead of linear scale.As human ears perceive the differences in frequencies in mel scale.

- The obtained mel specs are again processed to get log mel-spectrograms, A log mel spectrogram is a variation of the mel spectrogram where the intensity values in the mel-frequency bands are transformed using a logarithmic scale. 

- This transformation is applied to make the visualization and analysis of the spectrogram more meaningful and aligned with how humans perceive loudness.

- The audio is then fed into a VGG16 model with tranfer learning 

- We currently have two models one for cows and one for hens

- **Cow Model**

    - Has an accuracy of 96% and can detect distress/normal states of the cows.(HFC/LFC)

- **Chicken Model**

    - Has an accuracy of 97% and can detect healthy,unhealthy and distress states.

![image](https://github.com/srikharshashi/cattle-monioring-bioacoustics/assets/37980605/5eb3b5ba-7fb0-4cf9-8ab9-3d9a86bb9baf)


![image](https://github.com/srikharshashi/cattle-monioring-bioacoustics/assets/37980605/a51e014d-a092-4a98-8c0b-696fe6e6e752)




## User Interface and Frontend

- The frontend was written in Flutter and supports features like Localization(Telugu is shown as a POC in the secreenshots below)

- Integrates with Firebase seamlessly

![image](https://github.com/srikharshashi/cattle-monioring-bioacoustics/assets/37980605/0b5a8309-ec39-4a5e-bfba-1735e12a55b0)

![image](https://github.com/srikharshashi/cattle-monioring-bioacoustics/assets/37980605/7fdbe8b7-6ef9-4198-ac28-d96ec7069157)

## Demo Video

<div align="center">
  <a href="https://www.youtube.com/watch?v=lBWsUVvXhiE"><img src="https://img.youtube.com/vi/lBWsUVvXhiE/0.jpg" alt="Youtube Video"></a>
</div>


## Authors

- [Srikhar Shashi D](https://www.github.com/srikharshahsi) -- Team Leader and Flutter Developer
- [Pranav Batchu](https://github.com/batchu-29) -- Deep Learning and Audio Processing 
- [Shreyas Desai](https://github.com/sias01) -- Spectrogram modeling and inference optimization.

## Tech Stack

- Flutter for Frontend
- Flask for backend Services
- Cloud Firestore and Firebase Auth for DB and Auth
- Firebase Storage for online services
- Tensorflow ,Keras ,Librosa ,SciPy -- for Deep Learning and Audio Processing

## Datasets

- https://gitlab.com/is-annazam/bovinetalk/-/tree/main/Cattle%20sounds%20database%20(raw%20data)?ref_type=heads
- https://data.mendeley.com/datasets/zp4nf2dxbh/1
- https://www.kaggle.com/datasets/pcaackdataset/15-sec-splitted-chicken-distress-audio


## Related Work and References

```Jung, D.-H.; Kim, N.Y.; Moon, S.H.; Jhin, C.; Kim, H.-J.; Yang, J.-S.; Kim, H.S.; Lee, T.S.; Lee, J.Y.; Park, S.H. Deep Learning-Based Cattle Vocal Classification Model and Real-Time Livestock Monitoring System with Noise Filtering. Animals 2021, 11, 357. https://doi.org/10.3390/ani11020357```

- https://doi.org/10.3390/ani11020357

```Stowell D. Computational bioacoustics with deep learning: a review and roadmap. PeerJ. 2022 Mar 21;10:e13152. doi: 10.7717/peerj.13152. PMID: 35341043; PMCID: PMC8944344.```

- https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8944344/

```Jung, Dae-Hyun & Kim, Na & Moon, S.H. & Jhin, Changho & Kim, Hak-Jin & Yang, Jung-Seok & Kim, Hyoung & Lee, Taek & Lee, Ju Young & Park, Soo Hyun. (2021). Deep Learning-Based Cattle Vocal Classification Model and Real-Time Livestock Monitoring System with Noise Filtering. Animals. 11. 357. 10.3390/ani11020357. ```

- https://www.researchgate.net/publication/348963235_Deep_Learning-Based_Cattle_Vocal_Classification_Model_and_Real-Time_Livestock_Monitoring_System_with_Noise_Filtering

```BovineTalk: Machine Learning for Vocalization Analysis of Dairy Cattle under Negative Affective States . Dinu Gavojdian, Teddy Lazebnik, Madalina Mincu, Ariel Oren, Ioana Nicolae, Anna Zamansky```

- https://arxiv.org/abs/2307.13994

```Defalque, Guilherme Augusto, et al. "Ingestive Behaviour Activities Based on Bioacoustic Signals in Grazing Cattle." IJAEIS vol.11, no.4 2020: pp.69-83. http://doi.org/10.4018/IJAEIS.2020100105```

- https://www.researchgate.net/publication/345093465_Ingestive_Behaviour_Activities_Based_on_Bioacoustic_Signals_in_Grazing_Cattle

