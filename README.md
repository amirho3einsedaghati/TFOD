# Tensorflow Object Detection Walkthrough
[![License: MIT](https://img.shields.io/github/license/amirho3einsedaghati/TFOD?color=yellow)](https://github.com/amirho3einsedaghati/TFOD/)
[![GitHub repo size](https://img.shields.io/github/repo-size/amirho3einsedaghati/TFOD?color=red)](https://github.com/amirho3einsedaghati/TFOD/)
[![GitHub pull requests](https://img.shields.io/github/issues-pr/amirho3einsedaghati/TFOD?color=yellow)]((https://github.com/amirho3einsedaghati/TFOD/pulls))
[![GitHub issues](https://img.shields.io/github/issues-raw/amirho3einsedaghati/TFOD?color=red)](https://github.com/amirho3einsedaghati/TFOD/issues)

<p>In this Notebook, You should follow the <b>Tensorflow Object Detection API</b> and a pre-trained model such as <b>ssd_mobilenet_v2_fpnlite_320x320_coco17_tpu-8</b> or other pre-trained models provided in <a href='https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/tf2_detection_zoo.md'>Tensorflow Model Zoo</a> to implement your custom object detection model, but I recommend using the same model that told because It has an acceptable, good speed, 22ms, and mAP, 22.2. I used all of these to train an object detection model that can detect some Sign Language objects like Hello, ThumbsUp, ThumbsDown, ThankYou, and LiveLong, but Maybe you want to use these to train your intended objects. This Notebook is done thanks to the different sources on the internet.
<br/>
This project is executable not only on Windows machines but Linux. So definitely, You can also use this on <a href="https://colab.research.google.com/">Google Colab</a>. 
<br /><br/>
<img src="https://i.postimg.cc/zXSzghG9/1.jpg">
<br /><br/>
<b>Prerequisites:</b>
<ul>
  <li>Install <a href="https://www.python.org/downloads/">Python</a>.</li>
  <li>Install <a href="https://docs.anaconda.com/anaconda/install/index.html">Anaconda</a>.</li>
  <li>Install <a href="https://visualstudio.microsoft.com/vs/community/">Visual C++ Build Tools</a>.</li>
  <li>Install Tensorflow dependecies(find the appropriate, compatible version of the dependencies like CUDA, cuDNN, and so forth with your Tensorflow and Python for Linux from <a href="https://www.tensorflow.org/install/source">here</a> and for Windows from <a href="https://www.tensorflow.org/install/source_windows">here</a>).</li>
</ul>

## Steps
<br />
<b>Step 1.</b> Clone this repository: https://github.com/amirho3einsedaghati/TFOD.
<br/><br/>
<b>Step 2.</b> Create a new virtual environment(venv).
<br/>
You can name your venv whatever you want, but ensure put your venv name where tfod exists.
<pre>
python -m venv tfod
</pre> 
<br/>
<b>Step 3.</b> Activate the virtual environment.
<pre>
source tfod/bin/activate # Linux
.\tfod\Scripts\activate # Windows 
</pre>
<br/>
<b>Step 4.</b> Install dependencies and add the virtual environment to the Python Kernel.
<pre>
python -m pip install --upgrade pip
pip install ipykernel
python -m ipykernel install --user --name=tfodj
</pre>
<br/>
<b>Step 5.</b> Collect and Label images using the Notebook <a href="https://github.com/amirho3einsedaghati/TFOD/blob/master/1.%20Image%20Collecting%20and%20labeling.ipynb">1. Image Collecting and labeling.ipynb</a> - ensure you have changed the kernel to the virtual environment that has been created before as shown below.
<br /><br/>
<img src="https://i.postimg.cc/4NM5pY2Q/2.png"> 
<br/>
<b>Step 6.</b> All folders and annotations should be split between the following two folders either manually, as shown below
<pre>
\TFOD\Tensorflow\workspace\images\train
\TFOD\Tensorflow\workspace\images\test
</pre>
,or automatically by running section 6 in the Notebook <a href="https://github.com/amirho3einsedaghati/TFOD/blob/master/1.%20Image%20Collecting%20and%20labeling.ipynb">1. Image Collecting and labeling.ipynb</a>.
<br /></br>
<img src="https://i.postimg.cc/LXymR2pT/5.png">
<br /></br>
<b>Step 7.</b> Begin training process by opening <a href="https://github.com/amirho3einsedaghati/TFOD/blob/master/2.%20Training%20and%20Detection.ipynb">2. Training and Detection.ipynb</a>. This notebook will walk you through installing Tensorflow Object Detection API, training and evaluating the model, making detections, saving and exporting your model, and so forth. 
<br /><br/>
<b>Step 8.</b> To ensure whether we've got the Tensorflow Object Detection API installed successfully or not, We should run section 1.2 in the Notebook <a href="https://github.com/amirho3einsedaghati/TFOD/blob/master/2.%20Training%20and%20Detection.ipynb">2. Training and Detection.ipynb</a>.
<br /><br/>
<img src="https://i.postimg.cc/4NZKqs7R/3.png">
If you didn't receive <b>ok</b> in the last line, You should follow the next cells of this very Notebook.
<br /> <br/>
<b>Step 9.</b> Once you get to section <b>6. Train the custom model by using train records</b>, inside the Notebook <a href="https://github.com/amirho3einsedaghati/TFOD/blob/master/2.%20Training%20and%20Detection.ipynb">2. Training and Detection.ipynb</a>, You can simply train the pre-trained model either inside the very Notebook or in the cmd or terminal window by running the content of the <b>command</b> variable.
If you train the pre-trained model inside the cmd or terminal window, You can see loss metrics and training time per step. 
<br /><br/>
<img src="https://i.postimg.cc/tgzYV04b/4.png">
As you can see in this image, You can change the number of training steps to train your model shorter or longer. In my last training process, I used 30000 steps to boost the model performance. As a result, It was obtained mAP≈89 and mAR≈90.
<br /><br/>
<br /> 
<b>Step 10.</b> Once your custom-trained model has been trained, You should run the evaluation command under Step 7 to see the mean average precision(mAP), mean average recall(mAR), and the other performance metrics, or You can optionally evaluate your model inside the Tensorboard.

To do this, You should first navigate the following path. 
<pre> cd Tensorlfow/workspace/models/CUSTOM_MODEL_NAME/eval</pre> 
In my case, This path is <pre> cd Tensorlfow/workspace/models/sign_language_2nd_tuned/eval</pre>
Then open Tensorboard with the following command.
<pre>tensorboard --logdir=. </pre>
After running this, Tensorboard will be accessible through your browser, and You will be able to see evaluation metrics.
<br />
