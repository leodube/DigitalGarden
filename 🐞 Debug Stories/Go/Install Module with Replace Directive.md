# Install Module with Replace Directive
#bug #go #solution

## Background
One of my project, QuartzSN, is a modified version of the open source [Quartz](https://github.com/jackyzha0/quartz) application. The goal of my project is to add a sidebar navigation menu which the open source app lacks. In order to accomplish this goal, I needed to also customize the [`hugo-obsidian`](https://github.com/jackyzha0/hugo-obsidian) Go module.

I had created a fork of the `hugo-obsidian` project, and tried using my custom version of the module in QuartzSN. To do this I had to change the Go module name, and add a `replace` directive at the bottom of `go.mod` to point to 
