# Adversarial Attack and Defense
aka Adversarial examples

## [Medium: Adversarial Attack and Defense on Neural Networks in PyTorch](https://towardsdatascience.com/adversarial-attack-and-defense-on-neural-networks-in-pytorch-82b5bcd9171)

Past researchers have indicated that as long as you know the "correct" method to change your data, you can force your network to perform poolrly on data which may not seem to be visually different through human eyes.
* adversarial attacks: these **deliberate manipulations of the data to lower model accuracies**

The war of attack and defense is an ongoing popular research topic in the maching learning domain.

This article provides an overview of **Fast Gradient Signed Method Attack**, one of the easiest yet effective attacks
* along with implmentation and defense through adversarial training in PyTorch

#### History of Adversarial Examples and Attacks
Adversarial Examples: inputs or data that are pertubed in order to fool a machine learning network.
* formulated by Ian et al. "Explaining and Harnessing Adversarial Examples" (ICLR 15)
* argues that neural networks are vulnerable to adversarial examples due to high linearity of the architecture
  * LSTMs and ReLUs still often behave in a very linear way
  * therefore these models will be very easily fooled by linear pertubations
  * Fast Gradient Sign Method(FGSM) was introduced here

FGSM: white box attack
* i.e. attack is generated based on given network architecture
* based on the idea that normal networks follow a gradient descent to find the lowest point of loss
* sign of the gradient is OPPOSITE in direction from the gradient descent
  * If we follow the sign of the gradient, we can maximize the loss by just adding a small amount of pertubation.

Pertubed x = adding e (a small constant with the sign equal to the direction of the gradient of loss J wrt x) to x.
* the fact that these simple methods can actually fool a deep nn -> further evidence that adversarial examples exist because of neural network's linearity.

**[CleverHans Library](https://github.com/tensorflow/cleverhans)**
* provided and maintained by Ian Goodfellow and Nicolas Papernot
* provides multiple attacks and defenses and is widely used today for benchmarking.
* Majority of the attacks were implemented in Tensorflow, recently released codes for FGSM in PyTorch as well
  * calls for more implementations from tf to pt?

The example in this article drops MNIST accuracy from 98% to 4%.
* `xs = fast_gradient_method(fgsm_model, xs, eps=0.1, norm=np.inf, clip_min=0., clip_max=1.)`

#### Adversarial Training
In the same paper, they proposed adversarial training method
* i.e. the adversarial samples generated from the training set were also included in the training.
* both types of data (original and adversarial samples) should be used to prevent loss in accuracy on the original set of data.
  * What happens if only adversarial samples are used? Then do original examples act as adversarial samples?
* Note that the network starts from the checkpoint where it is already trained on clean data. 
* Both the clean and adversarial examples are fed into the network during adversarial training to prevent an accuracy decrease on clean data during further training.
  * accuracy increased back to 90% for adversarial samples while maintaining accuracy on clean data

Problem: Adversarial training could be adopted to generalize the model architecture, but they will ONLY BE EFFECTIVE ON A SPECIFIC TYPE OF ATTACK that the model is trained on.
* the adversarial training method needs to be further investigated and evaluted for better adversarial defense.

Other medium writeups:
* https://medium.com/mlreview/the-intuition-behind-adversarial-attacks-on-neural-networks-71fdd427a33b
* https://medium.com/onfido-tech/adversarial-attacks-and-defences-for-convolutional-neural-networks-66915ece52e7
* Adversarial Attacks. Is the drawing above a portrait of a… | by Jonathan Hui | Jul, 2020 | Medium