# Autoencoders for solving Photomosaics, or "Automosaics"
Transform an image of your choice into a beautiful photomosaic consisting of artificially generated tiles.

<p align="center">
<img src="https://user-images.githubusercontent.com/42875258/138995837-b2da6a40-3706-47e7-8eb3-2efc6959241e.png" width="500">
</p>

Vary the number of tiles to achieve different levels of detalization.

<p align="center">
<img src="https://user-images.githubusercontent.com/42875258/138996178-49b0102f-6685-4c0e-8033-3ee7b327520d.png" width="600">
</p>

This approach makes use of a specially pretrained autoencoder to encode tiles into a dense latent space and decode them as images close to the autoencoder’s original training set.

# How is this different from pre-prepared tiles?
There are many great search-based algorithms to create photomosaics. They find tiles from a dataset of original tiles based on a certain similarity metric. These algorithms come with an advantage in the form of the perfect quality of tiles. You can find a large number of such artworks on the web. For example, if you are a fan of British football, on the left there is a portrait of Bobby Robson made up of 2,000 pictures of Newcastle (with repetitions) by Welsh artist Nathan Wyburn. It contains about 5,000 tiles. For comparision, on the right there is a photomosaic of yours truly consisting of about 1,700 MNIST-type tiles. 

<p align="center">
<img src="https://user-images.githubusercontent.com/42875258/138990510-210716c6-f4f1-431d-826e-5b6306b590a2.jpg" height="250" width="160">
<img src="https://user-images.githubusercontent.com/42875258/138997696-9b961e55-3815-4656-ad92-6f1aaa785330.png" height="253" width="190">
</p>

This comparison clearly demonstrates that search-based models lack flexibility, and their effectiveness and speed depend heavily on the diversity and size of datasets. The autoencoder approach has three main advantages over search-based models. 
1)	Tiles fit better in their neighborhoods because they are generated for each location individually. 
2)	Fewer tiles are required to process images in a meaningful way. 
3)	The speed does not suffer from the size of the dataset used for autoencoder training. This promises to be useful with large and complex datasets.

Overall, the search-based approach is still better for creating meaningful artworks, while the autoencoder approach can act as a quick online operating filter.

# Efficiency of this approach 
Generation of realistic images from “something a bit better than random noise” while keeping some visual information presents many challenges. 

It is necessary to keep the balance between the quality of tiles and the overall accuracy of photomosaics. By this token, it is vitally important to keep the set of possible encodings in the latent space as dense as possible to ensure that each tile satisfies the desired quality.

For MNIST, I successfully used a two-dimensional latent space. To support uniformity, I included a sigmoid activation function to limit the latent space to $(0, 1)^2$ and added a layer of Gaussian noise to the model during training as regularization. These are several examples of distributions of digits within the latent space.

<p align="center">
<img src="https://user-images.githubusercontent.com/42875258/138975309-1c8247a7-6e2a-4376-8fe2-707a8b07170a.png" width="250">
<img src="https://user-images.githubusercontent.com/42875258/139004522-f107cac6-731b-4e71-a466-5b72991849d2.png" width="250">
<img src="https://user-images.githubusercontent.com/42875258/139004548-555eb4b5-0b0b-4472-bc92-3a84d429db24.png" width="250">  
</p>

Finally, I must mention that a more advanced autoencoder or even a separate GAN might overcome these problems. Preparing such models takes time, but a good photomosaic is certainly worth it. 
