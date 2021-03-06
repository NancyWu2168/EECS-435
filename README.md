# EECS-435
# Project: It’s time to save whales —— Humpback Whale Identification
The final project of EECS 435 in Northwestern  
Group member: Yunan Wu, Yifan Le

video address: https://www.youtube.com/watch?v=TN4PY52cAYk

# Background
As known, Japanese and Norway are the two major countries in the whaling industry. Japanese whaling incredibly began in the Jomon period[1] (the first 131st century - the first 4th century), which was considered as the significant part of fisheries. After the International Whaling Commission banned commercial whaling, Japan’s massive commercial whaling in the 20th century ended[2].But after centuries of intense whaling, recovering whale populations still have a hard time adapting to warming oceans and struggle to compete every day with the industrial fishing industry for food.

To aid whale conservation efforts, scientists use photo surveillance systems to monitor ocean activity. They use the shape of whales’ tails and unique markings found in footage to identify what species of whale they’re analyzing and meticulously log whale pod dynamics and movements. For the past 40 years, most of this work has been done manually by individual scientists, leaving a huge trove of data untapped and underutilized.  There lies the problem that effective and precise identification is able to lead to a better compact on both whale conservation and natural regulation. To be more specific, the International Union for Conservation of Nature has classified Minke whales as a “non-hazardou” species but the fin whale as an endangered species such that identification could be regarded as the important aid of whale conservation by avoid from waste on resources and finance.

In this project, we plan to use the whale tails to predict the classes of that whale. Not only does this method help scientists survive the whales but also a good way to record the whale activity. Tourists can upload the photo on the website they took by chance and get what does this whale belong to. This AI method is a new applications in many aspects.  


# Optimization steps 

## 1. [version1.0](https://github.com/NancyWu2168/EECS-435/blob/master/version1.0.ipynb)

For the first time, we simply do some analysis on the dataset. Training the model without any augmentation. Using Alexnet described as five convolutional layers and three fully connected layers, we train the first model and the final result is 63.8%, which seems not good enough.

However, we found that the number of classes is not balance (see in Figure 1). New whale contains 9664 images while some types only have 1 image. Then we decide to do data augmentation.

<p align=center>
  
  <img width="250" height="250" src="https://github.com/NancyWu2168/EECS-435/blob/master/file/1.png">

</p>

## 2. [version2.0](https://github.com/NancyWu2168/EECS-435/blob/master/version2.0.ipynb)

This time, we did augmentation operation. Enlarge the small number of whales by rotation, filp, whitening and let all the images to have similar sizes, which gives us accuracy of 83.1%

## 3. [version3.0](https://github.com/NancyWu2168/EECS-435/blob/master/version3.0.ipynb)

Through the forum, we realized that many people train the images seperately by first detecting the new whale and then training other images. We also train a model without the new whales. Then, the accuracy was improved to 86.7%

## 4. [version4.0](https://github.com/NancyWu2168/EECS-435/blob/master/version4.0.ipynb)

The background sea or the sky has a big impact when training the model, so we plan to extract only the whale tails in each image. In order to ao that, another model was trained based on the annotations (see in Figure 2). The iou reaches 82%. 

<p align=center>
  
  <img width="450" height="450" src="https://github.com/NancyWu2168/EECS-435/blob/master/file/2.png">

</p>

## 5. [version5.0](https://github.com/NancyWu2168/EECS-435/blob/master/version5.0.ipynb)

Finally, we trained the last model based on the images we extracted above. Inatead of using AlexNet, we use ResNet34, which has fewer parameters but with more features. Furthermore, we pretrained the model on ImageNet rather than training the model from scratch. The final result reaches 90%.


# Conclusion
In this project, we understand the process of optimization. Some small tricks were used in this optimization, such as augmentation, pre-training, which often takes more time than just training the model.





References

[1] Watson, Paul (June 27, 2006). "The Truth about "Traditional" Japanese Whaling". Dick Russel.

[2] "History of whaling". Japan Whaling Association. Retrieved 2013-08-16.

[3] https://happywhale.com/home

