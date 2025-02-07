## Question

When I try to run the following SVG code in a Microsoft Edge, I get the following error, why?

> This page contains the following errors:
>
> error on line 2 at column 6: XML declaration allowed only at the start of the document
>
> Below is a rendering of the page up to the first error.

```svg

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!-- Created with Inkscape (http://www.inkscape.org/) -->

```
<svg
...
</svg>

## Answer

The error you're encountering occurs because the XML declaration (<?xml version="1.0" encoding="UTF-8" standalone="no"?>) is placed in the middle of the document, which violates XML syntax rules.

* The XML declaration should be the very first thing in the document, before any other content, including spaces or comments. It is meant to define the document's encoding and other properties.
* In your case, it is followed by a comment (<!-- Created with Inkscape -->) before the SVG root element <svg>. This is what's causing the error in Microsoft Edge.
