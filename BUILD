#!/bin/bash

echo "Will now build $1 with arg $2"

echo "Updating docker image from remote..."
git pull

echo "Building docker image..."
sudo docker build --build-arg TAG=$2 --tag=$1 .

echo "Converting to singularity..."
sudo docker run -v /var/run/docker.sock:/var/run/docker.sock -v $(pwd):/output --privileged -t --rm singularityware/docker2singularity --name $1 $1

echo "Transferring image to the server..."
rsync -rlt --info=progress2 $1.simg stark.criugm.qc.ca:/data/cisl/CONTAINERS
