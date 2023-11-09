# A_Docker_Example_for_ISICDM2023
This is a Docker Image creation process for uploading your model.

Before starting this process, you need to install Docker on your server.

# Step 1
First, you need to copy all the files you need into the same directory, including your code, model weights, shell scripts, and others:


# Step 2
Create your Docker image by entering the following command:


Note that Docker will automatically mount the 'teamname' image when creating the Docker image.
# Step 3

Test whether your Dokcer Image is available.

First, make sure that you have mounted the Docker image named 'teamname'.Next, you need to create a directory named 'input_images' and place the CT scans used for testing into it. Then, run the test using the command provided by us:


Of course, you can change the device number of your GPU, but please note that our maximum GPU number is 1 and the maximum GPU memory is 11G.


# Step4
Finally, you only need to package your Docker Image through the following command line and provide us with a download link!

# Acknowledgement:
