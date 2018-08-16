# Tadpole-Tracker-Python
This is a computational system that applies computer vision and deep learning to record and analyze movement data of many *Xenopus laevis* tadpoles in real time, for neuroscience research. This is my undergraduate thesis, and is in collaboration with the neuroscience department at Bard College.

The program will be implemented in both Java and Python, to increase portability and allow wider access for researchers in biology. The Java code is available [here](https://github.com/alexander-hamme/Tadpole-Tracker).

-----

There are two major components of this tracker program: **Detection** and **Tracking**.
  * detection is the process of finding regions of interest (ROI) in each frame (image) from the video input stream
  * tracking is the process of connecting where each animal was in previous frames to its new position in sequential frames, 
    i.e. connecting ROIs to the corresponding tadpoles. This becomes complicated when tracking multiple animals, because of the potential for collisions and collusions. Therefore, trajectory prediction algorithms need to be implemented.

Approaches:

  * Detection: Convolutional neural networks will be the building block for the tadpole detection system. I trained deep neural networks for xenopus tadpole detection and localization using the [YOLOv2](https://pjreddie.com/darknet/yolov2/) architecture.

  * Tracking (specifically, trajectory prediction): I will train a Long Short-Term Memory (LSTM) recurrent neural network on recorded tadpole movement data. 

-----

Current Progress:

Running inferences on each video frame with a deep neural network is very computationally expensive, on a CPU it takes ~4-5 seconds per frame. Running on a GTX 1070 GPU, I recently reached 19 fps with accurate detection on tadpoles from a video stream, which is nearly fast enough to do (accurate) real-time analysis. The next step is to try to optimize this process to hit a higher fps rate, and then implement the trajectory prediction tracking system and embed it in the system.


###### Proof of Concept gif:

![Uh oh, it appears the gif didn't load. Please find the gif in the images folder of this repositiory.](/images/proof_of_concept.gif?raw=true "Proof of Concept")

<br>

###### Detection results of custom trained Yolo

![Uh oh, it appears the gif didn't load. Please find it as "yolo_detections.jpg" in the images folder of this repositiory.](/images/yolo_detections.jpg?raw=true "Detection Results")

###### More files will be added soon.
