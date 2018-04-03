# Skin-Cancer-image-classification-with-Tensorflow
We classify whether the cancer is benign or malignant

I am spoon feeding the procees for beginners beacause i am beginner too ;)

Here we are using the concept of transfer learning

We were using Inception-v3 model which is already trained by google on 1000 classes but what if we want to do the same thing but with our own images. We are going to use transfer learning which will help us to retrain final layer of already trained Inception-v3 model with new categories from scratch. It will take around 30 minutes on a laptop, without any GPU.

The datasets we have used is from this website
https://isic-archive.com/#images

Download both malignanat and benign images, and place them in two separate folders. We are going to use the folder names as labels.

go to this location
C:\Users\Hari

and create a folder tf-files 

place label_image.py and retrain.py in users/hari/tf_files

tf_files/cancer/(place downloaded malignant and benign images here)

create 2 two more folders with names bottlenecks and Inception( case sensitive)

tf-files/cancer/bottlenecks

tf-files/cancer/Inception

Now download the Inceptio model trained by google 

http://download.tensorflow.org/models/image/imagenet/inception-2015-12-05.tgz

extract the content into tf_files/cancer/Inception


Lets start the work guys

# steps

1. Install python 3.5 or above versions
2. Install docker tool box from here https://docs.docker.com/toolbox/toolbox_install_windows/
   its tough to install and configure the docker, so we using docker tool box which runs virtually
3. Turn of hyper-v in "windows features"
4. Most of you already did this, enable virtualization in bios Menu.
5. Install sublime lime text editor (you will love it)

# most important thing

1. install tensorflow
   open command prompt and enter the command 
  
  "pip install tensorflow"
   
   by default it will install cpu version of tensorflow
 
2. Now open docker tool box
   install tensor flow image in docker tool box
   
   docker run -it -v ~/tf_files/cancer:/tf_files/cancer gcr.io/tensorflow/tensorflow:latest-devel
   it will download 900 mb data approx
  
  Now retraining
  
  python tensorflow/retrain.py --bottleneck_dir=tf_files/bottlenecks --how_many_training_steps=100 --model_dir=tf_files/inception --output_graph=tf_files/retrained_graph.pb --output_labels=tf_files/retrained_labels.txt --image_dir=tf_files/cancer/
  
  
 100 training steps is reasonable
  
Now the final layers of inception is retrained

3. in docker

python tf_files/label_image.py tf_files/target.jpg

it will predict the probability of the class of which the image belongs


