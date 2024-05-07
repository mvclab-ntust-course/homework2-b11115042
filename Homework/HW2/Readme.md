# Install nvidia/cuda
```
docker pull nvcr.io/nvidia/cuda:latest
```
# Test nvcc 
```
docker run --gpus all -it nvcr.io/nvidia/cuda:latest /bin/bash
```
# run in container to test 
```
nvcc --version
```
### using VcXsrv as Xhost
# build irti
```
docker build -t <containerName> .
```
# run 
``` 
docker run <containerName>
```
### if Error occured 
```
Attempting to deserialize object on a CUDA device but torch.cuda.is_available() is False. If you are running on a CPU-only machine, please use torch.load with map_location=torch.device('cpu') to map your storages to the CPU.
```
# try 
```
docker run --gpus all -it <containerName>
```

