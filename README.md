# Planets-and-stars

This project decides whether an object is a planet or a star. Because these are both objects in outer space, sometimes they can get hard to differentiate from far away. This project can be used to quickly decide whether an object is a planet or a star. Because of this discovery, it might be easier to find correlations between planets and stars, discover unknown planets, and learn more about our universe.


## The Algorithm

This project uses a resnet18 model which has been transfer learned so that it can find planets and stars. It uses the image
network to find these objects. Using datasets from kaggle, I trained my resnet18 model using 4 epochs and achieved a stunning accuracy of 99%!
![Pluto](https://i.imgur.com/y1eemB2.jpg)


## Running this project

1. Make sure you're logged into the nano and that the nano is connected to vs code through ssh.
2. Go to the folder to download the model and the dataset.(Make sure to only download folders that say project)
   https://drive.google.com/drive/folders/1rEkZX5-af7_hanELkhzHILiglar2NMEq?usp=sharing
4. Open the terminal and navigate to the classification directory
5. Set the NET and DATASET variables
```ts
$ NET=models/PROJECT
$ DATASET=data/PROJECT
```
5. Run the imagenet command
```ts
$ imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/[FOLDER]/[IMAGE NAME].jpg [NAME OF NEW IMAGE].jpg
```
6. If you would like to test your own image, move the image into the test directory inside the PROJECT directory inside the data directory.
6. Your output image will be in the classification directory! Enjoy!

[View a video explanation here](video link)
