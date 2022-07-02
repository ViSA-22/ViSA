# Deepstream Facenet

Face Recognition on Jetson Nano using DeepStream and Python.

## DeepStream Installation
`install-deepstream.sh` will install DeepStream and its dependencies
1. Download DeepStream using [this link](https://developer.nvidia.com/assets/Deepstream/5.0/ga/secure/deepstream_sdk_5.0.1_x86_64.tbz2)
2. get Jetpack version 
```
$ dpkg-query --show nvidia-l4t-core
nvidia-l4t-core 32.3.1-20191209225816
```
3. export needed variables
```
export JETPACK_VERSION=32.3
export PLATFORM=t210
export DEEPSTREAM_SDK_TAR_PATH=<path>
```
4. running installation script
```
chmod +x install-deepstream.sh
sudo -E ./install-deepstream.sh
```
5. Making sure installation is fine by running a sample app
```
cd /opt/nvidia/deepsteream/deepstream-5.0/sources/deepstream_python_apps/apps/deepstream-test1
python3 deepstream-test1.py /opt/nvidia/deepstream/deepstream-5.0/samples/streams/sample_720p.h264
```
take some time to compile the model and running the application for first time.

## App
This demo is built on top of Python sample app [deepstream-test2](https://github.com/NVIDIA-AI-IOT/deepstream_python_apps/tree/master/apps/deepstream-test2) 
 - Download [back-to-back-detectors](https://github.com/NVIDIA-AI-IOT/deepstream_reference_apps/tree/master/back-to-back-detectors) (the mode can detect faces). It is primary inference.
 - The secondary inference facenet engine. 
 - No changes regarding the tracker.
 - Note: embedding dataset (npz file) should be generate by your dataset.
 - Note: you should count avg mean and avg std for your dataset:
    - Put avg mean in offsets parameter and in the net-scale-factor parameter put (1/avg std) in classifier_config.txt to make facenet model work efficient.
 

### Steps to run the demo:

- Download models
  - https://drive.google.com/file/d/1tS6aVIrkK8U0BQ4gtHVr0xVx_4Ihu3YG/view?usp=sharing
- Change the model-engine-file path to the your facenet engine file in `classifier_config.txt`.
- `python3 deepstream_test_2.py`


## Reference
- https://github.com/riotu-lab/deepstream-facenet 

