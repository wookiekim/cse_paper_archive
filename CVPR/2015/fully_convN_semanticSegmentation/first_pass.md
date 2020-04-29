# Fully convolutional Networks for Semantic Segmentation
[Paper link](https://arxiv.org/pdf/1605.06211.pdf)

## Category
Application of convolutional networks
* A FULL end-to-end convolutional network for semantic segmentation

A new approach to semantic segmentation using convolutional networks
* not the first approach using convnet
* but differs from them by various settings

## Context
Mostly related to Convnet models for classification
* Used as backbone for pre-trained model

Tries to implement the novelty of other semantic segmentation into the FCN architecture
* patchwise training..
* upsampling..

## Correctness
Assumes that using pretrained networks would be efficient
* results prove this

In the process of implementing other novelties such as upsampling, patchwise training...
* Imitates (or implements?) them in different forms
  * *Upsampling is (fractionally strided) convolution*
  * *Patchwise training is loss sampling*

Wouldn't be "a hundred percent equal" in the result, so experiments are carried out for the best combination
* Still endeavors to maintain the best novelties up till the point the paper was written


## Contribution

1. First work to train FCNs end-to-end for pixelwise prediction
2. ...and from supervised pre-training
3. Precludes the need for complication in other works
* no need for patchwise training
* no pre or post processing complications
4. Fast and accurate than the methods at the time

## Clarity
Well written
* and great comparison context
