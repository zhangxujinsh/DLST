## Deep Location-Specific Tracking

by Lingxiao Yang, Risheng Liu, David Zhang, Lei Zhang at The Hong Kong Polytechnic University.


#### Introduction
Deep Location-Specific Tracking (DLST) is an tracking framework based on deep convolutional networks, which decouples the tracking problem into two sub-tasks: a localization task and a classification task. The localization is a preprocess step to estimate the target location in the current frame. The output of localization with target position in the previous frames are both utilized to generate samples for further classification. The classification network is developed based on ''1x1'' convolution and global average pooling to reduce the overfitting problem online.

This code has been tested on Windows 10 64-bit and Ubuntu on MATLAB 2015a/2016b.


#### Installation

**Prerequisites**
	
1. MATLAB (2015a/2016b).

2. MatConvNet (with version 1.0-beta23 or above).
	
3. For GPU support, a GPU at least 2GB memory is needed. 
	
4. Cuda toolkit 7.5 or above (8.0) is required. Cudnn is optional. 

5. OpenCV 3.0 (3.1) and MexOpencv are needed if you want faster speed.

**How to run the Code**

1. Compile the MatConvNet according to the [website](http://www.vlfeat.org/matconvnet/)

2. Compile the OpenCV and MexOpenCV if you need faster speed. Otherwise, please comment the line 98
in ``utils/im_crop.m``, and uncomment the line 93-94 to use the matlab ``imresize`` function (around 2x slower).

3. Change the path to your local path in ``setupDLST.m`` and the local tracker model path in ``utils/getDefaultOpts.m (opts.model)``.

4. If you want create your own tracker model, please see the details in ``createDLST.m``. Currently, we only adopt VGG-M model in our paper.

5. For VOT2016 testing, please install the [VOT official toolkit](https://github.com/votchallenge/vot-toolkit), and simply 
copy the ``DLST\VOT2016\wrapper\tracker_DLST.m`` to your VOT workspace. 


#### Packed Results for OTB and VOT2016

It is very time consuming for running this code on entire OTB100 and VOT2016 datasets. Ususally it will take around 1 day for OTB100 testing (One-Pass), and 3 ~ 4 days for VOT2016 evaluation. You can simply download all pre-computed results from following links.

[BaiduYun](https://pan.baidu.com/s/1gfvfyjL) and [OneDrive](https://1drv.ms/f/s!AjoDviVXbtjXgyzr_Nnc16AUS_yO)


##### Results on OTB50

![OTB50](https://raw.githubusercontent.com/ZjjConan/DLST/master/resultPlots/otb50.png)

##### Results on OTB100

![OTB100](https://raw.githubusercontent.com/ZjjConan/DLST/master/resultPlots/otb100.png)


#### Citation
If you find DLST useful in your research, please consider citing:

	@inproceedings{yangDLSTMM17,
  		title={Deep Location-Specific Tracking},
  		author={Lingxiao Yang and Risheng Liu and David Zhang and Lei Zhang},
  		booktitle={Proceedings of the 25th ACM international conference on Multimedia},
  		year={2017},
  		organization={ACM}
	}

#### License

This software is being made available for research purpose only. 

We utilize or re-implement many functions from project [MDNet](https://github.com/HyeonseobNam/MDNet) and 
[RCNN](https://github.com/rbgirshick/rcnn). please check their licence files for details.
