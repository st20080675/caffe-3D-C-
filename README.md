# caffe 3D C++ API simple example
---
take a look at CaffeNet C++ Classification example
this is a simple example for 3D
pay attention to the CMakeLists.txt and how to load the 3D data
---
----- input parameter/dir ----------------
the model I use is trained on http://rgbd-dataset.cs.washington.edu/dataset/rgbd-scene-labeling/
find a .pcd file to classify, specify the path infunction void PCL_Classifier::m_get_pcl()

-------------- my command ------------------------
./build/caffe_my model/3DCNN_deploy.prototxt  model/3DCNN_augmented__iter_8000.caffemodel  model/class_label_name.txt

--------- my output --------------------------------
0.9844 - "class 3   cereal box"
0.0151 - "class 5   soda can"
