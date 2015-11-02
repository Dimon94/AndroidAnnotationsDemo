#AndroidAnnotations框架的Demo
开源框架个人学习Demo   :)

My Version:
> targetSDKversion 22 + compileSdkVersion 22 + buildToolsVersion "22.0.1"

> IDEVersion：Android Studio 1.4.1


**EDIT**

Sharing build.gradle

    apply plugin: 'com.android.application'
    apply plugin: 'android-apt'
    def AAVersion = '3.3.2'
    android {
        compileSdkVersion 22
        buildToolsVersion "22.0.1"

        defaultConfig {
            applicationId "com.dimon.org.androidannotation"
            minSdkVersion 19
            targetSdkVersion 22
            versionCode 1
            versionName "1.0"
        }
        buildTypes {
            release {
                minifyEnabled false
                proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
            }
        }
    }

    dependencies {
        compile fileTree(dir: 'libs', include: ['*.jar'])
        testCompile 'junit:junit:4.12'
        compile 'com.android.support:appcompat-v7:22.2.1'
        apt "org.androidannotations:androidannotations:$AAVersion"
        compile "org.androidannotations:androidannotations-api:$AAVersion"
    }
    apt {
        arguments {
            androidManifestFile variant.outputs[0].processResources.manifestFile
            resourcePackageName 'com.dimon.org.androidannotation'
        }
    }

**EDIT2**

Root build.gradle


    buildscript {
        repositories {
            jcenter()
        }
        dependencies {
            classpath 'com.android.tools.build:gradle:1.3.0'
            classpath 'com.neenbedankt.gradle.plugins:android-apt:1.4'
            // NOTE: Do not place your application dependencies here; they belong
            // in the individual module build.gradle files
        }
    }

    allprojects {
        repositories {
            jcenter()
        }
    }

    task clean(type: Delete) {
        delete rootProject.buildDir
    }

###END