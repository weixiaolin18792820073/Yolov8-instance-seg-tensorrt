author : weixiaolin  2024/03/15
based on the yolov8，provide pt-onnx-tensorrt transcode and infer code by c++

	1、下载代码
	https://github.com/weixiaolin18792820073/Yolov8-instance-seg-tensorrt.git
	2、修改Cmakelist.txt
	1）cuda配置
		去掉第20行和21行前的#
		注意：下面的路径时cuda的安装路径/usr/local/cuda
		#include_directories(/usr/local/cuda/include)
		#link_directories(/usr/local/cuda/lib64)
	2）tensorrt配置
		(1) x86_64架构
		include_directories(/opt/perception/software/TensorRT-7.1.3.4/include)
		link_directories(/opt/perception/software/TensorRT-7.1.3.4/lib)
		其中，/opt/perception/software/TensorRT-7.1.3.4是tensorrt的压缩包解压路径
	     （2）aarch64(NVIDIA Jetson AGX Xavier)
	include_directories(/usr/include/aarch64-linux-gnu)
	link_directories( /usr/lib/aarch64-linux-gnu)
	
	
	
	
	3、编译运行【模型转换+推理测试】
	# Yolov8-instance-seg-tensorrt
	based on the yolov8，provide pt-onnx-tensorrt transcode and infer code by c++
	# mkdir build  
	# cd build  
	# cmake ..  
	# make  
	# sudo ./onnx2trt ../models/yolov8n-seg.onnx ../models/yolov8n-seg.engine  
	# sudo ./trt_infer ../models/yolov8n-seg.engine ../images/bus.jpg  
	![image](https://github.com/fish-kong/Yolov8-instance-seg-tensorrt/blob/main/x.jpg)
	
	
	
	注意：opencv需要安装在系统环境中; 若采用源码安装，则需要特殊指定CMakeList.txt，否则，会找不到opencv







