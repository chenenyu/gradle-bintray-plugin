# gradle-bintray-plugin

> Publish your android/java libraries to bintray.

1. Add official bintray plugin.

```gradle
buildscript {
    repositories {
        google()
        jcenter()
    }
    dependencies {
        // classpath 'com.android.tools.build:gradle:x.y.z'
        classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.8.0'
    }
}
```

2. Config secret info in `local.properties`.

Note: this file shouldn't be included in vcs.
```
BINTRAY_USER=your bintray account
BINTRAY_API_KEY=your bintray api key
```

3. Config library info in `build.gradle`.

```gradle
ext {
    GROUP = 'com.example'  // required.
    ARTIFACT = 'library' // required.
    VERSION = 1.2.3 // required.
    BINTRAY_NAME = 'example-library' // optional. 
    VCS_URL = 'https://github.com/user/repo.git' // optional. 
    LICENSES = ['Apache-2.0'] // optional. 
    USER_ORG = 'user or org' // optional. 
    PUBLISH = true // optional. 
    OVERRIDE = false // optional. 
    DRYRUN = false // optional. 
    ...
}
```

4. apply script from remote.

`apply from: 'https://raw.githubusercontent.com/chenenyu/gradle-bintray-plugin/master/publish.gradle'`
