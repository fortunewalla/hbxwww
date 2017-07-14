# hbxwww

Default website created from `blogdown::new_site(theme="yihui/hugo-xmin")` and customized.

__Why?__ Template for future websites. Minimal with focus on pages, posts and using web icons to represent sections and different parts.

My Customization (hbxwww):

* __Until July 13, 2016__
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