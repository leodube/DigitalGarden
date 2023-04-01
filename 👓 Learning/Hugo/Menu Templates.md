# Menu Templates
#learning #hugo

**Source:** [Gatsby Menu Templates](https://gohugo.io/templates/menu-templates/)

## Overview 

After [[👓 Learning/Hugo/Menus|defining menu entries]], use menu [variables and methods](https://gohugo.io/variables/menus/) to render a menu.

Three factors determine how to render a menu:

1. The method used to define the menu entries: automatic, in front matter, or in site configuration
2. The menu structure: flat or nested
3. The method used to localize the menu entries: site configuration or translation tables

The example below handles every combination.

## Example

This partial template recursively "walks" a menu structure, rendering a localized, accessible nested list.

`layouts/partial/menu.html`
```html
{{- $page := .page }}
{{- $menuID := .menuID }} 

{{- with index site.Menus $menuID }} 
	<nav> 
		<ul> 
			{{- partial "inline/menu/walk.html" (dict "page" $page "menuEntries" .) }} 
		</ul> 
	</nav> 
{{- end }} 

{{- define "partials/inline/menu/walk.html" }} 
	{{- $page := .page }} 
	{{- range .menuEntries }} 
		{{- $attrs := dict "href" .URL }} 
		{{- if $page.IsMenuCurrent .Menu . }} 
			{{- $attrs = merge $attrs (dict "class" "active" "aria-current" "page") }} 
		{{- else if $page.HasMenuCurrent .Menu .}} 
			{{- $attrs = merge $attrs (dict "class" "ancestor" "aria-current" "true") }} 
		{{- end }} 
		<li> 
			<a 
				{{- range $k, $v := $attrs }} 
					{{- with $v }} 
						{{- printf " %s=%q" $k $v | safeHTMLAttr }} 
					{{- end }} 
				{{- end -}} 
			>{{ or (T .Identifier) .Name | safeHTML }}</a> 
			{{- with .Children }} 
				<ul> 
					{{- partial "inline/menu/walk.html" (dict "page" $page "menuEntries" .) }} 
				</ul> 
			{{- end }} 
		</li> 
	{{- end }} 
{{- end }}
```

Call the partial above, passing a menu ID and the current page in context

`layouts/_default/single.html`
```html
{{ partial "menu.html" (dict "menuID" "main" "page" .) }} 
{{ partial "menu.html" (dict "menuID" "footer" "page" .) }}
```

## Page references
Regardless of how you define menu entries, an entry associated with a page has access to page variables and methods.