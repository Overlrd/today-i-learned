# Fine tuning a pretrained model

While using feature extraction with pretrained computer vision models one complementary technique is fine turing.
Usualy when doing feature extraction , we freeze the layers of the convolutional base extracted from the pretrained model.
Then add a custom classifier to the conv_base an then train it.
Then we can avoid that the error signal from the classifier we will add  propagate through the conv_base.

**Fine Tuning** consist in training the new model (frozen conv_base + new classifier), unfreeze some of the top layers of the 
conv_base and then retrain the new convolutional base and the previous trained classifier.
Doing this slighty adjust the abstract representations in the conv_base's layers and make them more relevant to the new task.

[Source](https://www.manning.com/books/deep-learning-with-python-second-edition)
