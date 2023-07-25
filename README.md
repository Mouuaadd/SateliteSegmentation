# SatelliteSegmentation
Segment features around residential buildings in UAV images of flooded area taken in Houston after Hurricane Harvey.

## Dataset Description
For this project we needed to perform image segmentation on Florida flood images. To solve this
problem we used a supervised deep learning approach, where we have labelled masks for each
image in the training dataset. The total number of classes is 25.

## Model Description 
In particular, we used transfer learning to build out model. The body of the model is transferred
from a MobileNetV2 network, pretrained on ImageNet. MobileNetV2 uses depthwise separable
convolutions, linear bottlenecks and Inverted residuals to obtain fewer parameters and therefore a
faster training time. In total, our model architecture consisted of 188 layers.
We went beyond that to optimize our model by using Tune library. Tune is a python library
used for automatic tuning of the hyper-parameters. this tool allowed us to explore the following
hyper-parameters:
• Learning rates: from 0.1 to 0.0001
• batch sizes: [2, 4, 8, 16]
• Optimizer: [SGD, Adam]
We also implemented early stopping to limit the number of epochs. The total run-time of the
hyper-parameter optimization module was 2 and a half hours and our best model used 0.00106 as a
learning rate, a batch size of 4 and Adam as Optimizer. It converged after 35 epochs for
an accuracy of 67 % on the validation set and an even better 71 % on the test set.
