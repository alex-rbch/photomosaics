# Autoencoders for solving Photomosaic

The provided algorithm demostrates how to transform an image of your choice into a beatiful photomosaic consisting of artificially generated images, using the magic of autoencoders. 



Unlike many other algorithms, this one does not implement a metric to search for the closest image in a dataset to fill each tile, the algorithm just generates it. Working with large datasets, this algorithm has potential to outpace and outperform search-based models. Depending on the quality of an autoencoder, this algorithm achieves truly eye-pleasing results.

## Story behind the project

As with many great things in life, the idea for this project was born from an argument with a friend. Paradoxically an autoencoder model, that ideally has the same input and output, can be useful by itself. The trick is to change the domain of the model from the original dataset. 

According to Wikipedia, Photomosaic, is a picture that has been divided into tiled sections, each of which is replaced with another photograph that matches the target photo. Behind this phenomenon is an incredible power of human vision that permits us to highlight certain elements of these tiles to generalize them into a large photo.

An autoencoder can transform tiles of an image into  
