# Sections
#learning #hugo

**Source:** [The Ultimate Guide to Hugo Sections](https://cloudcannon.com/blog/the-ultimate-guide-to-hugo-sections/)

## Intro

>[!quote] 
>Hugo assumes that the same structure that workks to organize you source content is used to organize the rendered site

Content goes in a Hugo project's top-level `content/` folder, and Hugo bases the overall site structure on what you put, and where, in that folder.

## The ABCs of sections

A content folder is automatically a section if the folder has in index file called `_index.md`. This causes Hugo to create a *navigable URL* for the section. For example, if `content/about-us/_index.md` exists, Hugo would create `xyzcompany.com/about-us/`.

By default, Hugo considers a section's top-level web page to be a *list* of the web pages within the section.

## Bundles

> [!question]
> `_index.md` vs `index.md`: which on do you use, and why?

*Page bundles* are mainly a way to group content with any related resources, such as images and PDFs. Hugo uses a *tree metaphor* to define the two most commonly encountered bundle types:

- *Branch bundle:* It's index file is called `_index.md`. It can have "children", such as nested folders. If there are additional `.md` files within, each will get its own navigable URL. Only a folder that's a branch bundle can be a section.
- *Leaf bundle:* Its index file is called `index.md` and, at build time, becomes a regular web page, not a list. It can't be a section, and therefore can have no "children". Any additional `.md` file in a leaf bundle won't get its own navigable URL. Other items within a leaf bundle are page resource for the `index.md` file.

Consider the following example:
```
.
└── content
    └── product1
        └── index.md
        └── prod1_brochure_large.pdf
        └── prod1_users_img1.jpg
```

Because its index file is `index.md`, `content/product`/ is a leaf bundle. If we add another `.md` file to this folder, it will not have its own navigable URL. The other contents are available as “local” page resources.