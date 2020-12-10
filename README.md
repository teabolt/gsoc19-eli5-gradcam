# gsoc19-eli5-gradcam
Google Summer of Code 2019 Work Product Submission for the ELI5 Grad-CAM project under Scrapy, Python Software Foundation.

Hi! Welcome to the final report for the project titled “Grad-CAM Neural Network Explanations for ELI5” (https://summerofcode.withgoogle.com/archive/2019/projects/5066973807902720/).

## Summary

All of my work was done as additions to the python library “ELI5” https://github.com/TeamHG-Memex/eli5. 

I have worked on adding support to explain image and text classifier predictions in Keras and PyTorch. I have implemented the Grad-CAM technique (https://arxiv.org/abs/1610.02391) for explanations. This resulted in mypy annotated and commented Python source code (`eli5.keras`, `eli5.nn`, `eli5.pytorch`, `eli5.formatters.image`), pytest unit and integration tests, and sphinx docstrings, library descriptions and tutorials.

I have decided to exclude adding support for Tensorflow and non-classifier networks in this project.

Example of an explanation for why a network classified this image as “dog”

![gradcam cat dog image heatmap overlay](images/gradcam-catdog.png?raw=true "Predicted class: dog. Explanation for prediction: highlighted area.")

Example explanation for why a certain score was given by a sentiment analysis network

![gradcam text heatmap over tokens](images/gradcam-text.png?raw=true "Predicted sentiment: low. Explanation for prediction: highlighted positive (green) and negative (red) words.")
  
## What is merged

### Explaining Keras image classifiers

In this piece of work we explain the predictions done by a Keras classifier that takes images as its input.

Covered by two merged pull requests
* https://github.com/TeamHG-Memex/eli5/pull/315
* https://github.com/TeamHG-Memex/eli5/pull/329 

See https://eli5.readthedocs.io/en/latest/libraries/keras.html and https://eli5.readthedocs.io/en/latest/tutorials/keras-image-classifiers.html for usage. The user can now call `eli5.explain_prediction()` top level function on a Keras image classifier.

## What is left to do

### Explaining Keras text models

We explain the predictions of a Keras classifier that takes text as its input.

Covered by this open pull request: https://github.com/TeamHG-Memex/eli5/pull/325
* LAST COMMIT - https://github.com/TeamHG-Memex/eli5/pull/325/commits/7616a4e8048ad349cdac00eace80800ccb050db3, “Add gradcam test utils. Move tests from integration to unit in Keras”

Left to do
* Complete some TODO items in source comments.
* Reviewer feedback.

### Explaining PyTorch image and text models

We explain classifiers defined in PyTorch that take either images or text as its input. This is a scaled down version of support we would have for Keras.

Covered by this open pull request: https://github.com/TeamHG-Memex/eli5/pull/327
* LAST COMMIT - https://github.com/TeamHG-Memex/eli5/pull/327/commits/9c8d7c6583d5142afbccbe1bbd68bd30b3477413, “Replace _forward_modules() with explicit named_modules() call (CI fix)”

Left to do
* Unit and integration tests.
* Text tutorial.
* PyTorch library description.
* Docstrings.
* Reviewer feedback.

What is working (based on manual testing)
* Reasonable explanations for image and text classifier predictions.
* Most of Keras features are supported (`targets`, `layer`, `relu`, `counterfactual`, and various text arguments).

### Other (according to the original project plan)

These are optional. Either I can do them myself or let the users/maintainers do it.

#### Delivering a release
* Open a PR to help maintainers make a new ELI5 release (bump version, etc).

#### Tensorflow
* Implement support for Keras models defined through Tensorflow (tf.keras).

#### Non-classifier models
* Support models for regression, Visual Question Answering, etc.
* Current code attempts to make this an easy thing to add support for.
* Regression can be converted into classification.

## Challenges
* Usual coding stuff - working with Keras, numpy, Pillow, PyTorch.
* Later down the line: making changes that “break” a lot of things, i.e. need to update other code, tests, docs.
* Prioritizing what to work on. Working up to speed to get "features" done.
* Estimating how long certain tasks will take.
* Finding hardware suitable for Machine Learning, i.e. using Kaggle kernels.

## Learnings
* Grad-CAM as a gradient method for explanations.
* Keras training and inference.
* PyTorch training and inference.
* Text and image preprocessing.
* Numpy, Pillow.
* Sphinx, reStructuredText.
* Mypy, pytest, tox, Travis CI, codecov.
* Git, virtualenv, pip.
* GitHub, Kaggle, Jupyter Notebook.


Thank you to my mentors [Konstatin](https://github.com/lopuhin) and [Mikhail](https://github.com/kmike). I hope this work proves useful!
