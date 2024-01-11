# Build TensorFlow
```shell
0. brew install bazel
1. git clone https://github.com/tensorflow/tensorflow.git
2. cd tensorflow
3. ./configure
4. bazel build -c opt //tensorflow/lite:libtensorflowlite.dylib
5. TFLITE_HOME=`pwd` # for using this in next script for copy
```

# Create C++ project
* Add tflite header and libraries to project
```shell
0. mkdir tflite_cpp && cd tflite_cpp
1. mkdir -p thirdparty/include/tflite thirdparty/include/tflite/tensorflow thirdparty/lib/tflite/mac thirdparty/lib/tflite/ios
2. cp ${TFLITE_HOME}/bazel-bin/tensorflow/lite/libtensorflowlite.dylib thirdparty/lib/tflite/mac/
3. cp -r ${TFLITE_HOME}/tensorflow/lite thirdparty/include/tensorflow/lite
4. cp -r ${TFLITE_HOME}/bazel-bin/external/flatbuffers/_virtual_includes/flatbuffers thirdparty/include/tflite/
```

* copy ${TFLITE_HOME}/tensorflow/lite/examples/minimal folder CMakeLists.txt and minimal.cc file to tflite_cpp

# Build the project using cmake
```shell
0. mkdir build && cd build
1. cmake ..
2. make
3. cd ..
```

# Download tflite model

1. visit https://www.tensorflow.org/lite/examples/image_classification/overview and download starter model

# Run tflite_cpp executable
```shell
1. ./build/tflite_cpp models/mobilenet/mobilenet_v1_1.0_224_quant.tflite
```

