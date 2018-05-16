---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---


# 👊 ✋ ✌️

We are going to get introduced to the fundamentals of building mobile applications using some of the most prominent and widely used programming technologies! In this guide, we will use Swift and Xcode to create a very simple rock paper scissors game for iOS.

## The App

The app will consist of three buttons, one for each of the moves you can play. Tapping on one of these buttons allows us to chose our move. Once we choose our move the iPhone will randomly choose a move and a we will either win, lose, or 👔.

![Screenshot of app](http://i.imgur.com/qH9KPq3.png)

## Rules of Rock Paper Scissors

* Each sign can beat one (and only one) other:
 - Rock smashes scissors.
 - Scissors cut paper.
 - Paper covers rock.
 - If both players choose the same sign, the game is a 👔.


----

## Getting Started

* Start by Creating a new application in Xcode and select the `Single View Application` template.

![Screenshot of Xcode Single View](http://i.imgur.com/kDKFlGw.png)

* Name your application `RockPaperScissors`.
* Select `Swift` as the language.
* Set `iPhone` as the Device.
* Click `Next` then click `Create` to create the new project.

![Screenshot of Xcode New App](http://i.imgur.com/9OOyNie.png)

## Let's play with the Storyboard

* Open up the `main.storyboard` file and make sure you can see your view controller. This is the first screen that will appear when you run the app so you're going to start here.
* In the left hand side panel, expand the array next to `ViewController` and select the `View` object.
* Open the right hand side panel and make sure that the attributes inspector is selected. The attributes inspector is where you can modify the appearance of the view.
* Find the `Background` attribute for the view and select this attribute to change the the background color of the main view.

![Screenshot of the storyboard](http://i.imgur.com/gHPsmDE.png)

If you run your app right now, you will see a blank screen with whatever color you selected as its background. 

* Select the play button in the top left corner of Xcode to run your app on the simulator. Remember that the iPhone 7 Plus simulator is a little large so it's a better option to select the iPhone 7 as your simulator.

![Screenshot of the app running](http://i.imgur.com/z9LMbh9.png)


## Setup your first button

Now you're going to start working on the game logic. Remember that in step 1 of the game, you have to be able to select either Rock, Paper or Scissors. You're now going to set up just a single button so that you can select rock 👊. Once everything is set up for rock, you will setup a button for paper and scissors as well.

* Open the objects inspector on the right hand side of Xcode and find the `UIButton` object in the list. 
* Drag a button from the objects inspector onto the storyboard.
* Place the button in the middle of the screen.

![Screenshot of dragging the button](http://i.imgur.com/V0hfcnD.png)

* Select the attributes inspector on the right hand side of Xcode. Here is where you can modify the appearance of your button. 
* Change the title from 'button' to '👊'. 
* Use the arrow buttons next to the button's font to increase the font to a bigger size. I think 80 looks good. You may have to increase the size of your button to compensate for the large font size.

![Screenshot of button attributes](http://i.imgur.com/oy1MVuG.png)


## Link your button to the code

So far you've added a button to the screen. This looks great but if you run your app and tap on the button, it doesn't do anything. You're going to change this by connecting the button to your code.

* Make sure you're in the `main.storyboard` and open the Assistant editor. This opens up the swift code file that is linked to the screen with the button on it.

![Screenshot of assistant editor](http://i.imgur.com/YD8Ywl8.png)

* Now right click, or ctrl+click, and drag from the button into a space in the code file. You should see a blue line when you start dragging. 

![Screenshot of dragging the action](http://i.imgur.com/hdGYsYL.png)

* After you let go of your mouse, you will see a dialog box open up. Make sure that `action` is selected as the connection type, name your action `playRock`, and click `connect`. This will create a new function in your swift file.

![Screenshot of connecting an action](http://i.imgur.com/yC0A7Xy.png)

Now that you've made this connection, every time you tap on the button, the code inside this function will get run. But there is currently no code inside this function, so let's change that. 

* Add the following line of code inside your new function:

```swift
print("User selected 👊")
```

This will print out your selection to the console.

* Now run you app by clicking the play button in the top left corner of Xcode. 
* When the iPhone simulator appears on your screen, tap the rock button. You should see "User selected 👊" printed to your console.

You have now created a button in the storyboard using the visual helpers of the storyboard. You then connected this button to the code so you can perform some logic when a user taps the button. 


## Generate random sign for the iPhone

Once you've selected your sign, what's the second step in the game? The other player, the iPhone, needs to choose a random sign.You are now going to setup the logic to generate a random sign to use as the iPhone's selection.

* Inside your view controller, create a new function called `generateRandomSign` and have this function return a `String` type. This function will return one of the following emojis: 👊 ✋ ✌️

```swift
func generateRandomSign() -> String {
    // Randomly return one of the following 👊 ✋ ✌️
}
```

* Now write the following code inside the `generateRandomSign` function:

```swift
// Generate a random number
let randomNumber = arc4random_uniform(3) // 1
 
// Create a new empty string variable to hold the computer's sign       
var computerSign = "" // 2

// Set the computer sign to one of the three emojis    
if (randomNumber == 0) { // 3
    computerSign = "✋"
} else if (randomNumber == 1) {
    computerSign = "👊"
} else if (randomNumber == 2) {
    computerSign = "✌️"
}
    
return computerSign // 4
```

> 1. Use the `arc4random_uniform` function to generate a random number. This function accepts a number as it's input and generate a random number between 0 and that number -1. So by passing in 3 to this function, you will get back a random number between 0 and 2
> 2. Create a new empty string variable to hold the sign for the computer.
> 3. Use the random number to assign a sign to the `computerSign` variable.
> 4. Return the sign.

Now if you call this function from anywhere in your code by running `generateRandomSign()`, a random sign will be created. 

* Go back to your `playRock` function that's connected to your button and call the `generateRandomSign()` function to get a sign for the iPhone. 
* Save the result of this function in a constant called `iPhoneSign`. 
* Now print out the iPhone's sign at the same time you print out your sign.

Your `playRock` function should look something like this:

```
@IBAction func playRock(_ sender: Any) {
    let iPhoneSign = generateRandomSign()
    print("User selected 👊, iPhone selected " + iPhoneSign)
}
```

At this point, you can select rock and compare it to the iPhone's selection.

## Determine the winner

Printing out the results of the game is fine, but you can do better than that. You're now going to compare your selection to the iPhone's selection to determine the winner, then print out who won.

* In your `playRock` function, use if statements to check which sign the iPhone selected and implement the following logic:

> * If the iPhone selected ✌️, print out that you won and the iPhone lost
> * If the iPhone selected ✋, print out that you lost and the iPhone won
> * If the iPhone selected 👊, print out that it's a 👔

Your `playRock` function should look something like this:

```
@IBAction func playRock(_ sender: Any) {
    let iPhoneSign = generateRandomSign()
    print("User selected 👊, iPhone selected " + iPhoneSign)
    
    if iPhoneSign == "✌️" {
        print("You won, the iPhone lost")
    } else if iPhoneSign == "✋" {
        print("You lost, the iPhone won")
    } else if iPhoneSign == "👊" {
        print("It's a 👔")
    }
}
```

You now have a working rock, paper, scissors game. Well, you have a working rock game.

## Add Paper and Scissors

Now that you have the rock button fully working, it's time to add the other two signs for you to choose from.

✌️ ✋

* Navigate back to your `main.storyboard` and add two more buttons to the screen.
* Use the following two emojis as the title for each of the buttons: ✌️ ✋
* Right click, or ctrl+click, and drag from the buttons into a space in the code file.
* Create an action for each button and name them `playPaper` and `playScissors`

![Screenshot of dragging from the new buttons to the view controller code](http://i.imgur.com/wzjwYbr.png)

* Inside each of these functions, write code to do the following:
	- Generate a random sign for the iPhone.
	- Check which sign the iPhone has.
	- Print out the winner of the game.

This code will be very similar to what you wrote for the `playRock` function, but the logic will be slightly different to apply to the sign that the user selects.

Once you've completed this step, you will have a fully functional Rock Paper Scissors game.

## Show the results on the screen

Logging out the results to the console is fine while you're developing the app, but if you're to put this piece of gold on the app store, you need to notify the user of the winner by displaying it on the iPhone screen. You're now going to add a label to the screen that will show the result of the game.

* Navigate back to main.storyboard and drag a label from the object inspector to the view controller.
* Position the label at the top of the screen and resize it so that it's large enough to show a couple of lines of text.
* Center text, increase the font size, and set the number of lines to 0. Setting the number of lines to 0 allows us to add any number lines of text to our label.

![Screenshot of updating the label](http://i.imgur.com/ZDCN5FU.png)

* Open the assistant editor, to show the code next to the storyboard.
* Right click, or ctrl+click, and drag from the label to the code file. Remember that when we're linking up an object as a property, we prefer to put it at the top of the swift file.
* When the dialog box opens, select `property` as the connection type, name your property `outcomeLabel`, and click `connect`. This will create a new property in your swift file. Properties can be accessed by all the functions inside the View Controller.

![Screenshot of creating a property 1](http://i.imgur.com/EyFDWO8.png)
![Screenshot of creating a property 2](http://i.imgur.com/zbZH6E8.png)
![Screenshot of creating a property 3](http://i.imgur.com/CIx2Tzm.png)

Now that the label on the screen is connected to our code, you can update the text of our label every time you play the game. You named the label `outcomeLabel` and you can access the label anywhere in the View Controller by simply using its name. So if you want to update the text of the label, you can assign a new value to the label's text property:

```swift
outcomeLabel.text = "New Text"
```

* In the `playRock`, `playPaper`, and `playScissors` functions; instead of printing the winner, set it as the `outcomeLabel`'s text. Here's what it will look like for the `playRock` function:

```swift
@IBAction func playRock(_ sender: Any) {
@IBAction func playRock(_ sender: Any) {
    let iPhoneSign = generateRandomSign()
    
    if iPhoneSign == "✌️" {
        outcomeLabel.text = "You: 👊\niPhone: " + iPhoneSign + "\nYou won, the iPhone lost"
    } else if iPhoneSign == "✋" {
        outcomeLabel.text = "You: 👊\niPhone: " + iPhoneSign + "\nYou lost, the iPhone won"
    } else if iPhoneSign == "👊" {
        outcomeLabel.text = "You: 👊\niPhone: " + iPhoneSign + "\nIt's a 👔"
    }
}
```

>`\n` is what we type inside a string to tell the iPhone that we want a new line in our text. So the following string in code:
>
>`"You: 👊\niPhone: ✌️\nYou won, the iPhone lost"`
>
>Will get printed out as:
>
>```
>You: 👊  
>iPhone: ✌️  
>You won, the iPhone lost
>```


## Summary

You have successfully created a fully functional Rock Paper Scissors game. During this process, you learned how to create an iOS app using Storyboards to setup the UI and Swift to add logic. 

Here are some links:

* Link to the completed project: <https://github.com/meech-ward/RPS>
* Link to the online music app project: <http://lighthouse-labs.thinkific.com/courses/iOS-Essentials>
* Link to the part time course: <http://www.lighthouselabs.ca/intro-to-ios>
* Link to the bootcamp: <http://www.lighthouselabs.ca/ios>

____

If you would like to keep adding features to your game, here are some stretch goals. Each of these can be done in any order:

## Add custom signs and logic 

You have setup a standard game of Rock Paper Scissors. But this is your game and you have the to power to change the rules if you like. Why don't you add some different emojis to the game and create your own custom logic for who wins. Maybe if you choose 🌋 as your sign, then you always win. Or if you choose 💩 as your sign, then everyone loses.

## Keep track of the score

Wouldn't it be nice if you could keep track of who was winning so you could play best 2 out of 3, or 3 out of 5? Try adding some code to your project to keep track of how many times each player wins and display that data in your outcome label.

* Add two new properties to the View Controller, one that keeps track of the number of times you win, and one that keeps track of the number of times that the iPhone wins:

```swift
var numberOfTimesIWon = 0;
var numberOfTimesiPhoneWon = 0;
```

* When you're determining the winner, increment the appropriate property by one:

```swift
// My sign is 👊

if iPhoneSign == "✌️" {
        ...
        
        numberOfTimesIWon += 1
    } else if iPhoneSign == "✋" {
        ...
        
        numberOfTimesiPhoneWon += 1
    }
```

* In the outcome label, display the number of times that you or the iPhone have won.


## DRY Code

**DRY: Don't Repeat Yourself**

You may have noticed that you've been repeating the same code in some places. This is not a good programming practice, you should try to write as little code as possible and remove duplication. This practice is called writing dry code. Right now your code is a little wet, time to make it dry.

Have you spotted the duplicate code yet? that's right, every action `playRock` `playPaper` and `playScissors` all have almost exactly the same game logic in each of them. Try writing the bulk of this logic in just one place, probably in a separate function, and have these functions use the same code.

* Create a new function called `determineOutcome` that accepts two strings, `mySign` and `iPhoneSign`, and returns a String:

```swift
func determineOutcome(mySign: String, iPhoneSign: String) -> String {   
    return ""
}
```

You can now use this function to evaluate the winner.

* Check for every possible combination of signs, and return a string stating who the winner is. Here's an example of two:

```swift
func determineOutcome(mySign: String, iPhoneSign: String) -> String {
    if iPhoneSign == "✌️" && mySign == "👊" {
        return "You: " + mySign + "\niPhone: " + iPhoneSign + "\nYou won, the iPhone lost"
    } else if iPhoneSign == "✋" && mySign == "👊" {
        return "You: " + mySign + "\niPhone: " + iPhoneSign + "\nYou lost, the iPhone won"
    }
	...
}
```

* Call this function from your play functions to assign the text to the `outcomeLabel`:

```swift
@IBAction func playRock(_ sender: Any) {
    let iPhoneSign = generateRandomSign()
    
    let outcomeText = determineOutcome(mySign: 👊, iPhoneSign: iPhoneSign)
    
    outcomeLabel.text = outcomeText
}
```