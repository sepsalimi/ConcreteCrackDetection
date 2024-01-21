# ConcreteCrackDetection

For my Capstone for BrainStation's Data Science bootcamp, I trained a model on 33,000 images of 256x256 cracks in concrete. The following parameters were fine tuned and these were the optimal results:

![image](https://github.com/sepsalimi/ConcreteCrackDetection/assets/75538784/b3e228cb-2e50-4ee5-b27a-892cce204b6f)

These paramters led to a 90% F1 Score model.

The following image are

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
