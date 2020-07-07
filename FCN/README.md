# FCN (Fully Connected Neural Network)
owe their name to their architecture, which is built only from locally connected layers, such as convolution, pooling and upsampling. Note that no dense layer is used in this kind of architecture. This reduces the number of parameters and computation time. Also, the network can work regardless of the original image size, without requiring any fixed number of units at any stage, givent that all connections are local. To obtain a segmentation map (output), segmentation networks usually have 2 parts :

#### 1) Downsampling path : capture semantic/contextual information
#### 2) Upsampling path : recover spatial information

The downsampling path is used to extract and interpret the context (what), while the upsampling path is used to enable precise localization (where). Furthermore, to fully recover the fine-grained spatial information lost in the pooling or downsampling layers, we often use skip connections.

A skip connection is a connection that bypasses at least one layer. Here, it is often used to transfer local information by concatenating or summing feature maps from the downsampling path with feature maps from the upsampling path. Merging features from various resolution levels helps combining context information with spatial information.

## Upsampling:
Upsampling is done by deconvolution method. Convolution is a process getting the output size smaller. Thus, the name, deconvolution, is coming from when we want to have upsampling to get the output size larger. (But the name, deconvolution, is misinterpreted as reverse process of convolution, but it is not.) And it is also called, up convolution, and transposed convolution. And it is also called fractional stride convolution when fractional stride is used.

![deconvolution](https://user-images.githubusercontent.com/50628520/86765060-5eeddc80-c068-11ea-9dff-dd9b34127135.gif)


## Architecture
![fcn](https://user-images.githubusercontent.com/50628520/86765342-c310a080-c068-11ea-85f4-02c43dbdda34.png)

## Model
There are variants of the FCN architecture, which mainly differ in the spatial precision of their output. For example, the figures below show the FCN-32, FCN-16 and FCN-8 variants. In the figures, convolutional layers are represented as vertical lines between pooling layers, which explicitely show the relative size of the feature maps.

![fcn-model](https://user-images.githubusercontent.com/50628520/86765936-8b562880-c069-11ea-9502-152e3472085f.png)
