The HockeySDK for Windows Phone allows users to send crash reports right from within the application. When your app crashes, a file with basic information about the environment (device type, OS version, etc.), the reason and the stacktrace of the exception is created. Then the apps is killed. The next time the user starts the app, he is asked to send the crash data to the developer. If he confirms the dialog, the crash log is sent to HockeyApp and then the file deleted from the device.

An example integration can be found [here](https://github.com/codenauts/HockeyAppTweets-WP7). The example app loads all tweets from the HockeyApp account. A crash can be provokoed by tapping the third row.

## Requirements

* Windows Phone SDK 7.1
* Visual Studio 2010

## Import Library

* Download the latest version of [HockeySDK-WindowsPhone](https://github.com/codenauts/HockeySDK-WindowsPhone/downloads).
* Unzip the file.
* Copy the HockeySDK.dll to your project directory.
* Open your solution in Visual Studio.
* Right-click the group "References" and select "Add Reference".
* Choose the tab "Browse", search for the HockeySDK.dll and confirm with OK. 

## Modify Code

* Open your App.xaml.cs
* Search the method "App" and add the following line at the top of the method:<pre>HockeyApp.CrashHandler.Instance.Configure(this, APP_ID);</pre>
* Replace APP_ID with the App ID of your app on HockeyApp.
* Open the root page of your app (or the page in which you want to check for new crashes), for example MainPage.xaml.cs.
* Search the method "Initialize" and add the following line at the bottom:<pre>HockeyApp.CrashHandler.Instance.HandleCrashes();</pre>
* Run your app from Visual Studio (menu Debug > Start Debugging).
* Stop your app to detach the debugger.
* Start your app from the home screen or the list of apps.

Now every time when an unhandled exception occurs, the app is killed. At the next start, you should be asked to send the crash data.

## Support

If you have any questions, problems or suggestions, please contact us at [support@hockeyapp.net](mailto:support@hockeyapp.net).