# Identification of Frost in Martian HiRISE Images

In this project, high resolution visible data (from HiRISE on MRO) with frost labels will be used to detect Mars' seasonal frost with deep learning techniques. I have used the following models and their variations:

## Neural Network Architectures

* Convolutional Neural Network (CNN)
* Multilayer Perceptrons (MLP)

## Transfer Learning with Pre-trained Models

For enhanced performance, the project employs transfer learning with the following pre-trained models:

* EfficientNetB0
* ResNet50
* VGG16


## Data Source: Jet Propulsion Laboratory Open Repository
This dataset was created to study Mars’ seasonal frost cycle and its role in the planet’s climate and surface evolution over the past 2 billion years. The data helps in identifying low-latitude frosted microclimates and their impact on climate.

Images (png files) and labels (json files) are organized in the data directory by “subframes.” Subframes are individual 5120x5120 pixel images which are crops of the original HiRISE images (often on the order of 50k x 10k pixels).
Individual subframes were annotated by the contributors and then sliced into 299x299 “tiles.” Each tile has an associated label for use in training ML algorithms.
There are 214 subframes and a total of 119920 tiles. Each tile has annotations which have been used to assign labels to the tiles ‘frost’ or ‘background.’ 
Each JSON file contains all the annotation information collected from human annotators.

* The dataset can be accessed [here](https://dataverse.jpl.nasa.gov/dataset.xhtml?persistentId=doi:10.48577/jpl.QJ9PYA).
* Data Augmentation techniques I applied: random contrast, resize

## Modeling
### CNN+MLP
Following is a three-layer CNN followed by a dense layer on the data:
* Dense layer (MLP) neurons: 128
* All layers: ReLU
* Softmax function, Batch normalization
* Dropout rate: 30%,
* L2 regularization: 0.1
* ADAM optimizer
* Cross entropy loss: sparse categorical crossentropy
* Output layer: Dense(2, activation='softmax')
* Learning rate: 0.00001

### Transfer Learning - EfficientNetB0
* Dense layer neurons: 32
* L2 regularization: 0.1
* Dropout rate: 30%
* Output layer: Dense(2, activation='softmax')
* Learning_rate: 0.000001
* Loss: sparse categorical crossentropy
* Batch size: 8

### Transfer Learning - ResNet50
* Dense layer neurons: 128
* L2 regularization: 0.1
* Dropout rate: 30%
* Output layer: Dense(2, activation='softmax')
* Learning_rate: 0.00001
* Loss: sparse categorical crossentropy

### Transfer Learning - VGG16
* Dense layer neurons: 128
* L2 regularization: 0.0005
* Dropout rate: 40%
* Output layer: Dense(2, activation='softmax')
* Learning_rate: 0.0001
* Loss: sparse categorical crossentropy

## Summary
In this project, four models have almost same performance. VGG16 model has a sightly better test f1 score (0.54), and a better performance on detecting frost (precision: 0.66; recall: 0.59). However, its validation loss fluctuated after 6 epochs, which means the model may be overfitting. Generally, CNN+MLP and ResNet50 models both have a reliable performance. <br>
* CNN+MLP (weighted avg): f1 score: 0.53 | precision: 0.55 | recall: 0.52
* ResNet50 (weighted avg): f1 score: 0.52 | precision: 0.55 | recall: 0.51<br>
Both models has a decreasing validation loss. <br><br>
Although EfficientNetB0 model has a same-level test performance, the result may not be very reliable. The prediction result is highly imbalanced. With many combinations of hyperparameters, the model was easy to be overfitting after two or three epoches.
* EfficientNetB0 (weighted avg): f1 score: 0.53 | precision: 0.54 | recall: 0.65










