# Word Guess Game - Instructions

- [Setup](#setup)
- [Overview](#overview)
  - [Approach](#approach)
  - [Commits](#commits)
  - [Before You Begin](#before-you-begin)
- [Part 1: Building the Word Guess Game](#part-1-building-the-word-guess-game)
  - [1. Game Logic Part 1 - Utility Functions](#1-game-logic-part-1---utility-functions)
    - [1.0 - `gameWords` variable](#10---gamewords-variable)
    - [1.1 - `randomWord` function](#11---randomword-function)
    - [1.2 - `isCorrectGuess` function](#12---iscorrectguess-function)
    - [1.3 - `getBlanks` function](#13---getblanks-function)
    - [1.4 - `fillBlanks` function](#14---fillblanks-function)
  - [1. Game Logic Part 2 - Game Management Functions](#1-game-logic-part-2---game-management-functions)
    - [1.5 - `setupRound` function](#15---setupround-function)
    - [1.6 - `updateRound` function](#16---updateround-function)
    - [1.7 - `hasWon` function](#17---haswon-function)
    - [1.8 - `hasLost` function](#18---haslost-function)
    - [1.9 - `isEndOfRound` function](#19---isendofround-function)
    - [1.10 - `setupGame` function](#110---setupgame-function)
    - [1.11 - `startNewRound` function](#111---startnewround-function)
    - [1.12 - `myGame` variable](#112---mygame-variable)
- [Part 2: Build your Webpage](#part-2-build-your-webpage)
    - [2.1 - Building the HTML](#21---building-the-html)
    - [2.2 - Deploying to GitHub Pages](#22---deploying-to-github-pages)
    - [2.3 - Customizing the CSS](#23---customizing-the-css)
- [Part 3: Handling Input and Output](#part-3-handling-input-and-output)
      - [Word Guess Game Bonuses](#word-guess-game-bonuses)
- [Finalizing & Submission on BCS](#finalizing--submission-on-bcs)

## Setup

Run `wheatley` to scaffold your homework assignment

```sh
wheatley --hw=word-guess
```

If you do not have `wheatley`, you can install by running the following command

```sh
npm install -g wheatley
```

This will setup your folder structure and create a repository for you on GitHub.

## Overview

In this assignment, you'll be building a web-based Word Guess game (also known as hangman) from the ground up, and feature JavaScript code which will dynamically update your HTML and CSS.

We recommend you read through the entire instructions for each section before writing any code!

![demo of basic word guess functionality](demo.gif)

### Approach

In building web applications, typically you want to break the large problem down into smaller, solvable problems and start tackling those. Then, you can start piecing those smaller problems together.

   * The ability to solve a large problem by treating it as a set of smaller ones is the hallmark of a strong programmer. Start adapting this approach into your development routine now, to better prepare for your more complex future projects.
   * Remember:
     1. Split the whole program into many distinct, pseudocoded problems.
     2. Focus on one of the smaller problems and solve it.
     3. Only when you solve one problem should you then move onto your next problem.

In this homework, you're going to take a similar approach. You're going to break the large problem of "build a hangman game for the browser" into smaller problems. At a high level, here are some of the things you'll want to do:

1. Build the game logic
2. Build your webpage
3. Handle user input and updates to the page

### Commits

Having an active and healthy commit history on GitHub is important for your future job search. It is also extremely important for making sure your work is saved in your repository. If something breaks, committing often ensures you are able to go back to a working version of your code.

* Committing often is a signal to employers that you are actively working on your code and learning.

  * We use the mantra “commit early and often.” This means that when you write code that works, add it and commit it!

  * Numerous commits allow you to see how your app is progressing and give you a point to revert to if anything goes wrong.

* Be clear and descriptive in your commit messaging.

  * When writing a commit message, avoid vague messages like "fixed." Be descriptive so that you and anyone else looking at your repository knows what happened with each commit.

* We would like you to have well over 200 commits by graduation, so commit early and often!

After each of the below steps, commit and push to your repository.

### Before You Begin
This homework has a suite of tests that you can run to see how you're progressing. They're all failing by default, but as you build out the app they should start to pass. They can also give you clues as to where your code might be breaking...

1. To get started, create a git repository on GitHub and clone it locally.

2. Inside of that git repository folder, unzip the provided zip file into it. Your folder structure should look as follows:

    ```bash
    word-guess (top level folder - name of your repo by default)
    │
    ├── tests
    │   └── methods.test.js
    ├── .eslintrc.json
    ├── index.html
    ├── logic.js
    ├── README.md
    ├── style.css
    └── test.html
    ```

   * Be sure to leave these folders/files in this structure! (don't move them around/create additional files for this one).

     * **Note**: You'll be doing all of your work in the `index.html`, `logic.js`, and `style.css` files (and explaining what you did in the `README.md`). For now, **don't worry about** the code in the `tests` folder, and don't worry about the `.eslintrc.json` file. 

3. Set up ESLint. This will warn you as you're developing if you have syntax problems or errors. It helps you write better code! Follow these steps:

   1. In your terminal, run `npm install -g eslint` to globally install eslint. You need to have node and npm installed and working for that command to work, so if you don't be sure to revisit those steps in the prework and/or reach out to your instructional staff to get you set up.
   
   2. Install the [eslint extension for VS Code](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

      * **Note**: the `.eslintrc.json` files provided define the "configuration" for the eslint tool, describing how the code should look and be styled. We suggest you don't edit them for now - do so at your own peril!

4. [Install Firefox](https://www.mozilla.org/en-US/firefox/new/), if you don't have it installed already. Then, open up the `test.html` file provided in Firefox (you have to use Firefox for it to work). You should see a number of failing tests - your goal is to slowly make them pass as you work through this homework! We recommend leaving the tests open and watching them go from failing to passing as you work through it (just refresh the page to re-run them).

   * Many of the tests have stack traces which can give you information about why your test may be failing. Pay closer attention to the first line in the error, and re-read the instructions carefully to be sure you're on the right path.

   * **Note**: These tests are a work in progress, and are trying to account for all possible approaches in solving the homework. You may run into a case where you think your code is working, but your test is failing. That's fine! Just notify Nick Bartlett - <nbartlett@trilogyed.com> - of the failing test and the code you wrote for the associated function.

## Part 1: Building the Word Guess Game

[Watch the demo](https://youtu.be/W-IJcC4tYFI). Choose a theme for your game! In the demo, we picked an 80s theme: 80s questions, 80s sound and an 80s aesthetic. You can choose any subject for your theme, though, so be creative!

Your end goal is to build something that functions like the demo. First, however, you are going to write some JavaScript to handle some of the game logic.

> Note: In working through this assignment, getting a working end result is more important than following the instructions explicitly. Try your best to follow the instructions, but if you can't get the tests to pass for a specific section, feel free to move on and try to come back to it later.

### 1. Game Logic Part 1 - Utility Functions

To start, you'll want to build some smaller utilities that you can use in the game. Specifically:

1. Picking a random word - [1.1 - `randomWord` function](#11---randomword-function)
2. Checking if a letter is in a word - [1.2 - `isCorrectGuess` function](#12---iscorrectguess-function)
3. Building the initial "blanks" array (what the user will see) - [1.3 - `getBlanks` function](#13---getblanks-function)
4. Filling in "blanks" - [1.4 - `fillBlanks` function](#14---fillblanks-function)

For each of these steps, you'll want to create a function.

First, you'll want to pick your words and create an array! - [1.0 - `gameWords` variable](#10---gamewords-variable)

#### 1.0 - `gameWords` variable

First, you'll want to keep track of your list of words. To do that, create an array named `gameWords`. It should have at least 5 elements, have all lowercase strings, and none of those strings should have spaces. You can choose whatever words and theme you like!

This is the array of words you're going to use for your game from here on out.

#### 1.1 - `randomWord` function

Create a function named `randomWord`. It should take a single argument, an array of words, and should return a random word from that array. 

For example:

```js
// sometimes returns farewell, sometimes goodbye, etc...
randomWord(["farewell", "goodbye", "adios", "au revoir" ]);

// sometimes returns bonjour, sometimes hola, etc...
randomWord(["greetings", "hello", "hola", "bonjour" ])
```

* In your solution, you should use `Math.random`

* Be sure that it's possible for the function to return any of the elements in the array.

You can use this function to pick a random word from your `gameWords` array any time you need to.

#### 1.2 - `isCorrectGuess` function

Next, you're going to need to have some way to check if a guessed letter is "correct". That is, if the guessed letter is in the current word.

Write a function named `isCorrectGuess` that takes two arguments, a word and a letter (in that order). This function should return `true` if the letter is in the word, and `false` otherwise.

For example:
```js
// returns true
isCorrectGuess('farewell', 'e');

// returns false
isCorrectGuess('adios', 'e');
```

#### 1.3 - `getBlanks` function

You're going to need some code to generate "blanks" ("_" characters) based on the length of the word.

To do this, create a function named `getBlanks` that takes one parameter: the word. It should return an array of "_" (underscore) characters with length equal to the length of the word.

For example:
```js
// returns ["_", "_", "_", "_", "_"]
getBlanks("hello");
```

#### 1.4 - `fillBlanks` function

The final "utility" you'll need is one which will fill a blanks array in the correct locations given a letter and the word that array was built from.

For example:
```js
// returns ["h", "_", "_", "_", "_"]
fillBlanks("hello", ["_", "_", "_", "_", "_"], "h");

// returns ["_", "e", "l", "l", "_"]
fillBlanks("hello", ["_", "e", "_", "_", "_"], "l");
```

Name your function `fillBlanks`, and have it take three arguments: the word string, the array of the current puzzle state, and the letter that is going to be filled in (arguments in that order).

### 1. Game Logic Part 2 - Game Management Functions

Next, you need logic to manage the state of the game. To do this, you'll want to keep track of two separate concepts: the individual `round` associated with a specific word, and the overall `game` for tracking persistent (multi-round) information.

To do this, you'll want functions to do the following:

1. Set up a new "round" (current word, guesses left, wrong guesses, puzzle state) - [1.5 - `setupRound` function](#15---setupround-function)
2. Update the "round" with a newly guessed letter - [1.6 - `updateRound` function](#16---updateround-function)
2. Check if the user has won the "round" - [1.7 - `hasWon` function](#17---haswon-function)
3. Check if the user has lost the "round" - [1.8 - `hasLost` function](#18---haslost-function)
4. Check if the "round" is over (won or loss) - [1.9 - `isEndOfRound` function](#19---isendofround-function)
6. Set up the "game" (wins, losses, words array, current round) - [1.10 - `setupGame` function](#110---setupgame-function)
7. Update the "game" with a new round (and alert that the round is over) - [1.11 - `startNewRound` function](#111---startnewround-function)

Finally, you'll want to set up a new game to use when you start handling user input! - [1.12 - `myGame` variable](#112---mygame-variable)

#### 1.5 - `setupRound` function

To start the game logic, you're going to need a way to track all of the information associated with an individual "round" of the game.

Create function named `setupRound` which will be used to create the "round" object. It should take a single argument: the word.

The function should return an object with the following properties and values:
- `word` - set to the word passed in as an argument
- `guessesLeft` - set to 9 to start
- `wrongGuesses` - an empty array to start (since there haven't been any guesses yet)
- `puzzleState` - array of blanks representation of `word` to start. You can update this later when someone makes a correct guess.

For this and the following functions, think about how you can use functions we've already created!

#### 1.6 - `updateRound` function

Now that you can create `round`s, you want to be able to update that round every time the user guesses a letter.

Write a function named `updateRound` that takes two arguments: the round object and the string letter guessed.

This function should, based on the letter guessed, update all relevant aspects of the round object passed as an argument.

#### 1.7 - `hasWon` function

To know when you need to start a new round, you're going to need to check if the game has been won or lost. Let's start with checking if the round has been won.

For this, use a function named `hasWon`, that takes the array `puzzleState` as the only argument.

How can you tell if the round has been won with this information?

The function should return true if the round is won, false otherwise.

#### 1.8 - `hasLost` function

Next, use a function named `hasLost` to check if the round is lost. This function should take as the only argument the number `guessesLeft`.

How can you tell if the round has been lost with this information?

This function should return true if the round is lost, false otherwise.

#### 1.9 - `isEndOfRound` function

Finally, to allow us to know if you need to start a new round, create a function to check if the round is over. Name it `isEndOfRound`. It should take the `round` object as an argument, and return true if the round is over, and false otherwise.

You'll want to use this function later to trigger starting a new round.

#### 1.10 - `setupGame` function

To track higher-level information like number of wins and losses, you'll need a new object: the `game` object. The game is the high-level overall object, where the round is the information associated with guessing around a specific word.

To build and return this `game` object, create a function named `setupGame`. It should take three arguments, in this order: the array of words for the game, the number of wins, and the number of losses.

The function should return an object with the following properties and values:
- `words` - the array of words passed as an argument
- `wins` - the number of wins passed as an argument
- `losses` - the number of losses passed as an argument
- `round` - a new round object created with a random word from `words`

#### 1.11 - `startNewRound` function

Now that you can check if you should start a new round, you need to create a function to start a new round on the game. To do this, create a function named `startNewRound` that takes a single argument: the `game` object. This function is going to update the round on the `game` object. It should:

  * Check to see if the user has won or lost, and update the number of wins and/or losses on the `game` accordingly.

  * Trigger a single alert that informs the user if they've won or lost, and what the word was (the alert just needs to contain the word somewhere).

    * For example: "You lost! The word was 'heart'. Try again! ❤️"

  * Finally, it should update the game object to have a new `round` with a new random word.

#### 1.12 - `myGame` variable

Last but not least, you'll want to create the game so you can update it later when the user interacts with the page.

Create a variable `myGame` at the global scope equal to the `game` object, with the same properties as defined above in the [`setupGame` function section](#110---setupgame-function).

## Part 2: Build your Webpage

Now that you have your game logic set up, you're going to shift gears a bit and set up your HTML skeleton.

Build a web page (you can style and choose whatever theme you like) that has elements with to show the relevant game information:
1. puzzle state (current representation of the word, with blanks and filled in letters)
2. wins (# times user has guessed word correctly before running out of guesses)
3. losses (# times user has failed to guess the word before running out of guesses)
4. letters (incorrect letters guessed this round so far)
5. guesses left (number of incorrect guesses left)

#### 2.1 - Building the HTML

Build your HTML however you like! The only limitations are:

* You must have elements on the page where you will store the aforementioned data. Specifically, these elements should have the following ids:

  * `puzzle-state`
  * `wrong-guesses`
  * `guesses-left`
  * `win-counter`
  * `loss-counter`

* **Don't include jQuery!** Do this assignment with pure HTML, CSS, and JS. You can, however, include Bootstrap styles and markup.

#### 2.2 - Deploying to GitHub Pages

Commit, push, and set up GitHub to deploy the page to GitHub Pages.

> Note: remember that sometimes it takes a while for you to see the changes on GitHub Pages. If it looks like your page isn't updating, try using `ctrl/cmd + shift + r` (hard refresh) to make sure you're not looking at a cached version of the page.

#### 2.3 - Customizing the CSS

For this section, just update your page to look however you want to fit your theme. You can add any content and styles you want, so long as you keep the elements with the ids above.

You can always come back to this step! The most important part of this homework for your practice is to get the game logic working with the page.

Don't forget to commit and push your work regularly!

## Part 3: Handling Input and Output
Now you have some game logic and a webpage, but you need to connect the two!

You're going to need to handle input, keep track of the user's progress, and update the page.

1. Use key events to listen for the letters that your players will type.

2. Update the web page based on the guessed letter. This includes updating the word/blanks on the page, the number of wins, losses, guesses remaining, and incorrect guesses so far.

3. After the user wins/loses, the game should alert, automatically choose another word, update the page, and allow the user to immediately play it.

You can implement this however you like! You can (and probably should) use some of the functions and variables you've defined up to this point.

##### Word Guess Game Bonuses

1. Play a sound or song when the user guesses their word correctly, like in the demo.
2. Show an image on the page of the word when the round is over.
3. Write some stylish CSS rules to make a design that fits your game's theme.

When expanding on the existing solution, just make sure that all of your tests still pass!

## Finalizing & Submission on BCS

* Remember to push up all of your final code to GitHub and deploy to GitHub Pages.

* Update your `README.md` to explain what you did, the functionality of your app, and your approach. Also include a screenshot, or even better use a tool like [Giphy Capture (mac)](https://itunes.apple.com/us/app/giphy-capture-the-gif-maker/id668208984?mt=12), [Gyazo](https://gyazo.com/), or [LICEcap](https://www.cockos.com/licecap/) to record a few `.gifs` of your app in action and include those in your readme to really stand out.

* Submit in BCS both the deployed github.io link to your homework AND the link to the GitHub Repository.

Good luck, and definitely talk with a TA or your instructor if you get tripped up during this challenge.
