# Project Name: Asian Ethnicity Classifier

This model will (attempt to) classify the input pictures into 4 different Asian ethinicities (Chinese, Japanese, Korean, and Vietnamese). *Please note that I accidentally miss-spelt "ethnicity" as "ethinicity" on my directories/files.*

![Logo created by me.](https://i.imgur.com/GXkfL4R.jpg)

## The Algorithm

I used the pre-trained ImageNet model and by using transfer-learning, I taught the model to classify those 4 classes (Chinese, Japanese, Korean, and Vietnamese). Since it was pretty hard to find datasets, I was only able to train for each class with around 80-90 images, so it's accuracy is not the greatest.

## Running this project

1. Create a new directory for this project to be placed in.
2. In that file, download all the linked files/directories (except for the README.md obviously).
3. Also build the jetson-inference directory that will contain some necessary networks and other needed pieces by following this tutorial video by Nvidia:

[View a video explanation here](video link)
