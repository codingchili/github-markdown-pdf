# github-markdown-pdf
Sometimes you're too lazy to get it right with pandoc.

This tiny script makes it possible to render markdown hosted on GitHub to pdf using the browser.

1) view a **markdown** file on github.
2) press alt+shift+I and open the chrome console.
3) paste the following snippet and print (save) to pdf.

```javascript
let markdown = document.getElementById('readme');

// remove the box-header if in file reader
if (markdown.firstElementChild.tagName === 'DIV') {
    markdown.removeChild(markdown.firstElementChild)
}
document.body.innerHTML = markdown.innerHTML;

let style = document.createElement('style');
style.type = 'text/css';
style.innerHTML = `
@page {
  margin: 0;
}

img {
   /* custom style for your images. */
}

body {
    padding: 24px;
}

`;
document.getElementsByTagName('head')[0].appendChild(style);
print();
location.reload();
```
