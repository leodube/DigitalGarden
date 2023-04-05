# Forking a Go Module
#bug #go #solution 

## Background 

One of my projects, QuartzSN, is a modified version of the open source [Quartz](https://github.com/jackyzha0/quartz) Hugo application. The goal of my project is to add a sidebar navigation menu to Quartz. In order to accomplish this goal, I needed to also customize the [`hugo-obsidian`](https://github.com/jackyzha0/hugo-obsidian) Go module.

## Bug

I had created a fork of the `hugo-obsidian` project, and renamed my version of the module. While trying to install the custom version of the module in the Hugo project I got:

>[!bug]
>```
>go: github.com/leodube/HugoObsidian upgrade => latest
>go get: github.com/leodube/HugoObsidian@latest: parsing go.mod:
> 	module declares its path as: github.com/jackyzha0/hugo-obsidian
> 	        but was required as: github.com/leodube/HugoObsidian
> ```

## Solution

The solution was to 