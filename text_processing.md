## Reverse a string

### Bash

```shell
echo +54321 | rev
```

> 12345+

In some usecases, instead of:

+12345

### JavaScript

```js
let number = "12345";
let reversed = number.split('').reverse().join('');
```

1. **Split** a string to individual characters.
2. **Take each** individual character and put it **after the last** individual character with `reverse()`.
3. **Join** the reversed individual characters to a new string.

We get a new, reorganized string of reversed characters which grow in size (length) each time a character was moved after the last character until getting the new string of the same size (length).
