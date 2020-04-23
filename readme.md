# Detecting Similar Images using a Deep-Learning Neural Network

My coworker, Jesse Fulton, asked me to look into bringing the knowledge gained in my recent machine-learning classes to bear on the problem of assigning attribution to an image based on its similarity to a known image in an existing corpus.

My initial response was to suggest that there might be a manual way to determine that two images were essentially the same, by hashing scaled-down copies of the images, and comparing the hashes.  This was naive and doesn't scale well.

I wasn't sure anything would scale well.  When checking an unknown image for similarity to an existing corpus of images, can you avoid comparing it to every known image?  Or can the comparison be sped up to make such a check feasible?

## Identifying a solution

Google turned up an article from 2017 that seemed to describe a possible solution to the problem: [Identifying Similar Images with TensorFlow](https://douglasduhaime.com/posts/identifying-similar-images-with-tensorflow.html).

The article explains how you can take one of Google's exsiting Tensorflow tutorials for image classification, and modify it to allow comparison of images.  The last layer in the original neural network contains a node for each label, containing the probability that that label is relevant.  By stripping away that last layer, you're left with a vector representation of the original image: a list of floating-point numbers representing the weights of the nodes in the model, for that image.

Once you have vector representations of images, they can be mapped into an N-dimensional space, and the distance between two such points can be calculated.  The closer two points are to each other, the greater the similarlity between the images.

## Proving it works

The article cited above links to the code necessary to implement the solution.  It even provides an example that produces images similar to one you choose.

But there are a couple of questions we would like to answer, beyond what is already shown:

1. Is there a useful "similarity distance" that can be configured to find images effectively identical to known originals, even when they have been modified to prevent easy identification?

2. How quickly can comparisons be performed?  How many images can we check in a given time period?  Is it fast enough to be useful?  Does it scale well enough?
