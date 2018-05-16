---
title: Adding Buttons
permalink: /instructions/adding-buttons/
layout: page
---

We're now going to start working on the game logic. Remember that in step 1 of the game, we have to be able to select either Rock, Paper or Scissors. We're going to start by setting up just a single button so that you can select rock 👊. Once everything is set up for rock, we will setup a button for paper and scissors as well.

## Setup up the first button

* Open the objects inspector on the right hand side of Xcode and find the `UIButton` object in the list. 
* Drag a button from the objects inspector onto the storyboard.
* Place the button in the middle of the screen.

![Screenshot of dragging the button](http://i.imgur.com/V0hfcnD.png)

* Select the attributes inspector on the right hand side of Xcode. Here is where you can modify the appearance of your button. 
* Change the title from 'button' to '👊'. 
* Use the arrow buttons next to the button's font to increase the font to a bigger size. 80 looks good. We may have to increase the size of the button to compensate for the large font size.

![Screenshot of button attributes](http://i.imgur.com/oy1MVuG.png)


## Link the button to the code

So far we've added a button to the screen. This looks great but if we run your app and tap on the button, it doesn't do anything. we're going to change this by connecting the button to the code.

* Make sure you're in the `main.storyboard` and open the Assistant editor. This opens up the swift code file that is linked to the screen with the button on it.

![Screenshot of assistant editor](http://i.imgur.com/YD8Ywl8.png)

* Now right click, or ctrl+click, and drag from the button into a space in the code file. You should see a blue line when you start dragging. 

![Screenshot of dragging the action](http://i.imgur.com/hdGYsYL.png)

* After you let go of your mouse, you will see a dialog box open up. Make sure that `action` is selected as the connection type, name your action `playRock`, and click `connect`. This will create a new function in your swift file.

![Screenshot of connecting an action](http://i.imgur.com/yC0A7Xy.png)

Now that we've made this connection, every time we tap on the button, the code inside this function will get run. But there is currently no code inside this function, so let's change that. 

* Add the following line of code inside your new function:

```swift
print("User selected 👊")
```

This will print out your selection to the console.

* Now run you app by clicking the play button in the top left corner of Xcode. 
* When the iPhone simulator appears on your screen, tap the rock button. You should see "User selected 👊" printed to your console.

We have now created a button in the storyboard using the visual helpers of the storyboard. We then connected this button to the code so you can perform some logic when a user taps the button. 


* Back: [Getting Started]({{ "/instructions/getting-started/" | relative_url }})
* Next: [Random Sign]({{ "/instructions/random-sign/" | relative_url }})