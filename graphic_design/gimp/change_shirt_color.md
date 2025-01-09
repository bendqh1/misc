## Question

I have an image in which only my upper body from the belly up can be seen on a White background.

In this image, I wear a blank Red shirt (a Red shirt with no symbols on it, so it's just plain Red).

With the help of the program GIMP, I want to change the color of the Shirt from Red to Blue.

How to do that?

## Answer (without working with layers)

1. Go to `View` and disable `Show Layer Boundary`.
2. Carefully select the Red parts with zoom in and zoom out by by the `Scissors`.
	* To start over with selection tools go to `Select > None`.
3. If needed, adjust selection by growing or shrinking to ensure touching all boundaries.
4. Adjust selection points by dragging them respectively.
5. Go to `Hue-Saturation` and change `Master Hue` to `-115`.
