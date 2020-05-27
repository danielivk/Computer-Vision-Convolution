# Computer-Vision-Convolution
Computer Vision Convolution Exercise


# Abstract
Convolutional Networks are based on the correlation operation (convolution without 180 degrees rotation of the filter kernel). 
In this work I have wrote and used the basic convolution operation, including Stride, Padding and normalized cross correlation.
The objective is to create the forward path of a convolutional layer (activation map), by adding to the convolution (correlation) Stride, Padding and Normalization (Normalized Cross Correlation to enable template matching), followed by an activation non linearity. Then to apply multiple kernels to a single input image / activation map.
The output image should have the correct size / dimensions, based in the input size and hyper parameters and the operation will work on all types of images: grey level / RGB / Float / UINT8.



# Introduction
Motivation: The Convolution/Correlation function is a very important feature in Computer Vision. It constitutes the basis for a Convolutional Neural Network which is used to analyze, categorize and create images.
It is very important to implement the Convolution in a precise manner because inside a neural network we can't always keep track on what's going on and it is important to forward correct and precise information forward.
We can use the function in order to extract vital information about an image for future use, this information is called features and we can do this while ignoring the things we don't want in the image.
These Features will then move forward in the Neural network and will be used to do what the network does.
We can also use the Convolution/Correlation function in order to find specific patches of information in a picture, we can use a small sub-image as the Filter to which we will use on the original image using a special normalization called Normalized cross validation – which is a form of similarity between the filter and the original image in each iteration.
The Convolution will result in a new image with higher frequencies in the most matching areas. This output can be threshholded and we will be left with white dots in the areas that Match the pattern almost correctly or prefectly.
scipy has a function called conv2d() which calculates the Convolution and a function called correlate2d() which calculates the Correlation.
These functions do not work on all types of images and need improvement working with  RGB Float / RGB UINT8.
Moreover, they do not have the option to use Normalized Cross Correlation which I have Implemented in this project.
Hyperparameters include: stride, padding, Norm, ACTV.
stride and padding influence the output size by the following template:
H1 = (H – F + 2*p)//stride + 1.
W1 = (W – F + 2*p)//stride + 1.



# Proposed Solution
Stage One:
Define shapes and Output Dimention according. ( W1, H1, N)
Check the input shapes and deal with them accordingly.
If they are GRAYSCALE then add a third axis to them.

Stage Two:
if the boolean value CORR is False: flip all kernels by 180 degrees.

Stage Three:
Calculate N times:
Convolve Each channel of the Image with the corresponding channel of the filter, taking into account the new hyper-parameter Norm.
If Norm is activated the function will Normilize Cross corelate every patch in each iteration.
If the ACTV is present in the input as another hyper-parameter the function shall then change the output according to the activation function presented.

In Each Channel Convolution between the Image and the Filter the output will be of shape (W1, H1, 1). After performing them all and adding to a numpy array the result Output will be (W1, H1, N).

Note: if we wish to find a patch in an image we will use 
norm= normalized_cross_correlation as an hyperparameter and pass it through a threshhold.


