
Homework exercise to do: [get set up, run through entire notebook](http://visions.media.mit.edu/howto-using-google-cloud/)

# Convolutions and Pooling

Convolutions: roughly multiply and add. Higher and higher levels of features. 9 weights (filter applied over entire image). Far more efficient than ANNs of past.

Multiply each pixel by the filter weight.

*Pooling*: combines all pixels to a single value (max / average).

# Generative Models & Unsupervised Learning

## Supervised vs Unsupervised Learning

(This will lead us to generative models)

**Supervised**: Given data X ➡️ predict output Y

Requires annotated data. Learns to do same thing on un-seen data.

* Some annotations attached to them (class/annotation: cat/dog).
* E.g. imageNet: every image annotated with data.
* E.g. segmentation: every cat is outlined 

**Unsupervised**: Given data X ➡ uncover underlying "latent" structure

Requires just data (not annotated).

Can gain info on correlation and clustering just from the data. (Principal component analysis)

* E.g. clustering / density and anomaly detection - 95% of data from dashcams are sunny, highway, straight road (mode/mean of data)
* E.g. compression
* E.g. **dimensionality reduction** (important for generative stuff we're doing in this class) — images are very **high dimension**, 19x19 pixel image = 361-dimension flat vector
    * Humans can do 15-20 numbers.

## Dimensionality Reduction
    
"Curse of dimensionality" - As the # of dimension linearly grows, the # of samples to cover the space grows exponentially. Thinking of it like a combinatorics problem, growing # of dice, hitting same number.
 
"Mean face" - you can apply arithmetic to vectors, including face images. "Mean face" is adding up vectors and dividing.

Dimensionality reduction / PCA: look at axes with highest variance. Get rid of all extra space in square (find a new )

[Eigen decomposition](http://mathworld.wolfram.com/EigenDecomposition.html)

Instead of just looking at pixel values, get better set of [eigenvectors](http://mathworld.wolfram.com/Eigenvector.html) (more compact representation).

90% of variance is covered by the first EVs (principal components / eigenvectors).

JPEG: applies discrete cosine transform: every 8x8, assign a code, determine how you need to add the encoded entities.

## Discriminative vs. Generative Modeling

**Discriminative models**: directly estimate P(y|x)

* Learn decision boundary.
* E.g. regressions, SVMs (draw a line/curve/etc. to separate items)

**Generative models**: estimate P(x|y) to deduce P(y|x)

* Learn probability distributions of data
* e.g. [Gaussian Discriminant Analysis](https://towardsdatascience.com/gaussian-discriminant-analysis-an-example-of-generative-learning-algorithms-2e336ba7aa5c), [Naive Bayes](https://towardsdatascience.com/introduction-to-naive-bayes-classification-4cffabb1ae54)

# Generative Modeling

* Check out [6.S191](http://introtodeeplearning.com/#schedule)

Goal: take input samples, create generated samples.

If one showed you a bunch of input samples, and asked you to draw another, you probably could. *Idea: could be an unplugged activity.*
    Activity: guess which drawing was the generated one.

From density estimation / compact representation, you can generate new data.  

## Autoencoders

    Input -> Encoder < Compact latent representation > -> Decoder -> Reconstruction
      |                                                                        |
      --------------------------------------------------------------------- loss
      
      
* Encoder takes data (high dimensions), encodes to very small bottleneck
* Autoencoding is a form of compression. Smaller latent space forces a larger training bottleneck.
* 2500 to 2 numbers. For easy dataset, compression can be huge.
* Can use autoencoder to warm up discriminator
* Autoencoders are good for de-noising images, smoothing motion capture

Can you use autoencoders to generate NEW data, cats the world hasn't seen before?

Problem: latent feature space (center) is unbounded, e.g. 5 random numbers, no MEANING.

One idea: assigning meaning to the features. Conditional GANs, GANs, use them to tweak meaningfully.

**Variational autoencoder (VAE)** - sample from mean / variance distribution (gaussian distribution)
    Sampling itself is non-deterministic and involves randomness
    Decoder takes sample, decodes back to something that looks like input image.
    
You train the VAE. Diff btwn input and output is the *reconstruction loss*.

Autoencoder vs VAE

VAE creates density estimation

Variational part gives intuition of what to do when generate the data
Instead of random #s, its a probability distribution
Reparameterization

## Generative Adversarial Networks (GANs)

What if we don't care about autoencoding/decoding, JUST want samples out of distribution.

Give random noise, generate new cats.

Going from 10 numbers to a million, training decoder is difficult.

Ian Goodfellow 2014 ([pdf](https://arxiv.org/abs/1406.2661)) (over 8,600 citations)

After a million iterations, discriminator won't be able to tell.

## E.g. Playing game of GAN training

give 8 fake samples, 4 real, train discriminator to tell if real vs. fake. ~10 iterations/epochs, then go back to generator.

Discriminator, through backprop, tells generator **where it went wrong**, and how to update its weights.
    Idea: if discriminator shared a shared higher dimension representation as to WHY it was wrong, as way to bootstrap early generator?

Loss function is not simple.

GANs are notoriously hard to train. Very slow.

[Fei Fei Li](http://cs231n.stanford.edu/slides/2017/cs231n_2017_lecture13.pdf)

Minimax


## GAN supervision (CGAN, InfoGAN)

* Deep Convolutional GANs (DCGans)
    * [Radford 2015](https://arxiv.org/abs/1511.06434) 
* VAE-GANs
    * Sample from distribution instead of random #s (uniform gaussian distribution)
    * Can do some arithmetic with latent variables (face + eyeglasses + gray hair etc.)
    * Find the MODE for all bald people, put through VAE, get latent space for them. Average of that == baldness.
        * Idea: 
* CGANs - conditional GANs ([Isola 2016](https://arxiv.org/abs/1611.07004))
    * Also condition it with some extra information (Add labeling / classification alongside)
    *  + InfoGAN
    * Image to Image - semantic segmentation into real images
    * [InfoGAN](https://arxiv.org/abs/1606.03657) - control thickness of pen, narrowness of digit
        * Face pose, elevation, lighting, wide/narrow
    * GauGAN - turning doodles into pictures
    * S(something)GAN
    * CycleGAN - horses to Zebras and back. [Zhu '17](https://junyanz.github.io/CycleGAN/), [Philip Isola @ MIT](http://web.mit.edu/phillipi/)
    * pix2pix - [Isola](https://arxiv.org/abs/1611.07004)
    * PGANs - progressive growing of GANs. 
    * Big GAN - generates images of everything you would want to make.
    * StyleGAN - add/mix features of different people
    * FUNIT Liu 19 - Turn dog into anything
    
Idea: Audio GANs style transfer


    
   
