# A_Docker_Example_for_ISICDM2023
This is the procedure of creating a Docker Image for uploading your model.

Before starting this process, you need to install Docker on your server.

# Step 1
First, copy all necessary files (such as your code, model weights, shell scripts, and others) into the same directory:
```
mkdir teamname
cp <-r> your_files teamname
cd teamname
```

# Step 2
Enter the following command to create your Docker Image:
```
docker build -t teamname .
```

Note that when you create this, Docker will mount the Image named 'teamname' automatically.

# Step 3

Verify if your Dokcer Image is available.

First, confirm that the Docker image with the name "teamname" is mounted.

Next, you need to make a directory called "input_images" and move the testing CT scans into it:

Then, run the test using the command provided by us:
```
mkdir input_images
cp -r your_CT_scans_dir/* input_images
docker container run --gpus "device=0" -m 60G --name teamname --rm -v $PWD/input_images/:/workspace/inputs/ -v $PWD/prediction_results/:/workspace/outputs/ teamname:latest /bin/bash -c "sh predict.sh"
```

Of course, you can change the device number of your GPU, but please note that our maximum GPU number is 1 and the maximum GPU memory is 11G.


# Step4
Finally, all you have to do is package your Docker image using the following command line and give us a download link:
```
docker save -o  teamname.tar.gz teamname
```

# Testing procedure

The following two commands will be entered to carry out our testing procedure; for further information, see our testing [video](https://github.com/Meiyan88/A_Docker_Example_for_ISICDM2023/blob/main/testing_stage.mp4):
```
docker load -i  teamname.tar.gz
docker container run --gpus "device=0" -m 60G --name teamname --rm -v $PWD/input_images/:/workspace/inputs/ -v $PWD/prediction_results/:/workspace/outputs/ teamname:latest /bin/bash -c "sh predict.sh"
```

# Acknowledgement:

The code of this repository is borrowed from [Huang's work](https://github.com/Ziyan-Huang/FLARE22).
