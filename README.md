# 277B_final_code
link to dataset :https://www.kaggle.com/datasets/awsaf49/brats20-dataset-training-validation (note that patient 355 mask file is incorrectly named, must change it to match the others.)

start with 3d_unet.ipynb note book, it has directions on how to create augmented data with the 3d_unet_aug.ipynb. It takes ~12 hours to train the model. 

## Results
<img width="761" alt="Screenshot 2025-03-13 at 8 17 51 PM" src="https://github.com/user-attachments/assets/aa2ac621-4338-45b4-9a32-e50a78f81bb1" />
<img width="778" alt="Screenshot 2025-03-13 at 8 17 41 PM" src="https://github.com/user-attachments/assets/726a9ebb-4ac6-4fbb-a387-5fd980fb9528" />
<img width="1002" alt="Screenshot 2025-03-13 at 7 56 09 PM" src="https://github.com/user-attachments/assets/00d44a55-2d9e-449b-a821-274076505ecb" />
<img width="772" alt="Screenshot 2025-03-13 at 8 07 53 PM" src="https://github.com/user-attachments/assets/e4b387c8-5bd9-456f-afb1-c906fda95328" />
<img width="866" alt="Screenshot 2025-03-13 at 8 17 24 PM" src="https://github.com/user-attachments/assets/13f9a665-6ee0-4464-b389-8a9bf1ce31b3" />
<img width="909" alt="Screenshot 2025-03-13 at 8 18 02 PM" src="https://github.com/user-attachments/assets/2caa1730-2a26-498a-b8fc-d2339ad5122f" />

## Conclusion

While the accuracy of both the models, with and without augmentation, displayed
reliability of the model, the model with augmentation performed slightly better, improving from
93.07% to 97.82%. The dice and IOC coefficients decreased from 0.8851 to 0.7130
and from 0.8114 to 0.5617, respectively. The reason why the accuracy increased but
the coefficients decreased, could come from the model’s prediction of non-tumor voxels. In
medical image segmentation, the amount of non-tumor voxels can heavily outweigh the presence
of tumor voxels. Because accuracy is the measure of the proportion of correctly identified
voxels, if the model has increased its accuracy in labeling the majority of the voxels, then it can
increase the accuracy. We can visualize this by seeing the reduction in the amount of false
positives in the Ground Truth Mask vs Predicted Mask scans. A decrease in these coefficients
implies that the model has a reduced ability to detect the true positive voxels. We can see this in
the differences in the Ground Truth Mask vs Predicted Mask scans, where the model with
augmentation displays a more conservative approach to the classification of tumor voxels. This
idea coupled with the idea that the presence of non-tumor voxels heavily outweighs the
tumor-voxels, shows us that our model with augmentation may be overpredicting the non-tumor
voxels, leading to a higher accuracy, and, therefore, a decrease in overlap between the ground
truth and predicted masks, leading to a lower dice and IOU score.

Overall, while the model demonstrated strong potential in accurately segmenting brain tumors
from MRI scans, the present challenge is to balance the model’s ability to generalize across new
data against its understanding of training data. The current implementation of the model only
consists of basic preprocessing, the addition of feature engineering such as textural feature
analysis which can be achieved through Gabor or amplifying the transition in tumor edges
through Sobel Edge are critical to further enhance the diagnostic accuracy and reliability of this
model. In future implementations this model could also benefit from re-evaluation of
augmentation techniques. Moreover, implementing a loss function that heavily penalizes false
negatives could also help focus the model




