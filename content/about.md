---
title: About
---

### Grateful to the amazing work of Yihui Xie https://yihui.name/ !!!

_The aim is to use R based packages and tools for website creation and maintainence_

Main documentation for setup & customization:

* From start to finish https://apreshill.rbind.io/post/up-and-running-with-blogdown/
* Hugo-Xmin Theme Information https://xmin.yihui.name/about/
* Rbind Domain Support https://support.rbind.io/about/

General website with `hugo-xmin` theme

* In RStudio, Create File -> New Project.
* Create new website with command `blogdown::new_site(theme = "yihui/hugo-xmin")`
* To update theme, delete `hugo-xmin` folder in `themes`. Then in RStudio `blogdown::install_theme('yihui/hugo-xmin')`. Then 'Build Website' again.

For `hbxwww` customized website

* `git clone https://github.com/fortunewalla/hbxwww.git`
* Open `hbxwww.RProj` in RStudio
* Theme folder `hugo-xmin` is untouched. So theme can be updated without losing customized changes.
* To update theme, delete `hugo-xmin` folder in `themes`. Then in RStudio `blogdown::install_theme('yihui/hugo-xmin')`. Then 'Build Website' again.

----

Customization:

* __Until July 13, 2017__
* Added 'Posts' to menu through `config.toml` [done]
* Removed 'Notes' . Delete `content/notes` directory. [done]
* Removed 'Posts' from appearing in the Home Page. In `layouts/_default/list.html` Add if condition. [done]
* [Enable highlight.js for syntax highlighting of code blocks](https://github.com/yihui/hugo-xmin/pull/5)  `layouts/partials/foot_custom.html` and `layouts/partials/head_custom.html` and `static/css/terms-octicons-hljs-style.css` add `.pre` style
* Added [Categories & Tags](https://github.com/yihui/hugo-xmin/commit/f1e3a90489ec61d903429a582a058b8a1b4d7093) to every post page. In `layouts/_default/single.html` and `static/css/terms-octicons-hljs-style.css` add `.terms` style
* Changed posts layout in `config.toml` to `post = "/post/:slug/"` [done]
* Changed Date Format in `layouts/_defaults/list.html` to `2006, Jan 2` and in  `layouts/_defaults/single.html` to `Jan 2, 2006` [done]
* Added Octicons & FontAwesome CSS to `layouts/partials/head_custom.html` for specific icons e.g. telescope <i class="octicon octicon-telescope"></i> , microscope <i class="octicon octicon-microscope"></i> etc... [done]
* Added CSS code `.mega64-octicon` for 64px icons in `/static/css/terms-octicons-hljs-style.css` add `.megaocticon` and `.mega64octicon` style [done]
* Copied FontAwesome and Octicon fonts and CSS to local directory `static/css` and `static/fonts` instead of CDN. [done]
* Added `favicon.ico` to `static/images/` and link to file `layouts/partial/head_custom.html` [done]




### `config.toml`

Original:
```toml
[permalinks]
    post = "/post/:year/:month/:day/:slug/"
    note = "/note/:year/:month/:day/:slug/"
```
Modified:
```toml
[permalinks]
    post = "/post/:slug/"
```

### `layouts/partials/foot_custom.html`

Original: 
```
No support for syntax highlighting
```
Modified:
```html
<!-- Highlight Code-->
<script src="//cdn.bootcss.com/highlight.js/9.12.0/highlight.min.js"></script>
<script src="//cdn.bootcss.com/highlight.js/9.12.0/languages/r.min.js"></script>

<script>
hljs.configure({languages: ['r','bash','css','html','json','tex','latex','sql','toml','yaml']});
hljs.initHighlightingOnLoad();
</script>
```
### `layouts/partials/head_custom.html`
Original:
```
File did not exist.
```
Modified:

* favicon local
* octicons-catandpoststerms-hljs css local
* fontawesome local
* octicon local
* highlight.js remote
* github style in highlight.js remote
* typekit for cn character spacing.


```html
<link rel="shortcut icon" href="/images/favicon.ico">
<link rel="stylesheet" href="/css/terms-octicons-hljs-style.css">
<!-- <script async src="https://use.fontawesome.com/32c3d13def.js"></script> -->

<link rel="stylesheet" href="/css/font-awesome.min-4.7.0.css"><!-- beaker -->

<link rel="stylesheet" href="/css/octicons-3.0.1.css"><!-- beaker -->
<link rel="stylesheet" href="/css/octicons-2.4.1.css"> <!-- microscope -->
<link href="//cdn.bootcss.com/highlight.js/9.12.0/styles/github.min.css" rel="stylesheet"> <!-- for highlight.js -->
<!-- <link href="/css/github.min-9.12.0.css" rel="stylesheet"> local for highlight.js -->
{{ if or .IsHome (len (findRE "^/cn/" .URL)) }}
<script async src="/js/load-typekit.js"></script>
{{ if lt (.Date.Year) 2017 }}
<script>
(function(u, c) {
  var d = document, t = 'script', o = d.createElement(t), s = d.getElementsByTagName(t)[0];
  o.src = u;
  if (c) { o.addEventListener('load', function (e) { c(e); }); }
  s.parentNode.insertBefore(o, s);
})('//cdn.bootcss.com/pangu/3.3.0/pangu.min.js', function() {
  pangu.spacingPage();
});
</script>
{{ end }}
{{ end }}
```

### `static/css` folder
Original:
```
folder does not exist
```
Modified:
```bash
font-awesome-4.7.0.css
font-awesome.min-4.7.0.css
github.min-9.12.0.css  not used, using bootcss remote
octicons-2.4.1.css
octicons-3.0.1.css
```

### `static/fonts` folder
Original:
```
does not exist
```
Modified:
```bash
static/fonts:
fontawesome-4.7.0  octicons-2.4.1  octicons-3.0.1

static/fonts/fontawesome-4.7.0:
FontAwesome.otf          fontawesome-webfont.svg  fontawesome-webfont.woff
fontawesome-webfont.eot  fontawesome-webfont.ttf  fontawesome-webfont.woff2

static/fonts/octicons-2.4.1:
octicons.eot  octicons_files  octicons.svg  octicons.ttf  octicons.woff

static/fonts/octicons-2.4.1/octicons_files:
viewsource.css

static/fonts/octicons-3.0.1:
octicons.eot  octicons_files  octicons.svg  octicons.ttf  octicons.woff

static/fonts/octicons-3.0.1/octicons_files:
viewsource.css
```

### `static/images` folder for favicon
Original:
```
does not exist
```
Modified:
```bash
static/images:
favicon.ico
```
### `layouts/_default/list.html` to remove posts listing on any page.
Original:
```
does not exist
```
Modified:
```yaml
{{ partial "header.html" . }}

{{if not .IsHome }}
<h1>{{ .Title }}</h1>
{{ end }}

{{ .Content }}

{{if not .IsHome }} // Extra Line of Code
<ul>
  {{ range (where .Data.Pages "Section" "!=" "") }}
  <li>
    <span class="date">{{ .Date.Format "2006, Jan 2" }}</span>
    <a href="{{ .URL }}">{{ .Title }}</a>
  </li>
  {{ end }}
</ul>
{{ end }}  // Extra Line of Code

{{ partial "footer.html" . }}

```
### `layouts/_default/single.html` to add categories and tags to posts.
Original:
```
does not exist
```
Modified:
```yaml
{{ partial "header.html" . }}
<div class="article-meta">
<h1><span class="title">{{ .Title }}</span></h1>
{{ with .Params.author }}<h2 class="author">{{ . }}</h2>{{ end }}
{{ if .Params.date }}<h2 class="date">{{ .Date.Format "Jan 2, 2006" }}</h2>{{ end }}
<!-- Start: Adding categories and tags to articles -->
<p class="terms">
  {{ range $i := (slice "categories" "tags") }}
  {{ with ($.Param $i) }}
  {{ $i | title }}: {{ range $k := . }}<a href="{{ relURL (print "/" $i "/" $k | urlize) }}">{{$k}}</a> {{ end }}
  {{ end }}
  {{ end }}
</p>
<!-- End: Adding categories and tags to articles -->

</div>

<main>
{{ .Content }}
</main>

{{ partial "footer.html" . }}
```

# About Hugo XMin

**XMin** is the first Hugo theme I have designed. The original reason that I wrote it was I needed a minimal example of Hugo themes when I was writing the  [**blogdown**](https://github.com/rstudio/blogdown) book. Basically I wanted a simple theme that supports a navigation menu, a home page, other single pages, lists of pages, blog posts, categories, tags, and RSS. That is all. Nothing fancy. In terms of CSS and JavaScript, I really want to keep them minimal. In fact, this theme does not contain any JavaScript code at all, although on this example website I did introduce some JavaScript code (still relatively simple anyway). The theme does not contain any images, either, and is pretty much a plain-text theme.

The theme name "XMin" can be interpreted as "**X**ie's **Min**imal theme" (Xie is my last name) or "e**X**tremely **Min**imal theme".

# config.toml

For this example site, I defined permalinks for two sections, `post` and `note`, so that the links to pages under these directories will contain the date info, e.g., `https://xmin.yihui.name/post/2016/02/14/a-plain-markdown-post/`. This is optional, and it is up to your personal taste of URLs.

```
[permalinks]
    post = "/post/:year/:month/:day/:slug/"
    note = "/note/:year/:month/:day/:slug/"
```

You can define the menu through `menu.main`, e.g.,

```
[[menu.main]]
    name = "Home"
    url = "/"
    weight = 1
[[menu.main]]
    name = "About"
    url = "/about/"
    weight = 2
[[menu.main]]
    name = "Categories"
    url = "/categories/"
    weight = 3
[[menu.main]]
    name = "Tags"
    url = "/tags/"
    weight = 4
[[menu.main]]
    name = "Subscribe"
    url = "/index.xml"
```

Alternatively, you can add `menu: main` to the YAML metadata of any of your pages, so that these pages will appear in the menu.

The page footer can be defined in `.Params.footer`, and the text is treated as Markdown, e.g.,

```
[params]
    footer = "&copy; [Yihui Xie](https://yihui.name) 2017"
```

# Custom layouts

There are two layout files under `layouts/partials/` that you may want to override: `head_custom.html` and `foot_custom.html`. This is how you inject arbitrary HTML code to the head and foot areas. For example, this site has a file `layouts/partials/foot_custom.html` to support LaTeX math via MathJax and center images automatically:

```html
<script src="//yihui.name/js/math-code.js"></script>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
  tex2jax: {
    inlineMath: [['$','$'], ['\\(','\\)']],
    processEscapes: true
  }
});
</script>
<!-- <script async src="//cdn.bootcss.com/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML"></script> -->
<script async src="//mathjax.rstudio.com/latest/MathJax.js?config=TeX-MML-AM_CHTML"></script>
</script>

<script async src="//yihui.name/js/center-img.js"></script>
```

You can certainly enable highlight.js for syntax highlighting by yourself through `head_custom.html` and `foot_custom.html` if you want.

If you do not like the default fonts (e.g., `Palatino`), you may provide your own `static/css/fonts.css` under the root directory of your website to override the `fonts.css` in the theme.

# Other features

I could have added more features to this theme, but I decided not to, since I have no intention to make this theme feature-rich. However, I will teach you how. I have prepared several examples via pull requests at https://github.com/yihui/hugo-xmin/pulls, so that you can see the implementations of these features when you check out the diffs in the pull requests. For example, you can:

- [Enable Google Analytics](https://github.com/yihui/hugo-xmin/pull/3)

- [Enable Disqus comments](https://github.com/yihui/hugo-xmin/pull/4)

- [Enable highlight.js for syntax highlighting of code blocks](https://github.com/yihui/hugo-xmin/pull/5)

- [Display categories and tags on a page](https://github.com/yihui/hugo-xmin/pull/2)

- [Add a table of contents](https://github.com/yihui/hugo-xmin/pull/7)

- [Add a link in the footer of each page to "Edit this page" on Github](https://github.com/yihui/hugo-xmin/pull/6)

To fully understand these examples, you have to read [the section on Hugo templates](https://bookdown.org/yihui/blogdown/templates.html) in the **blogdown** book.

# Design philosophy

Lastly, a few words about my design philosophy for this theme: I have been relying on existing frameworks like Bootstrap for years since I'm not really a designer, and I was always scared by the complexity of CSS.

When I started writing this theme, I asked myself, "_What if I just write from scratch?_" No Bootstrap. No Normalize.css. I don't care about IE (life could be so much easier without IE) or inconsistencies among browsers (for personal websites). As long as the theme looks okay in Chrome, Firefox, and Safari, I'm done. Thanks to the simplicity of Markdown, you cannot really produce very complicated HTML, and I think styling the HTML output from Markdown is much simpler than general HTML documents. For example, I do not need to care much about form elements like textareas or buttons.

After I finished this theme, I started to wonder why I'd need `normalize.css` at all (it sounds like a religious belief). The default appearance of modern browsers actually looks pretty good in my eyes, after I tweak the typeface a little bit.

Compared to inconsistencies across browsers, I care much more about these properties of HTML elements:

- Tables should always be centered, and striped tables are easier to read especially when they are wide. Tables should not have vertical borders.
- An image should be centered if it is the only child element of a paragraph.
- The `max-width` of images, videos, and iframes should be `100%`.

I hope you can enjoy this theme. The source code is [on Github](https://github.com/yihui/hugo-xmin). Happy hacking!
