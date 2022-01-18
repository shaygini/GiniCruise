id: app-development-gini-gradle
summary: gradle and build tools
authors: Shay markovich

# App develovment in android studio and using gradle

<!-- ------------------------ -->
##General
In this codelab you will learn about app stracture, how andoird build process is done, and how android studio use gradle to build the files

<!-- ------------------------ -->
##Creating new app

###Using android studio
In android studio press file - > create new App
Fill in app name, package name, location, language - Kotlin, and Minimum SDK, and press finish

###Examin the app
android studio created an app files lets look at the file stracture

> **_TIP:_**  to see hiden in finder files press Command + Shift + '.'

**hidden files:** 

`` .gitignore `` - file - This is the of the git source control - it says which files to ignore and not insert into the git, it usaly has the build folder, .idea folder and some other files, you can also see it inside the app folder where it has the build foler

`` .gradle/ `` - directory - This folder contails files gradle hidden files - using for gradle internal use

`` .idea/ `` - directory - This folder contails files of the idea (android studio) it has configurations and other definitions about the project

> **_TIP:_**  After download new project if the project donesn't complile you can try to delete the .idea folder and build folder and rebuild, this will recreate the project from start and can solve the prolbems, you can also use `` Invalidate Cashes \  Reset ...``

**About gradle**
Gradle help us to **build** our app and **manage dependencies**

**gradle files:**

Open each file and look at the content check what each files does

- settings.gradle - the main gradle project, contain all the gradle sub project (app module and libraries module)

```
include ':app'
```
- gradle.properties
- build.gradle (project)
    - buildscript - this are used during the build time - if you want to add plugin to the app add repositories to and claspath here under buildscript object
    - allProject - use this to definition for all subProjects


Each sub project (module) has its own build.gradle file


<!-- ------------------------ -->
## build.gradle

The app build.gradle include

```
plugins {
    id 'com.android.application'
    id 'kotlin-android'
}
```

The custom plugins costomize the build process and creating new gradle task that we can use

Plugin - **'com.android.application'** - This Android plugin add the ability to compile the app into android apk file

[app build process](https://developer.android.com/studio/build)
The build process convert your project into an Android Application Package (APK) or Android App Bundle (AAB)
[build digram](https://developer.android.com/images/tools/studio/build-process_2x.png)

During the build an apk is created with all the compile code your project including all the libraries and all the resouces

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

This is the android tag it used to tell the android plugin how to build the code
it contains 
- defult config like - compile ask, min sdk version code, version name, application id
- build types - release / debug
- flavours
- more option like compile option, kotlin option, build features


### Dependencies:
[dependency diagram](https://docs.gradle.org/current/userguide/img/dependency-management-resolution.png)

Dependencies:
We can add dependencies of several types:
- From repository
- SubProject
- jars or aar included in the project


#### Add file from repository:
```
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
```

dependencty from repository has the fallowing strature:

artifectGroup:artifectName:version

 - androidx.core **:** core-ktx **:** 1.7.0
    -- androidx.core - artifect group name
    --  core-ktx - artifect name
    -- 1.7.0 - artifect version

> **_TIP:_**  don't use '+' in the version name - when change dependency version name always check that the app still behaving as it should !!


#### Add file from subProject (module)
```
dependencies {
    ...
    
    implementation project('**:ProjectName**')

    // Or if you want to exclude some libraries
    implementation (project('')) {
        exclude ......
    }

}
```

#### Add local jar / aar file

inside app/build.gradle:
```
{
    repositories {
        flatDir {
            dirs 'libs'
        }
    }


    dependencies {
        ...
        // Adding xxx.aar file that is inside the app/libs folder
        implementation (name:'xxx', ext:'aar')
    }
}
```



<!-- ------------------------ -->
## Libraries

### Libraries as sub project
To create a library we will add gradle subProject with the **'com.android.library'** plugin (instead of the **'com.android.application'** plugin)
its artifect is an aar files,

It can be used by the app module by adding the subProject to the depedencies implementation:

#### Create new module:
In android studio:
* File -> New -> New Module ...
* Choose android library
* Press finish

### libraries to be used by other project
Somtimes we want to create libraries to be used by other project

In this senario we will publish the library and create artifect aar file that we will used by the  consumer, or publish the artifect directrly to remote repository like jfrog


#### Library dependncies - api vs implemenataion vs compile only

- `api` - the dependencis is visible to the consumer of the library
- `implemenation` - the dependencis is not visible to the consumer of the library
- `compileOnly` - the dependencis is visible to the consumer of the library and also is not added in the pom file, so the consumer need to add them indendetly

#### When develop library for external project 
- Try to avoid using dependenis as posible
- Make the library size small as posible
- When using progurd make sure the expose the necessary classes (see [using progurd](./#4) for more details)


#### Publish library 

Using the **'maven-publish'** plugin:

Add 'maven-publish' plugin

```
plugins {
    id 'maven-publish'
}
```

Add publishing configuration 

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

The Maven Publish plugin creates publishing tasks that you can use to publish your artifact to the repositories that you specify.

```
./gradlew clean build publish
```

> **_TIP:_**  You can publish the library to "maven local repository" - this is repository inside your computer in ~/.m2/repository, and you can use it if you add the repository MavenLocal()
```
./gradlew clean build publishToMavenLocal
```

**Note**
You can use the Jfrog plugin to publish directly to jforg repository 



<!-- ------------------------ -->
## Using proguard
Progurd is a tool that allowing code obsfectd (hide code implementation deatils) and minify (reduce code size)

```
 buildTypes {
        release {
            minifyEnabled true
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }
    }
```

We use it to obsfectd (hide implementation deatils) and minify (reduce code size) of our code
Use proguard-rules.pro file to tell progurd which class to keep



### using progurd inside a library
- 'consumerProguardFiles' - the rules that are used when the code is consumed as a sub module in the project (app modulde that use library module in the same project)
- 'proguardFiles' - the rules that are used when compile the library - the compiled aar file is upload to the reposity




<!-- ------------------------ -->
## Return to main
[return to main](../)

