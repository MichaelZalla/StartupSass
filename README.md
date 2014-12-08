# StartupSass

StartupSass is a small, responsive scaffolding designed to accelerate your web project. StartupSass offers a Sass framework that scales easily with your site, in addition to a basic build system for common development tasks. StartupSass helps to minimize the time it takes to get your project off the ground, allowing you to focus on what makes your project *special*.

StartupSass uses ZURB Foundation's Normalize and Grid modules to support layouts that are consistent and responsive across browser environments. The rest of the framework is written from scratch, giving you complete freedom to extend or remove style information, or simply write your styles on top of the existing framework.

##### TODOS

- [ ] Write project customization walkthroughs
- [ ] Reconsider usefulness of `.view-content` page wrapper

---

### Getting Up and Running
	
##### Dependencies

1. [node](http://nodejs.org/) (~0.10.31)
2. [grunt-cli](http://gruntjs.com/getting-started#installing-the-cli) (~v0.1.13) — `npm install -g grunt-cli`
3. [bower](http://bower.io/#install-bower) (~1.3.12) — `npm install -g bower`

##### Installation

1. Clone this repository:
	
	```bash
	git clone https://github.com/MichaelZalla/StartupSass.git && mv StartupSass YOUR_PROJECT && cd YOUR_PROJECT
	```

2. Install the submodule(s) that StartupSass depends on:
	
	```bash
	git submodule init && git submodule update
	```

3. Set your remote project repository as the new remote origin:
	
	```bash
	git remote set-url origin https://github.com/YOUR_USERNAME/YOUR_PROJECT.git
	```

4. Install node dependencies for building with Grunt:
	
	```bash
	sudo npm install
	```

5. Customize your `README.md`, `package.json`, and `bower.json` files (optional)
	
	```bash
	vi README.md
	# Update fields ...
	vi package.json
	# Update fields ...
	```

6. Fetch front-end dependencies and build to `dist` directory:
	
	```bash
	grunt build && grunt watch
	```

7. Start a live-reload server and view the site in-browser:
	
	```bash
	# In a separate console session ...
	barkeep -p 8000
	```

---

### Build System Tasks

StartupSass comes with several pre-configured tasks that can be run from the command-line with Grunt. Tasks are defined within `Gruntfile.js` in your project's root directory. You may want to re-configure or remove certain tasks to fit the needs of your project (in addition to adding new tasks).

- **`bower:install`**: Fetch Bower dependencies and save them locally.

- **`copy`**: Copies HTML, favicons, images, fonts, and custom scripts from `src` to `dist`.

- **`concat`**: Copies front-end JavaScript dependencies into your project's scripts directory.

- **`sass`**: Compiles Sass into a minified stylesheet that is placed in your project's styles directory.

- **`watch`**: Watch for changes to files for auto-compilation and auto-copying (**Blocking**).

**\*Note**: The `grunt build` command will run the `bower:install`, `concat`, `copy`, and `sass` tasks, in that order.

<!---

### Customizing A New Project

Here are some easy first steps to add some originality to your new site, while helping your get more familiar with the scaffold.

**Notice**: If you've cloned this repository with Git and are working on the `master` branch, be sure to consider setting a new remote origin for the repo. Otherwise, issuing a `git pull` may bring in changes from the StartupSass repository that could overwrite or break your local changes or additions.

##### Update Site Metadata

StartupSass provides an `index.html` file at the base of the `src` folder. You can think of this as a test page which lets you explore a small amount of responsive functionality that's built into the scaffold. However, you may find it's easiest to use this HTML as a basis for a landing page.

Let's update the metadata in the `head` of the HTML. Out of the box, it should look something like this:

```html
<title>Startup Sass</title>
<meta name="description" content="Small, responsive scaffolding designed to accelerate your web project">
<meta name="author" content="Michael Zalla (https://github.com/MichaelZalla)">
```

In your text editor, change the `title` tag's text value and the content values stored in the `description` and `author` metadata tags to match your project.

##### Update Site Favicon

The site's favicon files are located alongside the `index.html` file in `src`.
Changes to the favicon files may not be immediately reflected by your browser; you may need to append or change an arbitrary parameter (such as '?v=0.1') to the favicon URLs to trigger a re-cache in the browser.

##### Add New Page Content

##### Adding Custom Stylesheets

##### Adding Custom Scripts

-->

---

### Sass Framework Reference

#### Configuration

The `config` module defines a number of global Sass variables for controlling some basic attributes of your page, including the maximum width of your content (for large screens), and the base typographic point sizes for large and small screens.

The module is located at `src/scss/modules/_config.scss`. You can extend this module with your own project-specific variables.

#### Fonts

Default font definitions are written inside of the `fonts` module. Writing definitions is simplified with the `fontface` Sass 
mixin (included):

```Sass
@mixin fontface($family, $source,
				$weight: $font-weight-regular,
				$style: normal)
```

This mixin module also defines some global `font-weight` variables that provide better symantics to your font definitions and typographic style rules:

```
$font-weight-regular: 	400 !default;
$font-weight-bold: 		700 !default;
// etc...
```

This module is located at `src/scss/partials/global/_fonts.scss`. You can extend this module with your own @font-face definitions for custom fonts used by your project.

**\*Note**: All font files stored in `src/fonts` will be automatically copied (overwritten) to `dist/fonts` whenever Grunt is used to run the `copy` task.

#### Colors

The `colors` module defines RGB-formatted color values for use across your Sass modules, including values for defining the default appearance of type and link elements on your page. When adding a project-specific color palette, you may wish to prefix your own color variables with a project namespace:

```
$mySite-color-1:rgb(127,127,127);
$mySite-color-2:rgb(255,255,255);
```

This module is located at `src/scss/modules/_colors.scss`.

**\*Note**: The pre-defined color variables are used by Sass modules that come bundled with StartupSass. Removing these variable definitions will cause the Sass compiler to throw an *`Undefined variable`* error. Renaming one of these variables requires that you replace each reference to the color inside of all modules with a valid variable reference.

#### Mixins

StartupSass also provides a number of useful global mixins for common styling tasks. Many of these mixins come from the (SassMixins)[https://github.com/MichaelZalla/SassMixins] submodule, which is a separately hosted repository.

For information about these mixins (with examples), see: https://github.com/MichaelZalla/SassMixins/blob/master/_bundle.scss

#### Typography

The `typography` module sets up a number of basic styles, classes, and `@extend` directives for controlling the appearance of type on your page. 

The `$ss-type-default-font-family` variable defined in this module can be used to specify your document's default (or root) typeface. This value must correspond to a font which you have defined in the `fonts` module, or defined elsewhere, or it must be a [default system font](http://www.cssfontstack.com/).

This module is also responsible for setting base typographic point sizes for large and small screens. All typographic elements nested beneath the `html` tag may have their point sizes specified relative to this root value, resulting in a more flexible, relative hierarchy.

Built-in typographic decorator classes include:

- `.heading`
- `.subheading`
- `.label`
- `.callout`
- `.quotes`
- `.light`

<!---
The `.center` class and `%center` @extend directive can be used to make typographic elements serve as centered content containers.
-->

The module is located at `src/scss/particles/global/_typography.scss`.

#### Layout

The `layout` module is used in conjunction with Foundation's Grid module to set up a basic responsive structure for your web content. It relies on variables defined in the `config` module to determine things like size and padding.

To deliver the best experience across devices, it is suggested that you structure your page's content (including headers and footers) into discrete sections, wrapped by a `.view-content` element, like so:

```html
<body>
	<div class="view-content">
		<!-- Content sections go in here! -->
	</div>
	<!-- Page scripts -->
	<script src="/to/my/script.js"></script>
</body>
```

Conventionally, content sections use wrapper elements to achieve horizontal and vertical centering:

```html
<body>
	<div class="view-content">
		<section>
			<div class="content">
				<div class="container">
					<!-- Section content -->
				</div>
			</div>
		</section>
	</div>
</body>
```

The framework's built-in header and footer implementations also follow this convention:

```html
<body>
	<div class="view-content">
		<footer>
			<div class="content">
				<div class="container">
					<!-- Footer content -->
				</div>
			</div>
		</footer>
	</div>
</body>
```

A `section` will, by default, stretch to be the full width of the display, even if its content is constrained to be smaller. This means that background images applied to sections will still extend to the edges of the screen. You can use the `.fullscreen` class on a section to stretch it to be the full height of the screen as well (this is especially useful for mobile-first layouts).

This module is located at `src/scss/partials/global/_layout.scss`.

---

### License

Copyright (c) 2014 Michael Zalla

Licensed under the [MIT License](http://opensource.org/licenses/MIT).