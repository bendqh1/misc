## How to compress an image to reduce its file size from about 10 mb to 1 mb with gimp

1. Go to `Image > Scale Image`, and reduce the resolution (e.g., width and height). This can significantly lower the file size.
1. Go to `File > Export As`.
1. Choose your file format (e.g., JPEG).
1. In the export options, adjust the Quality slider to a lower value (around 60–70% for JPEG).
1. Preview the file size in the bottom-left corner and adjust quality until it's below 1 MB.
1. Click Export.

## How to add an overlay of CSS rgba(1, 1, 1, 0.7) to an image in GIMP?

1. Do Layer > New Layer
1. Double click the foreground colour square in the tool bar, and set #010101 as the colour
1. Do Edit > Fill with FG colour
1. In the Layers panel set the layer opacity to 70%

[Answer by Billy Kerr](https://graphicdesign.stackexchange.com/a/162470/183169), to whom be the credit.

## Dyeing a picture doesn't succeed

Sometimes bucket fill won't work because a picture is **color indexed**. In general, we can take care of that by changing the image to be **color-full-RGB** in `Image > Mode > RGB`.

* https://graphicdesign.stackexchange.com/questions/162147/bucket-fill-wont-fill-a-shape-with-color-in-gimp-2-10-34
