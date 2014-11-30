# jekyll-table-of-contents

A simple JavaScript table of contents generator. Works well with [jekyll](https://github.com/mojombo/jekyll) static sites. At [Tanda](https://www.tanda.co) we are using it for our [help pages](https://github.com/ghiculescu/payaus-docs).

## Usage

The script requires the library jQuery. First, reference `toc.js` in templates where you would like to add the table of content.
Then, create an HTML element wherever you want your table of contents to appear:

```html
<div class="toc"></div>
```

Finally, call the `toc()` function when the DOM is ready:

```html
<script type="text/javascript">
$(document).ready(function() {
    $('.toc').toc();
});
</script>
```

The script works by looking for headers (h1, h2, h3, h4, h5, h6) which have an `id`.
An id is added automatically if you're using Jekyll and [Markdown](http://daringfireball.net/projects/markdown/syntax#header).

Note: If you use redcarpet, you need to have the option `with_toc_data` in order to add HTML anchors to each header:

```yaml
markdown: redcarpet
redcarpet:
    extensions: [with_toc_data]
```

Note: If you use rdiscount, enable the following option in order to generate the TOC:
```yaml
markdown: rdiscount
rdiscount:
    extensions:
      - generate_toc
```
*You may have to modify slighty the toc.js file to target specifically the main content of the page to generate properly the TOC. For example:*
```js
// line 13
var headers = $('h1, h2, h3, h4, h5, h6').filter(function() {
```
to
```js
// line 13
var headers = $('.content h1, .content h2, .content h3, .content h4, .content h5, .content h6').filter(function() {
```
*In that way it shouldn't check the titles located elsewhere in the page.*

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

By default the table of contents is rendered as an `<ol>`, so you can change the number formatting using CSS.
However you can use the `<ul>` tag, using the `listType` option:

```javascript
    $('.toc').toc({ listType: 'ul' });
```

The script also adds an `<i>` tag next to each header. This uses the class `icon-arrow-up`, which if you're using [Bootstrap](http://twitter.github.io/bootstrap/), will be an arrow pointing to the top of the page.
Clicking that arrow will scroll you to the top, while clicking on a header will get a permanent link to that particular header (using `window.location.hash`).

If you don't want this feature, add this setting:

```javascript
    $('.toc').toc({ noBackToTopLinks: true });
```

Otherwise, you can use the stylesheet below to have the icon and the header aligned nicely:

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

By default the table of content is displayed when at least 3 headers are found. 
You can customize the minimum number of headers required with this setting:

```javascript
    $('.toc').toc({ minimumHeaders: 2 });
```

Finally, you can also change the way the toc is displayed, choosing a `slideShow` or a `fadeIn` effect instead of `show`:

```javascript
    $('.toc').toc({ showEffect: 'slideDown' });
```

Otherwise, to deactivate the effect, set it up like this:

```javascript
    $('.toc').toc({ showSpeed: 0 });
```

## Copyright

See LICENSE.txt for further details. But basically, do what you like with this.
