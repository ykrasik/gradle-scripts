# Gradle publish script 
A re-usable Gradle script that should be applied to every gradle project that should be able to publish to Sonatype Central.
Adds commonly needed functionality, like:
* Build type: Local / Snapshot / Release
* Confirmation before publish

## Apply:
In you main ```build.gradle```:

```
subprojects {
    apply from: 'https://raw.githubusercontent.com/ykrasik/gradle-scripts/master/publish.gradle'
}
```

## Use:
Publish local:
```
gradlew uploadArchives
```

Publish snapshot:
```
gradlew uploadArchives -Psnapshot
```

Publish release:
```
gradlew uploadArchives -Prelease
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

Any property can be overridden from the command line with -P{property}={value}.
So to publish with a different version then what is specified in gradle.properties:
```
gradlew uploadArchives -Pversion=0.1.1
```

# Gradle provided configuration
Creates a 'provided' configuration, for cases where libraries are only needed for compilation & tests, but should not
be exported with the generated artifacts.

## Apply:
In you main ```build.gradle```:

```
subprojects {
    apply from: 'https://raw.githubusercontent.com/ykrasik/gradle-scripts/master/provided.gradle'
}
```

## Use:
In order to declare a 'provided' dependency, use the following dependency declaration: 

```
dependencies {
    provided "org.projectlombok:lombok:$lombokVersion"
}
```

This will declare 'lombok' as a compile-only declaration (also available to tests and javadoc task), but will not be
exported with the artifact.