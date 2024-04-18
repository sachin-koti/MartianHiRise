# Identification of Frost in Martian HiRISE Images:

This project is completed using Keras and Python.

The goal is to build a classifier that distinguishes images of
Martian terrain with frost.

# Steps taken to complete this project:
1. ## Data Exploration and Pre-processing:
  Images (png files) and labels (json files) are organized in the data directory
by “subframes.” Subframes are individual 5120x5120 pixel images which are
crops of the original HiRISE images (often on the order of 50k x 10k pixels).
Individual subframes were annotated by the contributors and then sliced into
299x299 “tiles.” Each tile has an associated label for use in training ML
algorithms.
There are 214 subframes and a total of 119920 tiles. Each tile has annotations
which have been used to assign labels to the tiles ‘frost’ or ‘background.’
Each JSON file contains all the annotation information collected from human
annotators.
The following are relevant to the assignment:
Image tiles are organized into folders of ‘background’ and ‘frost’ classes (binary).

2. ## Training CNN + MLP
   1. performed empirical regularization, crop, randomly zoom, rotate, flip, contrast, and translate images on my training set for image augmentation using various tools, including OpenCV.
   2. Train a three-layer CNN followed by a dense layer on the data for 20 epochs. Used ReLU’s in all of the layers. Used the softmax function, batch normalization and a dropout rate of 30%, L2 regularization, as well as ADAM optimizer. Also used cross-entropy loss. 

3. ## Transfer Learning
   1. used transfer learning, which uses deep learning models that are trained on very large datasets such as ImageNet as feature extractors. The idea is that such deep networks have learned to extract meaningful features from an image using their layers, and those features can be used in learning other tasks.
   2. used pre-trained models (EfficientNetB0, ResNet50, and VGG16). For these pre-trained networks, I only trained the last fully connected layer,and freezed all layers before them (i.e. you do not change their parameters during training), and used the outputs of the penultimate layer in the original pre-trained model as the features extracted from each image
   3. Same again as before, to perform empirical regularization, crop, randomly zoom, rotate, flip, contrast, and translated images in my training set for image augmentation.
   4. Used ReLU activation functions in the last layer and a softmax layer, along with batch normalization and a dropout rate of 30% as well as ADAM optimizer. Used cross-entropy loss. A batch size of 5 was used.
   5. Training was done for 10 epochs and early stopping was performed.

4. ## Plotted the training and validation errors vs. epochs (Please look out for them in the notebooks attached)
5. ## Reported the Precision, Recall, and F1 score for all the model ((Please look out for them in the notebooks attached)
6. ## Final Conclusion


the part1 notebook file contains CNN+MLP model and the transfer learning using EfficientNetB0 model. the part2 notebook file contains the transfer learning using ResNet50 and VGG16 models.
