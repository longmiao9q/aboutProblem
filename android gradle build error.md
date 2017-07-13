# 本章记录了在使用 gradle build project时候的常见错误以及 解决办法

### Problem information
> \build\intermediates\res\resources-anzhi-debug-stripped.ap_' specified for property 'resourceFile' does not exist

### reason
Android Plugin for Gradle 2.2(and above) seems to hava a bug with shrinkResource

### soulucion
对于Android Studio 2.2及以上:
```
    buildTypes {
        release {
            signingConfig signingConfigs.release
            minifyEnabled false
            shrinkResources false
            zipAlignEnabled true
            debuggable false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
    }
}
```

### problem information
Installation error: INSTALL_PARSE_FAILED_NO_CERTIFICATES

### reason
Every Android .apk needs to be signed if it is going to be installed on a phone

### solution
for gradle assemableRelease build
```
signingConfigs {
        releaseConfig {
            keyAlias 'android.keystore'
            storeFile file("android.keystore")
            keyPassword '123456'
            storePassword '123456'
        }
    }
```