# ConcreteCrackDetection

For my BrainStation's Data Science bootcamp capstone, I trained and fine-tuned a model on 33,000 images of 256x256 cracks in concrete. This model was combined with Meta's Segment Anything Model to isolate the foreground of inspection images of concrete infastructure. 

![image](https://github.com/sepsalimi/ConcreteCrackDetection/assets/75538784/a2546b75-5dbd-479b-aa8c-e9617b26adbf)

The following is the fine-tuning process of the crack detection model:

![output-2](https://github.com/sepsalimi/ConcreteCrackDetection/assets/75538784/9d1524cf-d291-4ad4-b2d9-ea2bf3d21081)

The optimum paramters led to a 87% F1 Score model and the final results are shown below.

![image](https://github.com/sepsalimi/ConcreteCrackDetection/assets/75538784/b0e47d4e-dfc3-4af1-8510-7ea8e91c84ad)

![image](https://github.com/sepsalimi/ConcreteCrackDetection/assets/75538784/3d9e1b64-c813-4422-b439-740bfbd639a5)

![image](https://github.com/sepsalimi/ConcreteCrackDetection/assets/75538784/8b53aaa5-63a3-4b77-baeb-dcfb6746349c)

More information can be read through the PDF report and fine-tuning notes below:

** Fine Tuning Notes **:

**Layers:**

- Switching from 7 layers to 6 layers loss improved. (Run 1 to 2)
- Switching from 6 layers to 5 increased loss.  (Run 2 to 3)

Conclusion: 6 layers is optimal

**Kernels:**

- Switching from 5,5 to 3,3 improved loss. (Run 4 to 5)

Conclusion: 3,3 kernels are optimal

**Kernel Initializer**

- Switching to he_uniform increased loss. (Run 5 to 6)

Conclusion: he_normal > he_uniform

**Activation Function**

- Switching from ReLu to Leaky ReLu (0.01) improved loss. (Run 6 to 7)
- Leaky ReLu (0.1) improved loss (Run 7 to 8)
- Leaky ReLu (0.5) increased loss. (Run 8 to 9)
- Switching to 0.25 increased loss (Run 9 to 10)
- Switching to 0.375 improves loss. Best so far. (Run 10 to 11)
- Leaky ReLu switch Run 7 to 8 also included hu_normal switch. Therefore switched to regular ReLu and saw (Run 13 to 16 back and forth. Leaky Relu 0.375 is still optimal)

Conclusion: Leaky ReLu with coefficient 0.375 is optimal

**Optimizer:**

- Switched to RMSprop and loss increased (Run 11 to 12)
- Switched to SGD with momentum 0.9 and loss increased even more. Least effective. (Run 12 to 13)

Conclusion: Adam is optimal


**Loss Function Weights:**

- Increased weight of positive from 1 to 1.1. Improved loss (Run 17 to 18)
- Increased weight of positive to 1.5. (Run 18 to 19). Overfitting problem.
- Reverted positive weight to 1.1, decreased negative weight to 0.9. Seems like beginning to overfit. Wiil not explore anymore (Run 19 to 20)

Conclusion: negative weight = 0.9, postive weight = 1.1 is optimal

**The final training model is:** 
- Sample: 0.1, 
- Batch: 20, 
- bin_crossentropy(0.9,1.1), 
- Leaky Relu (0.375), 
- he_normal, 
- adam=0.0001, 
- 6 layers, 
- kernel(3,3)

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
