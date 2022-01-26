# Fesyg-System

### Executive summary
In this research, the FesygNet is proposed to further strengthen the perception ability of autonomous driving under complicated road conditions. FesygNet includes feature extraction module and SVD-YOLO GhostNet module. SVD-YOLO GhostNet module combines Singular Value Decomposition (SVD), You Only Look Once (YOLO) and GhostNet. In the feature extraction module, we propose an algorithm based on VoxelNet to extract point cloud features and image features. In SVD-YOLO GhostNet module, the image data is decomposed by SVD, and data with stronger spatial and environmental characteristics is obtained. YOLOv3 are used to obtain the future map, then convert to GhostNet, which can generate more feature maps with fewer parameters. In the process of system model evaluation, we use public data sets to do experiments and the results show that the FesygNet proposed in this paper is more robust and can further enhance the accuracy of autonomous driving perception.


### Code Organization
All code are written in Python3


### Model
FesygNet is composed of two modules: feature extraction module and SVD-YOLO GhostNet module. The first module is used to extract important perceptual scene features. The second module is responsible for using the model and training parameters to obtain high accuracy perceptual recognition results. 

* `Architecture diagram of feature extraction module.png`: This figure illustrates the architecture for feature extraction module, which is the first module in FesygNet. Feature extraction learning includes two branches: LiDAR Stream and Camera Stream, which extract point cloud features and image features respectively. The VFE layer designed by VoxelNet is inspired by PointNet. The VFE layer is composed of a large number of stacked full connection layers (FCN). Through the mapping operation, the features of the internal points of each voxel grid can be aggregated to encode the surface shape information inside the voxel. Here, FCN is composed of linear layer, batch normalization (BN) layer and ReLU layer, When a point wise feature representation is obtained, element by element maximization is used (Element-wise MaxPooling) to obtain the local aggregation features. Finally, in order to strengthen the point level features, the point level features output by FCN layer are spliced to obtain the final point level combination features. The voxel feature extractor designed in this paper consists of two VEF layers. For the camera branch, a 2D convolution neural network similar to ResNet is designed to extract the point level features Take the image features corresponding to the point cloud data, which can capture deeper image texture features to achieve better modal fusion. Then the result of two streams will merge in feature fusion stage, where has an attention fusion layer to deal with the combined data. After that, it will convert to Region Proposal Network (RPN) in 3D box estimation stage. Finally, the future map with extracted feature will be generated.
<div align=center><img src="https://github.com/WangHewei16/FesygNet-for-Autonomous-Driving-Recognition/blob/main/Architecture%20diagram%20of%20feature%20extraction%20module.png?raw=true" width="900"/></div>


* `Architecture diagram of SVD-YOLO3 structure.png`: This figure illustrates the architecture for SVD-YOLO3 structure in the second module in FesygNet. After finishing the operations of SVD-YOLO algorithm in this module, I connect a GhostNet at the end of the module. The GhostNet is the plug-and-play module that converts the original model into a more compact model while maintaining comparable performance.
<div align=center><img src="https://github.com/WangHewei16/FesygNet-for-Autonomous-Driving-Recognition/blob/main/Architecture%20diagram%20of%20SVD-YOLO3%20structure.png?raw=true" width="900"/></div>

### Data
We use KITTI dataset which is available in this link (http://www.cvlibs.net/datasets/kitti/eval_object.php?obj_benchmark=2d)

### Experiment figure
<div align=center><img src="https://github.com/WangHewei16/FesygNet-for-Autonomous-Driving-Recognition/blob/main/Figure1-ablation.png?raw=true" width="300"/></div>

<div align=center><img src="https://github.com/WangHewei16/FesygNet-for-Autonomous-Driving-Recognition/blob/main/Figure2-qualitative.png?raw=true" width="500"/></div>

<div align=center><img src="https://github.com/WangHewei16/FesygNet-for-Autonomous-Driving-Recognition/blob/main/Figure3-quantitative.jpg?raw=false" width="250"/><img src="https://github.com/WangHewei16/FesygNet-for-Autonomous-Driving-Recognition/blob/main/Figure4-quantitative.jpg?raw=false" width="250"/><img src="https://github.com/WangHewei16/FesygNet-for-Autonomous-Driving-Recognition/blob/main/Figure5-quantitative.jpg?raw=false" width="250"/><img src="https://github.com/WangHewei16/FesygNet-for-Autonomous-Driving-Recognition/blob/main/Figure6-quantitative.jpg?raw=false" width="250"/></div>
### Experiment table
<div align=center><img src="https://github.com/WangHewei16/FesygNet-for-Autonomous-Driving-Recognition/blob/main/Table1.png?raw=true" width="350"/></div>

<div align=center><img src="https://github.com/WangHewei16/FesygNet-for-Autonomous-Driving-Recognition/blob/main/Table2.png?raw=true" width="350"/></div>

<div align=center><img src="https://github.com/WangHewei16/FesygNet-for-Autonomous-Driving-Recognition/blob/main/Table3.png?raw=true" width="350"/></div>
