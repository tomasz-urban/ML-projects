# Microcontrolers detection with yolov4 
## The goal

The goal is to prepare the data and train the model to detect microcontrolers in images

##  Description

1) Train the microcontrolers detector using yolov4 and data from repository:
https://github.com/TannerGilbert/Tensorflow-Object-Detection-API-Train-Model/tree/master/images

    Data:
    - training images: train folder
    - testing images: test folder
    - bbox description "ground truth", train - train_labels.csv
    - bbox description "ground truth", test - test_labels.csv

    Change bbox description from files train_labels.csv and test_labels.csv to files required by yolov4.
     
2) In configuration file (.cfg) set parameters for training.  

    2.1) parameters:

    width=416

    height=416	

    burn_in=100

    max_batches=1000

    policy=steps

    steps=800,900

    random=0

    2.2) the rest set just like in configuration file from notebook:
         https://colab.research.google.com/drive/1VNc-Ywrs1XmfHcsq-BWpXZ5Zv_A2FcFn?usp=sharing
         Pay attention to the number of classes and filters (if it's correct for the dataset).  



## Result

1. Prepare .png file of the loss function graph (during training).

2. Get the mAP metrics on the test set for the best weights (highest value of mAP metrics on the graph).
   Output in .txt file

    Example output:

    detections_count = 89, unique_truth_count = 7  
    class_id = 0, name = Arduino_Nano, ap = 33.33%   	 (TP = 0, FP = 0) 

    class_id = 1, name = Heltec_ESP32_Lora, ap = 50.00%   	 (TP = 0, FP = 0) 

    class_id = 2, name = ESP8266, ap = 45.00%   	 (TP = 1, FP = 1) 
    
    class_id = 3, name = Raspberry_Pi_3, ap = 100.00%   	 (TP = 1, FP = 3) 

    for conf_thresh = 0.25, precision = 0.33, recall = 0.29, F1-score = 0.31 
    for conf_thresh = 0.25, TP = 2, FP = 4, FN = 5, average IoU = 23.08 % 

    IoU threshold = 50 %, used Area-Under-Curve for each unique Recall 
    mean average precision (mAP@0.50) = 0.570833, or 57.08 % 
    Total Detection Time: 1 Seconds

 
3. Prepare detection results for test images (for the best weights checkpoint from training). Detekctions as print screen's or images.

    Test images:
    - IMG_20181228_102636.jpg
    - IMG_20181228_102641.jpg
    - IMG_20181228_102658.jpg
    - IMG_20181228_102706.jpg
    - IMG_20181228_102745.jpg
    - IMG_20181228_102749.jpg
    - IMG_20181228_102757.jpg

4. Prepare files with bbox description "ground truth" on the test images:
    - IMG_20181228_102636.txt
    - IMG_20181228_102641.txt
    - IMG_20181228_102658.txt
    - IMG_20181228_102706.txt
    - IMG_20181228_102745.txt
    - IMG_20181228_102749.txt
    - IMG_20181228_102757.txt

5. Get files used for training:
    - file with classes names (.names)
    - train.txt
    - test.txt
    - configuration file(.cfg)


## Useful links

1. https://towardsdatascience.com/yolov4-in-google-colab-train-your-custom-dataset-traffic-signs-with-ease-3243ca91c81d
    Traffic Signs Dataset detector training using yolov4
   
   https://colab.research.google.com/drive/1VNc-Ywrs1XmfHcsq-BWpXZ5Zv_A2FcFn?usp=sharing
   Google Colab Notebook for training YOLOv4 with custom dataset (traffic signs) 
   
   https://github.com/AlexeyAB/darknet
   Yolov4 repository

2. Data preparation, mAP, compilation, configuration etc.:
    - https://github.com/AlexeyAB/darknet
    - https://github.com/AlexeyAB/darknet#how-to-compile-on-linux-using-make
    - https://github.com/AlexeyAB/darknet#how-to-train-to-detect-your-custom-objects

3. Google colab(2.1) notebook compilation where for GPU we have to set "ARCH=" in Makefile file.
   Example for Tesla K80:
   ARCH= -gencode arch=compute_37,code=sm_37

    - https://stackoverflow.com/questions/62451222/cuda-error-no-kernel-image-is-available-for-execution-on-the-device?noredirect=1&lq=1


