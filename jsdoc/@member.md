# @member
## Synonyms

`@var`

## Syntax

`@member [<type>] [<name>]`

## Overview

The @member tag identifies any member that does not have a more specialized kind, such as "class", "function", or "constant". A member can optionally have a type as well as a name.

## Examples

Using @member with Data#point

```javascript
/** @class */
function Data() {
    /** @member {Object} */
    this.point = {};
}
```

Here is an example of using @var, a synonym of @member, to document a (virtual) variable 'foo'.

Using @var to document a virtual member

```javascript
/**
 * A variable in the global namespace called 'foo'.
 * @var {number} foo
 */
```

The above example is equivalent to the following:

```javascript
/**
 * A variable in the global namespace called 'foo'.
 * @type {number}
 */
var foo;
```