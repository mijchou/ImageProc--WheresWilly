# ImageProc--Where's willy

To be edited...

## The task:

The good old Lena's back!

![Lena_Origin](/lena.png)

With Willy aside.

![Lena_wit_Willy](/lena_modified.png)

Along the rise of wearable technology, we no longer need to spot out Willy the old way we do--we ask the computer to do it. So, how do we extract the difference between two images?

Setup
=====

The R library *png* will be used to load and save images in to .png files. To *install.packages()* the package for the first time using it.

``` r
install.packages('png')
library(png)
```

Load images
===========

Store two images into img.a (the original lena) and img.b (with Willy.)

``` r
img.a <- readPNG("lena.png")
img.b <- readPNG("lena_modified.png")
```

Data checking
=============

Each image comes as an array of 3 dimentions. The 

``` r
str(img.a) ; str(img.b) # Array 512*512*4
```

    ##  num [1:512, 1:512, 1:4] 0.635 0.635 0.635 0.635 0.635 ...

    ##  num [1:512, 1:512, 1:4] 0.635 0.635 0.635 0.635 0.635 ...

Difference extraction
=====================

1. Create an empty array (a blank sheet!) to store the differences (where Willy is) between two images.
2. Find out which entries of img.a and img.b aren't equivalent. That's where Willy is! Store the location of Willy to be used later.
3. On the blank sheet we created from 1., assign the entries of img.b to where we find Willy - the location obtained from 2.

``` r
diff.arr <- array(1L, dim = c(512, 512, 4))
diff.index <- which(img.a != img.b)
diff.arr[diff.index] <- img.b[diff.index]
```

Export image
============

That's it! Export the image using writePNG().

``` r
writePNG(diff.arr, "difference.png")
```

![Difference](/difference.png) 

Done!
