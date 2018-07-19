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
    VERSION = '1.2.3' // required.
    ...
}
```

4. apply script from remote.

`apply from: 'https://raw.githubusercontent.com/chenenyu/gradle-bintray-plugin/master/publish.gradle'`

## Support params

| name         | type                                     | meaning                                  | required |
| ------------ | ---------------------------------------- | ---------------------------------------- | -------- |
| GROUP        | String                                   | group id                                 | yes      |
| ARTIFACT     | String                                   | artifact id                              | yes      |
| VERSION      | String                                   | version                                  | yes      |
| AAR_ARTIFACT | The following types/formats are supported: <br>  - Instances of MavenArtifact. <br>  - Instances of AbstractArchiveTask, for example jar. <br>  - Instances of PublishArtifact <br>  - Maps containing a 'source' entry, for example [source: '/path/to/file', extension: 'zip']. <br>  - Anything that can be converted to a file, as per Project.file() <br>See `org.gradle.api.publish.maven.MavenPublication` | Specify the aar artifact.                |          |
| BINTRAY_NAME | String                                   | The bintray repo name which you upload library to. default to **ARTIFACT**. |          |
| BINTRAY_REPO | String                                   | Repo type. default to 'maven'.           |          |
| VCS_URL      | String                                   | Such as 'https://github.com/user/repo.git'. default to ''. |          |
| LICENSES     | String[]                                 | ['Apache-2.0']                           |          |
| USER_ORG     | String                                   | Upload to user or org. default to  **BINTRAY_USER**. |          |
| PUBLISH      | boolean                                  | Whether to publish or not after upload. default to trute. |          |
| OVERRIDE     | boolean                                  | Override the remote library if current version exists. |          |
| DRYRUN       | boolean                                  | Just dry run, not upload.                |          |

