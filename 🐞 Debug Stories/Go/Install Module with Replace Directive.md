# Install Module with Replace Directive
#bug #go #solution

## Background

This is a continuation of the issue I encountered [[🐞 Debug Stories/Go/Forking a Go Module|forking a go module]].

## Bug

When trying to install the custom Go module, I got the following problem:

>[!bug]
>```
>The go.mod file for the module providing named packages contains one or more replace directives. It must not contain directives that would cause it to be interpreted differently than if it were the main module.
>```

## Solution
[*Based on this StackOverflow answer*](https://stackoverflow.com/a/69807233)

I had to change the `Dockerfile` to clone the custom git repo, and install the module from within the added directory. It's not a great solution but it's [a known limitation on what `go install` can install](https://utcc.utoronto.ca/~cks/space/blog/programming/GoInstallLimitation).