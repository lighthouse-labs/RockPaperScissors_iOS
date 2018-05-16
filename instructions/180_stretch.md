---
title: Stretch
permalink: /instructions/stretch/
layout: page
---

If you would like to keep adding features to your game, here are some stretch goals. Each of these can be done in any order.

---

## Add custom signs and logic 

We have setup a standard game of Rock Paper Scissors. But this is now your game and you have the to power to change the rules if you like. Why don't you add some different emojis to the game and create your own custom logic for who wins. Maybe if you choose 🌋 as your sign, then you always win. Or if you choose 💩 as your sign, then everyone loses.

---

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

---

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

* Back: [Conclusion]({{ "/instructions/conclusion/" | relative_url }})