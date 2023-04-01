# Menus
#learning #gatsby

**Source:** [Gatsby Menus](https://gohugo.io/content-management/menus/)

## Overview

To create a menu for your site:

1. Define the menu entries
2. Localize each entry
3. Render the menu with a [[👓 Learning/Hugo/Menu Templates|template]]

Create multiple menus, either flat or nested. For example, create a main menu for the header, and a separate menu for the footer.

There are three ways to define menu entries:

1. Automatically
2. In front matter
3. In site configuration

## Define Automatically

To automatically define menu entries for each top-level section of your site, enable the section pages menu in your site configuration.

`config.yaml`
```yaml
sectionPagesMenu: main
```

This creates a menu structure that you can access with `site.Menus.main` in your templates. See [[👓 Learning/Hugo/Menu Templates|menu templates]] for details.

## Define in front matter

To add a page to the "main" menu:

`content/about.md`
```yaml
---
menu: main
title: About
---
```

Access the entry with `site.Menus.main` in your templates. See [[👓 Learning/Hugo/Menu Templates|menu templates]] for details.

## Define in site configuration

To define entries for the "main" menu:

`config.yaml`
```yaml
menu: 
	main: 
	- name: Home 
	  pageRef: / 
	  weight: 10 
	- name: Products
	  pageRef: /products
	  weight: 20
```

This creates a menu structure that you can access with `site.Menus.main` in your templates. See [[👓 Learning/Hugo/Menu Templates|menu templates]] for details.