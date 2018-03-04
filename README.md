# Video Surveillance for Road Traffic Monitoring
Master in Computer Vision - M6 Visual Analysis

## Group 06
Name: Group 06 
Juan Felipe Montesinos(jfmontgar@gmail.com)  
Ferran Carrasquer(ferrancarrasquer@gmail.com)  
Yi Xiao(yi.xiao@e-campus.uab.cat)  

<img src=header.jpeg" width="200" height="200">

## Abstract   
The goal of this 5-week project is to learn the basic concepts and techniques related to video sequences processing, mainly for surveillance applications.

## Framework structure
Framework is OOP-based.  
* Each motion estimation algorith is coded as a inheritance class.
* Each class has specific methods to model background, evaluate, plot and run estimations.

### Main class
All the classes have the following attributes:

name: [str] Brief description up to you. For example dataset name.  
im_dir: [str] Frame's folder directory  
gt_dir: [str] Groundtruth's folder directory  
color: [bool] [default=False] Using greyscale (false) or RGB images (true)  

### gaussian1D
This class allows to perform a gaussian-based motion estimation. One gaussian (mean,std) per pixel is computed

Aditional attributes:  
mean: MxN(xc if color) numpy array which contains mean per pixel (per channel)  
std:  MxN(xc) numpy array which contains std per pixel (per channel)  

Methods:  
* **get_1D(frame_list)**
Compute gaussian for every pixel in every channel and store them in the mean-std attributes.

*frame_list:* list containing names of each frame which will be used to compute the gaussian background model. These frames
are supossed to be stored in im_dir folder

* **get_motion(im,th)**
Computes probabilistic motion estimation for a given image (im) using the model saved in the instance.
*im:* [cvMat] RGB Image opened with cv2.imread procedure.
*th:* [numerical] threshold for tunning probability of being motion.
		if |Pixeli-MEANi|> (std+2)*th 

* **evaluateSeveralFrames(frame_list,gt_list)**
Return precision, recall and F1 values for a set of frames (absolute values, not averaging frames)

*frame_list:* list containing names of each frame which will be used to compute the evaluation. These frames
are supossed to be stored in im_dir folder.  
*gt_list:* list containing names of each groundtruth which will be used to compute the evaluation. These gt
are supossed to be stored in gt_dir folder.  

Note: frames and their related grountruth images MUST share the same position in their respective lists.

