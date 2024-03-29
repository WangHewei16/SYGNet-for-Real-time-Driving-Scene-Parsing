# SYGNet-for-Real-time-Driving-Scene-Parsing

### Executive summary
In this research, the SYGNet is proposed to further strengthen the scene parsing ability of autonomous driving under complicated road conditions. SYGNet includes feature extraction component and SVD-YOLO GhostNet component. SVD-YOLO GhostNet component combines Singular Value Decomposition (SVD), You Only Look Once (YOLO) and GhostNet. In the feature extraction component, we propose an algorithm based on VoxelNet to extract point cloud features and image features. In SVD-YOLO GhostNet component, the image data is decomposed by SVD, and data with stronger spatial and environmental characteristics is obtained. YOLOv3 are used to obtain the future map, then convert to GhostNet, which to realize the real-time scene parsing. We use KITTI data set to do experiments and the results show that the SYGNet is more robust and can further enhance the accuracy of real-time driving scene parsing.


### Code Organization
All code are written in `Python3`.


### Model
SYGNet is composed of two modules: feature extraction module and SVD-YOLO GhostNet module. The first module is used to extract important perceptual scene features. The second module is responsible for using the model and training parameters to obtain high accuracy perceptual recognition results. `Architecture of FE.png` illustrates the architecture for feature extraction module.


### Data
We use KITTI dataset which is available in this link (http://www.cvlibs.net/datasets/kitti/eval_object.php?obj_benchmark=2d)

### Experiment figure
* `Figure1-ablation.png`: This figure illustrates the SVD-YOLOv3 algorithm has the best performance in the whole test process compared with the performance of YOLOv3, RCNN, SVD-YOLOv2, SVD-RCNN and SVD-YOLOv3. Hence, we decide to use SVD-YOLOv3 as the beginning component of the second module in FesygNet.

<div align=center><img src="https://github.com/WangHewei16/SYGNet-for-Real-time-Driving-Scene-Parsing/blob/main/Figure1-ablation.png?raw=true" width="300"/></div>

* `Figure2-qualitative.png`: This figure shows the qualitative results on the KITTI data set. Different colors mark different categories of objects
recognized. We can see that our perceptual recognition effect is good, and we have good recognition processing on the edges of two different types of objects.
<div align=center><img src="https://github.com/WangHewei16/SYGNet-for-Real-time-Driving-Scene-Parsing/blob/main/Figure2-qualitative.png?raw=true" width="500"/></div>

* `Figure3,4,5,6-quantitative.jpg`: This figure shows the experiment about the accuracy’s changes of different models in four different scene modes (cars,
human, road and All mode) with the increase of training time. We can see that at the end of the training, our proposed FesygNet has far surpassed other comparison methods. In the “All mode” scene, FesygNet ranks first among these methods in the whole process, which can prove the superiority of our method in accuracy and training optimization.
<div align=center><img src="https://github.com/WangHewei16/SYGNet-for-Real-time-Driving-Scene-Parsing/blob/main/Figure3-quantitative.png?raw=false" width="250"/><img src="https://github.com/WangHewei16/SYGNet-for-Real-time-Driving-Scene-Parsing/blob/main/Figure4-quantitative.png?raw=false" width="250"/></div>
<div align=center><img src="https://github.com/WangHewei16/SYGNet-for-Real-time-Driving-Scene-Parsing/blob/main/Figure5-quantitative.png?raw=false" width="250"/><img src="https://github.com/WangHewei16/SYGNet-for-Real-time-Driving-Scene-Parsing/blob/main/Figure6-quantitative.png?raw=false" width="250"/></div>

### Experiment table
* `Table1.png`: This table demonstrates the SVD-YOLOv3 algorithm has the best performance in five different mode (Cars, People, Edge, Side and Light mode) in KITTI data set, which further confirmed that SVD-YOLOv3 has good performance in perceptual recognition. Hence I decide to use SVD-YOLOv3 in this module.
<div align=center><img src="https://github.com/WangHewei16/SYGNet-for-Real-time-Driving-Scene-Parsing/blob/main/Table1.png?raw=true" width="320"/></div>

* `Table2.png`: This table show the comparison with different methods in three different scene modes (cars, human and edge mode), it can be found that the FesygNet has good performance in terms of reliability, which verifies the reliability under the same data set.
<div align=center><img src="https://github.com/WangHewei16/SYGNet-for-Real-time-Driving-Scene-Parsing/blob/main/Table2.png?raw=true" width="390"/></div>

