# Car classifier

Machine Learning project to classify car models by photos. Inspired by [fastai](https://www.fast.ai) course & code. So far this is just the first version and a proof of concept. Current version classifies cars by 8 categories, which represents 8 generations of Volkswagen Golf model.

*[**Try it!**](https://huggingface.co/spaces/kulich-ua/vw-golf-classifier) (on mobile or desktop)*

All parts of this application are written in python in form of [Jupyter Notebooks](https://jupyter.org). Further I will describe the main steps of this project and point out which notebooks are responsible for them.

## Table of Contents

- [Data](#data)
  - [Gathering](#gathering)
  - [Splitting](#splitting)
- [Training](#training)
  - [Model](#model)
  - [Accuracy](#accuracy)
  - [Example of Predictions](#example-of-predictions)
- [Application](#application)
  - [Deployment](#deployment)
- [Main Dependencies](#main-dependencies)

## Data

### Gathering

##### ([GatherDataBing.ipynb](GatherDataBing.ipynb), [GatherDataDDG.ipynb](GatherDataDDG.ipynb))
Data for this project was collected from Internet. Partially using scripts and search engines (Bing & DuckDuckGo). But mostly by searching & downloading by hand.  
**1500** images there collected in total. Approximately **190** images per category (so far there are **8** VW Golf generations).
In addition, **67** photos were collected on the street with the iPhone camera.

*The training data is not a part of this repo.*

### Splitting
##### ([Split.ipynb](Split.ipynb))

The data was then split in 3 sets: training (67%), validation (19%) & test (14%).

## Training
##### ([Train.ipynb](Train.ipynb))
### Model

A pre-trained ResNet50 model was selected for the training. Then it was *fine tuned* using training data for **100** epochs using MacBook Pro (2018, i7, 16 GB) and only CPU (the training took about 6 hours). A standard set of augmentations from fastai library were applied to the training data.

You can download the model [here](https://drive.google.com/file/d/170T-MMyYRKQGUJF9z1RhLypIkvLoVZg-/view?usp=sharing).

### Accuracy

Validation set - **96%**  
Test set - **95%**  
Own iPhone photos taken on street - **88%**

### Example of predictions
![predictions example](readme/predictions.png)

## Application

##### ([app.py](https://huggingface.co/spaces/kulich-ua/vw-golf-classifier/blob/main/app.py))

A web application is build using [Gradio](https://www.gradio.app/) library.

<details>
  <summary>older alternative</summary>
  
  A web application ([Inference.ipynb](Inference.ipynb)) is rendered from Jupyter Notebook using [Voilà](https://github.com/voila-dashboards/voila/) library.
</details>

### Deployment

<details open>
  <summary>Hugging Face</summary>

  The Gradio web application is deployed for free on [Hugging Face](https://www.heroku.com/) platform.
</details>

<details>
  <summary>Heroku (not active)</summary>

  The Voila web application is deployed ~~for free~~(not anymore) on [Heroku](https://www.heroku.com/) platform.
  *The model is hosted on Google Drive and downloaded at runtime to bypass storage limits for free hosting.*
</details>

 ## Main dependencies
 - [fastai](https://docs.fast.ai)
 - [fastbook](https://github.com/fastai/fastbook)
 - [Jupyter Notebooks](https://jupyter.org)
 - [Voilà](https://github.com/voila-dashboards/voila/)
 - [Gradio](https://www.gradio.app/)
 - macOS