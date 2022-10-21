# @description
## Synonyms

`@desc`

## Syntax

`@description <some description>`

## Overview

The @description tag allows you to provide a general description of the symbol you are documenting. The description may include HTML markup. It may also include Markdown formatting if the [Markdown plugin](https://jsdoc.app/plugins-markdown.html) is enabled.

## Examples

If you describe a symbol at the very beginning of a JSDoc comment, before using any block tags, you may omit the @description tag.

Describing a symbol without the @description tag

```javascript
/**
 * Add two numbers.
 * @param {number} a
 * @param {number} b
 * @returns {number}
 */
function add(a, b) {
    return a + b;
}
```

By using the @description tag, you can place the description anywhere in the JSDoc comment.

Describing a symbol with the @description tag

```javascript
/**
 * @param {number} a
 * @param {number} b
 * @returns {number}
 * @description Add two numbers.
 */
function add(a, b) {
    return a + b;
}
```

If there's both a description at the beginning of a JSDoc comment and a description provided with the @description tag, the description specified with the @description will override the description at the beginning of the comment.