# Super Smash Bros Character Guessing Game
Website: [https://ssbu-guess.herokuapp.com/](https://ssbu-guess.herokuapp.com/)

Github: xxx

## Summary
I love super smash bros! This is my tribute to Mr. Sakurai, inspired by the classic hangman. It's a short game where the user is shown a slice of a smash bros character,
and has to type their name as fast as possible. Each mistake will cost them some time and show more of the character. After 30 seconds is up, if their score
is in the top 10 scores on the server, they get to send in their name to record their high score!

## Project Specs
- the game slices up an image and progressively shows more of it 
- a HUD to display current score, time, and user input
- fun sound effects played for different actions in the game, with a mute button
- a table for displaying high scores, and communication between client and server to send high scores
- a method for validating scores on the server, so that clients cannot just send random high scores
- preloading image and sound assets for a seamless game experience

## Implementation and Issues Faced
This app was built with a React frontend and a NodeJS Express server in the back. Image and sound assets for the game were available freely on the internet 
(Smash Ultimate's fanbase published everything in the game!), so all that's left is to put the pieces together.

The first issue I encountered was slicing up an image. Native HTML/CSS has some methods to mask an image, but the complexity here was better suited to 
drawing the image on a canvas object. This was not too difficult, as I have worked with building simple games on the canvas before.

After implementing the game with a small batch of images, it became clear that there was a lag time between when an image was required and when it was 
displayed. I had anticipated this beforehand, but needed to see how bad the effect actually was before deciding how to solve this. I ended up going with
preloading all assets (not too bad as it is about 70 characters and 20 sounds), and displaying a loading message instead of a start game button until 
loading completes.

The next issue dealt with determining the random order that characters are displayed. I believe every well-designed game should have a nice way of showing the 
history of a round. For this game, simply seeding the random generator at the start with a number sent from the server is sufficient. This way, the client
will report their high score by sending back the seed, their score, and the last character typed in. The server can then validate this score by checking that
the seed was the correct one sent, then replaying the whole game by generating N characters (N=their score) and seeing if the last generated character matches!
Of course, ridiculously high scores will be filtered out so the server doesn't crash--the player only has 30 seconds after all.

When creating the leaderboard, I opted to go without an external database to save on DB costs. From the past, I know that saving to a local file doesn't
work on Heroku so I didn't bother (and their internal DB tools will be premium features soon). Unfortunately that means the high scores will not be saved
on server reboots, so I manually saved some scores into the code that me and my tester friends set :)

As my application grew in size, I started to incrementally tackle the object/class/file structure. Especially for smaller learning projects, I am a big fan
of not overplanning the initial structure, and planning for refactors along the way as it becomes apparent what my needs are. One thing I realized, which 
demonstrates my initial *lack* of understanding of React's useState function (go ahead and cringe front-end devs), is that essentially all variables used
within the actual game need to be stored in the same gameData structure, not just for ease of access, but because that is what allows them to be accessed
in real time together in different event/useEffect handlers. I wish I understood this at the beginning, as I was creating way too many useState() variables
initially and losing track of them! Perhaps experiencing the issue, then learning how to properly use useState, is my greatest takeaway from this project. 
After the gameData structure was refactored in, passing around data--especially into subcomponents--became much easier.

The final issue, which I did not fully address, is mobile compatibility. From making reactive mobile designs in the past, I knew how to make the overall
layout look good on desktop+mobile without too much issue. However, the keyboard does not display on mobile without a text input field, and my design for
browser did not use a text input field (you just type on your keyboard and letters show up). So I had to create a new mechanism where a text input pops
up on mobile, autofocuses, and functions the same as the browser display (incorrect inputs will delete the key you typed within the input field). At the
time of writing, this method still has some user quality of life issues:
- though autofocused, it requires one more click to bring the keyboard up
- mobile does a weird scroll/zoom thing when the keyboard is brought up, and currently the image/HUD will look bad afterwards unless the user manually also
zooms out. Ahh!!
To make things worse, these niche keyboard interactions are not easily testable on Chrome Devtools, where the Responsive display settings can simulate the
dimensions of a phone, but not all the wonky keyboard features. I would love to meet a professional mobile developer one day and pick their brain on this
type of problem.

Time spent on project: 18 hours over 4 days.




