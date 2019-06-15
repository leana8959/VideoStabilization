# VideoStabilization 

## Description

This is a python-openCV implementation of this [research paper](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/37041.pdf) by Matthias Grundmann, Vivek Kwatra and Irfan Essa. The basic goal of this piece of code is to do some PreProcessing on a given wobbly video, and then output a relatively stable video which resembles professional videography(without bumps).

## Basic Algorithm and Working

### Transforms Extraction(achieved by preproc.py)

Firstly, the affine transform between all the consecutive 2 frames are computed, so that we achieve an estimate of the camera trajectory.

### Stabilizing(achieved by stabilize.py)

Now, the above camera trajectory will be wobbly and needs to be smoothened. This is achieved by converting the problem to an optimization problem where the derivative needs to be minimized and the constraint is that the values don't differ more than a threshold from the original ones.

### Video Output(achieved by generate.py)

Finally a cropped region of the video is outputted where the cropped region box follows a trajectory that smoothens the output.

## How To

* Run the webapp: 	
```console
	bar@foo:~/VideoStabilization$ python3 preproc.py <video_file>
	bar@foo:~/VideoStabilization$ python3 stabilize.py
	bar@foo:~/VideoStabilization$ python3 generate.py <video_file>	
```

## Built With

* [Python3](https://www.python.org/download/releases/3.0/)
* [OpenCV](https://docs.opencv.org/)

## Author

* Vaibhav Garg