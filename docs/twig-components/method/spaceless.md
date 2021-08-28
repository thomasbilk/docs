# spaceless

`spaceless` is a Twig filter to remove whitespace between HTML tags, not whitespace within HTML tags or whitespace in
plain text:

```twig
{{
    "<div>
        <strong>foo</strong>
    </div>
"|spaceless 
}}


{# output will be <div><strong>foo</strong></div> #} 
```

You can combine spaceless with the `apply` tag to apply the
transformation on large amounts of HTML:

```twig
{% apply spaceless %}
    <div>
        <strong>foo</strong>
    </div>
{% endapply %}

{# output will be <div><strong>foo</strong></div> #} 
```

This tag is not meant to "optimize" the size of the generated HTML
content but merely to avoid extra whitespace between HTML tags to avoid browser rendering quirks under some
circumstances.

### Caution 

As the filter uses a regular expression behind the scenes, its performance is directly related to the text size
you are working on (remember that filters are executed at runtime).

### Tip 

If you want to optimize the size of the generated HTML content, gzip compress the output instead.

### Tip 

If you want to create a tag that actually removes all extra whitespace in an HTML string, be warned that this is not
as easy as it seems to be (think of textarea or pre tags for instance). Using a third-party library like Tidy is
probably a better idea.

### Tip 

For more information on whitespace control, read the dedicated section of the documentation and learn how you can
also use the whitespace control modifier on your tags.

Source: [Twig](https://twig.symfony.com/spaceless)