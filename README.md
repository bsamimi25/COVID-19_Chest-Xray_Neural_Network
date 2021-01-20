# COVID-19_Chest-Xray_Neural_Network


<p align="center">
<img width="753" alt="Screen Shot 2021-01-15 at 9 11 40 AM" src="https://user-images.githubusercontent.com/67808057/104757314-c2d91800-5711-11eb-86ac-9b3b530c6767.png">
  
                          Covid19                     Normal                          Viral_Pneumonia
                                      
# Overview 
In this project I created a Multiclass Classification Neural Network in which I determined based on a image dataset consisting of Chest X-rays, if a patient is classified as diagnosed with COVID-19, Normal, or has Pneumonia.

# Preprocessing
With our Dataset, I decided to only have three classes with more photos more ability of the neural network to learn. 
These are the following classes with the number of photos in total: 
  - Covid images: 1327
  - Normal images: 1341
  - Viral_Pneumonia: 1463
  
# Models

**Base Models**
I began by making one base model by my own creation which kept improving over time. This base model I made was 5 layers but this time I used increasing neurons from 16, 32, 64, 128, back to 64 then I finished off with a flatten and the dense layers with the classes. These base models we not learning as a proper machine learning algorithm due to the fact that our training set had a lower accuracy than our validation. This means that our model was underfitted so we did not pursure these in spite of the great scores. 

**Transfer Learning Models**
Unsatisfied by my results from my base models, I tried to build on top of what I had already made. I began with VGG16 transfer learning model pretrained for image datasets. On top of the VGG16 Model I added another dense layer for the number of classes and flattened the images.We continued by using various drouputs functions on VGG16 and adding more complexity but we still saw no improvement in our scores. But it seemed that the best results for these models was to keep it simple and barely add anything to it and just add the Dense layer with the class names.


My second transfer learning model was the ResNet50 model gave similar results so far out of all my models. I did the same with ResNet where i only added a Dense layer with the number of classes and to flatten the images. We again added more complexity just as with VGG16 but again we saw little improvement on these models so we decided to keep it simple because it was giving the best results.

With my tranfer learning models I used another parameter called callback which allowed me to have EarlyStopping which in entails that our model be stopped when essentially there is no improvement in this case "val_loss". This is what led me to have only 22 epochs for our final model.

# Results

**ResNet MODEL**

Training:
        Loss=0.4442575076
        Accuracy=0.8325042823
         
Validation:
        Loss=0.4181249711
        Accuracy=0.8417360008



--------------------------------------



**VGG_16 MODEL- FINAL MODEL PROPOSED**

**Training:**
        Loss=0.2025
        Accuracy=0.9356
         
**Validation:**
        Loss=0.3186
        Accuracy=0.8736
        
<img width="329" alt="Screen Shot 2021-01-15 at 8 54 49 AM" src="https://user-images.githubusercontent.com/67808057/104755722-ab992b00-570f-11eb-95d2-76b5dfc45747.png">



<img width="439" alt="Screen Shot 2021-01-11 at 10 29 21 PM" src="https://user-images.githubusercontent.com/67808057/104755828-d3888e80-570f-11eb-91a9-73a198d6bded.png">


**Confusion Matrix of Final Model**


<img width="757" alt="Screen Shot 2021-01-11 at 10 55 00 PM" src="https://user-images.githubusercontent.com/67808057/104756288-7b9e5780-5710-11eb-941e-bdac39f95fe8.png">

Here we can see that we had a problem with our Normal and Viral_Pneumonia classes and it was our last hurdle before getting to that above 90% validation accuracy score and minimal validation loss which is most important! In the future we would have individually preprocess that Virual_Pneumonia class for more accurate results. Overall we were satisfied with the recall (sensitvity) of our Covid19 and Normal classes thus this led to a higher average.


As a reminder for looking at this confusion matrix: 

**Precision** answers the question, “When it predicts the positive result, how often is it correct?”
  
**Recall** answers the question, “When it is actually the positive result, how often does it predict correctly?”

My branch has all the information needed to look into this final model if desired!
