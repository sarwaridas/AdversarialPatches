# Adversarial Patches <img width=90 align="right" src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e6/Duke_University_logo.svg/1024px-Duke_University_logo.svg.png">

## Project Summary

The last two decades have witnessed a tremendous increase in the applicability and performance of deep neural networks, with accuracy rates of CNNs matching or even out-performing human perception. 

At the same time, a myriad of adversarial attacks has demonstrated the vulnerability of these systems by exposing the threats associated with implementing them in the real world. While most of these attacks are image-dependent and focus on making imperceptible changes to the input, in this project, we develop a “physical” attack in the form of  adversarial patches that can be printed and applied to attack image and video classification models.  These patches have shown to generalize to the real world, and will continue to be adversarial to classifiers even under different lighting conditions and orientations. 

In this project, we take the role of an attacker to craft and train these patches to then mislead neural networks. We will:
- Develop “physical” attacks, or patches, that could be printed and applied in the real world without prior knowledge of the scene. 
- Generate patch attacks in untargeted (failure to classify) and targeted (incorrect classification) fashions.
- Test the effect of rotation, location and transferability of the patches. 

Note: This project is an implementation of the methods described in the paper [Adversarial Patch](https://arxiv.org/abs/1712.09665) [1]

## Data and Methods

- The CIFAR-10 data set consists of 60,000 colored images with 10 label classes. Each image is of the size 32 by 32 pixels in terms of height and width. The dataset was split into training and testing data with 50,000 images in the training data and 10,000 images in the test data.
- A convolution neural network following the Resnet-20 architecture was trained on this data and tuned to achieve an accuracy of 90% on the test dataset. This trained model was then used to generate targeted and untargeted patches. Due to a lack of computing resources, we were only able to generate a limited number of patches. The targeted patches were generated for the car, bird, truck, and the plane classes.
- A rectangular patch of the required size (3x3, 5x5, 7x7 and 16x16) was initialized and placed at a random location in the training images. The patch was then optimized over 10 epochs with a learning rate of 0.1 and Adam optimizer. 
- The generated patches were then placed at a random location inside the test images. The untargeted patches were evaluated using test accuracy and the targeted patches were evaluated using both test accuracy and attack success rate (ASR). ASR was defined as the proportion of images that were predicted as the target class. 

Results

[1] Brown, T. B., Mane, D., Roy, A., Abadi, M., and Gilmer, J. *Adversarial patch*. CoRR, abs/1712.09665, 2017. URL http://arxiv.org/abs/1712.09665.

