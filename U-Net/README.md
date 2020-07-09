# U-Net
U-Net is a convolutional neural network that is designed for performing semantic segmentation on biomedical images by Olaf Ronneberger, Philipp Fischer, Thomas Brox in 2015 at the paper “U-Net: Convolutional Networks for Biomedical Image Segmentation”. Its architecture is built and modified in such a way that it yields better segmentation with less training data. It is build using the fully convolutional network (FCN), which means that only convolutional layers are used and no dense or recurrent layers are used at all. 

# Architecture
![Unet](https://user-images.githubusercontent.com/50628520/87025695-71981b00-c1fa-11ea-90df-e362978e37d5.png)

The architecture is U shaped thats why it is named as U-Net.
It has main three path.

1) The Contracting Path (Downsampling Path)
2) Bottleneck
3) The Expanding Path(Upsampling Path)

## Contracting Path:
It consists of two 3×3 convolutions (unpadded convolutions), each followed by a rectified linear unit (ReLU) and a 2×2 max pooling operation with stride 2 for downsampling. At each downsampling step we double the number of feature channels.

## Expanding Path:
Every step in the expansive path consists of an upsampling of the feature map followed by a 2×2 convolution (“up-convolution”), a concatenation with the correspondingly feature map from the downsampling path, and two 3×3 convolutions, each followed by a ReLU.

## Skip Connection:
The skip connections from the downsampling path are concatenated with the feature map during upsampling path. These skip connections provide local information to global information while upsampling.

## Ouput Layer:
At the output layer a 1×1 convolution is used to map each feature vector to the desired number of classes.

Link to the Original U-Net paper: [a link] (https://arxiv.org/abs/1505.04597)
Link to the dataset: [a link] (https://www.kaggle.com/c/data-science-bowl-2018)

## Result of Simple U-Net Trained on nuclei dataset

### Input Image:
![input](https://user-images.githubusercontent.com/50628520/87027727-51b62680-c1fd-11ea-9dea-d18c94379245.png)

### Predicted Mask
![predicted](https://user-images.githubusercontent.com/50628520/87027775-61356f80-c1fd-11ea-85f2-0eecca556fec.png)
