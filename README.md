<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    android:versionCode="2"
    android:versionName="2"
    android:compileSdkVersion="34"
    android:compileSdkVersionCodename="14"
    package="devsylnet.pinik.proxy"
    platformBuildVersionCode="34"
    platformBuildVersionName="14">
    <uses-sdk
        android:minSdkVersion="23"
        android:targetSdkVersion="34" />
    <!-- Have full network access -->
    <uses-permission android:name="android.permission.INTERNET" />
    <!-- View network connections -->
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <!-- View Wi-Fi connections -->
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <!-- Use certificate -->
    <uses-permission android:name="android.permission.USE_CREDENTIALS" />
    <!-- Read the contents of your shared storage -->
    <uses-permission
        android:name="android.permission.READ_EXTERNAL_STORAGE"
        android:maxSdkVersion="32" />
    <!-- Control vibration -->
    <uses-permission android:name="android.permission.VIBRATE" />
    <!-- Modify or delete the contents of your shared storage -->
    <uses-permission
        android:name="android.permission.WRITE_EXTERNAL_STORAGE"
        android:maxSdkVersion="28" />
    <!-- Close other apps -->
    <uses-permission android:name="android.permission.KILL_BACKGROUND_PROCESSES" />
    <!-- Run at startup -->
    <uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />
    <!-- Prevent phone from sleeping -->
    <uses-permission android:name="android.permission.WAKE_LOCK" />
    <!-- Install shortcuts -->
    <uses-permission android:name="com.android.launcher.permission.INSTALL_SHORTCUT" />
    <!-- Run foreground service -->
    <uses-permission android:name="android.permission.FOREGROUND_SERVICE" />
    <!-- Show notifications -->
    <uses-permission android:name="android.permission.POST_NOTIFICATIONS" />
    <!-- Run foreground service -->
    <uses-permission android:name="android.permission.FOREGROUND_SERVICE" />
    <!-- Run foreground service with the type "specialUse" -->
    <uses-permission android:name="android.permission.FOREGROUND_SERVICE_SPECIAL_USE" />
    <supports-screens
        android:anyDensity="true"
        android:smallScreens="true"
        android:normalScreens="true"
        android:largeScreens="true"
        android:resizeable="true"
        android:xlargeScreens="true" />
    <uses-permission android:name="com.google.android.gms.permission.AD_ID" />
    <uses-permission android:name="android.permission.ACCESS_ADSERVICES_AD_ID" />
    <uses-permission android:name="android.permission.ACCESS_ADSERVICES_ATTRIBUTION" />
    <uses-permission android:name="android.permission.ACCESS_ADSERVICES_TOPICS" />
    <queries>
        <intent>
            <action android:name="android.intent.action.VIEW" />
            <category android:name="android.intent.category.BROWSABLE" />
            <data android:scheme="https" />
        </intent>
        <intent>
            <action android:name="android.support.customtabs.action.CustomTabsService" />
        </intent>
    </queries>
    <permission
        android:name="devsylnet.pinik.proxy.DYNAMIC_RECEIVER_NOT_EXPORTED_PERMISSION"
        android:protectionLevel="signature" />
    <uses-permission android:name="devsylnet.pinik.proxy.DYNAMIC_RECEIVER_NOT_EXPORTED_PERMISSION" />
    <!-- Reorder running apps -->
    <uses-permission android:name="android.permission.REORDER_TASKS" />
    <application
        android:theme="@style/AppTheme"
        android:label="@string/app_name"
        android:icon="@drawable/ic_launcher"
        android:name="com.tknetwork.tunnel.activities.OpenVPNApplication"
        android:excludeFromRecents="true"
        android:allowBackup="true"
        android:supportsRtl="true"
        android:extractNativeLibs="true"
        android:usesCleartextTraffic="true"
        android:appCategory="productivity"
        android:appComponentFactory="androidx.core.app.CoreComponentFactory"
        android:requestLegacyExternalStorage="true">
        <uses-library
            android:name="org.apache.http.legacy"
            android:required="false" />
        <activity
            android:theme="@style/AppTheme.NoActionBar"
            android:name="com.tknetwork.tunnel.activities.LauncherActivity"
            android:exported="true"
            android:windowSoftInputMode="adjustPan|stateHidden">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        <activity
            android:label="VPN Killer"
            android:name="com.tknetwork.tunnel.activities.VpnKiller"
            android:exported="true" />
        <service
            android:name="com.tknetwork.tunnel.service.OpenVPNService"
            android:permission="android.permission.BIND_VPN_SERVICE"
            android:exported="false"
            android:foregroundServiceType="specialUse">
            <intent-filter>
                <action android:name="android.net.VpnService" />
            </intent-filter>
        </service>
        <activity
            android:name="com.tknetwork.tunnel.activities.v2raySettingsActivity"
            android:exported="true" />
        <service
            android:label="V2RayVpnService"
            android:name="com.v2ray.ang.service.V2RayVpnService"
            android:permission="android.permission.BIND_VPN_SERVICE"
            android:enabled="true"
            android:exported="false"
            android:foregroundServiceType="specialUse">
            <intent-filter>
                <action android:name="android.net.VpnService" />
            </intent-filter>
            <meta-data
                android:name="android.net.VpnService.SUPPORTS_ALWAYS_ON"
                android:value="true" />
            <property
                android:name="android.app.PROPERTY_SPECIAL_USE_FGS_SUBTYPE"
                android:value="vpn" />
        </service>
        <service
            android:label="V2RayProxyOnlyService"
            android:name="com.v2ray.ang.service.V2RayProxyOnlyService"
            android:exported="false"
            android:process=":RunSoLibV2RayDaemon"
            android:foregroundServiceType="specialUse" />
        <service
            android:name="com.tknetwork.tunnel.utils.TimerService"
            android:foregroundServiceType="specialUse" />
        <service
            android:name="com.tknetwork.tunnel.service.TunnelVPN"
            android:foregroundServiceType="specialUse" />
        <service
            android:name="com.tknetwork.tunnel.service.c_06"
            android:foregroundServiceType="specialUse" />
        <activity
            android:label="Logs"
            android:name="com.tknetwork.tunnel.logger.JcLogs"
            android:parentActivityName="com.tknetwork.tunnel.activities.ActivityUi" />
        <activity
            android:label="About"
            android:name="com.tknetwork.tunnel.activities.AboutActivity"
            android:parentActivityName="com.tknetwork.tunnel.activities.ActivityUi" />
        <activity
            android:label="WI-FI Tethering"
            android:name="com.tknetwork.tunnel.wifi.MainActivityWifi"
            android:parentActivityName="com.tknetwork.tunnel.activities.ActivityUi"
            android:foregroundServiceType="specialUse" />
        <service
            android:name="com.tknetwork.tunnel.wifi.ProxyService"
            android:permission="android.permission.BIND_VPN_SERVICE"
            android:enabled="true"
            android:exported="false"
            android:foregroundServiceType="specialUse" />
        <receiver
            android:name="com.tknetwork.tunnel.core.MainReceiver"
            android:exported="false">
            <intent-filter>
                <action android:name="com.tknetwork.tunnel.vpn.core.MainReceiver.ACTION_SERVICE_STOP" />
                <action android:name="com.tknetwork.tunnel.vpn.core.MainReceiver.ACTION_SERVICE_RESTART" />
            </intent-filter>
        </receiver>
        <activity
            android:theme="@style/AppTheme.NoActionBar"
            android:name="com.tknetwork.tunnel.activities.ActivityUi"
            android:launchMode="singleTask"
            android:windowSoftInputMode="adjustPan|stateHidden" />
        <activity android:name="com.tknetwork.tunnel.activities.OpenVPNPrefs" />
        <activity android:name="com.tknetwork.tunnel.view.FileDialog" />
        <activity
            android:theme="@android:style/Theme.NoDisplay"
            android:name="com.tknetwork.tunnel.activities.OpenVPNDisconnect" />
        <activity
            android:label="Logs"
            android:name="com.tknetwork.tunnel.activities.LogActivity"
            android:parentActivityName="com.tknetwork.tunnel.activities.ActivityUi" />
        <activity
            android:label="Privacy"
            android:name="com.tknetwork.tunnel.activities.PrivacyActivity"
            android:parentActivityName="com.tknetwork.tunnel.activities.ActivityUi" />
        <activity
            android:label="Login"
            android:name="com.tknetwork.tunnel.activities.LoginActivity"
            android:parentActivityName="com.tknetwork.tunnel.activities.ActivityUi" />
        <activity
            android:label="Application Error"
            android:name="com.tknetwork.tunnel.activities.ExceptionActivity"
            android:foregroundServiceType="specialUse" />
        <activity
            android:label="Panel"
            android:name="com.tknetwork.tunnel.activities.ResellerPanelActivity"
            android:parentActivityName="com.tknetwork.tunnel.activities.ActivityUi" />
        <activity
            android:label="Options"
            android:name="com.tknetwork.tunnel.activities.SshActivity"
            android:parentActivityName="com.tknetwork.tunnel.activities.ActivityUi" />
        <activity
            android:label="Networks"
            android:name="com.tknetwork.tunnel.activities.NetworkActivity"
            android:parentActivityName="com.tknetwork.tunnel.activities.ActivityUi" />
        <activity
            android:label="Servers"
            android:name="com.tknetwork.tunnel.activities.ServerActivity"
            android:parentActivityName="com.tknetwork.tunnel.activities.ActivityUi" />
        <meta-data
            android:name="com.google.android.gms.ads.APPLICATION_ID"
            android:value="ca-app-pub-8083717080317651~3846338751" />
        <activity
            android:theme="@style/AppTheme.NoActionBar"
            android:label="Import Config"
            android:name="com.tknetwork.tunnel.activities.ExportActivity"
            android:exported="true"
            android:excludeFromRecents="true"
            android:launchMode="singleTask"
            android:noHistory="true"
            android:parentActivityName="com.tknetwork.tunnel.activities.ActivityUi">
            <intent-filter>
                <action android:name="android.intent.action.VIEW" />
                <category android:name="android.intent.category.DEFAULT" />
                <data android:scheme="file" />
                <data android:scheme="content" />
                <data android:host="*" />
                <data android:mimeType="*/*" />
                <data android:pathPattern=".*.pinikproxy" />
                <data android:pathPattern=".*..*.pinikproxy" />
                <data android:pathPattern=".*..*..*.pinikproxy" />
                <data android:pathPattern=".*..*..*..*.pinikproxy" />
                <data android:pathPattern=".*..*..*..*..*.pinikproxy" />
                <data android:pathPattern=".*..*..*..*..*..*.pinikproxy" />
                <data android:pathPattern=".*..*..*..*..*..*..*.pinikproxy" />
                <data android:pathPattern=".*..*..*..*..*..*..*..*.pinikproxy" />
                <data android:pathPattern=".*..*..*..*..*..*..*..*..*.pinikproxy" />
                <data android:pathPattern=".*..*..*..*..*..*..*..*..*..*.pinikproxy" />
                <data android:pathPattern=".*..*..*..*..*..*..*..*..*..*..*.pinikproxy" />
            </intent-filter>
        </activity>
        <service
            android:name="app.tunnel.ssh2.tunnel.vpn.TunnelVpnService"
            android:permission="android.permission.BIND_VPN_SERVICE"
            android:enabled="true"
            android:exported="false">
            <intent-filter>
                <action android:name="android.net.VpnService" />
            </intent-filter>
        </service>
        <service
            android:name="app.tunnel.vpncommons.auth.AuthService"
            android:exported="false" />
        <activity
            android:theme="@android:style/Theme.Translucent.NoTitleBar"
            android:name="com.google.android.gms.common.api.GoogleApiActivity"
            android:exported="false" />
        <activity
            android:theme="@android:style/Theme.Translucent"
            android:name="com.google.android.gms.ads.AdActivity"
            android:exported="false"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize|smallestScreenSize|uiMode" />
        <provider
            android:name="com.google.android.gms.ads.MobileAdsInitProvider"
            android:exported="false"
            android:authorities="devsylnet.pinik.proxy.mobileadsinitprovider"
            android:initOrder="100" />
        <service
            android:name="com.google.android.gms.ads.AdService"
            android:enabled="true"
            android:exported="false" />
        <activity
            android:name="com.google.android.gms.ads.OutOfContextTestingActivity"
            android:exported="false"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize|smallestScreenSize|uiMode" />
        <activity
            android:theme="@android:style/Theme.Translucent.NoTitleBar"
            android:name="com.google.android.gms.ads.NotificationHandlerActivity"
            android:exported="false"
            android:taskAffinity=""
            android:excludeFromRecents="true"
            android:launchMode="singleTask" />
        <property
            android:name="android.adservices.AD_SERVICES_CONFIG"
            android:resource="@xml/gma_ad_services_config" />
        <meta-data
            android:name="com.google.android.gms.version"
            android:value="@integer/google_play_services_version" />
        <provider
            android:name="androidx.startup.InitializationProvider"
            android:exported="false"
            android:authorities="devsylnet.pinik.proxy.androidx-startup">
            <meta-data
                android:name="androidx.emoji2.text.EmojiCompatInitializer"
                android:value="androidx.startup" />
            <meta-data
                android:name="androidx.work.WorkManagerInitializer"
                android:value="androidx.startup" />
            <meta-data
                android:name="androidx.lifecycle.ProcessLifecycleInitializer"
                android:value="androidx.startup" />
            <meta-data
                android:name="androidx.profileinstaller.ProfileInstallerInitializer"
                android:value="androidx.startup" />
        </provider>
        <service
            android:name="androidx.work.impl.background.systemalarm.SystemAlarmService"
            android:enabled="@bool/enable_system_alarm_service_default"
            android:exported="false"
            android:directBootAware="false" />
        <service
            android:name="androidx.work.impl.background.systemjob.SystemJobService"
            android:permission="android.permission.BIND_JOB_SERVICE"
            android:enabled="@bool/enable_system_job_service_default"
            android:exported="true"
            android:directBootAware="false" />
        <service
            android:name="androidx.work.impl.foreground.SystemForegroundService"
            android:enabled="@bool/enable_system_foreground_service_default"
            android:exported="false"
            android:directBootAware="false" />
        <receiver
            android:name="androidx.work.impl.utils.ForceStopRunnable$BroadcastReceiver"
            android:enabled="true"
            android:exported="false"
            android:directBootAware="false" />
        <receiver
            android:name="androidx.work.impl.background.systemalarm.ConstraintProxy$BatteryChargingProxy"
            android:enabled="false"
            android:exported="false"
            android:directBootAware="false">
            <intent-filter>
                <action android:name="android.intent.action.ACTION_POWER_CONNECTED" />
                <action android:name="android.intent.action.ACTION_POWER_DISCONNECTED" />
            </intent-filter>
        </receiver>
        <receiver
            android:name="androidx.work.impl.background.systemalarm.ConstraintProxy$BatteryNotLowProxy"
            android:enabled="false"
            android:exported="false"
            android:directBootAware="false">
            <intent-filter>
                <action android:name="android.intent.action.BATTERY_OKAY" />
                <action android:name="android.intent.action.BATTERY_LOW" />
            </intent-filter>
        </receiver>
        <receiver
            android:name="androidx.work.impl.background.systemalarm.ConstraintProxy$StorageNotLowProxy"
            android:enabled="false"
            android:exported="false"
            android:directBootAware="false">
            <intent-filter>
                <action android:name="android.intent.action.DEVICE_STORAGE_LOW" />
                <action android:name="android.intent.action.DEVICE_STORAGE_OK" />
            </intent-filter>
        </receiver>
        <receiver
            android:name="androidx.work.impl.background.systemalarm.ConstraintProxy$NetworkStateProxy"
            android:enabled="false"
            android:exported="false"
            android:directBootAware="false">
            <intent-filter>
                <action android:name="android.net.conn.CONNECTIVITY_CHANGE" />
            </intent-filter>
        </receiver>
        <receiver
            android:name="androidx.work.impl.background.systemalarm.RescheduleReceiver"
            android:enabled="false"
            android:exported="false"
            android:directBootAware="false">
            <intent-filter>
                <action android:name="android.intent.action.BOOT_COMPLETED" />
                <action android:name="android.intent.action.TIME_SET" />
                <action android:name="android.intent.action.TIMEZONE_CHANGED" />
            </intent-filter>
        </receiver>
        <receiver
            android:name="androidx.work.impl.background.systemalarm.ConstraintProxyUpdateReceiver"
            android:enabled="@bool/enable_system_alarm_service_default"
            android:exported="false"
            android:directBootAware="false">
            <intent-filter>
                <action android:name="androidx.work.impl.background.systemalarm.UpdateProxies" />
            </intent-filter>
        </receiver>
        <receiver
            android:name="androidx.work.impl.diagnostics.DiagnosticsReceiver"
            android:permission="android.permission.DUMP"
            android:enabled="true"
            android:exported="true"
            android:directBootAware="false">
            <intent-filter>
                <action android:name="androidx.work.diagnostics.REQUEST_DIAGNOSTICS" />
            </intent-filter>
        </receiver>
        <uses-library
            android:name="androidx.window.extensions"
            android:required="false" />
        <uses-library
            android:name="androidx.window
