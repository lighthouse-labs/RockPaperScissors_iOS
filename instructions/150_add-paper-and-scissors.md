---
title: Add Paper And Scissors
permalink: /instructions/add-paper-and-scissors/
layout: page
---

Now that we have the rock button fully working, it's time to add the other two signs to choose from.

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

Once we've completed this step, we will have a fully functional Rock Paper Scissors game.

* Back: [Determine The Winner]({{ "/instructions/random-sign/" | relative_url }})
* Next: [Display the Results]({{ "/instructions/display-results/" | relative_url }})