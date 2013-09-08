#Custom Crestron XPanel Android Application

##History
Since I couldn't find a native Android app for Crestron systems, I figured I might as well make my own. 
It was called HomeAutomationApp because that was the original purpose of the app for me, but it serverd as a generic Crestron Android app meant for customization to your needs. In the first version I made my own SIMPL module, but that did not allow multiple connections. Once I found an example of the CIP Crestron protocol on GitHub, I modified all the code to use that protocol instead.  I still couldnt find the whole protocol, so I implemented only the parts that were known. If you have the document, please send it to me and I can try to implement more features if they make sense.

###Android 4.0+
The current master branch is compatible with only Android 4+ devices as it uses a library instead of the custom viewflipper. It is also orientation locked, all which are changes that can be made in your [res](/CrestronXPanelApp/res) folder.

###Android 2.3
The first version was limited to a 800x480 Android 2.3.3 phone, however as things got newer and better (i.e. more mods released), I begun making updates to incorporate those added features. The current android 2.3 version is on its own branch, and will not receive any further updates from me.


##How It Works
With this app you can add buttons, seekbars, or textviews linked to the XPanel (eControl for PC) Digital/Analog/Serial inputs and outputs. All that is necessary is to update the [res](/CrestronXPanelApp/res) folder to include the images and layouts that you want for the app. 
###Quick Start
1. [Install the Android SDK](http://developer.android.com/sdk/installing/index.html)
2. Load the project and build ([First App?](http://developer.android.com/training/basics/firstapp/index.html))
3. Customize to your needs, changing only the contents of the [res](/CrestronXPanelApp/res) folder

###Operating
* Analog inputs - drag the seekbar (minor rounding issues may arise)
* Serial inputs - when updated from Crestron will update while the application is running
* Digital inputs - press and release
* Special keys - can mute/pause/play if a phone call comes in, or use the side keys
###Navigating
I incorporated the built in ViewPager (with TitleStrip) which allows you to "fling" on non-input items so that you can have multiple pages. The limitation is that you cannot fling on components, because you have to register a button down and up press which overrides the fling event handler.

![Sample Screen Shot](CrestronXPanelAppScreenShots.png)


##Configuring
* The IP, Port, and XPanel IDs are dynamic and can change in the app once you load it. Use the setting button on your phone to access the menu option and update your values
 * You may also choose to edit the [strings](/CrestronXPanelApp/res/values/strings.xml) file to your defaults
* The views need to be customized, use the examples [first](/CrestronXPanelApp/res/layouts/first.xml) | [second](/CrestronXPanelApp/res/layouts/second.xml) | [third](/CrestronXPanelApp/res/layouts/third.xml) as a starting point, and use the built in editor to make it look good
* To add or remove views, update the [res/xml/layouts](/CrestronXPanelApp/res/xml/layouts.xml) file
* Special keys supported:
 * mute = toggles when phone call received
 * pause/play = goes high (if needed) when phone call occurs - use the toggle in SIMPL feedback to aid
 * sideup/sidedown = connects the volume keys to a button

##Updating/Contributing
The src/libs folders are the only things that needs to change, you can copy/paste these as you go or use `ln -s` if you want to have the GitHub and your version using the same codebase (makes it easier to update while testing your application). Feature requests always welcome.

##More
I also have C# and Python (GLADE) versions of this app if you want a Windows/Mac/Linux mechanism to control your Crestron system. Let me know if you are interested or if you need help. 