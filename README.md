# ImageProc--Where's willy

Big data ain't all about the big 'amount' of data, but also the 'big' variety of their kinds. Today we deal with not only data handed to us in the spreadsheet, but also those in all forms such as texts, audio and images. 

## The task:

The good old Lena's back! \\
![Lena_Origin](/lena.png) \\

And with Willy aside. \\
![Lena_wit_Willy](/lena_modified.png) \\

Along the rise of wearable technology, we no longer need to spot out Willy the old way we do--we ask the computer to do it. \\

So, how do we extract the difference between two images? \\

## 

The library we'll be needing here is called *png*. Remember to *install.packages()* the package for the first time using it.

``` r
install.packages('png')
library(png)
```

Load images
===========



``` r
img.a <- readPNG("lena.png")
img.b <- readPNG("lena_modified.png")
```

Data checking
=============

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

![Difference](/difference.png) \\

