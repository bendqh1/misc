`figure` tags don't behave as plain text inside `pre` tags, so the following code will break in execution:

```
<pre>
    <figure>
        <img src="img.jpg" alt="Some alternative text"></img>
        <figcaption>Some text under the image</figcaption>
    </figure>
</pre>
```

Currently the only way to solve the problem is to escape all relevant tag characters which in this case are all the < and > characters inside the <pre></pre> tags:

```
<pre dir="ltr">
&lt;figure&gt;
    &lt;img src="img.jpg" alt="Some alternative text"&gt;
    &lt;figcaption&gt;
        Some text under the image
    &lt;/figcaption&gt;
&lt;/figure&gt;
</pre>
```

## using `xmp` tags
I have tried to put the original code inside <xmp></xmp> tags but currrently these are totally deprecated so it didn’t work; for now we should use the escaping solution above.

## Notes

* The syntax highlighting here is general, not `html` unique, so that both the regular HTML and the escaped HTML will get syntax highlighting.
