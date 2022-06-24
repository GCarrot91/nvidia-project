# Asian Ethnicity Classifier

This model will (attempt to) classify the input pictures into 4 different Asian ethinicities (Chinese, Japanese, Korean, and Vietnamese). *Please note that I accidentally miss-spelt "ethnicity" as "ethinicity" on my directories/files.*

![Logo created by me.](https://i.imgur.com/GXkfL4R.jpg)

## The Algorithm

I used the pre-trained ImageNet model and by using transfer-learning, I taught the model to classify those 4 classes (Chinese, Japanese, Korean, and Vietnamese). Since it was pretty hard to find datasets, I was only able to train for each class with around 80-90 images, so it's accuracy is not the greatest.

## Running This Project

Here are the steps.

### Prerequistes

1. You're going to obviously need a Jetson Nano with a proper headless setup (there are videos by Nvidia that you can view) and will need some sort of a personal computer to SSH with.
2. Please have a basic understanding of navigating through the linux terminal.

### The Process

1. Build the jetson-inference directory that will contain some necessary networks and other needed pieces by following this tutorial video by Nvidia:
  a. sudo apt-get update
  b. sudo apt-get install git cmake libpython3-dev python3-numpy
  c. git clone --recursive https://github.com/dusty-nv/jetson-inference
  d. cd jetson-inference
  e. mkdir build
  f. cd build
  g. cmake ../
  h. make -j$(nproc)
  i. sudo make install
  j. sudo ldconfig
2. Create a new directory for this project to be placed in (not within jetson-inference).
3. In the jetson-inference directory, download the zip file using scp and unzip the file (you can delete the zipped file now).
4. Cd into the data directory (jetson-inference/python/training/classification/data) and move the asian_ethinicity file into our new directory & place that file inside a new directory within our project directory and name it "my-data."
5. Go back to the jetson-inference directory and cd into the models directory (jetson-inference/python/training/classification/models). Move the entire directory over to our project directory.
6. Set DATASET=my-data/asian_ethinicity
7. Set NET=models/asian_ethinicity
8. Run this command: imagenet.py --model=resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/chinese/01.JPG output_0.jpg
9. You can additionally scp the file on to your home computer by the following commands (use the computer's terminal in a new window):
  Windows: scp nvidia@192.168.55.1:/home/nvidia/nvidia-project/output_0.jpg C:\Users\<Username>\Desktop
  Mac: scp nvidia@192.168.55.1:/home/nvidia/nvidia-project/output_0.jpg ./
