id: app-development-gini-gradle
summary: gradle and build tools
authors: Shay markovich

# App develovment in android studio and using gradle

<!-- ------------------------ -->
##General
In this codelab you will learn about app stracture, how build process is done, and how android studio use gradle to build the files

<!-- ------------------------ -->
##Creating new app

###Using android studio
in android studio press file - > create new App
fill in app name, package name, location, language - Kotlin, and Minimum SDK, and press finish

###Examin the app
android studio created an app files lets look at the file stracture

> **_TIP:_**  to see hiden in finder files press Command + Shift + '.'

**hidden files:** 
<u>.gitignore</u> - file - this is the of the git source control - it says which files to ignore and not insert into the git, it usaly has the build folder, .idea folder and some other files, you can also see it inside the app folder where it has the build foler

<u>.gradle</u> - directory - this folder contails files gradle hidden files - using for gradle internal use

<u>.idea</u> - directory - this folder contails files of the idea (android studio) it has configurations and other definitions about the project

> **_TIP:_**  after download new project if the project donesn't complile you can try to delete the .idea folder and build folder and rebuild, this will create the project from start and can solve mismatch prolbems

**about gradle**
gradle help us to build our app and manage dependencies
``
![depenency diagram](https://docs.gradle.org/current/userguide/img/dependency-management-resolution.png)
``



**gradle files:**
/open each file and look at the content check what each files does/

- settins.gradle - in the main gradle project, contain all the gradle sub project (app module and libraries module)
```
include ':app'
```
- gradle.properties
- build.gradle (project)
    - this are used during the build time - if you want to add plugin to the app add repositories to here buildscript 


in each sub project (module) has its own build.gradle file
- build.gradle 
    - dependenties


<!-- ------------------------ -->
## build.gradle

The app build.gradle include

```
plugins {
    id 'com.android.application'
    id 'kotlin-android'
}
```

This custom plugins adds read the build gradle files and add task in order

id 'com.android.application' - add ability to compile the app into apk file

android:

```
android {
    
    defaultConfig {
    }

    buildTypes {
    }

    compileOptions {
    }

    kotlinOptions {
    }

    buildFeatures {
    }


}
```

this is the android tag it used to tell the android plugin how to build the code
it contsins defult config like
- compile ask, min sdk version code, version name, application id
- build types - release / debug
- flavours
- more option like compile option kotlin option build features


### dependencies:

````
dependencies {
    implementation ''
    implementation 'androidx.appcompat:appcompat:1.3.1'
    implementation 'com.google.android.material:material:1.4.0'
    implementation 'androidx.constraintlayout:constraintlayout:2.1.1'
    implementation 'androidx.navigation:navigation-fragment-ktx:2.3.5'
    implementation 'androidx.navigation:navigation-ui-ktx:2.3.5'
    testImplementation 'junit:junit:4.+'
    androidTestImplementation 'androidx.test.ext:junit:1.1.3'
    androidTestImplementation 'androidx.test.espresso:espresso-core:3.4.0'
}
````

add local jar file
````
dependencies {
    ...
    implementation files('libs/something_local.jar')
}
````

dependencty stracture:
 - androidx.core **:** core-ktx **:** 1.7.0
    -- androidx.core - artifect group name
    --  core-ktx - artifect name
    -- 1.7.0 - artifect version

> **_TIP:_**  never use + in the version name - when change dependency version name always check that the app still behave as it should !!


using local sub project (module):
```
dependencies {
    ...
    
    implementation project('')

    implementation (project('')) {
        exlude ......
    }

}
```

<!-- ------------------------ -->
## libraries

android library is gradle sub project with the 'com.android.library' plugin (instead of the 'com.android.application' plugin)
its artifect is aar files,
it can be used by the app module directrly by adding project implementation:
```
dependencies {
    ...
    
    implementation project('')

}
```

### manualy
* 


### automaticly
in android studio 
* file -> new -> New Module ...
* Choose android library
* press finish



### publish library
you can publish the libraries by using the **'maven-publish'** plugin:

```
// Because the components are created only during the afterEvaluate phase, you must
// configure your publications using the afterEvaluate() lifecycle method.
afterEvaluate {
    publishing {
        publications {
            // Creates a Maven publication called "release".
            release(MavenPublication) {
                // Applies the component for the release build variant.
                from components.release

                // You can then customize attributes of the publication as shown below.
                groupId = 'com.example.MyLibrary'
                artifactId = 'final'
                version = '1.0'
            }
            // Creates a Maven publication called “debug”.
            debug(MavenPublication) {
                // Applies the component for the debug build variant.
                from components.debug

                groupId = 'com.example.MyLibrary'
                artifactId = 'final-debug'
                version = '1.0'
            }
        }
    }
```

After you create publications, the Maven Publish plugin creates publishing tasks that you can use to publish your artifact to the repositories that you specify.

```
./gradlew clean build publish
```

> **_TIP:_**  you can publish the library to "maven local repository" - this is repository inside your computer in ~/.m2/repository and you can use it if you add the repository MavenLocal()
```
./gradlew clean build publishToMavenLocal
```


### library api vs implemenataion vs compile only

api - the dependencis is visible to the consumer of the library
implemenation - the dependencis is not visible to the consumer of the library
compile only - the dependencis is visible to the consumer of the library and also is not added in the pom file, so the consumer need to add them indendetly

<!-- ------------------------ -->
## Using proguard
progurd is a tool for we use it to obsfectd(hide implementation deatils) and minify (reduce code size) of our code


```
 buildTypes {
        release {
            minifyEnabled true
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }
    }
```

we use it to obsfectd(hide implementation deatils) and minify (reduce code size) of our code
it will go over the code and throw code that is not in use
it will go over the code and change functions name for obsferction



### using progurd inside a library
consumerProguardFiles - the rules that are used when the code is consumed as a sub module in the project (app modulde that use library module in the same project)

proguardFiles - the rules that are used when compile the library - the compiled aar file is upload to the reposity






