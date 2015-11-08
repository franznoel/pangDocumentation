## Compiling Javascript Projects using Grunt

Compiling JavaScript has a similar concept of using Ant (of Java). This documentation will compile all JavaScript codes using npm, grunt, and 

**For Java Experienced developers:** _Grunt compiles files, libraries, or packages  using JavaScript configuration. In other words, it is similar to Ant, a software that helps compile Java codes before the main Java program runs._

### Installing Grunt 

Here's a simple procedure how to install Grunt:

1. Install `npm` by installing Node.js (Node.js contains both `npm` and `node`)
2. Create a new project folder called `my-project`
3. Create two empty files named `Gruntfile.js` and `package.json`:

	```
	touch Gruntfile.js package.json
	```
	
4. Add content to the file `package.json`. See example package config.

	**Note:** Depending on your dependencies, Grunt will install the plugins coming from its [plugin server](http://gruntjs.com/plugins).
		
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
   
5. Install the dependencies `grunt`, `grunt-contrib-jshint`, `grunt-contrib-nodeunit` and `uglify` by running.

	```
	sudo npm install
	```

6. Add content to the file `Gruntfile.js`. See example configuration:

	**Note:** Depending on your configuration, Grunt will treat how to compile the configurations.

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
7. Run Grunt command:

	```
	grunt
	```
	
 