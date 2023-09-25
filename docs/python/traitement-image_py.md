Library `opencv-python` importer `cv2`

[Tuto Université de Virginie](https://learning.rc.virginia.edu/notes/opencv/)

Library `opencv-python`

`import cv2`

`cv2.imread(image, type)` charger l'image.
Type :
`cv2.COLOR_BGR2RGB`
`cv2.IMREAD_COLOR`

`.shape` dimension de l'image.

```
img = cv2.imread(image)
cv2.imshow('image window', img) # show the image, provide window name first
cv2.waitKey(0)
```
Afficher une image.

.cvtColor(image, cv2.COLOR_BGR2GRAY)

Les filtres morphologiques

# binarize the image
binr = cv2.threshold(img, 0, 255, cv2.THRESH_BINARY+cv2.THRESH_OTSU)[1]


# define the kernel
kernel = np.ones((5, 5), np.uint8)
 
# invert the image
invert = cv2.bitwise_not(binr)
 
# erode the image
erosion = cv2.erode(invert, kernel, iterations=1)

kernel est une matrice.

Numpy : 
np.ones((3, 3), np.uint8) 
