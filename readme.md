# Image Captioning

## Intro
Image captioning is a task that involves generating natural language descriptions of images. It has practical applications in fields such as robotics, virtual assistants, and accessibility. The Flickr30k dataset is a popular benchmark for image captioning, consisting of 31,783 images, each with five captions written by different human annotators. In this project, we explore the task of image captioning using the Flickr30k dataset and a deep learning model based on the Xception architecture for image feature extraction. One of the challenges in image captioning is to generate captions that are not only accurate but also fluent and natural sounding.

## Dataset
The Flickr30k dataset consists of 31,783 images and 158,915 captions. Each image in the dataset has five captions written by different human annotators. This allows for a diverse set of captions for each image, which is helpful in training models that can generate varied and natural-sounding captions. In this project, we explore the task of image captioning using the Flickr30k dataset and a deep learning model based on the Xception architecture for image feature extraction.

## Preprocessing
The first step in building an Image captioning model is to preprocess the data. Since we are dealing with two types of data i.e., Text data (Captions) and Images. First, we processed the text data. This involves cleaning the data, tokenizing the words, creating a vocabulary.
### Cleaning the Data
The first step in cleaning the data is to remove any captions that are not well-formed. This includes captions that are incomplete, grammatically incorrect, or nonsensical. Words startseq and endseq are added in front and end of each caption, so we know to stop predicting.
### Tokenizing the Words
The next step is to tokenize the words in the captions. This means splitting the words into individual tokens. For example, the sentence “Two friends enjoy time spent together” would be split into the token’s “Two”, “friends”, “enjoy”, “time”, “spent” and "together".
### Creating a Vocabulary
The final step in preprocessing the text data is to create a vocabulary. This is a list of all the unique words that appear in the captions. The vocabulary is used to represent the words in the captions as integers. This makes it easier for the model to learn the relationship between images and their corresponding captions.

Next step is preprocessing of Images data. We have used Xception model as the base model to preprocess the images. In this step images are converted to array of numbers. Then we created sequences to feed into the model.

## Models
The pre-trained CNN we used for image feature extraction was Xception which is a state-of-the-art CNN that has been pre-trained on ImageNet. We fine-tuned the CNN on the Flickr30k dataset and extracted the image features using the final convolutional layer of the CNN. We then fed the image features into the deep learning models for caption generation. We have used several different models for training.

Our best model had 4 layers for text data including one LSTM (Long Short-Term Memory) layer and three layers for image processing. Then the output of these two were combined in the decoder layer and then after two more dense layers was our output layer. This model performed well. We tried more models with more layers, but they did not perform that well.

After trying multiple combinations of layers, we found that having more layers in the model does not necessarily means better model. But giving the model more training with more epochs improved the captions accuracy.

## Evaluation
To evaluate our models, we used the standard metrics used in image captioning tasks: Sentence bleu and Meteor score which measure the similarity between the generated captions and the human-written captions in the dataset. The following is example of caption and predicted caption with bleu score and Meteor score.
#### Captions
1. two young guys with shaggy hair look at their hands while hanging out in the yard.
2. two young white males are outside near many bushes.
3. two men in green shirts are standing in yard.
4. man in blue shirt standing in garden.
5. two friends enjoy time spent together.
#### Predicted
man in blue shirt is standing in front of the building
#### Scores
Bleu Score: 0.51
Meteor Score: 0.79

## Conclusion
In this project, we explored the task of image captioning using the Flickr30k dataset and a deep learning model based on the Xception architecture for image feature extraction. Our model achieved competitive results on the Flickr30k dataset, outperforming some of the previous state-of-the-art models. Future work could involve exploring different pre-trained models for image feature extraction and using more advanced techniques such as attention mechanisms to improve caption generation.
