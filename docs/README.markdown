---
layout: default
title: README
nav_order: 99
---

## Jekyll
GitHub pages recommend [Jekyll](https://jekyllrb.com), a static site generator with built-in support for GitHub Pages and a simplified build process.  The IronCity project is using Jekyll to render our documentation site.  This README provides a quickstart for creating documentation pages, if you are interested in building more sophisticated pages please reference the [Jekyll Documentation](https://jekyllrb.com).

## Jekyll Theme
The Iron City Documentation GitHub pages are using the ['Just The Docs'](https://pmarsceill.github.io/just-the-docs/)
Jekyll theme, which provides a great template for laying out and building a documentation based site.  We are following their recommendations for how to structure our documentation site and the associated respository.

## Navigation Tree Strucuture
As recommended by [Just The Docs - Navigation](https://pmarsceill.github.io/just-the-docs/docs/navigation-structure/#pages-with-children) our repository has a structure similiar to the one depicted below.  All of the documentation will be saved under the /docs directory, with sub-directories for each section of our documentation.  For each directory there must be a markdown file named identical to the directory folder and will have a file extension of 'markdown'.  For example, the admin_manual directory contains an index file named 'admin_manual.markdown'.  This requirement is enforced by a GITHub workflow action.

```
+-- ..
|-- (Jekyll files)
|
|-- docs
|   |-- admin_manual
|   |   |-- admin_manual.markdown  (parent page)
|   |   |-- buttons.markdown
|   |   |-- code.markdown
|   |   |-- labels.markdown
|   |   |-- tables.markdown
|   |   +-- typography.markdown
|   |
|   |-- user_manual
|   |   |-- user_manual.markdown  (parent page)
|   |   |-- color.markdown
|   |   |-- layout.markdown
|   |   |-- responsive-modifiers.markdown
|   |   +-- typography.markdown
|   |
|   |-- (other md files, pages with no children)
|   +-- ..
|
|-- (Jekyll files)
+-- ..
```

## Front Matter
Jekyll is powered by the Liquid Templating language, which uses variables substitution to build pages.  These variables are provide by a YAML [Front Matter](https://jekyllrb.com/docs/front-matter/) block at the begining of each page.  The front matter must be the first thing in the file and must take the form of valid YAML set between triple-dashed lines ('---').  Here is a basic example:

```
---
layout: default
title: Administrators Manual
---
```

'Just The Docs' has predefined variables that are used to structure the site.  For our purpose we will have two different YAML configurations for structuring our pages. One for the 'index' page (parent) that defines a subsection and another that defines the content for each page within that section (children).

### Index Page (Parent) YAML 
The front matter for the Index Page requires at a minimum the following:
- title:  The title that will be displayed in the Navigation Tree
- has_children: true
It should also include, but is not required:
- layout: Specifies the layout template to use
- nav_order: The order of the page in the Navigation Tree.
An example of the Index Page YAML:

```
---
layout: default
title: Admin Manual
nav_order: 2
has_children: true
---
```

### Children YAML
The front matter for each content page (children) within a section requires the minimum:
- title:  The title that will be displayed in the Navigation Tree
- parent:  The title of the parent index page within which this page exists.

Child YAML should also include layout and nav_order variables.

**Note:**  A child page can also have children, so it's both a parent and a child.  Therefore it is required to have:
- title:  The title that will be displayed in the Navigation Tree
- parent:  The title of the parent index page within which this page exists.
- has_children: true

## YAML Validation
A GitHub workflow has been implemented for the IronCity Documentation repository. This workflow has an action which executes a Python Module that checks each page in the docs directory YAML Front Matter to ensure it complies with the requirements as stated above. You can check the GitHub actions page to see if the action has passed or failed. When it fails, the errors are displayed in the log.