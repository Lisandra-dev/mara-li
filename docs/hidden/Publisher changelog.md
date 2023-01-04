---
cssclass: cards
share: true
---

# 06-07-2022

Hello everyone! It's been some days since the last update, no ? I hope my workflow satisfy you :). Some update here, because I do a bunch of things.

Before start with update, I inform you that I finally reunite every issue into the [Github Publisher]() repository. It will be well better to follow bug report or feature request. So, now, when you need to ask some things, just select the workflow part!
Note : please, I beg you, before making a bug report, check the [Mkdocs documentation]() and the [Material Mkdocs]() documentation ❤️ !

Now, a bunch of hunder the hood shiny new things and hotfix.

##### **Github Publisher** :

- Update for the 0.15.3 Obsidian API version, with using the new placement for context menu. Well better! You will see (or already see)
- A big hotfix for the auto-clean function, that will loved to delete file with YAML list in the frontmatter. Now fixed. You can safely use the auto-clean function.
- The path of unshared linked file won't be converted anymore. Pretty convenient if you use shortlinks and won't to alias
- Embed files will be converted if there are shared.
- You can select a subfolder when using the Obsidian Path settings. This path will be "removed" from file during conversion. For example, if you set `vault/blog`, the file `vault/blog/epidemiology/odd ratio.md` will just become `epidemiology/odd ratio.md`.
- I added new shiny and cool commands to share only edited files (since the last repo update) and new files.
- A bunch of bugfixe, like relative links creator, crash on empty default path…

You can get the complete changelog at https://github.com/obsidianMkdocs/obsidian-github-publisher/blob/master/CHANGELOG.md

##### The template

Some QoL things on the template !
1. Hooks: I edited the hooks and move them into `overrides/hooks`. There is two hooks:
	- `on_env` add "filters" to jinja, used for the Blog list (see bellow for information about it)
	- `on_page_markdown` : Will strip the obsidian's comments (`%% comments %%`) and YAML because I noticed that the Material Mkdocs search explode on some condition. Intentionnaly, I transform `nested/tags` into a list `[nested, tags]`.
	You need to edit your `mkdocs.yml` if you update your repo to get them :
```yml
plugins:
	- search
	- mkdocs-simple-hooks:
		hooks:
			on_env: "overrides.hooks.on_env:on_env"
			on_page_markdown: "overrides.hooks.on_page_markdown:on_page_markdown" 
```
2. The 🌈 blog list 🌈 : A special template making a list of your article. You can see a [demo here](https://www.mara-li.fr/Compendium/#page1). To integrate it, create a file in the root of any folder with this yaml metadata :
```yaml
---
category: main_category/subcategory/subsub 
template: blog.html
hidden: true
index: true
---

An optional description
```
[Some example directly on my publish repo](https://github.com/Mara-Li/Seed_publish/blob/main/docs/hidden/index.md).

3. Grids layout, taken from Material Mkdocs. [Here the documentation](https://squidfunk.github.io/mkdocs-material/reference/grids/). It's an unofficial integration, but work the same! My code will be removed when the grid layout become free.

> ⚠️ **Depreciation notice about the python package**
> I don't mind to update and continue to maintain the python package, as the workflow now rely on :
> - [Simple hooks](https://pypi.org/project/mkdocs-simple-hooks/)
> - [Mkdocs Callout](https://pypi.org/project/mkdocs-callouts/)
> - [Custom tags attributes](https://pypi.org/project/mkdocs-custom-tags-attributes/)
> Please, check your workflow and `mkdocs.yml` to prevent future breaking. You can safely delete the `ci.yml` and `manual_run.yml`
> Also, the building process is more relyable and quick.
> Note that the last update are included directly in the template so you can just copy/paste the wanted part.

---

# 18-07-2022

Hello! What's up in this little summer ? I hope you drink well!

## Github Publisher

This week, a bunch of Hotfix, but also :
1. The plugin is now translated in french (including the documentation!) and chinese (only for the plugin). Here is a little tutorial to add a new language for the plugin (detected by your obsidian configuration).
	1. First, get your obsidian “language id”. I use templater for that, with that : `fr`
	2. Clone the file `i18n/locales/en-us.ts` and rename it with your language.
	3. Translate the differents variables in the new created file.
	4. In `i18n/index.ts` import the new file with `import <filename> from ".locales/<filename>"
	5. In the `localeMap`, add in a new line : `<obsidian language found>:<filename>`.
	6. Additionnality, try your new translation.
	7. Generate a pull request to add your translation.

2. With the last Dataview update, it is now possible to transform dataview (not javascript one) query in markdown, so the plugin support it naturally. Thanks to @ in obsidian-digital-garden, where i take the code !

# Mkdocs

The update touch mainly the preview plugin. It not as better than Obsidian hover but i do my best.

This mkdoc’s plugin is now compatible with callouts and Custom tags attributes and you can configure how much text you can preview and the truncate character. To get this, update your `mkdocs.yml` as follow :

```yaml
plugins:
	- search
	- tooltipster-links:
		callouts: true
		custom-attributes: 'assets/css/custom_attributes.css' #need to be the same file than the custom attribute plugin!
		max-characters: 400 #Use 0 or 1 for no limit
		truncate-characters: '...'		
```

⚠️ I noted that the plugin doesn’t work with `navigation.instant` feature of Material Mkdocs, so don’t forget to remove it if you use it!

I also created some CSS for material to recreate something similary to Obsidian Hovering feature. [Here the file](https://github.com/Mara-Li/mkdocs-preview-links-plugin/blob/master/docs/material.css)

I also updated the Embed File plugins, and it now supports callouts and custom-attributes. Update your `mkdocs.yml` as follow :
```yaml
plugins:
	- search
	- embed_file:
		custom-attributes: 'assets/css/custom_attributes.css'
		callouts: true
```

(Yeah, it’s a lot of repetition, i need to update the plugins to have a better configuration file, but I will stand with that for the moment huhu.)

I also updated the two plugins and the build will be faster!

---
