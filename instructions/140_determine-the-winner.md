---
title: Determine The Winner
permalink: /instructions/determine-the-winner/
layout: page
---

Printing out the results of the game is fine, but we can do better than that. We're now going to compare your selection to the iPhone's selection to determine the winner, then print out who won.

* In the `playRock` function, use if statements to check which sign the iPhone selected and implement the following logic:

> * If the iPhone selected ✌️, print out that you won and the iPhone lost
> * If the iPhone selected ✋, print out that you lost and the iPhone won
> * If the iPhone selected 👊, print out that it's a 👔

Our `playRock` function should look something like this:

```swift
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

We now have a working rock, paper, scissors game. Well, we have a working *rock* game.

* Back: [Random Sign]({{ "/instructions/random-sign/" | relative_url }})
* Next: [Add Paper and Scissors]({{ "/instructions/add-paper-and-scissors/" | relative_url }})