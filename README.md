# Planets-and-stars

This project decides whether an object is a planet or a star. Because these are both objects in outer space, sometimes they can get hard to differentiate from far away. This project can be used to quickly decide whether an object is a planet or a star. Because of this discovery, it might be easier to find correlations between planets and stars, discover unknown kinds of planets, and learn more about our universe.


## The Algorithm

This project uses a resnet18 model which has been transfer learned so that it can find planets and stars. It uses the image
network to find these objects. Using datasets from kaggle, I trained my resnet18 model using 4 epochs and achieved a stunning accuracy of 99%!
![Pluto](https://i.imgur.com/y1eemB2.jpg)


## Running this project


1. Make sure you're logged into the nano and that the nano is connected to vs code through ssh.
2. You should have the jetson-inference library and python3 already downloaded.
3. Go to the folder to download the model and the dataset.(Make sure to only download folders that say project)
   https://drive.google.com/drive/folders/1rEkZX5-af7_hanELkhzHILiglar2NMEq?usp=sharing
### Training your model(you can use mine if you want)
1. Head to the jetson-inference directory
   ```ts
   $ cd jetson-inference
   ```
3. Open the docker container
   ```ts
   $ ./docker/run.sh
   ```
4. Next, head to the classification directory.
   ```ts
   $ cd python/training/classification
   ```
5. Finally, to train the model, fill in the number of epochs you want to use and run this command
   ```ts
   python3 train.py --epochs=[NUMBER OF EPOCHS]--model-dir=models/PROJECT data/PROJECT
   ```
6. To export this model, all you have to do is run this command
   ```ts
   python3 onnx_export.py --model-dir=models/PROJECT
   ```
7. Exit the docker container with Cntrl+D
### Testing an image 
1. Open the terminal and navigate to the classification directory
2. Set the NET and DATASET variables
```ts
$ NET=models/PROJECT
$ DATASET=data/PROJECT
```
3. Run the imagenet command
```ts
$ imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/[FOLDER]/[IMAGE NAME].jpg [NAME OF NEW IMAGE].jpg
```
4. If you would like to test your own image, move the image into the test directory inside the PROJECT directory inside the data directory.
5. Your output image will be in the classification directory! Enjoy!

[View a video explanation here](video link)
