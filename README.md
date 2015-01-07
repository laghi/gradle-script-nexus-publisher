# gradle-script-nexus-publisher
===================

## About
This script is a simple custom task to publish gradle scripts to nexus. 

The need of an easy way to publish a script in a public site (inside a private network) appeared when the number of gradle projects in our team increased. 

At this point, we needed a way to centralize some common scripts, that would be used across many projects. We decided that using our nexus repository would be a good idea. This script is designed to upload this common gradle scripts to nexus, without manual intervention. 

## Usage
```groovy

	apply from: 'https://raw.githubusercontent.com/laghi/gradle-script-nexus-publisher/master/gradle-nexus-publish.gradle'
	
	uploadGradleScriptToNexus {
		fileName = 'your-gradle-script' 							// name of the gradle script. Notice that the name of the script in nexus will be the same name of the file itself. The location is relative to the project directory
		fileVersion = '1.0.0-0'										// the version to be appended to the fileName
		nexusUrl = 'http://sajwebbuild' 						 	// the nexus url
		nexusPath = '/nexus/content/sites/my-gradle-scripts/' 	// the path in which the file script will be distributed
		nexusUsername = 'user'										// nexus auth user 
		nexusPassword = 'foo'											// nexus auth password
	}

```

## License
Copyright (c) 2015 Murilo Laghi  
Licensed under the Apache-2.0 license.