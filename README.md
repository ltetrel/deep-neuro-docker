# Deep-Neuro-Docker
Container for deep learning in neuroscience, working with jupyter notebook.
It is based from the official [tensorflow build](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/tools/dockerfiles) and includes the following:
- jupyter
- keras
- matplotlib
- nilearn
- numpy
- pandas
- scikit-learn 
- scipy
- sklearn
- tensorflow
- ubuntu:16.04

# Building
### Docker
Firt clone the repository:
```
git clone git@github.com:SIMEXP/deeplearning-docker.git
```
Or simply download the Dockerfile.

`cd` to the path where you have the docker file.

You can now build the docker container:
```
sudo docker build --tag=deep-neuro-docker .
```
If you want to change the tensorflow release, please use `TAG`.
For example if you want to enable nvidia gpu support:
```
docker build--build-arg TAG=-gpu --tag=deep-neuro-docker .
```
### Singularity

First install [Docker2Singularity](https://github.com/singularityware/docker2singularity).
Finally, convert the docker image:
```
sudo docker run -v /var/run/docker.sock:/var/run/docker.sock \
-v /Where/to/save/simg:/output \
--privileged -t --rm \
singularityware/docker2singularity \
deep-neuro-docker
```
