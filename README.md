# minima

*Minima is a one-size-fits-all Jekyll theme for writers*. It's Jekyll's default (and first) theme. It's what you get when you run `jekyll new`.

[Theme preview](https://jekyll.github.io/minima/)

![minima theme preview](/screenshot.png)

## Installation

Add this line to your Jekyll site's `Gemfile`:

```ruby
gem "minima"
```

And add this line to your Jekyll site's `_config.yml`:

```yaml
theme: minima
```

And then execute:

```bash
> bundle
```

## Contents At-A-Glance

Minima has been scaffolded by the `jekyll new-theme` command and therefore has all the necessary files and directories to have a new Jekyll site up and running with zero-configuration.

### Layouts

Refers to files within the `Source/Layouts` directory, that define the markup for your theme.

- `default.html` &mdash; The base layout that lays the foundation for subsequent layouts. The derived layouts inject their contents into this file at the line that says ` {{ content }} ` and are linked to this file via [FrontMatter](https://jekyllrb.com/docs/frontmatter/) declaration `layout: default`.
- `home.html` &mdash; The layout for your landing-page / home-page / index-page. [[More Info.](#home-layout)]
- `page.html` &mdash; The layout for your documents that contain FrontMatter, but are not posts.
- `post.html` &mdash; The layout for your posts.

### Includes

Refers to snippets of code within the `Source/Includes` directory that can be inserted in multiple layouts (and another include-file as well) within the same theme-gem.

- `disqus_comments.html` &mdash; Code to markup disqus comment box.
- `footer.html` &mdash; Defines the site's footer section.
- `google-analytics.html` &mdash; Inserts Google Analytics module (active only in production environment).
- `head.html` &mdash; Code-block that defines the `<head></head>` in *default* layout.
- `header.html` &mdash; Defines the site's main header section. By default, pages with a defined `title` attribute will have links displayed here.

### Sass

Refers to `.scss` files within the `Source/CSS` directory that define the theme's styles.  
Contains the `main.scss` that imports sass files from within the `Source/CSS` directory. This `main.scss` is what gets processed into the theme's main stylesheet `main.css` called by `Source/Layouts/default.html` via `Source/Includes/head.html`.

- `minima.scss` &mdash; The core file imported by preprocessed `main.scss`, it defines the variable defaults for the theme and also further imports sass partials to supplement itself.
- `minima/_common.scss` &mdash; Common styling and mixins leveraged throughout the minima theme.
- `minima/_base.scss` &mdash; Resets and defines base styles for various HTML elements.
- `minima/_layout.scss` &mdash; Defines the visual style for various layouts.
- `minima/_syntax-highlighting.scss` &mdash; Defines the styles for syntax-highlighting.

### Assets

Refers to various asset files within the `Source/Assets` directory.

This directory can include sub-directories to manage assets of similar type, and will be copied over as is, to the final transformed site directory.

### Plugins

Minima comes with [`jekyll-seo-tag`](https://github.com/jekyll/jekyll-seo-tag) plugin preinstalled to make sure your website gets the most useful meta tags. See [usage](https://github.com/jekyll/jekyll-seo-tag#usage) to know how to set it up.

## Usage

### Home Layout

`home.html` is a flexible HTML layout for the site's landing-page / home-page / index-page.

#### Main Heading and Content-injection

From Minima v2.2 onwards, the *home* layout will inject all content from your `index.md` / `index.html` **before** the **`Posts`** heading. This will allow you to include non-posts related content to be published on the landing page under a dedicated heading. *We recommended that you title this section with a Heading2 (`##`)*.

Usually the `site.data.About.title` itself would suffice as the implicit 'main-title' for a landing-page. But, if your landing-page would like a heading to be explicitly displayed, then simply define a `title` variable in the document's front matter and it will be rendered with an `<h1>` tag.

#### Post Listing

This section is optional from Minima v2.2 onwards.  
It will be automatically included only when your site contains one or more valid posts or drafts (if the site is configured to `show_drafts`).

The title for this section is `Posts` by default and rendered with an `<h2>` tag. You can customize this heading by defining a `list_title` variable in the document's front matter.

--

### Customization

To override the default structure and style of minima, simply create the concerned directory at the root of your site, copy the file you wish to customize to that directory, and then edit the file.
e.g., to override the [`Source/Includes/head.html`](Source/Includes/head.html) file to specify a custom style path, create a `Source/Includes` directory, copy `Source/Includes/head.html` from minima gem folder to `<yoursite>/Source/Includes` and start editing that file.

The site's default CSS has now moved to a new place within the gem itself, [`Source/CSS/main.scss`](Source/CSS/main.scss). To **override the default CSS**, the file has to exist at your site source. Do either of the following:

- Create a new instance of `main.scss` at site source.
  - Create a new file `main.scss` at `<your-site>/Source/CSS/`
  - Add the frontmatter dashes, and
  - Add `@import "minima";`, to `<your-site>/Source/CSS/main.scss`
  - Add your custom CSS.
- Download the file from this repo
  - Create  a new file `main.scss` at `<your-site>/Source/CSS/`
  - Copy the contents at [Source/CSS/main.scss](Source/CSS/main.scss) onto the `main.scss` you just created, and edit away!
- Copy directly from Minima 2.0 gem
  - Go to your local minima gem installation directory ( run `bundle show minima` to get the path to it ).
  - Copy the `Source/CSS/` folder from there into `<your-site>/Source`
  - Change whatever values you want, inside `<your-site>/Source/CSS/main.scss`

--

### Customize navigation links

This allows you to set which pages you want to appear in the navigation area and configure order of the links.

For instance, to only link to the `about` and the `portfolio` page, add the following to your `Source/Data/Minima.yml`:

```yaml
header:
    pages:
        - about.md
        - portfolio.md
```

--

### Change default date format

You can change the default date format by specifying `date_format`
in `Source/Data/Minima.yml`.

```yaml
# Minima date format
# refer to http://shopify.github.io/liquid/filters/date/ if you want to customize this
date_format: "%b %-d, %Y"
```

--

### Enabling comments (via Disqus)

Optionally, if you have a Disqus account, you can tell Jekyll to use it to show a comments section below each post.

To enable it, add the following lines to your Jekyll site's `Source/Data/About.yml`:

```yaml
disqus:
    shortname: my_disqus_shortname
```

You can find out more about Disqus' shortnames [here](https://help.disqus.com/customer/portal/articles/466208).

Comments are enabled by default and will only appear in production, i.e., `JEKYLL_ENV=production`

If you don't want to display comments for a particular post you can disable them by adding `comments: false` to that post's YAML Front Matter.

--

### Social networks

You can add links to the accounts you have on other sites, with respective icon, by adding one or more of the following options in your `Source/Data/Author.yml`:

```yaml
social:
    - type: dribbble
      username: jekyll
    - type: facebook
      username: jekyll
    - type: flickr
      username: jekyll
    - type: github
      username:  jekyll
    - type: instagram
      username: jekyll
    - type: linkedin
      username: jekyll
    - type:  pinterest
      username: jekyll
    # Mastodon instances
    - type: mastodon
      username: jekyll
      instance: example.com
    - type: mastodon
      username: jekyll2
      instance: example.com
    - type: twitter
      username: jekyllrb
    - type: youtube
      username: jekyll
    - type: googleplus
      username: +jekyll
    - type: rss
      display_name: rss
      feed: /feed.xml
```

You can add an RSS feed for the site, with respective icon, by adding the following option in your `Source/Data/About.yml`:

```yaml
rss: rss
```

--

### Enabling Google Analytics

To enable Google Analytics, add the following lines to your Jekyll site's `Source/Data/About.yml`:

```yaml
google_analytics: UA-NNNNNNNN-N
```

Google Analytics will only appear in production, i.e. `JEKYLL_ENV=production`.

--

### Enabling Excerpts on the Home Page

To display post-excerpts on the Home Page, simply add the following to your `Source/Data/Minima.yml`:

```yaml
show_excerpts: true
```

## Contributing

Bug reports and pull requests are welcome on GitHub at [https://github.com/jekyll/minima](https://github.com/jekyll/minima). This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

## Development

To set up your environment to develop this theme, run `script/bootstrap`.

To test your theme, run `script/server` (or `bundle exec jekyll serve`) and open your browser at `http://localhost:4000`. This starts a Jekyll server using your theme and the contents. As you make modifications, your site will regenerate and you should see the changes in the browser after a refresh.

## License

The theme is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
