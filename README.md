# gradle-publish-script 
A gradle script that should be applied to every gradle project that should be able to publish to Sonatype Central.

## Use
In you main ```build.gradle```:

```
subprojects {
    apply from: 'https://raw.githubusercontent.com/ykrasik/gradle-publish-script/master/publish.gradle'
}
```

### Configure
The script expects certain properties to exist in the project context.  
A convenient way of doing this is to write them in a ```gradle.properties``` file under the project root.

gradle.properties:

```
version = 0.1.0

pomGroup = com.github.ykrasik

pomName = Gradle publish script
pomDescription = A gradle script for publishing artifacts to Sonatype.
pomUrl = https://github.com/ykrasik/gradle-publish-script
pomInceptionYear = 2015

pomScmUrl = https://github.com/ykrasik/gradle-publish-script
pomScmConnection = scm:https://github.com/ykrasik/gradle-publish-script.git
pomScmDeveloperConnection = scm:git://github.com/ykrasik/ogradle-publish-script.git

pomLicenseName = The Apache Software License, Version 2.0
pomLicenseUrl = http://www.apache.org/licenses/LICENSE-2.0.txt
pomLicenseDistribution = repo

pomDeveloperId = ykrasik
pomDeveloperName = Yevgeny Krasik
pomDeveloperEmail = ykrasik@gmail.com
```