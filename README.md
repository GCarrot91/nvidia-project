# Project Name: Asian Ethnicity Classifier

This model will (attempt to) classify the input pictures into 4 different Asian ethinicities (Chinese, Japanese, Korean, and Vietnamese). *Please note that I accidentally miss-spelt "ethnicity" as "ethinicity" on my directories/files.*

![Logo created by me.](https://i.imgur.com/GXkfL4R.jpg)

## The Algorithm

I used the pre-trained ImageNet model and by using transfer-learning, I taught the model to classify those 4 classes (Chinese, Japanese, Korean, and Vietnamese). Since it was pretty hard to find datasets, I was only able to train for each class with around 80-90 images, so it's accuracy is not the greatest.

## Running this project

1. Create a new directory for this project to be placed in through SSH.
2. In that file, download all the linked files/directories (except for the README.md obviously).
3. Also build the jetson-inference directory that will contain some necessary networks and other needed pieces by following this tutorial video by Nvidia:
  1. sudo apt-get update
  2. sudo apt-get install git cmake libpython3-dev python3-numpy
  3. git clone --recursive https://github.com/dusty-nv/jetson-inference
  4. cd jetson-inference
  5. mkdir build
  6. cd build
  7. cmake ../
  8. make -j$(nproc)
  9. sudo make install
  10. sudo ldconfig
4. Return back to our original directory for our project.
5. Set DATASET=my-data/asian_ethinicity
6. Set NET=models/asian_ethinicity
7. Run this command: imagenet.py --model=resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/japanese/01.jpg output_0.jpg
8. You can additionally scp the file on to your home computer by the following commands:
