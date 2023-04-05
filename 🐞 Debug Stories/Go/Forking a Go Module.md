# Forking a Go Module
#bug #go #solution 

## Background 

One of my projects, QuartzSN, is a modified version of the open source [Quartz](https://github.com/jackyzha0/quartz) Hugo application. The goal of my project is to add a sidebar navigation menu to Quartz. In order to accomplish this goal, I needed to also customize the [`hugo-obsidian`](https://github.com/jackyzha0/hugo-obsidian) Go module.

## Bug

I had created a fork of the `hugo-obsidian` project, and renamed my version of the module.

```
<!-- module github.com/jackyzha0/hugo-obsidian -->
module github.com/leodube/HugoObsidian

go 1.16

require (
	github.com/BurntSushi/toml v0.4.1 // indirect
	github.com/PuerkitoBio/goquery v1.8.0
	github.com/abhinav/goldmark-wikilink v0.3.0
	github.com/adrg/frontmatter v0.2.0 // indirect
	github.com/yuin/goldmark v1.4.4
	gopkg.in/yaml.v2 v2.4.0 // indirect
	gopkg.in/yaml.v3 v3.0.0-20210107192922-496545a6307b
)
```

While trying to install the custom version of the module in the Hugo project I got:

>[!bug]
>```
>go: github.com/leodube/HugoObsidian upgrade => latest
>go get: github.com/leodube/HugoObsidian@latest: parsing go.mod:
> 	module declares its path as: github.com/jackyzha0/hugo-obsidian
> 	        but was required as: github.com/leodube/HugoObsidian
> ```

## Solution

The solution was to add a `replace` directive to the bottom of `go.mod`

```
replace github.com/jackyzha0/hugo-obsidian => github.com/leodube/HugoObsidian main
```

And then run `go mod tidy`.