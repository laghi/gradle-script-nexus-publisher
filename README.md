# gradle-script-nexus-publisher

## About
This script is a simple custom task to publish gradle scripts to nexus.

The need of an easy way to publish a script in a public site (inside a private network) appeared when the number of gradle projects in our team increased.

At this point, we needed a way to centralize some common scripts, that would be used across many projects. We decided that using our nexus repository would be a good idea. This script is designed to upload this common gradle scripts to nexus, without manual intervention.

## Usage
In the gradle script that you want to upload, lets say, yourScript.gradle:

```gradle

	apply from: 'https://raw.githubusercontent.com/laghi/gradle-script-nexus-publisher/master/gradle-nexus-publish.gradle'

	uploadGradleScriptToNexus {
		scriptName = 'yourScript' 							// name of the gradle script in your machine. Notice that the name of the script in nexus will be the same name of the file itself. The location is relative to the project directory
		scriptVersion = '1.0.0-0'									// the version to be appended to the scriptName
		nexusUrl = 'http://yournexus' 						 		// the nexus url, can be provided with environment variable NEXUS_URL
		nexusPath = '/nexus/content/sites/my-gradle-scripts/' 		// the path in which the file script will be distributed, can be provided with environment variable NEXUS_PATH
		nexusUsername = 'user'										// nexus auth user, can be provided with environment variable NEXUS_USERNAME
		nexusPassword = 'foo'										// nexus auth password, can be provided with environment variable NEXUS_PASSWORD
	}

```

In the command line just type:
```
gradle -b yourScript.gradle uploadGradleScriptToNexus
```

## License
Copyright (c) 2015 Murilo Laghi  
Licensed under the Apache-2.0 license.
