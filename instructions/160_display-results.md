---
title: Display the Results
permalink: /instructions/display-results/
layout: page
---

Logging out the results to the console is fine while we're developing the app, but if we're to put this piece of gold on the app store, we need to notify the user of the winner by displaying it on the iPhone screen. We're now going to add a label to the screen that will show the result of the game.

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

Now that the label on the screen is connected to our code, we can update the text of our label every time we play the game. We named the label `outcomeLabel` and we can access the label anywhere in the View Controller by simply using its name. So if we want to update the text of the label, we can assign a new value to the label's text property:

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


* Back: [Add Paper and Scissors]({{ "/instructions/determine-the-winner/" | relative_url }})
* Next: [Conclusion]({{ "/instructions/conclusion/" | relative_url }})