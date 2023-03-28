# Extracting coarse-grained classifiers from large CNN models

**NOTE:** This is a repository with methods, instructions and examples on how to use the components created for the purpose of paper **"Extracting coarse-grained classifiers from large CNN models"**. We provide implementation of the vital software components and methods used in the study (**we plan to release our repository upon acceptance**). All of the methods are implemented  in such a way as to make them as flexible as possible not only for the easy reproduction of our experiments but hopefully also for other potential studies of other researchers. We made sure to add comments and guidelines on how to use our methods. Note, that we use only some tiny examplary data (compatible with the freely available dataset/images used in the study) just to show the operation od the notebooks and to make the use of our materials easy for other researchers.


The repository includes an example on how to create  coarse-grained classifiers from large pre-trained fine-grained CNN models from keras (https://keras.io/api/applications/) with 3 strategies. The code along with the original dataset (mentioned in the paper, and also at the end of this document) can be used to reproduce the results presented in paper **"Extracting coarse-grained classifiers from large CNN models"**. 

We present our methods via jupyter notebooks, but we also provide an HTML version of the notebooks.

We provide 3 notebooks - for each strategy of finding the fine-grained classes (ImageNet) for the given coarse-grained classes:
* Extraction-of-coarse-grained-classifiers-WordNet-structure-hyponyms.ipynb - in this strategy, we use ALL the available fine-grained classes for each coarse-grained class. We use WordNet hypernym-hyponym (is-a) hierarchy to find the hyponyms (sub-categories) of each coarse-grained class. This is a fully-automatic strategy.
* Extraction-of-coarse-grained-classifiers-WordNet-semantic-similarity.ipynb - in this strategy, we use one class per each coarse-grained class for the initialization of this coarse-grained class. We increase the representativeness of each coarse-grained class by using more than 1 class. We find other suitable classes based on the similarity of initialization classes with other classes. We use semantic similarity measure - WordNet path similarity. This is a semi-automatic strategy.
* Extraction-of-coarse-grained-classifiers-CNN-weights.ipynb - in this strategy, we use one class per each coarse-grained class for the initialization of this coarse-grained class. We increase the representativeness of each coarse-grained class by using more than 1 class. We find other suitable classes based on the similarity of initialization classes with other classes. We use learned visual similarities (learned by CNN models). This is a semi-automatic strategy. This method does not require an additional data source such as WordNet.

## Technical details:

In our paper, we used three pre-trained networks krom Keras Application (https://keras.io/api/applications/):
* InceptionV3
* MobileNetV2
* ResNet50V2

Keras provides crafted preprocessing functions for these models, so one can use them to prepare their input data for these models. At Keras Application, one can also find the docs regarding these models (required image size etc.). We use the ImageNet weights for these models.

The following Python libraries have to be installed for the example to work correctly:
* NumPy - version 1.24.0
* TensorFlow (+ Keras) - version 2.11.0
* SciKit-learn - version 1.1.3
* nltk - version 3.8.1

We used Kaggle Dogs vs. Cats dataset (see https://www.kaggle.com/c/dogs-vs-cats) in our original experiments (results presented in the paper), but we also provide a tiny dataset of our own to test the notebook operation correctness (it can be replaced with the original Dogs vs. Cats to reproduce the results, as it has the same format).
