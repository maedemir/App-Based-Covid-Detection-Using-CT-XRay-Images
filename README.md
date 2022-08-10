# App-Based-Covid-Detection-Using-CT-and-XRay-Images


![corona](https://user-images.githubusercontent.com/72692826/183350272-b6b79413-6bce-48af-9395-fc506b05bd99.gif)


This project is an implementation of an app-based covid-19 diagnosis system 
## Project description
The first step in the treatment of COVID-19 is to screen patients in primary health centers or hospitals. Although the final diagnosis still relies mainly on transcription-polymerase chain reaction (PCR) tests, in case of people with strong respiratory symptoms the election protocol nowadays in hospitals relays on medical imaging, as it is simple and fast, thus helping doctors to identify diseases and their effects more quickly. Following this protocol, patients that are suspected to suffer COVID-19 undergoes first an X-Ray session and then, in the case that more details are needed, they take a CT-scan session. As a result of this protocol, computed tomography scan (CT scan) and X-ray images are being widely used on the clinic as alternative diagnostic tools for detecting COVID-19.

Our goal was to implement a diagnosis sytem that classifies X-ray and CT images of patient's lungs into 2 categories: Covid and Non-Covid classes.

# About the datasets
We used 2 datasets for this project.
  * For implemeting CT-based model, we used [SARS-COV-2](https://www.kaggle.com/datasets/plameneduardo/sarscov2-ctscan-dataset) ct dataset containing 1252 CT scans that are positive for SARS-CoV-2 infection (COVID-19) and 1230 CT scans for patients non-infected by SARS-CoV-2, 2482 CT scans in total.
  * For implemeting X-ray-based model, we used [COVID-19 Radiography](https://www.kaggle.com/datasets/plameneduardo/sarscov2-ctscan-dataset) database.
  * Note that due to comutational limitations, we only used first 1200 images ff each classes from mentioned CXR dataset


## Methodology
### CNN
The CNN-based deep neural system is widely used in the medical classification task. [CNN](https://towardsdatascience.com/a-gentle-introduction-to-neural-networks-series-part-1-2b90b87795bc) is an excellent feature extractor, therefore utilizing it to classify medical images can avoid complicated and expensive feature engineering. 
BUT instead of building a CNN model from scratch, We used pre-trained models and [transfer learning](https://machinelearningmastery.com/transfer-learning-for-deep-learning/) to train our model. 
### Which models did we use?
We used 3 pre-trained models for both datasets tp trian our model
1. [VGG16](https://towardsdatascience.com/step-by-step-vgg16-implementation-in-keras-for-beginners-a833c686ae6c)

[<img width="450" alt="image" src="https://user-images.githubusercontent.com/72692826/182526626-ae106b18-f71b-4a56-b61f-8fc78d0205f4.png">](https://www.researchgate.net/publication/321829624/figure/fig2/AS:571845657481217@1513350037610/VGG16-architecture-16.png)

2. [VGG19](https://iq.opengenus.org/vgg19-architecture/#:~:text=VGG19%20is%20a%20variant%20of,VGG19%20has%2019.6%20billion%20FLOPs.)

[<img width="450" alt="image" src="https://user-images.githubusercontent.com/72692826/182526495-774a3816-36a6-4f9b-94e9-838f760782a0.png">](https://www.researchgate.net/figure/llustration-of-the-network-architecture-of-VGG-19-model-conv-means-convolution-FC-means_fig2_325137356)

3. [InceptionV3](https://medium.com/@AnasBrital98/inception-v3-cnn-architecture-explained-691cfb7bba08)

[<img width="450" alt="image" src="https://user-images.githubusercontent.com/72692826/182527742-c723f4d4-d322-4203-bbd8-8de0b585a77a.png">](https://production-media.paperswithcode.com/methods/inceptionv3onc--oview_vjAbOfw.png)

4. [Resnet50](https://cv-tricks.com/keras/understand-implement-resnets/)

[<img width="450" alt="image" src="https://user-images.githubusercontent.com/72692826/182528482-18a8f8c7-0888-40b1-83e5-51bc641a833c.png">](https://www.researchgate.net/figure/The-architecture-of-ResNet-50-model_fig4_349717475)



Basically our job to make a prediction model is done in these 4 steps:
- Loading and Visualizing the Dataset
- Data Pre-Processing
- Buliding & Training our Model Using Pre-traind Models (fine-tuning is done in 20 epoch with batch size of 32)
- Save and Evaluate the model

## Results
### CT Dataset 
- VGG16

<img width="450" alt="image" src="https://user-images.githubusercontent.com/72692826/183387982-192dc048-9d68-4517-b8ea-c4ccb96a1df7.png">

<img width="390" alt="image" src="https://user-images.githubusercontent.com/72692826/183388054-b1a3e9ff-c3fb-4ae1-89ec-19e28b16d8cb.png">

- VGG19

<img width="450" alt="image" src="https://user-images.githubusercontent.com/72692826/183388221-832b8861-454d-4281-9b3e-0a4cd304f702.png">

<img width="390" alt="image" src="https://user-images.githubusercontent.com/72692826/183388263-46aa2e2b-87f4-406e-a697-bd89f2615174.png">

- InceptionV3

<img width="450" alt="image" src="https://user-images.githubusercontent.com/72692826/183388522-2a2d8b65-8473-46c6-bf3b-43573a5a8c48.png">

<img width="390" alt="image" src="https://user-images.githubusercontent.com/72692826/183388570-e3a2f4fc-0bfd-43cc-86cd-4d08de5c052c.png">

### CXR Dataset 
- VGG16

<img width="450" alt="image" src="https://user-images.githubusercontent.com/72692826/183388678-79c9d536-5103-407a-a5a6-fcd999599acc.png">

<img width="390" alt="image" src="https://user-images.githubusercontent.com/72692826/183388713-499dbc94-e6a6-44f9-9e4b-e90f858c3545.png">

- VGG19

<img width="450" alt="image" src="https://user-images.githubusercontent.com/72692826/183388860-6c5c6f72-9223-47e0-b593-6af2ebdbbbf2.png">

<img width="390" alt="image" src="https://user-images.githubusercontent.com/72692826/183388896-d5adb5f7-d0aa-44e6-a70c-b41c8447a772.png">

- ResNet50

<img width="450" alt="image" src="https://user-images.githubusercontent.com/72692826/183943004-ad73aba4-1b80-4e22-90f2-db367fa281f4.png">


<img width="390" alt="image" src="https://user-images.githubusercontent.com/72692826/183943072-240ce606-2963-4709-b93a-d93ec01d7147.png">


