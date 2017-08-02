Add the SDK as a JAR library
============================

If you're running an environment which does not support Gradle, then you'll need to add the SDK manually.

First download and extract the following archive `SuperAwesomeAdvertiserSDK-<sdk_version>.Android.jars.zip <https://github.com/SuperAwesomeLTD/sa-sdk-build-repo/blob/master/package/adv_android/<sdk_version>/SuperAwesomeAdvertiserSDK-<sdk_version>.Android.jars.zip?raw=true>`_

The archive will contain a number of .jar files, representing the components of the SDK that you'll need to add to the **lib** folder in your Android project.

Then, add the following items in your *AndroidManifest.xml* file, under the Application tag:

.. code-block:: xml

    <service  android:name="tv.superawesome.lib.sanetwork.asynctask.SAAsyncTask$SAAsync"
              android:exported="false"
              android:permission="tv.superawesome.sdk.SuperAwesomeSDK"/>

    <receiver android:name="tv.superawesome.sdk.advertiser.SAVerifyInstall"
              android:exported="false"
              android:permission="tv.superawesome.sdk.SuperAwesomeSDK">
              <intent-filter>
                <action android:name="com.android.vending.INSTALL_REFERRER"/>
              </intent-filter>
    </receiver>

This will register one service and one receiver for your application, all needed by the SDK.

Also, add the following permissions to your AndroidManifest.xml file:

.. code-block:: xml

    <uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />

Once you've added the Android Advertiser SDK, you can access all functionality by including:

.. code-block:: java

    import tv.superawesome.sdk.advertiser.*;
