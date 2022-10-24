# Printing a web page

## Create a separate print CSS file:

```css
@page {
    margin: .5in;
}
body {
    color: black;
    background-color: white;
}
/* don't print buttons, images, links */
button, img, a, nav {
    visibility: hidden;
}
.noprint {
    display: none;
}
table {
    page-break-inside: avoid;
}
```

*.noprint* - This removes the tagged element from the display and collapses the space on the page.

*page-break-inside: avoid* - Do not break a table across pages.

## Add the css stylesheet to the html

Add the stylesheet and include the *media=print* attribute.

        <link href="css/cv-print.css" 
            rel="stylesheet" media="print">
