---
title: Jekyll SSG Note 
season: winter
tag: jekyll
---

Things to do for Jekyll static site generation (SSG).

# Error messages
Try to remove error messages: 
```
/var/lib/gems/2.7.0/gems/jekyll-4.0.0/lib/jekyll/convertible.rb:41: warning: Using the last argument as keyword parameters is deprecated
```

Might have to upgrade local gems version?

# Style

Use scss instead of css for easy styling (use variables for theme colors)
Create new theme with warmer, sepia-toned colors.

# Titles
Note titles are re-capitalised with only uppercase at beginning of title:

> Jekyll SSG Note

Becomes 

> Jekyll ssg note


# Links

## File title v. Title attribute
In Obsidian, internal links use file title, even when a title is specified in the header via a specific header (Obsidian doesn't care about headers). 
The SSG uses the title attribute, but with all letters to lowercase eg: 

> [ [Jekyll SSG note] ] will not work.
> 
> But [ [Jekyll ssg note] ] will.

[[Jekyll SSG note]] will not work.
But [[Jekyll ssg note]] will.

Related Github issue [here](https://github.com/Maxence-L/notenote.link/issues/10).

Edit `_includes/content.html`, around line 110:
```
 {%- assign post = site.notes | where: 'title',title -%}
```
Instead of matching titles litterally and using file titles, use case-insensitive matching and use titles from front matter.

## Link preview
Preview text does not render code blocks, but interprets Markdown (ex: [[Usefull miscellaneous snippets]]).