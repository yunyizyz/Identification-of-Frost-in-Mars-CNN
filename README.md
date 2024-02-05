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


## Dataset: Jet Propulsion Laboratory Open Repository
This dataset was created to study Mars’ seasonal frost cycle and its role in the planet’s climate and surface evolution over the past 2 billion years. The data helps in identifying low-latitude frosted microclimates and their impact on climate.

Images (png files) and labels (json files) are organized in the data directory by “subframes.” Subframes are individual 5120x5120 pixel images which are crops of the original HiRISE images (often on the order of 50k x 10k pixels).
Individual subframes were annotated by the contributors and then sliced into 299x299 “tiles.” Each tile has an associated label for use in training ML algorithms.
There are 214 subframes and a total of 119920 tiles. Each tile has annotations which have been used to assign labels to the tiles ‘frost’ or ‘background.’ 
Each JSON file contains all the annotation information collected from human annotators.

* The dataset can be accessed [here](https://dataverse.jpl.nasa.gov/dataset.xhtml?persistentId=doi:10.48577/jpl.QJ9PYA).
* Data Augmentation techniques I applied: random contrast, resize








