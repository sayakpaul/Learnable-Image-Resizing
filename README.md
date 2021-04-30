# Learnable-Image-Resizing
TensorFlow 2 implementation of [Learning to Resize Images for Computer Vision Tasks](https://arxiv.org/abs/2103.09950v1) by Talebi et al.

Accompanying blog post: [Learning to Resize in Computer Vision](http://keras.io/examples/vision/learnable_resizer/).

The above-mentioned paper proposes a simple framework to optimally learning representations for a given network architecture and given image resolution (such as 224x224). The authors find that the representations that are more coherent with the human perception system _may not always_ improve the performance of vision models. Instead, optimizing the representations that are better suited for the models can substantially improve their performance. 

The diagram presents the proposed learnable resizer module (source: original paper):

<div align="center">
<img src="https://i.ibb.co/gJYtSs0/image.png" width="750"></img>
</div>
<br>

Here's how the resized images look like after being passed through a learned resizer:

<div align="center">

![](figures/visualization.png)

</div>

The images may not make sense to our eyes in terms of their perceptual quality, but they help to improve the recognition performance of the vision models.

## About the notebooks
* `Standard_Training.ipynb`: Shows how to train a DenseNet-121 on the Cats and Dogs dataset with bilinear resizing (224x224).
* `Learnable_Resizer.ipynb`: Shows how to train the same network with the learnable resizing module included. 

These incorporate mixed-precision training along with distributed training. 

## Results
|           Model           	| Number of  parameters (Million) 	| Top-1 accuracy 	|
|:-------------------------:	|:-------------------------------:	|:--------------:	|
|   With learnable resizer  	|             7.051717            	|      52.02     	|
| Without learnable resizer 	|             7.039554            	|      50.3      	|

Both the models were trained for only 10 epochs from the same initial checkpoint.

You can reproduce these results with the model weights provided [here](https://github.com/sayakpaul/Learnable-Image-Resizing/releases/tag/v1.0.0).

## Acknowledgements
* [ML-GDE program](https://developers.google.com/programs/experts/) for providing GCP credit support. 
