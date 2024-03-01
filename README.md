# Wave SDK Unity Template

## Overview

**Unity 2021.3.35f1** template project for **Wave SDK 3.2.0** with fixed compatibility issues.

Tested on HTC Vive Focus Plus.

References:

* [Official Wave SDK 3.2.0][1]
* [Wave SDK 3.2.0 with fix for Unity 2021][2]
* [VIVE Wave SDK Developer Guide][3]

## Tips

### Android Manifest

`AndroidManifest.xml` located under `Assets\WaveVR\Platform\Android\AndroidManifest.xml`.

Check out official docs - [Configure App Capabilities][4].

### Disable controller pairing

To disable controller pairing pop-up menu, add this option to `AndroidManifest.xml`.

```xml
<meta-data android:name="no_controller_pairing" android:value="true" />
```

For example

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.unity3d.player"
    xmlns:tools="http://schemas.android.com/tools">
    <application android:icon="@drawable/app_icon"
                 android:label="@string/app_name"
                 android:theme="@style/Theme.WaveVR.Loading"
                 android:resizeableActivity="false"
				 tools:replace="android:theme">  <!--You can use your theme here.-->
        <activity android:name="com.htc.vr.unity.WVRUnityVRActivity"
                  android:label="@string/app_name"
				  android:configChanges="density|fontScale|keyboard|keyboardHidden|layoutDirection|locale|mnc|mcc|navigation|orientation|screenLayout|screenSize|smallestScreenSize|uiMode|touchscreen"
                  android:enableVrMode="@string/wvr_vr_mode_component">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
                <category android:name="com.htc.intent.category.VRAPP" />
            </intent-filter>
            <meta-data android:name="unityplayer.UnityActivity" android:value="true" />
            <meta-data android:name="unityplayer.SkipPermissionsDialog" android:value="true" />
        </activity>
        <meta-data android:name="no_controller_pairing" android:value="true" />
    </application>

    <!-- <uses-permission android:name="android.permission.CAMERA" /> -->
    <!-- <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" /> -->

    <uses-permission android:name="vive.wave.vr.oem.data.OEMDataRead" />
    <uses-permission android:name="vive.wave.vr.oem.data.OEMDataWrite" />
</manifest>
```

[1]: https://developer.vive.com/resources/vive-wave/download/archive/320
[2]: https://github.com/evgenii-d/ViveWaveSDK
[3]: https://hub.vive.com/storage/docs/en-us/UnityXR/UnityXRSdk.html
[4]: https://hub.vive.com/storage/app/doc/en-us/ConfigureAppCapabilities.html