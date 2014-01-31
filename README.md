# jekyll-table-of-contents

A simple JavaScript table of contents generator. Works well with [jekyll](https://github.com/mojombo/jekyll) static sites. At [Tanda](https://www.tanda.co) we are using it for our [help pages](https://github.com/ghiculescu/payaus-docs).

## Usage

Requires jQuery. Reference `toc.js` in pages where you'd like a table of contents. The script looks for:

```html
<div class="toc"></div>
```

so place that div wherever you want your table of contents to appear.

The script works by looking for headers (h1, h2, h3, h4, h5, h6) which have an `id`. An id is added automatically if you're using jekyll and [Markdown](http://daringfireball.net/projects/markdown/syntax#header)

The table of contents automatically handles nesting of headers. For example, this Markdown post:

    ## Title
    ## Page 1
    ### Note on Paragraph 3
    ## Page 2
    ### Note on Paragraph 2
    ### Note on Paragraph 4

Will render this table of contents:

    1. Title
    2. Page 1
      a. Note on Paragraph 3
    3. Page 2
      a. Note on Paragraph 2
      b. Note on Paragraph 4

The table of contents is rendered as an `<ol>`, so you can change the number formatting using CSS.

The script also adds an `<i>` tag next to each header. This uses the class `icon-arrow-up`, which if you're using [Bootstrap](http://twitter.github.io/bootstrap/), will be an arrow pointing to the top of the page. Clicking that arrow will scroll you to the top, while clicking on a header will get a permanent link to that particular header (using `window.location.hash`). Set:

```javascript
var no_back_to_top_links = true // defaults to false
```

in the first line of the file if you don't want this. Otherwise, I suggest you use CSS that looks something like this so the icon and header are aligned nicely.

```css
.clickable-header {
  cursor:pointer;
}
.clickable-header:hover {
  text-decoration:underline;
}
.top-level-header {
  display:inline;
}
.back-to-top {
  margin-left:5px;
  cursor:pointer;
}
```

## Copyright

See LICENSE.txt for further details. But basically, do what you like with this.
