
# SaveIT

<img src="https://github.com/Ihssene-Brahimi/SaveIT/blob/master/SaveIT%20logo%20white%20-03.png" alt="dziribert drawing" width="18%" height="18%" align="right"/>

SaveIT is an automated system developed based on Artificial intelligence and deep learning. The main goal of this artificial protection system is to offer the best supervision on forests against fire, it ensures an early detection of fire and sends a quick alert to the nearest firefighting department. in addition to many added values that will help in resisting wildfires, sensibilizing people to be more aware and getting the necessary precautions while facing these kinds of natural disasters.


## DataSet

To make sure our learners can handle forest fires from high placed cameras, the data collected was a set of aerial wildland images from weather towers, UAVs... This dataset included smoke, fire and non-fire images captured from far places at their first stage of development to ensure the early detection. After manual filtration, we created a single integrated dataset containing 737 smoke images and 4300 fire/non fire images.


## Modals 

In order to ensure that our model is robust to diverse scenarios and issues, we proposed three deep learners to make decisions together : 
-  **Yolov5** : acts as an object detector, it detects smoke locations in images by generating candidate boxes, during the day.
-  **EfficientDet** : is employed to detect fire locations at night, but it treats fire-like objects as fire.To avoid this issue, the output of the latter is cropped to the bounding boxes with top confidence and then fed to the classification model EfficientNetv2.
-  **EfficientNet** : acts as a binary classifier at night, and will determine whether the image contains fire objects   
Furthermore, integrating three learners will not affect the efficiency of the model, because they are structurally independent, and each one has a separate process responsible for it.

## Training

Different strategies were applied to train the three learners: Yolov5, EfficientDet, and EfficientNet. 
Object detectors, namely Yolov5 is trained with smoke images, while EfficientDet is trained with forest fire images. 
The image classifier, namely EfficientNet, is trained with forest fire and no fire images. 
Note that non-fire images contain normal images, and images with fire-like objects for instance: sunset. 
YOLOv5 and EfficientDet are built up by Pytorch and trained on colab and kaggle respectively. EfficientNetv2 is built by TensorFlow and trained on colab. The details of our training strategy are shown in the following table:



| Model     | Train    | Test | Optimizer | LR   | Batch size| Epochs| Interface |
| :-------- | :------- | :--- | :-------- | :----| :---------| :-----| :---------|
| `YOLOv5`  | 2190     | 162  | ADAM SDG  | 0.01 |  16       | 100   | Pytorch   |
| `EfficientDet`  | 3858     | 308  | ADAM   | 0.0001 |  8       | 100   | Pytorch   |
| `EfficientNet`  | 3858     | 308  | RMSprop    | 0.0005 |  16       | 10   | Tensorflow  |


## Demo



## Authors

- [@Meriembek](https://github.com/MeriemBek)
- [@Tiziri-k](https://github.com/Tiziri-k)
- [@Ilhembekkr](https://www.github.com/Ilhembekkr)
- [@Assalaabnk](https://www.github.com/assalaabnk)
- [@Ihssene-nasa](https://github.com/ihssene-nasa)

## Note
This work was pulished in the 3rd ACM International Conference on AI in Finance ICAIF 2022 - New York, NY. And in the Africa Research Schowcase Day - Deep Learning Indaba, Tunisia 2022.

    
