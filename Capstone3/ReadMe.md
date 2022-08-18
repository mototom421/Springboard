# Intro:

Chest X-rays are a quick and inexpensive diagnostic tool used in emergency rooms and primary care all over the world. They have proven themselves to be relatively reliable but misdiagnosis is still a large problem compared to other radiographic techniques of this region (ie chest CT or Ultrasound). One meta-analysis from the Society of Critical Care Medicine found that chest X-rays have an overall sensitivity of 48%, whereas Ultrasound sensitivity was 95% and both had similarly high specificities of 92-94%. It seems that either the images are not showing pathology or radiologists are not able to effectively diagnose based on the images. The American Journal of Emergency Medicine puts the sensitivity of chest X-rays for pneumonia specifically to be between 38% and 76%. It is my hope that machine learning tools, such as convolutional neural networks, may be able to diagnose based on image data better than human experts.


# Data:

In this project I aim to make a model that performs at least as well as human experts using data from Guangzhou Women and Children’s Medical Center. There are 5863 chest X-ray images of pediatric patients between 1 and 5 years old. Each image is labeled as Normal or Pneumonia. Images labeled Pneumonia were further classified into Bacterial/Viral categories. These X-rays were taken during routine visits and analyzed by 2 professional radiologists. 


# Image Processing:

Reshaping all these images results in different zoom values and some stretching/shrinking of image dimensions. The images were also each unique in their perspective of the patient, with some patients at an angle with respect to the X-ray machine. To best train a CNN model, ImageDataGenerator was used to create unique batches of images with different rotations, zoom, width shift and height shift. This creates more unique data where these arbitrary differences are not highly valued by the CNN model. These images were then randomly visualized to ensure no major loss in information was taking place. This function also normalized mean pixel value and their standard deviation to 0 and 1 respectively. 

# Modeling:

My CNN model was made up of 5 convolutional/pooling layers with a number of dropouts to minimize overfitting. It was then fit to the training data which was created from a subset of the original train set. The validation data was created from the corresponding subset of the original train data. Two callbacks were created so that the model would alter parameters or stop if an increase/decrease in specific metrics was not seen in a set number of epochs

Our model had accuracy of 0.88, sensitivity of 83%, roc_auc of 0.966



# Conclusion:


In conclusion it seems that CNN modeling can diagnose pneumonia with much higher accuracy and sensitivity than human experts. This leaves us with 2 possible solutions: start using CNN models in the field of medicine or start using different diagnostic tools that have higher sensitivity when observed by human experts. 


