# A real-time object detection magnifier iOS App

## Project Overview

Welcome to My capstone project. In this project, I will create a real time object detection magnifier, please follow below instruction to setup and run the environment. After running the whole process, you will get the classifier to detect hand and COCO objects. After import these classifiers in iOS App, below are some screenshots captured from final iOS App.

- __SSD detect hand__

| Normal  | Zoom in 3x |
|---|---|
|![](./images/SSD_hand.PNG =200x)|![](./images/SSD_hand_zoom.PNG =200x)|


- __SSD detect COCO__

| Normal  | Zoom in 3x |
|---|---|
|![](./images/SSD_COCO.PNG =200x)|![](./images/SSD_COCO_zoom.PNG =200x)|

- __YOLOv2 detect COCO__

|![](./images/YOLOv2_COCO.PNG =200x)|

- __Tiny YOLOv2 detect COCO__

|![](./images/TinyYOLOv2_COCO.PNG =200x)|

## Project Instructions

1. Pick one host system.
    - __Linux__: __Recommend__
    - __Mac__: Can just do the data pre-processing job.

2. Download docker image. I already setup all required software in this docker iamge, so just download and run it.
```
    docker pull dragon7/mlnd-Capstone
```

3. Run X Server in host system.
    - __Windows__: VcXsrv or Xming
    - __Mac__: XQuartz

4. Create a ___tmp__ folder in __$HOME__, to preserve the trained model file.

5. Run docker image.
    - __Linux__
    ```
        docker run --name mlnd -p 8888:8888 -p 6006:6006 \
        --net=host -e DISPLAY=10.0 -v $HOME/.Xauthority:/root/.Xauthority \
        -v $HOME/tmp:/root/tmp \
        -d dragon7/mlnd-capstone
    ```
    - __Mac__
    ```
        docker run --name mlnd -p 8888:8888 -p 6006:6006 \
        -e DISPLAY=[IP_ADDRESS]:0 -v $HOME/.Xauthority:/root/.Xauthority --privileged \
        -v $HOME/tmp:/root/tmp \
        -d dragon7/mlnd-capstone
    ```
    __NOTE:__ [IP_ADDRESS] should be changed to your valid IP address

6. Open browser and type below URI to Login to project.
```
    http://localhost:8888
    Password: root
```

7. Open project implementation file: `Project/capstone/implementation.ipynb`.

8. Change the kernel to match the pyton3 environment by using the drop-down menu (Kernel > Change kernel > python3). Then, follow the instructions in the notebook.

__Note__:  During the __%run egohands_setup.py__ step, if the popuped GUI can't stop normally, please stop the X Server in step 3 and continue. The X Server is only used for this step.
