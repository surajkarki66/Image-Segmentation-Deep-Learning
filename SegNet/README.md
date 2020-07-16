# SegNet
It is a deep convolutional Encoder-Decoder architecture for semantic segmentation. It is proposed by Vijay Badrinarayan, Alex Kendell, Roberto Cipolla et al.
SegNet has an encoder network and corresponding decoder network, followed by final pixel wise classification layer.

## Architecture
Encoder network consists of 13 convolutional layers which correspond to the first 13 convolutional layers in the VGG16 network designed for object classification.

Each encoder layer has corresponding decoder layer and hence the decoder network has 13 layers. The final decoder output is fed to a multiclass softmax classifier to produce class probabilities of each pixel independentlty.

![segnet](https://user-images.githubusercontent.com/50628520/87634853-cdfcbc80-c75d-11ea-8190-b09c96871c44.png)

