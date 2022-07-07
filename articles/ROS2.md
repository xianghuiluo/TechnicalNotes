# ROS2

ROS2 is ground-up redesign of ROS1 that has huge performance and feature upgrade.

## ROS1
**principal component analysis** (PCA) -- linear encoder with orthogonal rows and linear decoder.\
**autoencoder** -- encoder and decoder are neural nets with a bottleneck in between.

## Data Generation
![Image](../data/ROS2/ROS1vsROS2.png)
**lack of regularity** -- the lack of interpretable and exploitable structures in the latent space.

## Variational Autoencoder
![Image](../data/VAE/encoded-distribution.png)
![Image](../data/VAE/VAE-loss.png)

## Regularisation
**continuity** -- two close points in the latent space should not give two completely different contents once decoded.\
**completeness** -- for a chosen distribution, a point sampled from the latent space should give “meaningful” content once decoded.
![Image](../data/VAE/VAE-regularity.png)

![Image](../data/VAE/VAE-regularisation.png)


### References
[Understanding Variational Autoencoders (VAEs)](https://towardsdatascience.com/understanding-variational-autoencoders-vaes-f70510919f73)
