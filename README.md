# this just android version doesn't encloud IOS - admob-for-flash-android
this is admob for flash android ANE and it is a personnel update to  " lilili87222 / admob-for-flash  ANE"


Admob ANE for Flash Air
==============================
0. [Change log](#change-log)   
	1.[Interstitial changes](#1interstitial-changes)     
	2.[Rewarded video changes](#2rewarded-video-changes)    



1. [Admob ANE Description](#admob-ane-description)
2. [Admob ANE For Air Features](#admob-ane-for-air-features)
3. [Quick Start](#quick-start)    
	1.[Init Admob ANE ](#1init-admob-ane)     
	2.[Add Admob Banner in adobe Air App](#2add-admob-banner-in-adobe-air-app)      
	3.[Remove Banner](#3remove-banner)    
	4.[Admob ANE Show Interstitial](#4admob-ane-show-interstitial )     
	5.[Set Admob Target Param](#5set-admob-target-param)    
        6.[Admob Rewarded Video](#6admob-rewarded-video)       
	7.[android permission config](#7android-permission-config)    
	8.[Screen size function](#8screen-size-function)    
	9.[ANE ID](#9ane-id)    
4. [Screenshots](#screenshots)
5. [Links](#links)
6. [License](#license)

## Change-log
#### 1.Interstitial changes

 "isInterstitialReady()" is now back and you can use it again to check if interstitial is loaded.
```
     if (Admob.getInstance().isInterstitialReady()) {
      Admob.getInstance().showInterstitial();
     }

```


#### 2.Rewarded video changes
"isVideoReady()" is now back and you can use it again to check if Rewarded ad is loaded.
```
      if(Admob.getInstance().isVideoReady())
         {
            Admob.getInstance().showVideo();
         }

```




## Admob ANE Description
Admob Air Native Extention(Admob ANE) provides a way to integrate admob ads in Air Android Game and app.
You can use it for Android App with the same actionscript  code,not need any change ,not need java
or oc.

The Google Mobile Ads SDK is the latest generation in Google mobile advertising featuring refined ad formats and streamlined APIs for access to mobile ad networks and advertising solutions. The SDK enables Air mobile app developers to maximize their monetization in native mobile apps.





## Admob ANE For Air Features

- [x] Support banner(All Banner Sizes)
- [x] Support Intersitial
- [x] Support Rewarded Video
- [x] Support landscape and portrait  and autoOrient
- [x] Support AdRequest targeting methods,such as children target,test mode
- [x] Support Air SDK 32 and Air 33
- [x] Very simple API
- [x] Support android x64,x86,arm，and 32,64 bit support


## Quick Start
#### 1.Init Admob ANE 
Add Admob ane to air project build path , add the follow code in the script file
```
    import so.cuo.platform.admob.*;
    Admob.getInstance().initAdmobSDK(new ExtraParameter());

```
#### 2.Add Admob Banner in adobe Air App 
Here is the minimal code needed to show admob banner.
```

    Admob.getInstance().showBanner("your banner ID ",AdmobSize.SMART_BANNER,AdmobPosition.BOTTOM_CENTER);


```

The AdmobPosition class specifies where to place the banner. AdmobSize specifies witch size banner to show

#### 3.Remove Banner 
By default, banners are visible. To  hide a banner,
```
    Admob.getInstance().hideBanner();
```


#### 4.Admob ANE Show Interstitial 
How to integrate Interstitial into Air flex android app?
Here is the minimal  code to create an interstitial.
```
    Admob.getInstance().cacheInterstitial("your Interstitial ID "); 
```
show interstitials.
```
  
       if (Admob.getInstance().isInterstitialReady()) {
      Admob.getInstance().showInterstitial();
    }
    
```


#### 5.Set Admob Target Param
set Admob target param such as test Ads and children app
If you want to test the ads or the your app with children target,you can set with admob ANE easy
```
       extraParam=new ExtraParameter();
	extraParam.testDeviceID="true";
	extraParam.isChildApp=true;//if is tagForChildDirectedTreatment,set true
        extraParam.nonPersonalizedAds=true;//if want to load non Personalized ads set true
	Admob.getInstance().showBanner("Your banner ID",AdmobSize.BANNER_320x50,AdmobPosition.BOTTOM_CENTER,80,extraParam);
```


#### 6.Admob Rewarded Video
 _Video_ api is similar with _Interstitial_ 
    
Here the setting to load a video:
```
	Admob.getInstance().cacheVideo(videoID);

Here the setting to show video:
```

	if(Admob.getInstance().isVideoReady())
         {
            Admob.getInstance().showVideo();
         }



   





### 7.android permission config
Meta Config com.google.android.gms.ads.APPLICATION_ID  is required from admob 17
Please replace ca-app-pub-3940256099942544~3347511713 with your admob ID
```
<android>
        <manifestAdditions><![CDATA[
			<manifest android:installLocation="auto">
					<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
					<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
					<uses-permission android:name="android.permission.READ_PHONE_STATE"/>
					<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
					<uses-permission android:name="com.google.android.finsky.permission.BIND_GET_INSTALL_REFERRER_SERVICE" />
					 <application>
						<meta-data android:name="com.google.android.gms.version" android:value="@integer/google_play_services_version" />
					      <activity android:name="com.google.android.gms.ads.AdActivity" android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" android:theme="@android:style/Theme.Translucent"/>
						<receiver android:name="com.google.android.gms.measurement.AppMeasurementReceiver" android:enabled="true" android:exported="false" ></receiver>
					       <receiver android:name="com.google.android.gms.measurement.AppMeasurementInstallReferrerReceiver" android:enabled="true" android:exported="true" android:permission="android.permission.INSTALL_PACKAGES" >
							<intent-filter>
							    <action android:name="com.android.vending.INSTALL_REFERRER" />
							</intent-filter>
					        </receiver>

					        <service android:name="com.google.android.gms.measurement.AppMeasurementService" android:enabled="true" android:exported="false" />
					        <service android:name="com.google.android.gms.measurement.AppMeasurementJobService" android:enabled="true" android:exported="false" android:permission="android.permission.BIND_JOB_SERVICE" />
					        <receiver android:name="com.google.android.gms.measurement.AppMeasurementReceiver" android:enabled="true" android:exported="false" ></receiver>

					        <service android:name="com.google.android.gms.measurement.AppMeasurementService" android:enabled="true" android:exported="false" />
						  <meta-data android:name="com.google.android.gms.ads.APPLICATION_ID" android:value="ca-app-pub-3940256099942544~3347511713"/>
					</application>
			</manifest>

		]]></manifestAdditions>
    </android>
```

### 8.Screen size function
this will get  screen size ,unit is dp
```
Admob.getInstance().getScreenSize()

```

### 9.ANE ID
```
<extensionID>so.cuo.platform.admob</extensionID>
```

## version 20220727
1.update admob sdk to 21.0.0    




## Screenshots
![ScreenShot](https://github.com/lilili87222/admob-for-flash/blob/master/images/screen.jpg?raw=true)



This Admob ANE  was a monetization ANE plugin for Flash Air community,More people use, making the api more friendly,the plugin more stable.Thank you for feedback questions and provide advice, thank you for the support and donations.

## Links

Download lilili87222 ane  https://github.com/lilili87222/admob-for-flash/archive/master.zip    
Download nboy1 updated ane  [https://github.com/nboy1/admob-for-flash-android-GMA-21.0.0]    
admob http://apps.admob.com    

## License
[Apache 2.0 License](http://www.apache.org/licenses/LICENSE-2.0.html)

