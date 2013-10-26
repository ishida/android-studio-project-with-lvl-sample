# Android Studio Project Sample With LVL

Android Studio project sample with LVL (License Verification Library / play_licensing)

## Installation

Download:

    $ git clone https://github.com/ishida/android-studio-project-with-lvl-sample

Import Project by Android Studio Menu > File > Import Project...

Get your android application licence key on Google Play Developer Console.  
Note that your application need to be paid one and be released.

Set the key into `MainActivity.BASE64_PUBLIC_KEY` in LVLSample/src/main/java/com/example/android/market/licensing/MainActivity.java.

Run LVLSample by Android Studio Menu > Run > Run LVLSample.  
If some issues are happened, try "Sync Project with Gradle Files" or "Rebuild Project" at Android Studio Menu

## How to import LVL to your project

Copy LicenseVerificationLibrary to Your Android Studio Project

    $ cp -r LVLSampleProject/LicenseVerificationLibrary YourAppProject/
    $ cd YourAppProject

Add codes into AndroidManifest.xml

    $ vi YourApp/src/main/AndroidManifest.xml

        <manifest
            ...

            <!-- Devices >= 3 have version of Android Market that supports licensing. -->
            <uses-sdk android:minSdkVersion="3" />
            <!-- Required permission to check licensing. -->
            <uses-permission android:name="com.android.vending.CHECK_LICENSE" />

            ...
        </manifest>

Add codes into YourApp/build.gradle

    $ vi YourApp/build.gradle

        dependencies {
            ...

            compile 'com.android.support:support-v4:+'
            compile project(':LicenseVerificationLibrary')

            ...
        }

Edit settings.gradle

    $ vi settings.gradle

        include ':YourApp', ':LicenseVerificationLibrary'

Click "Sync Project with Gradle Files" and "Rebuild Project" at Android Studio Menu.

Run YourApp by Android Studio Menu > Run > Run YourApp.