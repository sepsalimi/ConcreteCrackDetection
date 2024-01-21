# ConcreteCrackDetection

For my BrainStation's Data Science bootcamp capstone, I trained and fine-tuned a model on 33,000 images of 256x256 cracks in concrete. 

![output-2](https://github.com/sepsalimi/ConcreteCrackDetection/assets/75538784/9d1524cf-d291-4ad4-b2d9-ea2bf3d21081)

And these were the final results:

![image](https://github.com/sepsalimi/ConcreteCrackDetection/assets/75538784/b0e47d4e-dfc3-4af1-8510-7ea8e91c84ad)

![image](https://github.com/sepsalimi/ConcreteCrackDetection/assets/75538784/3d9e1b64-c813-4422-b439-740bfbd639a5)

![image](https://github.com/sepsalimi/ConcreteCrackDetection/assets/75538784/8b53aaa5-63a3-4b77-baeb-dcfb6746349c)

These paramters led to a 87% F1 Score model and the image below shows the tuning run losses, F1 score, and IoU coefficient score for the train and validation dataset.


![image](https://github.com/sepsalimi/ConcreteCrackDetection/assets/75538784/0327ffc1-8621-4763-8bdc-0f2326183a3d)

More information can be read through the PDF report.

------------------------

To Run:

The majority of the files in segment_anything are from META's package. 

The notebooks that I've created have to be in this folder to work properly.

The notebooks that are relevant are listed below.

----------------------------------------------


1) Download data folder from: https://drive.google.com/drive/folders/1QBIBmfQgNXEU4E7gvOvoSuTKTjYHOWAC?usp=share_link

2) Place download folder under sesgment_anything folder. It should be: "//segment_anything//data/"

3) Open UNET_Model.ipynb for EDA, Wrangling, and Preliminary Training

4) Open UNET_Model_Training&Testing.ipynb for Training and Testing

5) Open Image_Segmentation.ipynb for META's SAM object detection being utlized

6) Open CrackDetection.py for utilizing both META's SAM, and the UNET model I saved. This is not done yet and work in progress.
