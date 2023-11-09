# A_Docker_Example_for_ISICDM2023
This is a simple Docker example for ISICDM2023. nnUNet was used to generate the sample.
This example necessitates the installation of Docker on the server first.

# Step1

Copy all of the required files and models to the same directory, including the dockerfile, codes, model weights, shell script, and others:
```
mkdir teamname
cp <-r> your_files teamname
cd teamname
```
# Step2
Create a Docker image based on the Dockerfile:
```
docker build -t teamname .
```
Docker will mount the image named 'teamname' once you run this command.

# Step3
Test the Docker image.

Copy the testing CT scans to the 'input_images' directory:
```
mkdir input_images
cp -r <scans_directory>/*  $PWD/input_images
```
Then type the command we provided:
```
docker container run --gpus "device=0" -m 60G --name teamname --rm -v $PWD/input_images/:/workspace/inputs/ -v $PWD/prediction_results/:/workspace/outputs/ teamname:latest /bin/bash -c "sh predict.sh"
```
You can alter the GPU device ID, but the maximum number of GPUs is one and the GPU memory restriction is 11G.


# Step4
Back up and upload your Docker image:
```
docker save -o teamname.tar.gz teamname
```
Please send us your download link, Finnaly!

# Acknowlegement
The code of this repository is borrowed from [Huang's work](https://github.com/Ziyan-Huang/FLARE22).
