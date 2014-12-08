# StartupSass

StartupSass is a small, responsive scaffolding designed to accelerate your web project. StartupSass offers a Sass framework that scales easily with your site. in addition to a basic build system for common development tasks. StartupSass helps to minimize the time it takes to get your project off the ground, allowing you to focus on what makes your project *special*.

StartupSass uses ZURB Foundation's Normalize and Grid modules to support layouts that are consistent and responsive across browser environments. The rest of the framework is written from scratch, giving you complete freedom to extend or remove style information, or simply write your styles on top of the existing framework.

### Getting Up and Running
	
##### Dependencies

1. [node](http://nodejs.org/) (~0.10.31)
2. [grunt-cli](http://gruntjs.com/getting-started#installing-the-cli) (~v0.1.13) — `npm install -g grunt-cli`
3. [bower](http://bower.io/#install-bower) (~1.3.12) — `npm install -g bower`

##### Installation

1. Clone this repository:
	
	```
	git clone https://github.com/MichaelZalla/StartupSass.git && cd StartupSass
	```

2. Install the submodule(s) for this repository:
	
	```
	git submodule init && git submodule update
	```

3. Set your remote project repository as the new remote origin:
	
	```
	git remote set-url origin https://github.com/YOUR_USERNAME/YOUR_PROJECT.git
	```

4. Install node dependencies for building with Grunt:
	
	```
	sudo npm install
	```

5. Customize your `README.md`, `package.json`, and `bower.json` files (optional)
	
	```
	vi README.md
	...
	```

6. Fetch frontend dependencies and build to `dist` directory:
	
	```
	grunt build && grunt watch
	```

7. Start a live-reload server and view the site in-browser:
	
	```
	// in a separate console session
	barkeep -p 8000
	```

### Customizing Your Project

These first steps will help you become more familiar with your scaffold, while
adding some originality to your new site:

##### Update Site Metadata


##### Update Site Favicon


##### Add New Page Content


##### Adding Custom Stylesheets


##### Adding Custom Scripts


<!---
helps your development efforts kick off on the right foo

starts your website off on the right foot 

StartupSass is a small, responsive website scaffolding designed to jump-start
front-end development. StartupSass gets your project 

allowing you to spend less time configuring a build system
or
-->