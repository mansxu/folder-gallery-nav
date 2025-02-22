# Folder Gallery
+ Contributors: mansxu
+ Original author: vjalby
+ Tags: gallery, folder, lightbox
+ Requires at least: 3.5
+ Tested up to: 4.2.2
+ Stable tag: 1.7.2
+ License: GPLv2 or later
+ License URI: http://www.gnu.org/licenses/gpl-2.0.html
+ Donate link: http://jalby.org/wordpress/donate/
+ Folder icon: License CC0 https://www.svgrepo.com/svg/37289/image
+ Up arrow icon: License CC0 https://www.svgrepo.com/svg/77182/up-arrow

This plugin generates picture (or document) galleries from a folder using a shortcode.

## Description 

This plugin creates picture (or document) galleries from a folder. 
The pictures folder must be uploaded (using FTP) somewhere on the server (e.g. wp-content/upload). It must be writable (chmod 777).

Folder Gallery Plugin does not include any lightbox JS engine anymore. You have to install one or use a compatible lightbox plugin. See FAQ.

To include a picture gallery in a post or a page, you have to use the following shortcode :

	[foldergallery folder="local_path_to_folder" title="Gallery title"]

For each gallery, a subfolder cache_[width]x[height] is created inside the pictures folder when the page is accessed for the first time. 

To include a document gallery or list, see FAQ.


A Settings page allows to set the default paramaters of the galleries :

* Lightbox JS Engine: Lightbox 2 (if installed), Fancybox 2 (if installed), Lightview 3 (if installed), Easy Fancybox Plugin (if available), Responsive Lightbox Plugin (if available) or none (default)
* Display Thumbnails (thumbnails): all = standard Gallery, single = displays a single thumbnail linked to the lightbox gallery, none = displays a link to the lightbox gallery
* Sort pictures by (sort) : pictures are sorted by filename (filename) or in reverse order (filename_desc) or by modification date (date or date_desc) or randomly (random)
* Number of images per row (columns)
* Thumbnails width and height (width & height)
* Picture border (border)
* Padding and Margin (padding & margin)
* Caption Format (caption): default (title + picture number), filename, filenamewithoutextension, smartfilename (filename with underscores and front numbers removed), modificationdate, modificationdateandtime, modificationdater (RFC 2822), modificationdatec (ISO 8601), iptctitle, iptccaption, none
* Show Thumbnail Captions (show_thumbnail_captions): yes (true) or no (false). Display (or not) the caption under the picture thumbnail.
* Fancybox Caption Style: Inside, Outside, Over, Float, None. Available with Fancybox 2 engine only (if installed).
* Fancybox Transition: Elastic, Fade. Available with Fancybox 2 engine only (if installed).
* Autoplay Speed: Slideshow speed in seconds. 0 to turn autoplay off. Available with Fancybox 2 engine only (if installed).
* Misc settings - Layout (gridlayout): Use a grid layout when Masonry plugin is active.
* Misc settings - Permissions: force 777 permissions on cache folder. Leave it uncheck unless you really know what you do!
* Misc settings - Orientation: Correct picture orientation according to EXIF tag. Rotated pictures will be overwritten. (Require EXIF library in PHP.) Delete the cache folder to apply to existing galleries.
 
Most of theses settings can be overridden using the corresponding shortcode :

	[foldergallery folder="path" title="title" columns=1 width=150 
			height=90 border=1 padding=2 margin=10 thumbnails=single]
 
Sample, contact available at http://jalby.org/wordpress/

## Installation

1. Unzip the archive foldergallery.zip
2. Upload the directory 'foldergallery' to the '/wp-content/plugins/' directory
3. Download and upload to '/wp-content/' directory at least on lightbox JS engine (see FAQ)
4. Activate the plugin through the 'Plugins' menu in WordPress
5. Go to Settings / Folder Gallery to change the default settings
6. Upload a folder of pictures to 'wp-content/upload/MyPictures'
7. Insert the following short code in post or page :

	[foldergallery folder="wp-content/upload/MyPictures" title="My Picture Gallery"]
	
7. To use Fancybox 2 engine, see FAQ

## Frequently Asked Questions 

### How to install Lightbox 2 JS engine? 

1. Download Lightbox 2 from http://lokeshdhakar.com/projects/lightbox2/
2. Unzip the archive
3. Upload the directory 'lightbox' to '/wp-content'.
4. Go To Wordpress > Settings > Folder Gallery and select Lightbox 2 as Gallery Engine.
5. Done!

### How to install Fancybox 2? 

1. Download fancybox 2 from http://fancyapps.com/fancybox/#license
2. Unzip the archive then rename the directory to 'fancybox'.
3. Upload the directory 'fancybox' to '/wp-content'.
4. Go To Wordpress > Settings > Folder Gallery and select Fancybox 2 as Gallery Engine.
5. Done!

### How to install Lightview 3? 

1. Download lightview from http://projects.nickstakenburg.com/lightview/download
2. Unzip the archive then rename the directory to 'lightview' (i.e., remove version number).
3. Upload the directory 'lightview' to '/wp-content'.
4. Go To Settings / Folder Gallery and select Lightview as Gallery Engine.
5. Done!

You can specify lightview options with the shortcode attribute 'options':

	[foldergallery folder="path" title="My Gallery"
		options="controls: { slider: false }, skin: 'mac'"]
	
You can set default options in Folder Gallery Options Page. 

See http://projects.nickstakenburg.com/lightview/documentation for details about Lightview options.

### Can I use Folder Gallery along with another Lightbox plugin? 

Folder Gallery has built-in support for "Easy Fancybox" plugin by RavanH, "Responsive Lightbox" plugin by dFactory, and "Slenderbox" plugin by Matthew Petroff. After activating the plugin, select it in Folder Gallery Settings (Gallery Engine).

Otherwise, if your Lightbox plugin automatically handles images, you may set the lightbox engine to 'None' in Folder Gallery Options.
This should work with

* Fancybox 1.0.7+ by Kevin Sylvestre
* jQuery Colorbox 4.5+ by Arne Franken
* Lightview Plus 3.1.3+ by Puzich
* Maybe other

### Can I use Easy Fancybox plugin along with Folder Gallery? 

Yes! First install and activate Easy Fancybox plugin. In Wordpress > Settings > Media > Fancybox > Images > Gallery, Disabled Autogllery. Then, in Wordpress > Settings > Folder Gallery, select "Easy Fancybox (plugin)" as Gallery Engine.

### How to use the GridLayout of jQuery Masonry Image Gallery Plugin with Folder Gallery? 

First install and activate jQuery Masonry Image Gallery, then check the GridLayout option in Folder Gallery Misc Settings. 

If thumbnails height is non-zero in Folder Gallery option, then width is used for landscape pictures and height for portrait pictures ; the other size is calculated to keep picture proportions. If thumbnails height is set to zero, then all pictures have the same width ; height is calculated to keep picture proportions.

### I'd like to display a single thumbnail instead of the full thumbnails list 

Add the attribute `thumbnails` in the shortcode with value `single` to display only the first thumbnail.

	[foldergallery folder="path" title="My Gallery" thumbnails="single"]

If you want to use a different picture (than the first) as the single thumbnail for the gallery, add a picture with name !!! (e.g., `!!!.jpg`) to your gallery. This picture will be used as thumbnail, but won't be included in the (lightbox) gallery. Another option is to use the shortcode attribute `thumbnails=-n` where `n`is the picture number (in the gallery) you want to use as single thumbnail. 

To hide gallery title under the thumbnail, add `title=""`. You then should set `caption' to something else than `default`, e.g., `caption="filename"`.

### I'd like to display only the n first thumbnails instead of the full thumbnails list 

Add the attribute `thumbnails` in the shortcode with value `n` to display only the n first thumbnails.

	[foldergallery folder="path" title="My Gallery" thumbnails=3]

### I'd like to display a (sub)title under each thumbnail 

You have to set show_thumbnail_captions to 1 (or change the global option in Folder Gallery Settings) using 

	[foldergallery folder="path" title="My Gallery" show_thumbnail_captions=true]

The caption format is set with the attribute `caption`. It can be set to `filename`, `filenamewithoutextension` or `smartfilename` which displays the filename without extension, front number removed and underscores (_) replaced with spaces.

	[foldergallery folder="path" title="My Gallery" show_thumbnail_captions=1 caption='smartfilename']
	
### How to display a document list ?

To build a list or gallery of a folder documents, use the following short code : 

[foldergallery folder="path" engine="documentlist" filetypes="pdf xlsx" caption="filename"] 

Two engines are available : documentlist and documentgallery. Filetypes is a space-separated list of document extensions.

A generic document thumbnail is used for all documents. To use a custom thumbnail for each document, put an image (png or jpg) with the same name as the document inside the document folder. If you want to change the generic thumbnail, put a file thumbnail.jpg or thumbnail.png inside the folder.

Engine and filetypes can be change in the Settings page.

## Screenshots
1. Folder Gallery Options
2. Folder Gallery in a post
3. Folder Gallery Lightbox

## Changelog 

= 1.8a7 [2015-08-12] =
* Basic support of subfolders.

= 1.8a4 [2015-06-07] =
* New GridLayout option for use with jQuery Masonry Image Gallery Plugin (and maybe other). See FAQ 

= 1.8a3 =
* Support for document list (see FAQ)
* Support for IPTC title/caption tag as caption

= 1.7.2 [2014-12-21] =
* Support for Slenderbox plugin

= 1.7.1 [20014-11-28] =
* Compatibility with WPML plugin
* Date and time caption formats

= 1.7 [2014-09-04] =
* Option to correct picture orientation according to EXIF tag. Require PHP with EXIF library. Rotated pictures will be overwritten.
* Support for Nivo Lightbox in Responsive Lightbox Plugin

= 1.6 [2014-07-17] =
* Because of license issue, Lightbox 2 is not included in Folder Gallery anymore. You have to install it yourself (see FAQ)
* Folder Gallery doesn't include any JS lightbox engine anymore. You have to install one yourself (see FAQ)
* Reorganize Settings page
* Add an option to force 777 permissions to cache folders
* Workaround for unactive glob function

= 1.5b2 [2014-02-22] =
* Because of license compatibility, Fancybox 2 is not included in Folder Gallery anymore. You have to install it yourself or use a Fancybox plugin (see FAQ)
* Change the location of Lightview 3 installation (see FAQ)
* Support for Responsive Lightbox Plugin
* Support for Easy Fancybox Plugin
* Global option to set transition effect when Fancybox 2 engine is selected
* Option (and attribute) to sort pictures randomly
* Rewrite directory scan : support for gif, bmp pictures ; sort by date option

= 1.4 [2013-08-31] =
* Global option to display the caption under the picture thumbnail.
* Several changes in layout and CSS. Hopefully it breaks nothing!
* New 'smartfilename' option for caption style
* Option (and attribute) to sort pictures by filename in reverse order
* Improved captions support
* Compatibility with PhotoSwipe WP plugin
* Minor bug fixes

= 1.3 [2013-08-05] =
* Update Lightbox 2 JS to 2.6 (JQuery/Wordpress 3.6 compatibility)
* Update Fancybox JS to 2.1.5
* Global option to set picture's caption style (default, filename, filenamewithoutextension, none)
* Global option to set autoplay speed when Fancy Box engine is selected.
* Option to display the thumbnails of the first pictures only. Read the FAQ!
* Several changes and improvements related to single-thumbnail-gallery (thumbnails="single"). Read the FAQ!
* Misc bug corrections

= 1.2 [2013-03-16] =
* Pictures are now sorted alphabetically
* Global option to change title style when fancybox engine is selected
* Misc changes to support a forthcoming plugin

= 1.1 [2013-02-18] =
* Add a 'thumbnails' option/attribute to set how many thumbnails should be displayed in the gallery : all (default), single or none (display a link instead).
* Improved error messages
* Update FAQ

= 1.0 [2013-02-03] =
* Fix a problem with case of file extension of thumbnails.
* Update Fancybox to 2.1.4

= 0.97 [2013-01-16] =
* Scripts are only loaded on pages with galleries
* Add support for fancybox (included)
* Add an option to change gallery 'engine' (Lightbox, Fancybox, Lightview when installed or None)
* Misc changes 

= 0.95 [2013-01-10] =
* Internationalization (English, French)
* Support for Lightview 3 (see FAQ)
* Code cleaning
* Small improvements

= 0.92 [2013-01-05] =
* Add a 0-column option (When 'Images per Row' is set to 0, the number of columns is set automatically.)
* Misc changes

= 0.90 [2013-01-05] =
* First released version
