---
title: Random Sign
permalink: /instructions/random-sign/
layout: page
---

Once we've selected a sign, what's the second step in the game? The other player, the iPhone, needs to choose a random sign. We are now going to setup the logic to generate a random sign to use as the iPhone's selection.

* Inside your view controller, create a new function called `generateRandomSign` and have this function return a `String` type. This function will return one of the following emojis: 👊 ✋ ✌️

```swift
func generateRandomSign() -> String {
    // Randomly return one of the following 👊 ✋️ ✌
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

Now if we call this function from anywhere in our code by running `generateRandomSign()`, a random sign will be created. 

* Go back to your `playRock` function that's connected to your button and call the `generateRandomSign()` function to get a sign for the iPhone. 
* Save the result of this function in a constant called `iPhoneSign`. 
* Now print out the iPhone's sign at the same time you print out your sign.

Our `playRock` function should look something like this:

```
@IBAction func playRock(_ sender: Any) {
    let iPhoneSign = generateRandomSign()
    print("User selected 👊, iPhone selected " + iPhoneSign)
}
```

At this point, we can select rock and compare it to the iPhone's selection.

* Back: [Getting Started]({{ "/instructions/getting-started/" | relative_url }})
* Next: [Determine The Winner]({{ "/instructions/determine-the-winner/" | relative_url }})