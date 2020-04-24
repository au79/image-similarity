# Source images

To be able to test code that analyzes image data, I need to find a reasonable source of images to use.  Both my limited experience and Google have pointed me at [ImageNet](http://image-net.org/), the image database organized using the [WordNet](http://wordnet.princeton.edu/) hierarchy.

It's possible to request access to download the original image set, but you need to assert you're using them for research or education pruposes.  Also, I don't need the entire set, but just enough images to prove the code works.

Unfortunately, many of the original images are no longer available at the original URL.  According to [an estimate from 2016](https://medium.com/@arjanwijnveen/how-copyright-is-causing-a-decay-in-public-datasets-f760c5510418), 30% of the image URLs return a 404.

## Steps forward

1. Gather image URLs by hand.  Searching on [image-net.org](http://image-net.org/search?q=dragonfly) by term returns relevant [synsets](https://en.wiktionary.org/wiki/synset).  The synset detail page contains a link to a list of the original URLs for its images.

2. Write a script to check for existing images, to winnow the list down.

3. Download the images.  Probably the winnowed list can be fed straight to `wget`.
