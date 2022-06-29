# Workshop 01
## Hello and welcome!

This first workshop will get you up to speed with interacting with your peers, and some internet fundamentals. In this workshop we will:</p>
 * Talk to each other about our past experiences
 * Share knowledge with our peers 
 * Play about with some basic HTML/CSS/JS 
 * Edit our first project in codesandbox
 * Make a basic bleepy button website

**Where code is provided, you are expected to write it out yourself rather than copying and pasting it. We know this is tempting, but the point of a university education is for you to learn the necessary skills for your field, and copying and pasting code will not be on any job descriptions.**

## Task 1 - Top Three Things
### Cast your mind back to the wonderful time we all had last year...!
Think of the most important or most inspiring 3 things that you learned related to:
 * creative coding
 * graphic and web design
 * introductory audio programming 
 * audio technology 

## Task 2 - A Group Decision
### Get into groups of 3-4
* Talk to each other about your respective Top Three
* Through a democratic process, decide on the most important two things - if you are a mixed DM and MT group then pick one from each discipline

## Task 3 - Quickfire Presentation
### Create a short presentation on powerpoint or keynote detailing all the relevant information about the two most important things you learned from last year
Present to the other groups! Order tbd in the class session...

## Task 4 - Dipping Our Toes into Codesandbox
Right, so let's try editing our first codesandbox project to acquaint ourselves with the environment.  We're going to make this little silly thing as our first project:

[jsintro](https://codesandbox.io/embed/jsintro-cxl0x)

You will be working in two browser windows for these worksheets, generally. So when we provide a start codesandbox link in the workshop just click on the "Open Sandox" button in the bottom right hand corner and it will open up a new tab with that sandbox ready for you to work in. 

You can then click the "fork" button in the top right hand corner which will automatically create a new project with this template as a starting point.

Take a look around the starter codesandbox we created below. You should be able to see that there are tabs across the top with various different file names: index.js; package.json; styles.css and index.html.
  
[jsintrostarter](https://codesandbox.io/embed/jsintrostarter-980ki)
 
styles.css is full of some styling stuff that I stole from elsewhere (which we're allowed to do if we credit it properly) and that's what we'll use to make our buttons look nice and have some nice little interactive responses when clicked.

In index.html we currently have one button, we'll add some more in a bit. But what we're really interested in is index.js
 
We've added some starter code here and at the top you can see that we're importing our CSS then also the Tone.js library that we mentioned in class. There's also a variable called <code>synth</code>, which we just turn down a bit on line 6. And a function called <code>playSynth</code> which isn't actually being called right now.

At the moment, the button doesn't actually do anything. So let's go ahead and change that. Add the following line of code below the `playSynth` function:
```javascript
document.getElementById("button1").addEventListener("click", playSynth);
```
If you open the console at the bottom right hand side of page, you should now see that we're printing the button's ID. What we're doing here is adding an event listener that will respond to a user clicking the button and we're passing the <code>playSynth</code> function as a callback. That means that when the button is clicked, the function is executed.

OK but that's not that interesting. So now let's make the synth play a note when the button is clicked. Inside the curly brackets of the <code>playSynth</code> below the <code>console.log(buttonID)</code> line, add the following:

```javascript
synth.triggerAttackRelease("C1", "1.5");
```
Great! This line triggers the synth's envelope to go into the attack phase and then release itself 1.5 seconds later. And it tells the synth to play a C1 note. Can you try changing it to a different note?

But hang on, we want three buttons and for them to do different things (trigger different notes) so head over to index.html and add the following directly beneath the button with the id of "button1":

```html
<button id="button2" class="btn orange">No, click me</button>
```

Now add a third button that will be red and have the id of "button3". Hopefully you should be able to do this bit on your own...

Remember how switch statements work and what the syntax is? It goes, a little, something like this:
```javascript
switch (myVariable) {
  case option1:
    doSomething;
    break;
  case option2:
    doADifferentThing;
    break;
  case option3:
    doSomethingElse;
    break;

  default:
    break;
}
```

Have a go at adding the switch statement inside the <code>playSynth</code> function so that each button plays a different note.
<details>
  <summary>Don't worry if you're struggling, click the dropdown to see the solution</summary>
  
  ```javascript
  function playSynth(event) 
  {
    let buttonID = event.target.id;
    console.log(buttonID);
    switch (buttonID) 
    {
      case "button1":
        synth.triggerAttackRelease("C1", "1.5");
        break;
      case "button2":
        synth.triggerAttackRelease("C2", "1.5");
        break;
      case "button3":
        synth.triggerAttackRelease("C3", "1.5");
        break;

      default:
        break;
    }
  }
  ```
</details>
  
