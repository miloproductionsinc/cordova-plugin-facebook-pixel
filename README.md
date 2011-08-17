Facebook Connect PhoneGap Plugin
================================

This is the offical plugin for Facebook Connect in PhoneGap!

The Facebook Connect plugin for PhoneGap allows you to use the same JavaScript code in your web application as you 
use in your native PhoneGap application, but your native PhoneGap application will use the Facebook native app to 
perform single sign on (SSO) for the user.

This is all licensed under MIT except for app/www/facebook_js_sdk.js which is the Facebook JS SDK and is Apache 2.0.

Getting Started
---------------

Download the latest version of PhoneGap from www.phonegap.com.

Create an Android or iOS PhoneGap project -- those are the only platforms that the Facebook native application 
currently runs on :(

On Android you will need to put the following in your phonegap.xml / plugins.xml file:

<pre>
&lt;plugin name="com.facebook.phonegap.Connect" value="com.phonegap.facebook.Connect" /&gt;
</pre>

http://wiki.phonegap.com/How%20to%20Install%20a%20PhoneGap%20Plugin%20for%20Android

On iOS you will need to put the following in your PhoneGap.plist file:




http://wiki.phonegap.com/How%20to%20Install%20a%20PhoneGap%20Plugin%20for%20iOS





From the PhoneGap Facebook Connect Plugin folder copy the contents of the native/android/ folder into foobar/

From the PhoneGap Facebook Connect Plugin folder copy the app/www folder into foobar/assets/ overwriting the index.html and icon.png files but keeping the phonegap...js file.

From the PhoneGap Facebook Connect Plugin folder copy the www folder into foobar/assets/

From terminal in the foobar folder (with an android device attached to your computer) run the following command:

<pre>
ant debug install
</pre>


iOS (Mac OS X)
--------------

1. Make sure you've registered your Facebook app with Facebook, and have an **APP__ID** and **APP__SECRET**
2. Get the latest iOS source from [http://github.com/phonegap/phonegap-iphone](http://github.com/phonegap/phonegap-iphone) and read the README there about getting started with iOS.
3. Create a new Xcode project from the PhoneGap template that you created and installed (you did that if you read the README on github I hope).
4. From the **PhoneGap Facebook Connect Plugin** folder copy the contents of the **native/ios** folder into your app in Xcode (usually in the **Plugins** folder group). Make sure it is added as a "group" (yellow folder)
5. Modify the **APP_SECRET** value in **FacebookConnectPlugin.m** with your Facebook app's **APP__SECRET**
6. Find the PhoneGap.plist file in the project navigator, expand the "Plugins" sub-tree, and add a new entry. For the key, add **com.phonegap.facebook.Connect**, and its value will be **FacebookConnectPlugin**
7. From the **PhoneGap Facebook Connect Plugin** folder copy the contents of the **app/www** folder into the **www** directory in Xcode overwriting the index.html and icon.png files but keeping the phonegap.*.js file 
8. From the **PhoneGap Facebook Connect Plugin** folder copy the contents of the **lib** folder into the **www** directory in Xcode 
9. for Xcode 4, you will need to build it once, and heed the warning - this is an Xcode 4 template limitation. The warning instructions will tell you to drag copy the **www** folder into the project in Xcode (add as a **folder reference** which is a blue folder).
10. Under the group **Supporting Files**, find you **[PROJECTNAME]-Info.plist**, right-click on the file and select "Open As -> Source Code", add the **URL Scheme** from the section below (you will need your Facebook **APP_ID**)
11. Download the **Facebook iOS SDK** from [https://github.com/facebook/facebook-ios-sdk](https://github.com/facebook/facebook-ios-sdk) and put it into your project folder
12. Drag the **facebook-ios-sdk.xcodeproj** file into your project, this will create it as a sub-project
13. Click on your project's icon (the root element) in Project Navigator, select your **Target**, and the **Build Phases** tab.
14. From the **Build Phases** tab, expand **Target Dependencies**, then click on the **+** button
15. Add the build product from the **facebook-ios-sdk sub-project**
16. From the **Build Settings** tab, search for **Header Search Paths**
17. Add the value **/Users/Shared/PhoneGap/Frameworks/PhoneGap.framework/Headers**
18. From the **facebook-ios-sdk.xcodeproj** sub-project, drag out the **FBConnect** folder into your project's **Plugins** folder, and add it as a group (yellow folder).
19. From your **Plugins/FBConnect** folder, remove the **JSON** folder (remove reference only)
20. Run the application in Xcode.

iOS URL Scheme
-----------

Make sure you add the scheme to your [PROJECTNAME]-Info.plist (located as one of the files in your Xcode project), substitute [APP_ID] and [SCHEME_ID] below to the appropriate values. This is to handle the re-direct from Mobile Safari or the Facebook app, after permission authorization.

* [**SCHEME_ID**] is usually a unique identifier for the scheme, in reverse domain name notation (i.e com.facebook.phonegap.myscheme)
* [**APP_ID**] is the Facebook app id given by Facebook

<pre>
&lt;key&gt;CFBundleURLTypes&lt;/key&gt;
&lt;array&gt;
	&lt;dict&gt;
		&lt;key&gt;CFBundleURLName&lt;/key&gt;
		&lt;string&gt;[SCHEME_ID]&lt;/string&gt;
		&lt;key&gt;CFBundleURLSchemes&lt;/key&gt;
		&lt;array&gt;
			&lt;string&gt;fb[APP_ID]&lt;/string&gt;
		&lt;/array&gt;
	&lt;/dict&gt;
&lt;/array&gt;
</pre>
