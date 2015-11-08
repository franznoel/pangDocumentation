# Compiling Javascript Packages using Grunt

Compiling JavaScript has a similar concept of using Ant (of Java). This documentation will compile all JavaScript codes using npm, grunt, and 

**For Java Experienced developers:** _Grunt compiles files, libraries, or packages  using JavaScript configuration. In other words, it is similar to Ant, a software that helps compile Java codes before the main Javanese program runs._

Here's a simple procedure how to install Grunt:

## Install Node.js
Install `npm` command by installing Node.js (Node.js contains both `npm` and `node`)


## Install Grunt

2. Create a new project folder called `my-project`
3. Create two empty files named `Gruntfile.js` and `package.json`:

	```
	touch Gruntfile.js package.json
	```
	
4. Add content to the file `package.json`. See example settings.
		
   ```
   {
        "name": "my-project",
        "version": "0.1.0",
        "description": "My Project",
        "license": "MIT",
        "repository": "my-project",
        "devDependencies": {
            "grunt": "~0.4.5",
            "grunt-contrib-jshint": "~0.10.0",
            "grunt-contrib-nodeunit": "~0.4.1",
            "grunt-contrib-uglify": "~0.5.0"
        }
   }
   ```
	**Note:** Depending on your dependencies, Node.js will install plugins coming from its plugin server. Here's a list of [Grunt plugins](http://gruntjs.com/plugins). Currently, we are installing the plugins `grunt` to run **Grunt commands**. Also, `grunt-contrib-jshint`, `grunt-contrib-nodeunit`, and `uglify` will allow the use of **Grunt plugins** in our grunt configuration.

5. Run `npm install` to install **Grunt dependencies**.

	```
	sudo npm install
	```

## Configure and Compile Using Grunt

1. Add content to the file `Gruntfile.js`. See example configuration:

	```
	module.exports = function(grunt) {
	
	  // Project configuration.
	  grunt.initConfig({
	    pkg: grunt.file.readJSON('package.json'),
	    uglify: {
	      options: {
	        banner: '/*! <%= pkg.name %> <%= grunt.template.today("yyyy-mm-dd") %> */\n'
	      },
	      build: {
	        src: 'src/<%= pkg.name %>.js',
	        dest: 'build/<%= pkg.name %>.min.js'
	      }
	    }
	  });
	
	  // Load the plugin that provides the "uglify" task.
	  grunt.loadNpmTasks('grunt-contrib-uglify');
	
	  // Default task(s).
	  grunt.registerTask('default', ['uglify']);
	};
	```
**Note:** Grunt will compile depending on your configuration. In this configuration, make sure that you have a `src/` folder_, which will allow **Grunt** to create a compilation in the `build/` folder.

7. Run Grunt command to minify (or `uglify`) the source file:

	```
	grunt
	```
	
 