cmake_minimum_required(VERSION 2.8)

# get tensorflow include dirs, see https://www.tensorflow.org/how_tos/adding_an_op/
execute_process(COMMAND python3 -c "import tensorflow; print(tensorflow.sysconfig.get_include())" OUTPUT_VARIABLE Tensorflow_INCLUDE_DIRS)

# C++11 required for tensorflow
set(CMAKE_CXX_FLAGS "-std=c++11 -fPIC -D_GLIBCXX_USE_CXX11_ABI=0 ${CMAKE_CXX_FLAGS}")

# build the actual operation which can be used directory
include_directories(${Tensorflow_INCLUDE_DIRS})
add_library(nms SHARED nms.cc)