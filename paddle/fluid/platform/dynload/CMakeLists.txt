cc_library(dynamic_loader SRCS dynamic_loader.cc DEPS glog gflags enforce)

list(APPEND CUDA_SRCS cublas.cc cudnn.cc curand.cc nccl.cc)
if (CUPTI_FOUND)
    list(APPEND CUDA_SRCS cupti.cc)
endif(CUPTI_FOUND)
nv_library(dynload_cuda SRCS ${CUDA_SRCS} DEPS dynamic_loader)
cc_library(dynload_warpctc SRCS warpctc.cc DEPS dynamic_loader warpctc)
