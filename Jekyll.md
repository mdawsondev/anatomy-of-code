# Jekyll

These notes were taken from the [official Jekyll docs](https://jekyllrb.com/docs/home/).

## What Is Jekyll

Jekyll is a blog aware static site generator. The content is created as Markdown and organized into folders. The shell of the site is built using [Liquid](https://shopify.github.io/liquid/)-enhanced HTML templates. Liquid is a template language used by Shopify, written in Ruby. Jekyll automatically compiles the content and template to generate a website made of static assets. Jekyll is also the engine behind GitHub Pages.

## Quick-start Guide

In order to use Jekyll, you must have Ruby and RubyGems installed (simple enough with the installer) 💎. Make sure to install the dev-tools package so the commands will work.

``` terminal
gem install jekyll bundler
jekyll new myblog
cd myblog
bundle exec jekyll serve

# Jekyll is now live at localhost:4000
```

### About Bundler

The `gem install bundler` installs the bundler gem - it's not part of the Jekyll package but is required to use it. Bundler is a gem that manages other Ruby gems; it makes sure the gems and versions are compatable and that all the dependencies are installed. ` Gemfile` informs Bundler about the gem requirements of the site. It is very much like `npm` in this sense. When `bundle exec jekyll serve` is run, Bundler uses the gems specified in the Gemfile to ensure Jekyll builds without compatability issues. If you're not using other gems, `jekyll serve` can be run without `bundle exec`.

### Jekyll Options

`jekyll new <PATH>` installs a new Jekyll site relative to the current directory. If the directory isn't empty, you can pass `--force` to force an installation. `jekyll new` will automatically initiate `bundle install`, but can be skipped with `--skip-bundle`. By default, `jekyll new` comes with a theme called Minima. Gem-based themes may abstract the file system away from immediate view. Jekyll devs recommend setting up Jekyll with a gem-based theme, but it can be started with a blank template by callign `--blank` in the `new` command.

## Basic Usage

The Jekyll gem enables `jekyll` in the termninal. Appending the following will have the resulting effects:

* `build`: The current folder is generated into ./_site
* `build --destination <destination>`: Build into destination.
* `build --source <source> --destination <destination>`: the source folder will be generated into destination.
* `build --watch`: builds the folder and watches for changes to regenerate automatically.

By default, jekyll can be accessed via `http://localhost:4000`. If you want to build for a production enviornment, set the production URL in `_config.yml`, eg `url: https://example.com` and run `JEKYLL_ENV=production build exec jekyll build`.

## Directory Structure

Jekyll functions basically as a text processing engine: you feed it Markdown/HTML and it runs that through a templating format to output static HTML. The typical site looks something like the following.

``` folders
.
├── _config.yml
├── _data
|   └── members.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.md
|   └── on-simplicity-in-technology.md
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.md
|   └── 2009-04-26-barcamp-boston-4-roundup.md
├── _sass
|   ├── _base.scss
|   └── _layout.scss
├── _site
├── .jekyll-metadata
└── index.html # can also be an 'index.md' with valid YAML Frontmatter
```

* _config.yml: Configuration data.
* _drafts: Unpublished posts.
* _includes: Template partials that can be mixed for reuse (e.g. header).
* _layouts: Templates that wrap posts.
* _posts: Dynamic content, must follow the format `YEAR-MONTH-DAY-title.MARKUP`; slugs can be customized.
* _data: Well-formatted site data (.json, .yml, .csv).
* _sass: Sass partials that can be imported to `main.css` and auto-processed.
* _site: The build folder.
* .jekyll-metadata: Helps Jekyll keep track of modified files.
* index.(html|md): Provided that it has a YAML Font Matter section it will be transfored by jekyll. Same happens for any `.html .markdown .md .textile` files.
* Other: `css`, `images`, `favicon.ico`, etc are copied verbatim when built.

## Configuration

Options can be specified in a _config.yml file in the root directory, or specified as flags in the terminal.

### Global Configs

* **Site Source**: `source: DIR`, `-s DIR` - Change directory where files are read.
* **Site Destination**: `destination: DIR`, `-d DIR` - Change directory where files are written.
* **Safe**: `safe: BOOL`, `--safe` - Disable custom plugins and ignore symbolic links.
* **Exclude**: `exclude: [DIR, FILE, ...]` - Exclude directories/files from conversion.
* **Include**: `include: [DIR, FILE, ...]` - Force inclusion of directories/files.
* **Time Zone**: `timezone: TIMEZONE` - Set the time zone for generation; sets `TZ` environmental var.
* **Encoding**: `encoding: ENCODING` - Set the encoding of files by name, default `utf-8`.
* **Defaults**: Set defaults for YAML Font Matter vars.

### Build Commands

* **Regeneration**: `-w`, `--[no-]watch` - Enable auto-regen of site build when modified.
* **Configuration**: `--config FILE1,[FILE2,...]` - Specifiy config files instead of using `_config.yml`.
* **Drafts**: `show_drafts: BOOL`, `--drafts` - Process/render drafts.
* **Environment**: `JEKYLL_ENV=production` - Use specific environment for build.
* **Future**: `future: BOOL`, `--future` - Publish docs with a future date.
* **Unpublished**: `unpublished: BOOL`, `--unpublished` - Render posts marked unpublished.
* **LSI**: `lsi: BOOL`, `--lsi` - Produce an index for related posts - requires plugin.
* **Limit Posts**: `limit_posts: NUM`, `--limit_posts NUM` - Limit the number of posts to parse/publish.
* **Force Polling**: `--force_polling` - Force watch to use polling.
* **Verbose Output**: `-V` - Print verbose output.
* **Silence Output**: `-q` - Silence the normal output.
* **Incremental Build**: `incremental: BOOL`, `-I` - Enable incremental build features only rebuilding pages that have changed.
* **Liquid Profiler**: `profile: BOOL`, `--profile` - Generate a Liquid profile to identify bottlenecks.
* **Strict Front Matter**: `strict_front_matter: BOOL`, `--strict_front_matter` - Causes fail if YAML syntax error.

### Server Commands

* **Local Port**: `port: PORT`, `--port PORT` - Listen to the given port.
* **Local Hostname**: `host: HOSTNAME`, `--host HOSTNAME` - Listen at the given hostname.
* **Base URL**: `baseurl: URL`, `--baseurl URL` - Serve site from given base URL.
* **Detach**: `detach: BOOL`, `-B` - Detach the server from the terminal.
* **Skip Initial Build**: `--skip-initial-build` - Skips initial site build before server init.
* **SSL Private Key**: `--ssl-key`
* **SSL Cert**: `--ssl-cert`

## WEBrick Headers

Headers can be added to `_config.yml`.

``` yml
# FILE: _config.yml
webrick:
  headers:
    My-Header: My-Value
    My-Other-Header: My-Other-Value
```

Jekyll provides default `Content-Type` and `Cache-Control` response headers.

## Environment Settings

You can specify a Jekyll environment and value to apply conditional statements for internal content. For example, by using the following, when you build the site the content inside the `if` statement wont run unless you also specify the production environment via `JEKYLL_ENV=production jekyll build`. Specifying environments allows you to contain content within specific environments. The default value is `development`, therefore if you omit the environment command from arguments, the default value will be `JEKYLL_ENV=development`, and any content inside the `development` conditional tags will appear in the build.

``` yml
{% if jekyll.environment == "production %}
  {% include disqus.html %}
{% endif %}
```

## Front Matter Defaults

Often there will be variables repeated across multiple files. This can be cut into by using the `defaults` key in the _config.yml file. The `defaults` key holds an array of scope/value pairs that define defaults for a particular file path or a file type in the path. For example, if you wanted to add a default layout to all pages in the side, you could add the following to your file. In order to ensure regernation, you must run `jekyll serve` again even if listening for automatic regeneration, as changes made to the config file are not included at reload.

``` yml
defaults:
  -
    scope:
      path: "" # an empty string here means all files in the project
    values:
      layout: "default"
```

You can also specify a type under the scope key to segregate certain sections in terms of things like CSS by adding the `type` value. This will **only** set the layout for files where the tpye is `posts`. You may also use `pages`, `posts`, `drafts`, or any collection in the site. While `type` is optional, `path` must be provided. Multiple scope/values can also be set simultaneously. Granting Liquid variables is also possible, for example you can set `page.author`vvar by setting `author: "My Name"`.

``` yml
defaults:
  -
    scope:
      path: ""
      type: "pages"
    values:
      layout: "my-site"
  -
    scope:
      path: "projects"
      type: "pages" # previously `page` in Jekyll 2.2.
    values:
      layout: "project" # overrides previous default layout
      author: "Mr. Hyde"
```

Glob patterns are also available for use, but crrently limited to `*` when matching. Globbing is known to have a negative effect on performance and increases build times in proportion to the size of the collection directory. Jekyll applies config settings but you can override settings by specifying a more specific path for the scope. Narrowing down the path to specific files will use the higher specificity (just like CSS).

[The Jekyll Default Config](https://jekyllrb.com/docs/configuration/#default-configuration) comes with a number of default files but the settings can be specified in the command line or changed.

## Incremental Regeneration

This is still an experemental feature. It helps shorten the build times by only generating changes that were updated since the previous build. It keeps track of this information in `.jekyll-metadata`. At the moment it will only generate a document or page if either it or a dependency is modified. The only types of dependencies tracked are includes (`{% include %}`) and layout. This means that plain references will not be detected (such as iterating over site.posts). This can be fixed by putting `regenerate: true` in the front-matter of a doc and it will force a regeneration whether it was modified or not. This will only work for the specified document.

## Misc

Liquid's response to errors can be configured by setting `error_mode` with the options `lax`, `warn`, and `strict`, where the first will ignore, the second will warn, and the last will stop the build. Liquid can also catch non-assigned vars by setting `strict_vars` and non-existant filters by `strict_filters` to true.

Jekyll supports various Markdown renderers but some provide extra features, like Redcarpet. More info can be found on the docs, I don't really care about this section because I won't be using Redcarpet. You can also use custom markdown processors if you're a masochist of some kind, but again: see the docs.
