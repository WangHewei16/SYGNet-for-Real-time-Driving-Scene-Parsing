# Fesyg-System

> Our research team plan to publish open-source code here in Frebruary 2022

In this paper, the Fesyg-System is proposed to further strengthen the perception ability of autonomous driving under complicated road conditions. Fesyg-System includes feature extraction module and SVD-YOLO GhostNet module. SVD-YOLO GhostNet module combines Singular Value Decomposition (SVD), You Only Look Once (YOLO) and GhostNet. In the feature extraction module, we propose an algorithm based on VoxelNet to extract point cloud features and image features. In SVD-YOLO GhostNet module, the image data is decomposed by SVD, and data with stronger spatial and environmental characteristics is obtained. YOLOv3 are used to obtain the future map, then convert to GhostNet, which 
can generate more feature maps with fewer parameters. In the process of system model evaluation, we use public data sets to do experiments and the results show that the Fesyg-System proposed in this paper is more robust and can further enhance the accuracy of autonomous driving perception.
