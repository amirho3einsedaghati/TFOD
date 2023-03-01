# Tensorflow Object Detection Walkthrough
<p>In this Notebook, We should use the <b>Tensorflow Object Detection API</b> and a pre-trained model <b>ssd_mobilenet_v2_fpnlite_320x320_coco17_tpu-8</b> to implement our custom object detection model. I use all of these to train an object detection model that can detect some Sign Language objects like Hello, ThumbsUp, ThumbsDown, ThankYou, and LiveLong, but maybe you want to use these to train your intended objects.
this Notebook is done thanks to the different sources on the internet.
<img src="https://i.postimg.cc/zXSzghG9/1.jpg">

## Steps
<br />
<b>Step 1.</b> Clone this repository: https://github.com/amirho3einsedaghati/TFOD
<br/><br/>
<b>Step 2.</b> Create a new virtual environment 
<pre>
python -m venv tfod
</pre> 
<br/>
<b>Step 3.</b> Activate the virtual environment
<pre>
source tfod/bin/activate # Linux
.\tfod\Scripts\activate # Windows 
</pre>
<br/>
<b>Step 4.</b> Install dependencies and add the virtual environment to the Python Kernel
<pre>
python -m pip install --upgrade pip
pip install ipykernel
python -m ipykernel install --user --name=tfodj
</pre>
<br/>
<b>Step 5.</b> Collect and Label images using the Notebook <a href="https://github.com/amirho3einsedaghati/TFOD/blob/master/1.%20Image%20Collecting%20and%20labeling.ipynb">1. Image Collecting and labeling.ipynb</a> - ensure you have changed the kernel to the virtual environment that has been created before as shown below
<img src="https://i.postimg.cc/4NM5pY2Q/2.png"> 
<br/>
<b>Step 6.</b> all folders and annotations should be split between the following two folders either manually or automatically by running section 6 in the Notebook <a href="https://github.com/amirho3einsedaghati/TFOD/blob/master/1.%20Image%20Collecting%20and%20labeling.ipynb">1. Image Collecting and labeling.ipynb</a>.
<pre>
\TFOD\Tensorflow\workspace\images\train
\TFOD\Tensorflow\workspace\images\test
</pre>
<br/><br/>
<b>Step 7.</b> Begin training process by opening <a href="https://github.com/amirho3einsedaghati/TFOD/blob/master/2.%20Training%20and%20Detection.ipynb">2. Training and Detection.ipynb</a>, this notebook will walk you through installing Tensorflow Object Detection API, training and evaluating the model, making detections, saving and exporting your model, and so forth. 
<br /><br/>
<b>Step 8.</b> to ensure whether we've got the Tensorflow Object Detection API installed successfully or not, we should run section 1.2 in the Notebook <a href="https://github.com/amirho3einsedaghati/TFOD/blob/master/2.%20Training%20and%20Detection.ipynb">2. Training and Detection.ipynb</a>.
<img src="https://i.postimg.cc/4NZKqs7R/3.png">
If you didn't receive <b>ok</b> in the last line, You should follow the next cells of this very Notebook.
<br /> <br/>
<b>Step 9.</b> Once you get to section <b>6. Train the pre-trained model by using train records</b>, inside the Notebook <a href="https://github.com/amirho3einsedaghati/TFOD/blob/master/2.%20Training%20and%20Detection.ipynb">2. Training and Detection.ipynb</a>, you can simply train the pre-trained model either inside the very Notebook or in the cmd or terminal window by running the content of the <b>command</b> variable.
if you trained the pre-trained model inside the cmd or terminal window, you can see loss metrics and training time per step. 
<br /> <br/>
<br />
<b>Step 10.</b> You can optionally evaluate your model inside of Tensorboard. Once your custom-trained model has been trained and you should run the evaluation command under Step 7, to see the mean average precision(mAP), mean average recall(mAR), and the other performance metrics, or you can optionally evaluate your model inside the Tensorboard. to do this, you should navigate the following path. 
<pre> cd Tensorlfow/workspace/models/CUSTOM_MODEL_NAME/eval</pre> 
And open Tensorboard with the following command.
<pre>tensorboard --logdir=. </pre>
Tensorboard will be accessible through your browser and you will be able to see evaluation metrics.
<br />
