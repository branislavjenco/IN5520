# Segmentation

Segmentation is a separation of regions in an image, based on some criteria. 

## Region

A region in an image can be defined by it's edge or by it's interior (two different representations). 

=> That's why some segmentation approchaes are edge based and some are region based.

Region-based methods are good because:
* you have more pixels to work with (more information), can use texture information
* edge detection is difficult in noisy images and edge linking is not trivial

Edge-based methods are good because:
* less comples algos
* edges are often the most important feature in separating regions
* works best with good contrast between object and background

## Edge-based segmentation

Usually, it consists of two steps:
1. We have to detect the edges using some filter (Gradient, Laplace, LoG, Canny)
2. Then we have to link these "edgels" into edges
  * Either locally using the gradient magnitude and vector
  * Or globally using smt like Hough transform
  
 The gradient operator often isn't enough to produce correct edges. It will rarely be zero (because the pixels always change in some way) and the distribution of the magnitured is often skewed. We therefore have to threshold this somehow, but simple thresholding doesn't often work.
 Couple of ways to do this
 1. Hysteresis thresholding - all gradient magnitudes above a certain strict threshold are assumed to be bona fide edges and then, all gradient magniturs above a certain unstrict threshold _and_ connected to a bone fide pixel are also real edges
 2. Thinning of edges - quantize directions into 8 or 4 directions and for all non-zero gradient magnitude pixels, inspect the two neighbouring pixels in the four/eight directions. If either of those pixels has a higher magnitude, mark this pixel. After doing this for all pixels, delete all the marked pixels in the image.
          
## Region-based segmentation

### Region growing

Uses a _similarity criterion_ to grow the segment along neighbouring pixels, starting from some seed pixels. These can be chosen by hand, or all pixels can be used, or they can be chosen randomly. 

We can either try to segment the whole image, in which case we select seeds from the whole range of gray levels and we grow until all pixels belong into some region. Alternatively, what is used often is that we only select seeds from objects of interest (f.e. pixels with the peak intensity) and grow those until the similarity criterion is fulfilled.

Questions:
* how to find good seeds
* how to find good similarity criteria

### Region merging

Kind of opposite to the previous approach. Start by giving all pixels a unique label -> all pixels belong to a different region -> as many regions as pixels.
