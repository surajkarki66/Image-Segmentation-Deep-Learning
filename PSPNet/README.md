# PSPNet (Pyramid Scene Parsing Network)

It won imageNet scene parsing challenge 2016. It is an improvement over fully convolutional network(FCN) based segmentation. The PSPNet architecture takes into account the global context of the image to predict the local level predictions.

Eg.
![comparision](https://user-images.githubusercontent.com/50628520/87843375-d414a980-c8d3-11ea-8746-a66bfc4cd448.png)


The boat inside the yellow bounding box in (a) is classified as a "car" by a FCN based classifier (c). It is because of its shape and appearance. But it is uncommon to see a car in river. If the model could gain information from the context, for example in our case water around the object, it will be able to correctly classify it. The PSPNet model (d) is able to capture the context of the whole image to classify the object as a boat (Green).

## 1) Architecture:
It is almost like encoder-decoder architecture but it contains pyramid pooling module.

### i) Encoder:
The PSPNet encoder contains the CNN backbone with dilated convolutions along with the pyramid pooling module. The paper uses ResNet as backbone architecture for the encoder of the PSPNet.

### a) Pyramid Pooling Module:
The pyramid pooling module is the main part of this model as it helps the model to capture the global context in the image which helps it to classify the pixels based on the global information present in the image.

![architecture](https://user-images.githubusercontent.com/50628520/87843506-d62b3800-c8d4-11ea-96cc-1b1044f018ae.png)
The feature map from the backbone is pooled at different sizes and then passed through a convolution layer and after which upsampling takes place on the pooled features to make them the same size as of the original feature map. Finally, the upsampled maps are concatenated with the original feature map to be passed to the decoder. This technique fuses the features different scales hence aggregating the overall context.

For example in the above figure from the paper, the four colours represent different scales which are 6, 3, 2, and 1 for colours green, blue, orange and red respectively. The feature map is pooled at these scales after which they are convolved with 1x1 filters to reduce the feature depth. Then all of these features are then upsampled at the size of the feature map and are concatenated. The 1x1 feature is the most coarse pooled feature map as it captures all the information in just 1x1 spatial location, whereas as the spatial resolution increases, the high resolution features are also taken in account as in the case of 6x6 pyramid size. A rule of thumb is that the if the pyramid size is small i.e ~1 or 2, the model will capture the low resolution and bigger features whereas if the the pyramid size is bigger i.e ~6-8, the model will be able to capture high resolution features.

### ii) Decoder:
After the encoder has extracted out features of the image, it is the turn of the decoder to take those features and convert them into predictions by passing them into its layers. The decoder is just another network which takes in features and results into predictions.

### a) 8x upsampling decoder:
The most common decoders that are found in various implementation of the PSPNet is a convolutional layer followed by 8 X bilinear upsampling. There is a downside of having a 8X upsampling decoder in the end is that there is no learnable parameters in them. Hence the result that we get are bolbby and it fails to capture high resolution information from the image.