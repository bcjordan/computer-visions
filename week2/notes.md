
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

 


