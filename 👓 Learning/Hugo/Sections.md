# Sections
#learning #hugo #sections

**Source:** [The Ultimate Guide to Hugo Sections](https://cloudcannon.com/blog/the-ultimate-guide-to-hugo-sections/)

## Intro

> Hugo assumes that the same structure that workks to organize you source content is used to organize the rendered site

Content goes in a Hugo project's top-level `content/` folder, and Hugo bases the overall site structure on what you put, and where, in that folder.

## The ABCs of sections

A content folder is automatically a section if the folder has in index file called `_index.md`. This causes Hugo to create a *navigable URL* for the section. For example, if `content/about-us/_index.md` exists, Hugo would create `xyzcompany.com/about-us/`.

By default, Hugo considers a section's top-level web page to be a *list* of the web pages within the section.