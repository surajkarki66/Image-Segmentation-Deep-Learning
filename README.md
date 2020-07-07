# Image-Segmentation

## Definition:
It is a critical process in a computer vision. It involves dividing a visual input into segments to simplify  image analysis. Segments represent objects or parts of objects, and comprise sets of pixels, or “super-pixels”. Image segmentation sorts pixels into larger components, eliminating the need to consider individual pixels as units of observation.

There are many types of image segmentation. But we only look in Semantic Segmentation.

## 1) Semantic Segmentation:
Classifies all the pixels of an image into meaningful classes of objects. These classes are “semantically interpretable” and correspond to real-world categories. For instance, you could isolate all the pixels associated with a cat and color them green. This is also known as dense prediction because it predicts the meaning of each pixel.

As following image shows the example of semantic segmentation.

<img width="692" alt="semantic" src="https://user-images.githubusercontent.com/50628520/86709949-2f27e000-c03a-11ea-8388-5877e9dab917.png">


## 2) Instance Segmentation:
Identifies each instance of each object in an image. It differs from semantic segmentation in that it doesn’t categorize every pixel. If there are three cars in an image, semantic segmentation classifies all the cars as one instance, while instance segmentation identifies each individual car.


I am going to implement the semantic segmentation using deep learning.
