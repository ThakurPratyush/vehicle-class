# vehicle-class
classification of vehicles

b) Vehicle classification:

1)	Preparing the dataset : We took the dataset and then converted all the images into 512x512.Then we put all the data into the train folder and the categories are encoded into the name only ex: in the car the name of the image would be of form 000001_08_Car.jpg.

2)	Image Augmentation : Performed to increase size of the dataset , we use OneOf method given by pytorch and use techniques like : HorizontalFlip, IAAAdditiveGaussianNoise() ,MotionBlur and a number of other techniques.We group them into functions and associate a probability as OneOf function parameter.

3)	Visualizing train images : Random 10 images are visualized to check if the dataset is being linked properly or not ,using the plt() function.

4)	Imbalanced dataset problem : Classes are not uniformly distributed in the dataset like the number of images for car is far more than any other vehicle So to deal with this problem We can use the weighted sampling approach. This means that we adjust probabilities of sampling a particular class by taking an inverse probability of that class.It was able to improve performance by a small amount.
5)	Preparing training and validation PyTorch loaders: In this step we would firstly check that if the set is balanced or imbalanced if imbalanced then balance it first and then we would load the data into train and validation sampler .Using the function Dataloader() in pytorch we would then make train and test loaders using the batch size of 32.
6)	Training : We use the transfer learning method.Transfer learning allows us to use the model trained for some other task to be used for our task.We used resnext50_32x4d for our task .We use the pretrained model and load all the parameters .While doing training we would then retrain the last layer of the model using fully connected layer and our train loaders (train loaders also have the dataset information).We use SGD optimized and weight decay of 0.001.Training is done for 10 epochs ,after it overfitting was observed.
![image](https://user-images.githubusercontent.com/42847642/123460069-b633e680-d604-11eb-8dc8-2c20da9f7b0f.png)

 
Fig6. Resnext50_32x4d pretrained model used 
7)	Predictions using  TTA on test set : Test-time augmentation is used to predict classes from differently augmented images.

 Steps :
1.	Apply different types of augmentation techniques on same image
2.	Taking the average from class probabilities obtained
3.	Choose a class with max. probability.
 
 ![image](https://user-images.githubusercontent.com/42847642/123460110-c51a9900-d604-11eb-88c2-3b74021cafa4.png)

                                            Fig7. Flow chart for vehicle classification

![image](https://user-images.githubusercontent.com/42847642/123460128-cba91080-d604-11eb-976d-8eef74abc85c.png)



 
 Fig8. Transfer learning block diagram
