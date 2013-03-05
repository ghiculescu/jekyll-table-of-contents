# jekyll-table-of-contents

A simple JavaScript table of contents generator. Works well with [jekyll](https://github.com/mojombo/jekyll) static sites. At PayAus we are using it for our [help pages](https://github.com/ghiculescu/payaus-docs).

## Usage

Reference `toc.js` in pages where you'd like a table of contents. The script looks for a

    <div class="toc"></div>

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

## Copyright

Copyright (c) 2013 Alex Ghiculescu. See LICENSE.txt for further details.
