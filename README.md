# ImageProc--Where's willy



## The task:

The good old Lena's back!

![Lena_Origin](/lena.png) \

And with Willy aside. \

![Lena_wit_Willy](/lena_modified.png) \

Along the rise of wearable technology, we no longer need to spot out Willy the old way we do--we ask the computer to do it. \

So, how do we extract the difference between two images? \

## 

We'll use the library *png* to load and save images of the format. Remember to *install.packages()* the package for the first time using it.

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

``` r
diff.arr <- array(1L, dim = c(512, 512, 4))
diff.index <- which(img.a != img.b)
diff.arr[diff.index] <- img.b[diff.index]
```

Export image
============

``` r
writePNG(diff.arr, "difference.png")
```

![Difference](/difference.png) 

Done!
