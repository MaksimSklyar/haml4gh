# haml4gh

## Overview
This is a "workaround" Jekyll plugin to use HAML for Github pages development.

As you may know, Jekyll supports HAML via plugins quite well, however, Github doesn't accept those (see its [plugins list](https://pages.github.com/versions/))

So, this plugin read all `*.haml` files from the source folder and does system call for `haml` to convert them. The directory structure will be preserved, `haml` extension will be replaced by `html`. When it happens `jekyll serve` detects it and run regeneration again. The plugin detects this cycle using OS file's update time to skip unnecessary file operations and stop vicious circle.

## Usage
Copy `haml4gh.rb` to the `_plugins` folder and run jekyll (serve or build). When development is finished - commit the results. Github pages will ignore the plugin and use generated HTML file as it was an ordinal input file, it can be either static or dynamic (in Jekyll's terms, see [Front Matter](http://jekyllrb.com/docs/frontmatter/)).

## Setup
By default `_source` folder is used. It can be overwritten via `_config.yml`:

```
haml4gh:
  source: <haml_source_folder>
```

In order to prevent Jekyll from copying its content to the output folder is should be named as something starting with underscore. Also `exclude` config section might be used to achieve the same result.

## Project status
Current project status is stable beta, issues will be fixed, discussions are welcomed. However, I'm not sure if this plugin is relevant :-)
