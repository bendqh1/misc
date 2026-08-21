A JavaScript bookmarklet is a normal browser bookmark whose "address" is a JavaScript instead of a URL.

1. Hit <kbd>Ctrl></kbd>+<kbd>Shift</kbd>+<kbd>B</kbd> to show the bookmarks toolbar.
2. Click on "Add Bookmark".
3. Set name "Force LTR".
4. Save the following code to it:

```js
javascript:(()=>{let s=document.getElementById('force-ltr-style')||document.head.appendChild(document.createElement('style'));s.id='force-ltr-style';s.textContent='html,body,body *{direction:ltr!important;text-align:left!important}';document.documentElement.dir='ltr';document.body.dir='ltr'})()
```

## Notes

LibreWolf might block JavaScript and if it does, run the command `java`, and then run the bookmarklet.
