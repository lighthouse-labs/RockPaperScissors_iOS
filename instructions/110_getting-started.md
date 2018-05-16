---
title: Getting Started
permalink: /instructions/getting-started/
layout: page
---

Let's start by creating a new iOS app with Xcode.

* Create a new application in Xcode and select the `Single View Application` template.

![Screenshot of Xcode Single View](http://i.imgur.com/kDKFlGw.png)

* Name your application `RockPaperScissors`.
* Select `Swift` as the language.
* Set `iPhone` as the Device.
* Click `Next` then click `Create` to create the new project.

![Screenshot of Xcode New App](http://i.imgur.com/9OOyNie.png)

We now have a blank iOS app.

## Let's play with the Storyboard

* Open up the `main.storyboard` file and make sure you can see your view controller. This is the first screen that will appear when you run the app so you're going to start here.
* In the left hand side panel, expand the array next to `ViewController` and select the `View` object.
* Open the right hand side panel and make sure that the attributes inspector is selected. The attributes inspector is where you can modify the appearance of the view.
* Find the `Background` attribute for the view and select this attribute to change the the background color of the main view.

![Screenshot of the storyboard](http://i.imgur.com/gHPsmDE.png)

If you run your app right now, you will see a blank screen with whatever color you selected as its background. 

* Select the play button in the top left corner of Xcode to run your app on the simulator. Remember that the iPhone 7 Plus simulator is a little large so it's a better option to select the iPhone 7 as your simulator.

![Screenshot of the app running](http://i.imgur.com/z9LMbh9.png)

* Back: [Introduction]({{ "/instructions/introduction/" | relative_url }})
* Next: [Adding Buttons]({{ "/instructions/adding-buttons/" | relative_url }})