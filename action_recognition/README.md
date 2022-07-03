# VSA_pipeline

Action Video recognition pipeline with DeepStream.

To execute, run the command below.

```
python3 app.py
```
Required dependency: Flask, docker image from https://courses.nvidia.com/courses/course-v1:DLI+S-RX-02+V2/

  

You can get the docker image by executing
```
sudo docker run --runtime nvidia -it --rm --network host --memory=500M --memory-swap=4G --volume ~/nvdli-data:/nvdli-nano/data --volume /tmp/argus_socket:/tmp/argus_socket --device /dev/video0 nvcr.io/nvidia/dli/dli-nano-ai:v2.0.2-r32.7.1
```