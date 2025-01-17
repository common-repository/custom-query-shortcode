=== Custom Query Shortcode ===
Contributors: peterhebert, shazdeh
Plugin Name: Custom Query Shortcode
Tags: query, shortcode, post
Requires at least: 3.3
Tested up to: 5.7
Stable tag: 0.4.0
License: GPLv2
License URI: http://www.gnu.org/licenses/gpl-2.0.html

A powerful shortcode that enables you to query anything you want and display it however you like, on both pages and posts, and in widgets.

== Description ==

This plugin gives you <code>[query]</code> shortcode which enables you to query and output any posts filtered by specific attributes.

= Usage =

You can use all parameters supported by <a href="http://codex.wordpress.org/Class_Reference/WP_Query">WP_Query class</a> to filter the posts; you can query for specific post types, categories, tags, authors, etc.

= Other supported parameters =

Aside from WP_Query parameters, the shortcode also supports the following additional parameters:

* *featured*: to query for sticky posts which by default are excluded from the query.
* *thumbnail_size*: to specify the size of the {THUMBNAIL} images. You can use <a href="http://codex.wordpress.org/Function_Reference/add_image_size#Reserved_Image_Size_Names">built-in image sizes</a> or custom ones you've defined.
* *content_limit*: to limit the number of words of the {CONTENT} var; by default it's "0" which means it outputs the whole content.
* *posts_separator*: text to display between individual posts.
* *lens*: custom output template - see description below.
* *twig_template*: output template using Twig templating engine - requires the Timber library.

= Formatting the output =
You can define how you want to format the output inline within an opening <code>[query]</code> and closing <code>[/query]</code> tag.
Available keywords are: TITLE, CONTENT, AUTHOR, AUTHOR_URL, DATE, THUMBNAIL, CONTENT, COMMENT_COUNT.

The following example will display the latest 5 posts from the category with the ID of 3, showing a post title and comment count, with a link to the post:
<code>[query posts_per_page="5" cat="3"] <h3><a href="{URL}">{TITLE} ({COMMENT_COUNT})</a></h3> [/query]</code>

<h5>Grid display</h5>
With the "cols" parameter you can display the output in a grid.
<code>[query posts_per_page="3" cols="3"] {THUMBNAIL} <h3>{TITLE}</h3> {CONTENT} [/query]</code>
will display the latest 3 posts in the defined template, in 3 columns.
The plugin will automatically divide the grid into rows based upon the 'posts_per_page' option, divided by the 'cols' option.

= Lenses (output templates) =
With the "lens" parameter you can customize the display of the query results using a template. Some basic lenses/templates are provided:

* **ul**: unordered list of linked post titles.
* **ul-title-date**: same as 'ul', but also displays the posted date.
* **article-excerpt**: series of articles, with a header containing the linked post title, and the excerpt.
* **article-excerpt-date**: same as 'article-excerpt', but also displays the posted date.
* **cards**: displays the post thumb above the header with linked post title, followed by the excerpt.

<h5>Bootstrap lenses</h5>
Some pre-defined lenses/templates are provided which use JavaScript Components from the <a href="http://getbootstrap.com/">Bootstrap</a> CSS framework.
This feature relies on Bootstrap library to be already loaded on the page, the plugin does *not* include it.
If you're using a Bootstrap-based theme, this *should* work; otherwise you can use the <a href="http://wordpress.org/extend/plugins/bootstrap/">Bootstrap plugin</a>).

<h6><a href="http://getbootstrap.com/javascript/#tabs">Tabs</a></h6>
This will show the latest 3 posts in a tabbed widget.
<code>[query posts_per_page="3" lens="tabs"]</code>

<h6><a href="http://getbootstrap.com/javascript/#tabs">Accordion</a></h6>
This will create an accordion widget of all our posts from the "faq" post type.
<code>[query posts_per_page="0" post_type="faq" lens="accordion"]</code>

<h6><a href="http://getbootstrap.com/javascript/#carousel">Carousel</a></h6>
This creates a carousel of latest five featured posts:
<code>[query posts_per_page="5" featured="true" lens="carousel"]</code>

<h5>Custom Lenses/templates</h5>
You can create your own custom templates and put them into one of these pre-defined folder names within your theme:

* 'query-shortcode-templates'
* 'partials/query-shortcode-lenses/'
* 'html/lenses/'

Or simply specify your own subfolder in the 'lens' parameter:
<code>[query lens="folder/template-name"]</code>

= Twig Template Support =
Starting with version 0.4, you can use Twig templates for your output. Support for Twig is provided by the <a href="https://github.com/timber/timber">Timber</a> library.

This requires that Timber be be installed as a <a href="https://en-ca.wordpress.org/plugins/timber-library/">plugin</a> or <a href="http://timber.github.io/timber/#getting-started">included in your theme</a>.

To use a Twig template for your query output, simply use the 'twig_template' parameter instead of the 'lens' parameter, and provide the path to your template:
<code>[query twig_template="folder/template-name.twig"]</code>

== Installation ==

1. Upload the whole plugin directory to the `/wp-content/plugins/` directory
2. Activate the plugin through the 'Plugins' menu in WordPress
3. Now use <code>[query]</code> shortcode anywhere you want.
4. Enjoy!



== Frequently Asked Questions ==

no questions have been asked yet.

== Screenshots ==

1. Example of shortcode syntax

== Changelog ==

= 0.4.0 =
* Added Twig templating support via the Timber Library

= 0.3 =
* Added a new directory to search for lenses within the current theme - 'query-shortcode-templates'
* Revamped readme.txt documentation

= 0.2.5 =
* Changed lens 'ul', removing post date. I also added lens 'ul-title-date', which is the equivalent of the previous 'ul' lens.

= 0.2.4 =
* Added lens 'ul', presenting an unordered list of query results with post date displayed.

= 0.2.3 =
* Added lens 'article-excerpt-date', which is the same as 'article-excerpt', except with the post date displayed.

= 0.2.2 =
* Added a filter to allow shortcodes within widget areas, which makes this plugin a lot more useful.

= 0.2.1.1 =
* Added a second directory to search for lenses within the current theme - 'partials/custom-query-lenses'.

= 0.2.1 =
* Added posts_separator parameter.

= 0.2 =
* Added Lens functionality. Now you can build tabs, accordions, and carousels (and build custom ones) out of queried posts. Relies on Twitter Bootstrap framework.

== Upgrade Notice ==
Upgrades are handled just like any other WordPress plugin.

