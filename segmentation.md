## Segmentation

Segmentation is a separation of regions in an image, based on some criteria. 

## Region

A region in an image can be defined by it's edge or by it's interior (two different representations). 

=> That's why some segmentation approchaes are edge based and some are region based.

Region-based methods are good because:
- you have more pixels to work with (more information), can use texture information
- edge detection is difficult in noisy images

Edge-based methods are good because:
- less comples algos
- edges are often the most important feature in separating regions

## Edge-based segmentation

Usually, it consists of two steps:
1. We have to detect the edges using some filter (Gradient, Laplace, LoG, Canny)
2. Then we have to link these "edgels" into edges
  2.1. Either locally using the gradient magnitude and vector
  2.2. Or globally using smt like Hough transform
  
 The gradient operator often isn't enough to produce correct edges. It will rarely be zero (because the pixels always change in some way) and the distribution of the magnitured is often skewed. We therefore have to threshold this somehow, but simple thresholding doesn't often work.
 Couple of ways to do this
 1. Hysteresis thresholding - all gradient magnitudes above a certain strict threshold are assumed to be bona fide edges and then, all gradient magniturs above a certain unstrict threshold _and_ connected to a bone fide pixel are also real edges
 2. Thinning of edges - quantize directions into 8 or 4 directions and for all non-zero gradient magnitude pixels, inspect the two neighbouring pixels in the four/eight directions. If either of those pixels has a higher magnitude, mark this pixel. After doing this for all pixels, delete all the marked pixels in the image.
          
 
