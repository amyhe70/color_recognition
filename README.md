# color_recognition

This model is used to recognize color shades. It is trained on an imagenet Resnet-18 model using transfer learning.

## The Algorithm
The algorithim can be used with VSCode and different image files of colors - supported by Jetson nano. It uses a 2GB Jetson Nano, and so it uses it a preflashed SD card flashed from the NVIDIA webpage. It is meant to detect shades that can be associated basic colors (red, orange, yellow, green, blue, purple, black, white) and determine which color group the shade belongs in.

## Running this project

1. Connect your Jetson Nano to your computer on PuTTY and VSCode
2. Download an image of a solid color that you want to test
3. Make sure that resnet18.onnx is downloaded under models/color_recognition using "ls models/color_recognition". If it is not there, go to jetson-inference/python/training/classification in the docker in PuTTY and run "python3 onnx_export.py --model-dir=models/color_recognition"
4. Set the NET and DATASET variables in VSCode (NET=models/color_recognition, DATASET=data/color_recognition)
5. Run "imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/[folder in /test/ in which you put your image]/[initial image name] [new image name]
6. Open the newly generated image with the prediction

Ex.

![identifying white as white](https://i.imgur.com/Krwrii4.jpg)

[View a video explanation here](video link)
