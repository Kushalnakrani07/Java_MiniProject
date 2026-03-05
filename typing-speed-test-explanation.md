# TYPING SPEED TEST - COMPLETE CODE EXPLANATION

## TABLE OF CONTENTS
1. HTML Structure
2. CSS Styling
3. JavaScript Logic
4. How Everything Works Together

---

## 1. HTML STRUCTURE (Lines 1-134)

### Document Setup (Lines 1-7)

```html
<!DOCTYPE html>
```
**What it does:** Tells the browser this is an HTML5 document
**Why we need it:** So the browser knows how to interpret the code

```html
<html lang="en">
```
**What it does:** Opens the HTML document and sets language to English
**Why we need it:** Main container for all HTML content

```html
<head>
```
**What it does:** Contains information about the page (not visible content)
**Why we need it:** Holds metadata, title, and styles

```html
<meta charset="UTF-8">
```
**What it does:** Sets character encoding to UTF-8
**Why we need it:** Ensures special characters display correctly
**Simple explanation:** Like setting your keyboard to type in English

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
**What it does:** Makes the page responsive on mobile devices
**Why we need it:** So the page looks good on phones and tablets
**Technical terms:**
- `width=device-width` - page width matches device screen width
- `initial-scale=1.0` - page starts at 100% zoom (no zooming in/out)

```html
<title>Typing Speed Test</title>
```
**What it does:** Sets the text shown in the browser tab
**Why we need it:** Users see this in their browser tab/bookmark

---

### CSS STYLES (Lines 8-118)

```html
<style>
```
**What it does:** Opens the CSS section where we write styling rules
**Why we need it:** To make the page look good (colors, sizes, positions)

#### Universal Reset (Lines 9-13)

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```
**What it does:**
- `*` - Selects EVERY element on the page
- `margin: 0` - Removes default outer spacing from all elements
- `padding: 0` - Removes default inner spacing from all elements
- `box-sizing: border-box` - Makes width/height calculations include padding and border

**Why we need it:** Browsers add default spacing that looks inconsistent. This resets everything to zero so we have full control.

**Simple explanation:** Like clearing a messy desk before organizing it your way.

#### Body Styling (Lines 15-23)

```css
body {
    font-family: Arial, sans-serif;
    background-color: #1a1a1a;
    color: #ffffff;
    padding: 40px;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
}
```
**What each property does:**

- `font-family: Arial, sans-serif` 
  - Sets the text font to Arial (or any sans-serif if Arial unavailable)
  
- `background-color: #1a1a1a`
  - Sets background to very dark gray (almost black)
  - `#1a1a1a` is a hexadecimal color code
  
- `color: #ffffff`
  - Sets default text color to white
  - `#ffffff` is white in hexadecimal
  
- `padding: 40px`
  - Adds 40 pixels of space inside the body on all sides
  
- `display: flex`
  - Turns body into a flexbox container
  - **Technical:** Enables flexible layout system
  - **Simple:** Makes it easier to center things
  
- `justify-content: center`
  - Centers content horizontally
  - Only works because `display: flex` is set
  
- `align-items: center`
  - Centers content vertically
  - Only works because `display: flex` is set
  
- `min-height: 100vh`
  - Minimum height is 100% of viewport height (full screen height)
  - `vh` = viewport height (100vh = full screen)

**Overall effect:** Creates a dark page with white text, centered content, taking up full screen.

#### Container Styling (Lines 25-28)

```css
.container {
    max-width: 800px;
    width: 100%;
}
```
**What the `.` means:** Selects elements with `class="container"`

**What each property does:**
- `max-width: 800px` - Container can't be wider than 800 pixels
- `width: 100%` - Container takes full width available (up to 800px max)

**Why we need it:** Prevents content from stretching too wide on large screens. On small screens it shrinks, on large screens it stops at 800px.

**Where it's used:** Line 130 - `<div class="container">`

#### Heading Styling (Lines 30-33)

```css
h1 {
    font-size: 48px;
    margin-bottom: 30px;
}
```
**What it does:**
- `font-size: 48px` - Makes h1 text 48 pixels tall
- `margin-bottom: 30px` - Adds 30 pixels of space below the heading

**Where it's used:** Line 131 - `<h1>Typing Speed Test</h1>`

#### Word Display Area (Lines 35-44)

```css
.word-display {
    background-color: #2a2a2a;
    padding: 40px;
    border-radius: 10px;
    margin-bottom: 20px;
    min-height: 150px;
    display: flex;
    align-items: center;
    justify-content: center;
}
```
**What each property does:**
- `background-color: #2a2a2a` - Dark gray background
- `padding: 40px` - 40px space inside the box
- `border-radius: 10px` - Rounds the corners by 10 pixels
- `margin-bottom: 20px` - 20px space below this element
- `min-height: 150px` - Box is at least 150 pixels tall
- `display: flex` - Enables flexbox
- `align-items: center` - Centers content vertically
- `justify-content: center` - Centers content horizontally

**Overall effect:** A dark gray rounded box that centers the word inside it.

**Where it's used:** Line 137 - `<div class="word-display">`

#### Word Text Styling (Lines 46-49)

```css
.word {
    font-size: 36px;
    color: #ffffff;
}
```
**What it does:**
- `font-size: 36px` - Makes text 36 pixels large
- `color: #ffffff` - White text color

**Where it's used:** Line 138 - `<div class="word" id="currentWord">`

#### Input Field Styling (Lines 51-61)

```css
.input-area {
    width: 100%;
    padding: 15px;
    font-size: 24px;
    background-color: #2a2a2a;
    color: #ffffff;
    border: 2px solid #444;
    border-radius: 5px;
    margin-bottom: 20px;
}
```
**What each property does:**
- `width: 100%` - Takes full width of container
- `padding: 15px` - Space inside the input box
- `font-size: 24px` - Text size when typing
- `background-color: #2a2a2a` - Dark gray background
- `color: #ffffff` - White text
- `border: 2px solid #444` - 2-pixel border in medium gray
- `border-radius: 5px` - Slightly rounded corners
- `margin-bottom: 20px` - Space below

**Where it's used:** Line 141 - `<input type="text" class="input-area" id="inputBox">`

#### Input Focus State (Lines 63-66)

```css
.input-area:focus {
    outline: none;
    border-color: #4a9eff;
}
```
**What `:focus` means:** Styles applied when user clicks inside the input box

**What it does:**
- `outline: none` - Removes default browser outline
- `border-color: #4a9eff` - Changes border to blue when focused

**Overall effect:** When you click in the input box, the border turns blue.

#### Button Styling (Lines 68-76)

```css
button {
    padding: 15px 40px;
    font-size: 18px;
    background-color: #4a9eff;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    margin-bottom: 20px;
}
```
**What each property does:**
- `padding: 15px 40px` - 15px top/bottom, 40px left/right padding
- `font-size: 18px` - Button text size
- `background-color: #4a9eff` - Blue background
- `color: white` - White text
- `border: none` - No border
- `border-radius: 5px` - Rounded corners
- `cursor: pointer` - Shows hand cursor when hovering
- `margin-bottom: 20px` - Space below button

**Where it's used:** Line 143 - `<button id="startBtn">Start Test</button>`

#### Button Hover State (Lines 78-80)

```css
button:hover {
    background-color: #3a8eef;
}
```
**What `:hover` means:** Styles applied when mouse hovers over button

**What it does:**
- `background-color: #3a8eef` - Darker blue when hovering

**Overall effect:** Button gets slightly darker when you move mouse over it.

#### Button Disabled State (Lines 82-85)

```css
button:disabled {
    background-color: #555;
    cursor: not-allowed;
}
```
**What `:disabled` means:** Styles applied when button is disabled (can't click)

**What it does:**
- `background-color: #555` - Gray background
- `cursor: not-allowed` - Shows "not allowed" cursor

**When this happens:** During the test, start button is disabled (JavaScript does this)

#### Results Container (Lines 87-94)

```css
.results {
    background-color: #2a2a2a;
    padding: 30px;
    border-radius: 10px;
    display: none;
}

.results.show {
    display: block;
}
```
**What `.results` does:**
- Sets dark gray background, padding, rounded corners
- `display: none` - HIDES the results by default

**What `.results.show` does:**
- `display: block` - SHOWS the results
- This class is added by JavaScript when test finishes

**How it works:** Results are hidden until JavaScript adds the "show" class.

**Where it's used:** Line 145 - `<div class="results" id="results">`

#### Result Items Styling (Lines 96-100)

```css
.result-item {
    font-size: 18px;
    margin-bottom: 10px;
    font-family: 'Courier New', monospace;
}
```
**What it does:**
- `font-size: 18px` - Text size
- `margin-bottom: 10px` - Space between result lines
- `font-family: 'Courier New', monospace` - Uses monospace font (like code)

**Where it's used:** Lines 146-150 (each result line)

#### Info Text Styling (Lines 102-106)

```css
.info {
    margin-bottom: 20px;
    font-size: 14px;
    color: #888;
}
```
**What it does:**
- `margin-bottom: 20px` - Space below
- `font-size: 14px` - Smaller text
- `color: #888` - Medium gray color

**Where it's used:** Line 133 - `<div class="info">`

#### Correct/Incorrect Word Colors (Lines 108-115)

```css
.correct {
    color: #4a9eff;
}

.incorrect {
    color: #ff4a4a;
}
```
**What they do:**
- `.correct` - Blue color for correct words
- `.incorrect` - Red color for incorrect words

**When they're used:** JavaScript adds these classes when you type a word correctly or incorrectly

---

## 2. HTML BODY CONTENT (Lines 119-154)

```html
<body>
```
**What it does:** Contains all visible content on the page

#### Main Container (Line 130)

```html
<div class="container">
```
**What it does:** Wraps all content
**Class used:** `.container` (max-width: 800px)

#### Title (Line 131)

```html
<h1>Typing Speed Test</h1>
```
**What it does:** Displays the main heading
**Styling:** h1 styles (48px font)

#### Instructions (Lines 133-135)

```html
<div class="info">
    <div>Test will show one word at a time. Type each word correctly and press space to continue.</div>
</div>
```
**What it does:** Shows instructions to user
**Class used:** `.info` (gray, 14px text)

#### Word Display Box (Lines 137-139)

```html
<div class="word-display">
    <div class="word" id="currentWord">Press Start to begin</div>
</div>
```
**What it does:** Shows the current word to type

**Classes used:**
- `.word-display` - The gray rounded box
- `.word` - The word text styling

**ID used:** `id="currentWord"`
- **Purpose:** JavaScript targets this to change the displayed word
- **Why ID not class:** There's only ONE current word display, IDs are for unique elements

#### Input Box (Line 141)

```html
<input type="text" class="input-area" id="inputBox" placeholder="Type the word here..." disabled>
```
**What it does:** Where user types

**Attributes explained:**
- `type="text"` - Text input field
- `class="input-area"` - Applies input styling
- `id="inputBox"` - JavaScript uses this to get/clear typed text
- `placeholder="Type the word here..."` - Gray hint text
- `disabled` - Can't type until test starts

**Class used:** `.input-area` (dark background, white text)
**ID used:** `id="inputBox"` (JavaScript reads what you type here)

#### Start Button (Line 143)

```html
<button id="startBtn">Start Test</button>
```
**What it does:** Button to start the test

**ID used:** `id="startBtn"`
- JavaScript listens for clicks on this
- JavaScript enables/disables this

#### Results Section (Lines 145-151)

```html
<div class="results" id="results">
    <div class="result-item">Total Time Taken: <span id="timeTaken"></span></div>
    <div class="result-item">Words Typed: <span id="wordsTyped"></span></div>
    <div class="result-item">Correct Words: <span id="correctWords"></span></div>
    <div class="result-item">Accuracy: <span id="accuracy"></span></div>
    <div class="result-item">Speed: <span id="speed"></span></div>
</div>
```
**What it does:** Shows test results (hidden by default)

**Classes used:**
- `.results` - Container styling (hidden by default)
- `.result-item` - Each result line styling

**IDs used:**
- `id="results"` - JavaScript adds "show" class to display this
- `id="timeTaken"` - JavaScript puts time here
- `id="wordsTyped"` - JavaScript puts total words here
- `id="correctWords"` - JavaScript puts correct count here
- `id="accuracy"` - JavaScript puts accuracy percentage here
- `id="speed"` - JavaScript puts characters per minute here

**How `<span>` works:** Empty containers that JavaScript fills with calculated values

---

## 3. JAVASCRIPT CODE (Lines 156-303)

```html
<script>
```
**What it does:** Opens JavaScript section where we write logic

### Variable Declarations (Lines 157-167)

#### Word List Array (Lines 157-161)

```javascript
var words = [
    "the", "be", "to", "of", "and", "a", "in", "that", "have", "I",
    "it", "for", "not", "on", "with", "he", "as", "you", "do", "at",
    "this", "but", "his", "by", "from", "they", "we", "say", "her", "she",
    "or", "an", "will", "my", "one", "all", "would", "there", "their", "what",
    "so", "up", "out", "if", "about", "who", "get", "which", "go", "me"
];
```
**What it is:** An array (list) containing 50 common English words

**Technical terms:**
- `var` - Variable declaration (older way, still works)
- `words` - Variable name
- `[...]` - Square brackets create an array
- Each word is a string in quotes, separated by commas

**What it's used for:** Random words are picked from this list for the test

**Simple explanation:** Like a bag of word cards we randomly pull from

#### Game State Variables (Lines 163-169)

```javascript
var currentWordIndex = 0;
```
**What it is:** Number tracking which word we're on
**Initial value:** 0 (first word)
**Type:** Number
**Used for:** Knowing which word in testWords array to show

```javascript
var startTime;
```
**What it is:** Will store when test started
**Initial value:** undefined (empty)
**Type:** Will be a Date object
**Used for:** Calculating how long test took

```javascript
var endTime;
```
**What it is:** Will store when test ended
**Initial value:** undefined (empty)
**Type:** Will be a Date object
**Used for:** Calculating total test duration

```javascript
var isTestRunning = false;
```
**What it is:** Boolean (true/false) tracking if test is active
**Initial value:** false
**Type:** Boolean
**Used for:** Not actually used in this code (redundant variable - student mistake!)

```javascript
var correctCount = 0;
```
**What it is:** Counter for correctly typed words
**Initial value:** 0
**Type:** Number
**Used for:** Calculating accuracy and showing correct word count

```javascript
var incorrectCount = 0;
```
**What it is:** Counter for incorrectly typed words
**Initial value:** 0
**Type:** Number
**Used for:** Not used in calculations (redundant - another student pattern!)

```javascript
var totalWords = 0;
```
**What it is:** Total number of words attempted
**Initial value:** 0
**Type:** Number
**Used for:** Calculating accuracy percentage

```javascript
var testWords = [];
```
**What it is:** Array that will hold the 50 random words for this test
**Initial value:** Empty array []
**Type:** Array
**Used for:** Stores the specific words for this test session

#### DOM Element References (Lines 171-174)

```javascript
var startBtn = document.getElementById('startBtn');
```
**What it does:** Gets the start button element from HTML
**Technical breakdown:**
- `document` - The entire HTML page
- `.getElementById()` - Method to find element by its ID
- `'startBtn'` - The ID we're looking for (from line 143)
- `var startBtn` - Stores reference to this button

**Simple explanation:** Like giving a nickname to the button so we can easily control it

```javascript
var inputBox = document.getElementById('inputBox');
```
**What it does:** Gets the text input element
**References:** Line 141 - `<input id="inputBox">`
**Used for:** Reading typed text, clearing it, enabling/disabling

```javascript
var currentWordElement = document.getElementById('currentWord');
```
**What it does:** Gets the word display element
**References:** Line 138 - `<div id="currentWord">`
**Used for:** Changing which word is displayed

```javascript
var resultsDiv = document.getElementById('results');
```
**What it does:** Gets the results container
**References:** Line 145 - `<div id="results">`
**Used for:** Showing/hiding results by adding/removing 'show' class

### Event Listeners (Lines 176-184)

#### Start Button Click Listener (Lines 176-178)

```javascript
startBtn.addEventListener('click', function() {
    startTest();
});
```
**What it does:** Waits for user to click start button, then runs startTest function

**Technical breakdown:**
- `startBtn` - The button element we got earlier
- `.addEventListener()` - Method to listen for events
- `'click'` - Type of event (mouse click)
- `function() { ... }` - Anonymous function (function without a name)
- `startTest()` - Calls the startTest function

**Simple explanation:** When someone clicks "Start Test", run the startTest function

#### Space Bar Press Listener (Lines 180-184)

```javascript
inputBox.addEventListener('keypress', function(event) {
    if (event.key === ' ') {
        event.preventDefault();
        checkWord();
    }
});
```
**What it does:** Listens for keys pressed in input box, runs checkWord when space is pressed

**Technical breakdown:**
- `inputBox` - The text input element
- `'keypress'` - Event type (any key pressed)
- `function(event)` - Function that receives event information
- `event` - Parameter containing details about the key press
- `if (event.key === ' ')` - Checks if the key pressed is space bar
- `event.preventDefault()` - Stops default space bar behavior (prevents space appearing in input)
- `checkWord()` - Calls function to check if typed word is correct

**Simple explanation:** When you press space bar while typing, check if the word is correct

### startTest Function (Lines 186-213)

```javascript
function startTest() {
```
**What it is:** Function that initializes and starts the typing test

**When it runs:** When user clicks "Start Test" button

#### Resetting Variables (Lines 187-191)

```javascript
currentWordIndex = 0;
correctCount = 0;
incorrectCount = 0;
totalWords = 0;
isTestRunning = true;
```
**What this does:** Resets all counters to starting values

**Why we need it:** So each new test starts fresh (important if user retakes test)

**Line by line:**
- `currentWordIndex = 0` - Start at first word
- `correctCount = 0` - No correct words yet
- `incorrectCount = 0` - No incorrect words yet
- `totalWords = 0` - No words typed yet
- `isTestRunning = true` - Mark test as active

#### Hiding Previous Results (Line 193)

```javascript
resultsDiv.classList.remove('show');
```
**What it does:** Removes 'show' class from results div

**Technical breakdown:**
- `resultsDiv` - The results container element
- `.classList` - Property containing all classes on element
- `.remove('show')` - Removes the 'show' class

**Effect:** Results div goes back to `display: none` (hidden)

**Why:** Hides old results before starting new test

#### Generating Random Words (Lines 195-199)

```javascript
testWords = [];
for (var i = 0; i < 50; i++) {
    var randomIndex = Math.floor(Math.random() * words.length);
    testWords.push(words[randomIndex]);
}
```
**What it does:** Creates array of 50 random words from the words list

**Line by line breakdown:**

```javascript
testWords = [];
```
- Empties the testWords array
- `[]` creates new empty array

```javascript
for (var i = 0; i < 50; i++) {
```
**Loop structure:**
- `var i = 0` - Start counter at 0
- `i < 50` - Continue while i is less than 50
- `i++` - Add 1 to i after each loop

**What it means:** Run this code 50 times

```javascript
var randomIndex = Math.floor(Math.random() * words.length);
```
**What it does:** Generates random number between 0 and 49

**Technical breakdown:**
- `Math.random()` - Generates random decimal between 0 and 0.999...
- `words.length` - Number of words in array (50)
- `Math.random() * words.length` - Random decimal between 0 and 49.999...
- `Math.floor(...)` - Rounds down to whole number (0-49)
- Result: Random integer from 0 to 49

**Example:** If Math.random() returns 0.73:
- 0.73 * 50 = 36.5
- Math.floor(36.5) = 36

```javascript
testWords.push(words[randomIndex]);
```
**What it does:** Adds random word to testWords array

**Technical breakdown:**
- `words[randomIndex]` - Gets word at random position
- `.push()` - Adds item to end of array
- `testWords` - Our test words array

**Example:** If randomIndex is 36, adds words[36] to testWords

**Overall effect:** After loop, testWords contains 50 random words

#### Preparing Input Box (Lines 201-204)

```javascript
inputBox.value = '';
inputBox.disabled = false;
inputBox.focus();
startBtn.disabled = true;
```
**What each line does:**

```javascript
inputBox.value = '';
```
- Clears any text in input box
- `value` property contains input text
- `''` is empty string

```javascript
inputBox.disabled = false;
```
- Enables the input box
- `disabled = false` means NOT disabled (enabled)
- Now user can type

```javascript
inputBox.focus();
```
- Puts cursor in input box automatically
- `.focus()` method activates element
- User doesn't need to click input box

```javascript
startBtn.disabled = true;
```
- Disables start button during test
- `disabled = true` prevents clicking
- Prevents starting multiple tests at once

#### Recording Start Time (Line 206)

```javascript
startTime = new Date();
```
**What it does:** Records current time

**Technical breakdown:**
- `new Date()` - Creates Date object with current date/time
- Stores in `startTime` variable

**Used for:** Calculating how long test took

#### Showing First Word (Line 208)

```javascript
showNextWord();
```
**What it does:** Calls showNextWord function to display first word

### showNextWord Function (Lines 211-219)

```javascript
function showNextWord() {
    if (currentWordIndex < testWords.length) {
        currentWordElement.textContent = testWords[currentWordIndex];
        currentWordElement.className = 'word';
    } else {
        endTest();
    }
}
```
**What it does:** Displays next word or ends test if finished

#### Checking If Words Remain (Line 212)

```javascript
if (currentWordIndex < testWords.length) {
```
**What it checks:** Is current index less than total words?

**Technical breakdown:**
- `currentWordIndex` - Current position (starts at 0)
- `testWords.length` - Total words (50)
- `<` - Less than operator

**Example:** 
- If currentWordIndex = 0 and length = 50: 0 < 50 is TRUE
- If currentWordIndex = 50 and length = 50: 50 < 50 is FALSE

**Result:** If TRUE, show next word. If FALSE, test is done.

#### Displaying the Word (Line 213)

```javascript
currentWordElement.textContent = testWords[currentWordIndex];
```
**What it does:** Shows word on screen

**Technical breakdown:**
- `currentWordElement` - The word display div
- `.textContent` - Property containing text inside element
- `testWords[currentWordIndex]` - Gets word at current index

**Example:** If currentWordIndex = 5, displays testWords[5]

#### Resetting Word Styling (Line 214)

```javascript
currentWordElement.className = 'word';
```
**What it does:** Resets classes to just 'word'

**Why needed:** Removes 'correct' or 'incorrect' classes from previous word

**Technical breakdown:**
- `.className` - Property containing element's class
- `= 'word'` - Replaces all classes with just 'word'

#### Ending Test When Done (Lines 215-217)

```javascript
} else {
    endTest();
}
```
**When this runs:** When currentWordIndex >= testWords.length (no more words)

**What it does:** Calls endTest function to finish and calculate results

### checkWord Function (Lines 221-241)

```javascript
function checkWord() {
```
**What it does:** Checks if typed word matches current word

**When it runs:** When user presses space bar

#### Getting Typed Word (Line 222)

```javascript
var typedWord = inputBox.value.trim();
```
**What it does:** Gets text from input box and removes extra spaces

**Technical breakdown:**
- `inputBox.value` - Text in input box
- `.trim()` - Removes spaces from start and end
- Stores in `typedWord` variable

**Example:** If user types "  hello  ", trim makes it "hello"

#### Getting Correct Word (Line 223)

```javascript
var correctWord = testWords[currentWordIndex];
```
**What it does:** Gets the word user should have typed

**Technical breakdown:**
- `testWords[currentWordIndex]` - Word at current position
- Stores in `correctWord` variable

#### Incrementing Total Count (Line 225)

```javascript
totalWords++;
```
**What it does:** Adds 1 to total words counter

**Technical breakdown:**
- `++` is increment operator (adds 1)
- Same as `totalWords = totalWords + 1`

**Why:** Counts every word attempt for accuracy calculation

#### Checking If Correct (Lines 227-233)

```javascript
if (typedWord === correctWord) {
    correctCount++;
    currentWordElement.classList.add('correct');
} else {
    incorrectCount++;
    currentWordElement.classList.add('incorrect');
}
```
**What it does:** Compares typed word to correct word

**If correct (lines 227-230):**

```javascript
if (typedWord === correctWord) {
```
- `===` strict equality (must be exactly same)
- Checks if typed matches correct

```javascript
correctCount++;
```
- Adds 1 to correct counter

```javascript
currentWordElement.classList.add('correct');
```
- Adds 'correct' class to word display
- Turns word blue (from CSS .correct class)
- `.classList.add()` adds class without removing others

**If incorrect (lines 231-233):**

```javascript
} else {
```
- Runs if words don't match

```javascript
incorrectCount++;
```
- Adds 1 to incorrect counter

```javascript
currentWordElement.classList.add('incorrect');
```
- Adds 'incorrect' class
- Turns word red (from CSS .incorrect class)

#### Moving to Next Word (Lines 235-239)

```javascript
setTimeout(function() {
    inputBox.value = '';
    currentWordIndex++;
    showNextWord();
}, 100);
```
**What it does:** Waits 100 milliseconds, then clears input and shows next word

**Technical breakdown:**

```javascript
setTimeout(function() { ... }, 100);
```
- `setTimeout()` - Delays code execution
- `function() { ... }` - Code to run after delay
- `100` - Milliseconds to wait (0.1 seconds)

**Why delay:** Gives brief moment to see correct/incorrect color

```javascript
inputBox.value = '';
```
- Clears input box for next word

```javascript
currentWordIndex++;
```
- Moves to next word index
- `++` adds 1

```javascript
showNextWord();
```
- Displays next word (or ends test if done)

### endTest Function (Lines 243-249)

```javascript
function endTest() {
    endTime = new Date();
    isTestRunning = false;
    inputBox.disabled = true;
    startBtn.disabled = false;
    
    calculateResults();
}
```
**What it does:** Stops test and triggers result calculation

**When it runs:** When all 50 words are completed

#### Recording End Time (Line 244)

```javascript
endTime = new Date();
```
**What it does:** Records current time when test ends

**Used for:** Calculating total time taken

#### Marking Test Inactive (Line 245)

```javascript
isTestRunning = false;
```
**What it does:** Sets test running flag to false

**Note:** Not actually used anywhere (redundant variable - student pattern)

#### Disabling Input (Line 246)

```javascript
inputBox.disabled = true;
```
**What it does:** Disables input box

**Effect:** User can't type anymore

#### Enabling Start Button (Line 247)

```javascript
startBtn.disabled = false;
```
**What it does:** Re-enables start button

**Effect:** User can click "Start Test" to try again

#### Calculating Results (Line 249)

```javascript
calculateResults();
```
**What it does:** Calls function to compute and display results

### calculateResults Function (Lines 251-301)

```javascript
function calculateResults() {
```
**What it does:** Calculates all test statistics and displays them

#### Calculating Time Taken (Lines 252-254)

```javascript
var timeDiff = endTime - startTime;
var minutes = timeDiff / 1000 / 60;
var seconds = Math.floor((timeDiff / 1000) % 60);
```
**Line 252:**
```javascript
var timeDiff = endTime - startTime;
```
- Subtracts start time from end time
- Result is in milliseconds
- Example: If test took 75000 milliseconds (75 seconds)

**Line 253:**
```javascript
var minutes = timeDiff / 1000 / 60;
```
- Converts milliseconds to minutes
- `/1000` converts to seconds
- `/60` converts to minutes
- Result can be decimal (e.g., 1.25 minutes)

**Line 254:**
```javascript
var seconds = Math.floor((timeDiff / 1000) % 60);
```
**Technical breakdown:**
- `timeDiff / 1000` - Convert to seconds
- `% 60` - Modulo operator (remainder after dividing by 60)
- `Math.floor()` - Rounds down
- Gets remaining seconds after removing full minutes

**Example:** 
- timeDiff = 75000 milliseconds
- 75000 / 1000 = 75 seconds
- 75 % 60 = 15 (remainder)
- Result: 15 seconds

#### Formatting Time Display (Lines 256-257)

```javascript
var totalMinutes = Math.floor(minutes);
var displaySeconds = seconds;
```
**Line 256:**
- Rounds minutes down to whole number
- Example: 1.25 minutes becomes 1 minute

**Line 257:**
- Stores seconds in separate variable
- (Redundant assignment - student pattern)

#### Building Time String (Lines 259-270)

```javascript
var timeString = '';
if (totalMinutes > 0) {
    timeString = totalMinutes + ' minute';
    if (totalMinutes > 1) {
        timeString += 's';
    }
    if (displaySeconds > 0) {
        timeString += ' ' + displaySeconds + ' seconds';
    }
} else {
    timeString = displaySeconds + ' seconds';
}
```
**What it does:** Creates human-readable time string

**Line 259:**
```javascript
var timeString = '';
```
- Creates empty string variable

**Lines 260-269: If test took at least 1 minute:**

```javascript
if (totalMinutes > 0) {
```
- Checks if at least 1 minute

```javascript
timeString = totalMinutes + ' minute';
```
- Starts string with number of minutes
- Example: "1 minute"

```javascript
if (totalMinutes > 1) {
    timeString += 's';
}
```
- Adds 's' for plural if more than 1 minute
- `+=` adds to existing string
- Example: "2 minutes"

```javascript
if (displaySeconds > 0) {
    timeString += ' ' + displaySeconds + ' seconds';
}
```
- Adds seconds if any remain
- Example: "1 minute 30 seconds"

**Lines 269-271: If test took less than 1 minute:**

```javascript
} else {
    timeString = displaySeconds + ' seconds';
}
```
- Just shows seconds
- Example: "45 seconds"

#### Calculating Accuracy (Lines 272-275)

```javascript
var accuracyPercent = 0;
if (totalWords > 0) {
    accuracyPercent = Math.round((correctCount / totalWords) * 100);
}
```
**What it does:** Calculates accuracy percentage

**Line 272:**
```javascript
var accuracyPercent = 0;
```
- Initializes accuracy to 0

**Lines 273-275:**
```javascript
if (totalWords > 0) {
    accuracyPercent = Math.round((correctCount / totalWords) * 100);
}
```
**Why check totalWords > 0:** Prevents division by zero

**Calculation breakdown:**
- `correctCount / totalWords` - Fraction correct (e.g., 48/50 = 0.96)
- `* 100` - Convert to percentage (0.96 * 100 = 96)
- `Math.round()` - Round to nearest whole number

**Example:** 48 correct out of 50 = 96%

#### Calculating Characters Typed (Lines 277-280)

```javascript
var totalChars = 0;
for (var i = 0; i < correctCount; i++) {
    totalChars += testWords[i].length;
}
```
**What it does:** Counts total characters in correctly typed words

**Note:** This has a BUG - student mistake!

**The bug:**
- Loop uses `i < correctCount` but should check all testWords
- Only counts characters in first `correctCount` words
- Assumes all correct words are at beginning (not true!)

**What it should be:**
```javascript
for (var i = 0; i < testWords.length; i++) {
    if (user typed testWords[i] correctly) {
        totalChars += testWords[i].length;
    }
}
```

**How it works (buggy way):**
- Loops through first `correctCount` words
- `testWords[i].length` - Number of characters in word
- `+=` adds to total

**Example:** If correctCount = 48, counts characters in first 48 words

#### Calculating Speed (Lines 282-285)

```javascript
var charsPerMinute = 0;
if (minutes > 0) {
    charsPerMinute = Math.round(totalChars / minutes);
}
```
**What it does:** Calculates typing speed in characters per minute

**Line 283:**
```javascript
if (minutes > 0) {
```
- Prevents division by zero

**Line 284:**
```javascript
charsPerMinute = Math.round(totalChars / minutes);
```
- Divides total characters by minutes
- Rounds to whole number

**Example:** 240 characters in 1.25 minutes = 192 CPM

#### Displaying Results (Lines 287-291)

```javascript
document.getElementById('timeTaken').textContent = timeString;
document.getElementById('wordsTyped').textContent = totalWords;
document.getElementById('correctWords').textContent = correctCount;
document.getElementById('accuracy').textContent = accuracyPercent + '%';
document.getElementById('speed').textContent = charsPerMinute + ' characters per minute';
```
**What each line does:**

**Line 287:**
```javascript
document.getElementById('timeTaken').textContent = timeString;
```
- Finds element with id="timeTaken"
- Sets its text to calculated time string
- Updates: Line 146 `<span id="timeTaken">`

**Line 288:**
```javascript
document.getElementById('wordsTyped').textContent = totalWords;
```
- Updates total words display
- Updates: Line 147 `<span id="wordsTyped">`

**Line 289:**
```javascript
document.getElementById('correctWords').textContent = correctCount;
```
- Updates correct words display
- Updates: Line 148 `<span id="correctWords">`

**Line 290:**
```javascript
document.getElementById('accuracy').textContent = accuracyPercent + '%';
```
- Updates accuracy display
- `+ '%'` adds percent sign to number
- Updates: Line 149 `<span id="accuracy">`

**Line 291:**
```javascript
document.getElementById('speed').textContent = charsPerMinute + ' characters per minute';
```
- Updates speed display
- Updates: Line 150 `<span id="speed">`

#### Showing Results and Final Message (Lines 293-294)

```javascript
resultsDiv.classList.add('show');
currentWordElement.textContent = 'Test Complete! Press Start to try again';
```
**Line 293:**
```javascript
resultsDiv.classList.add('show');
```
- Adds 'show' class to results div
- CSS rule `.results.show { display: block; }` makes it visible
- Results appear on screen

**Line 294:**
```javascript
currentWordElement.textContent = 'Test Complete! Press Start to try again';
```
- Changes word display to completion message
- Tells user test is done

---

## 4. HOW EVERYTHING WORKS TOGETHER

### Complete User Flow:

1. **Page Loads:**
   - HTML structure created
   - CSS styles applied (dark theme, centered layout)
   - JavaScript loads and runs
   - Variables initialized
   - Event listeners attached to button and input

2. **User Clicks "Start Test":**
   - `startTest()` function runs
   - Counters reset to 0
   - 50 random words selected
   - Input box enabled and focused
   - Start button disabled
   - Timer starts
   - First word displayed

3. **User Types Each Word:**
   - User types in input box
   - Presses space bar when done
   - `checkWord()` function runs
   - Compares typed word to current word
   - If correct: adds to correctCount, word turns blue
   - If incorrect: adds to incorrectCount, word turns red
   - Brief 100ms pause
   - Input cleared
   - Next word shown

4. **After 50 Words:**
   - `showNextWord()` detects no more words
   - `endTest()` function runs
   - End time recorded
   - Input disabled
   - Start button enabled
   - `calculateResults()` runs

5. **Results Calculated:**
   - Time difference calculated (end - start)
   - Time formatted to readable string
   - Accuracy calculated (correct / total * 100)
   - Characters counted
   - Speed calculated (chars / minutes)
   - All values displayed
   - Results div shown
   - Completion message displayed

6. **User Can Retry:**
   - Start button is enabled again
   - Clicking it starts whole process over

### Key JavaScript Concepts Used:

**Variables:**
- Store data (numbers, text, objects)
- `var` declares variables

**Arrays:**
- Lists of items
- `[]` creates array
- Access items with index: `array[0]`

**Functions:**
- Reusable blocks of code
- `function name() { ... }` defines function
- `name()` calls/runs function

**Objects:**
- Elements are objects with properties
- `.property` accesses property
- `.method()` calls method

**Events:**
- User interactions (clicks, key presses)
- `.addEventListener()` listens for events

**Conditionals:**
- `if (condition) { ... }` runs code if true
- `else { ... }` runs if false

**Loops:**
- `for` repeats code multiple times
- `while` repeats while condition true

**DOM Manipulation:**
- Changing HTML from JavaScript
- `.getElementById()` finds elements
- `.textContent` changes text
- `.classList.add()` adds classes

### CSS-JavaScript Connection:

**How they work together:**
1. CSS defines styles for classes
2. JavaScript adds/removes classes
3. Styles automatically update

**Examples:**
- `.results { display: none }` hides results
- JavaScript adds 'show' class
- `.results.show { display: block }` shows results

### Common Student Patterns in This Code:

1. **Using `var` instead of `let/const`:**
   - Older syntax, still works
   - Modern code uses `let` and `const`

2. **Redundant variables:**
   - `isTestRunning` declared but not used
   - `incorrectCount` incremented but not used
   - `displaySeconds = seconds` unnecessary assignment

3. **String concatenation with `+`:**
   - Modern code uses template literals: `` `${variable}` ``
   - This code uses: `'text ' + variable`

4. **Anonymous functions:**
   - `function() { }` without names
   - Modern code uses arrow functions: `() => { }`

5. **Bug in character counting:**
   - Counts first N words instead of correct words
   - Works but gives wrong results if errors aren't at end

These patterns make it look like a student project - functional but not perfectly optimized!

---

## SUMMARY

This typing speed test is a fully functional web application that:

1. **Displays** one random word at a time
2. **Accepts** user input
3. **Validates** each word typed
4. **Tracks** accuracy and speed
5. **Calculates** and displays results

It uses HTML for structure, CSS for styling, and JavaScript for interactivity. The code follows beginner patterns while being completely functional - perfect for a student project!
