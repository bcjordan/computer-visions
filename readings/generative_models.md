“What I cannot create, I do not understand.”
—Richard Feynman

*"so the models are forced to discover and efficiently internalize the essence of the data in order to generate it."*

Generative models are good at automatically learning the natural features of a dataset

Generative model: large NN that outputs image (outputs are samples from the model)

# DCGAN

100 random numbers (code), changed gradually, outputs an image.

- Convolution / CNNs - https://cs231n.github.io/convolutional-networks/
    - Width/height: of image. Depth - color depth
    - Layer types:
        - Convolutional layers: (dot product between self and? or input and?) surrounding kernel
            - intuition: why we see resolution blocks refining during training?
            - 12 filters, stack them along depth
                 
                 
End @ Local Connectivity
        

# Stats

- [ImageNet](http://www.image-net.org) - 1.2 million images, often resized to ~256x256

# Concepts

- Code / Latent variables - variables inferred instead of observed
- Convolution layer - kernel/filter (kernel is block being looked at)
    - Strides: skip over
    - Padding: edges (0s) - can avoid changing dimensionality
- Volume (3-dim matrix)
- Receptive field of neuron - essentially filter size

    


