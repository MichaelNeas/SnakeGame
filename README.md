# VIM Controlled SnakeGame

h - Left
j - Down
k - up
l - right

Snake in html5 canvas made Freshman Year of college

**Initial Planning Process:**

This was my first attempt at creating the game of snake using JavaScript. Coming into the project I had fairly little information about JavaScript and the possibilities that it contains. The first thing I had to do was come up with how I was even going to start creating this game. I looked at examples of how people made snake in the past and tried to come up with a game plan for implementation. I checked out websites like [http://www.html5rocks.com/en/](http://www.html5rocks.com/en/) , [http://www.w3schools.com/](http://www.w3schools.com/) , and [http://htmldog.com/](http://htmldog.com/) to learn about JavaScript. Then made the plan to use the new HTML5 element <canvas>, which draws graphics “on the fly, via scripting”. Pretty much canvas is a way to draw by using code which makes a lot of sense, you figure you draw the initial setting , board, snake, and food, and when the snake moves it gets redrawn in a way. I modeled my game off of a couple other peoples codes that were made in past when they were learning too. This allowed me to find my way if I ever got lost. Anyways below is a bunch of notes on everything in the 180-ish lines of code.

**Snake-Index Id’s:**

To start every website needs the traditional <!doctype html> code and from there I created a div wrap by the id of “snake-playground” in order to move around the game when the website was to be produced after the game was made.

“banner” was used in order to modify the title to allow new players to type their name on a prompt and from there the variable name would forever take the property of whatever name was typed into the prompted, and from there would be incorporated in the title.

“thescore” is an important id that is changed in the javascript whenever the snake eats a food, the score would increase 100 points each time. And after the score reaches 1000 points the level would increase as well.

“myart” provides the space for the canvas, here the canvas is initially given a boundary, which can be thought of as a legit canvas where I can draw anything within the bounds using the new html5 code explained later.

“instruction” is simply a tag to allow the player to know what to press at the points of the game during play and after loss.

From there, right before the </body> is where all the magic takes place and the script is implemented, for the game code itself, I reference an external script file “js/snake.js” and following that is the banner and instruction alerts.

**The JavaScript used:**

- _var_ creates a surname or string that can be altered later, and can be referenced to later on in code as well. These variables take a ton of different types of properties for whatever the coder needs. Declaration allows for you to create a new variable, and allows it to exist. Initialization gives the variable a value for the first time and requires the var before the name, but this is not necessary for alteration.

- _alert_ will produce a message on the screen of the user when gives an instruction or just provides information.

- _prompt_ gives the ability for a variable to be assigned some input asked in an alert form.

- _document.getElementById_ allows the coder to retrieve information from the index/html and alter it with a different input for example you see a reference to a variable with a period followed by innerHTML which is equal to the thing you want to change it to, which can include a previously defined variable. After document can also be…. getElementsByClassName, getElementsByTagName, querySelector.

- = (_sign)_ shows what a variable is equal to or assigned to… this can pretty much be anything from numbers, to Boolean values, to arrays and more.

- _logic_ A Boolean value is true or false, which can allow help with if then statements and programming direction later on. We can retrieve true or false values many different ways, like a triple equals (===) which compares two values to be true or false. < > <= >= signs can all be used like taught in grade school, they all return true or false values.

- _conditionals_ are very powerful and perhaps the main core components for how things work. _If_ is the main thing to call for a conditional, if (some case) then {in brackets run a code.} There are _if-else ­_statements which say if (some case) is true then { some code} or else { run a different type of code}

- _i++_ is the same thing as incrementing the value of i by 1.

- _forloops_ are important in my code and are similar to if statements, but combines three different pieces of information. Starting with “initialization” which is the part for creating a variable to let you know how far through the loop you are a start…; then “condition” is where the logic loop goes aka the end; and then “expression” is run after each individual loop which accumulates some value.

- _functions_ reusable blocks of code that carry a specific task out. A function can take parameters and gets arguments. Or it could not take any parameters and just do a function.

- _objects_ contain a bunch of information that can be called for different instances and changes by using dot syntax. You can call a variable.somethinginside variable to trigger exactly what you need or want.

- _arrays_ are lists of any data, which can be other arrays, each has an index, which can be used to get an element from the array. Each element is 1 -> however many things make up the array. Arrays have lengths and can push and pop in order to alter whats inside. Push will insert something into the array at the end of the array, pop will remove it. Arrays are stacks of information.

- _addEventListener_ allows for the winder to register the inputs from the keyboard

- _DOM_ is a way to manipulate the structure and style of an HTML page, it represents the internals of the page.

- _functionalscope_ –pretty much if something is defined inside of a function it can only be called throughout the function it was created and is not found somewhere else not global scope.

## --------Code Walk Through/ plan of attack----------

**Variables of the whole game (global variables):**

- mygame holds the entire code

- width & height for the canvas, game playing area.

- snakesize sets the snakes initial length to 3, the level starts at 1, and the body size, is 10 px to allow for easy visibilities.

- xcoordinateofbody and ycoordinateofbody are set up so that the snake begins horizontally moving to the right, and the array is set up with an initial 3 parts of the snakes body.

- xmovement and ymovement is an array that holds the speed of the snake as it moves to the right.

- instructions will hold how the user controls the snake with whater input you select

- xfood and yfood will take coordinates later to put the food on the canvas

- score starts at 0 and will increment, scorecontext references “thescore” in the html.

- if the snake nom’s then a new location of food must be placed and if the game is over we will be able to restart the game later on.

**Drawing the game on the canvas, background, snake and food:**

So the canvas is a new element in HTML5 and takes a boat-load of inputs in the drawing stages I used shadowBlur, shadowColor, lineWidth, fillStyle, fillRect, fill, strokeStyle, and strokeRect in the making of the board and snake.

- makeboard function draws out the board, and each call to the canvas requires a previous call to mygame which is how you add the effects to the gameboard. Its moderately self explanatory, but shadowBlur is equal to pixels of blur from around the borders with a black color. Also, fillStyle gives the board its blue property and the fillRect gives the board its 2D dimensions. strokeStyle outlines the boarder with a color and same deal with the strokeRect.

- snakeposition takes two parameters, one being thex coordinate and the other being the y coordinate. This gives the properties to each square on the board, also used in the declaration of the food properties later on. The parameters come into use when calling fillRect and strokeRect which allow for specific positioning of the squares of the snake, with the bodysize giving the other remaining information.

- makesnake will draw the snake by calling the snakeposition function and allowing the x and y to be the coordinated defined above. This function takes a for statement, where n starts at 0, and goes until n is smaller than the snakesize, and each time the loop is called n is incremented by 1.

- makefood takes 2 if statements one being and if-else to provide the makefood always does something. So basically this function says if true…aka the food is eaten or not there then allow the variables for the coordinates of the food initially set in place to be set to a random number that has the largest integer less than or equal to a random number, multiplied by the bodysize. The x coordinate specifically take this integer of the width times a randomnumber dividied by the bodysize then multiplied by the bodysize. Then the loop of if it is eaten reoccurs with a checkhit function shown later in the code. And if it wasn’t eaten then its false and the code doesn't need to worry about creating a new food element. I reused the snakeposition function to place the food coordinates randomly on the board.

- gameloop sends the drawing to the main game loop. First it calls the canvas in the html and allows it to draw by using getContext(“2d”) which says that the graphics of canvas are 2d. This function draws the boundary, and the snake. I add the rest of this but the replenish calls the movement after the time of 500 this gives the speed in level 1\. This gameloop also take the scorecontext and instructions and really gives them their definitions by retrieving them from the html code. Then finally the listener takes an onload event to call the function.

**Moving the snake:**

I started the snake motion by assigning the keycontrol function to take one parameter. Basically it's a bunch of if then statements that take a specific keyCode which is registered to the computer keyboard. Followed by the comparison of the key press with the xmovement of 0 and does not allow the keymovement to go backwards into its self with the != operator. And if that code is true then it changes the movement to move in the negative x direction. This is repeated for the other wasd keys allowing them to be directions instead of the arrow keys. The last key code is to restart the game and only is registered when the game is over and the space bar is pressed, and it valls the tryagain function.

- snakemotion takes uses two forloops to allow the snake to move. The first for loop will take the coordinate of the body and set it equal to the addition of the movements times the bodysize. The second loop is a decrementing forloop that allows the snake to be forced to keep direction of coordinates, the motion is constrained by the preciding body part. The direction of the vector gets copied as the snakesize increases. And allows registration once the food is eaten.

- naturally in order to redraw the snake, the previous snake needs to be cleared or else there would be a huge trail, it’d be more like the game of slug instead of snake, clearit takes the properties of the canvas and clears its trail.

**Eating the food:**

Eatfood is an array changing function that contains two if statements. The first being if the snakes head hits the food coordinates then it has been eaten. I used functional scope here to define an addition of the tail. These tail coordinates directly increment the snakesize and location of the snakes body part. I used the tendency of arrays to push these new variables onto the xcoordinates of the movey and to be taken into consideration when the sanke moves in the x and y directions. Not only does the snakesize variable increase by 1, the score is also incremented 100 each time there is a new piece of food eaten. The next if statement comes in to directly affect the html. If the score percent out of 1000 is equal to 0 then the level is increased by 1, this is a modulo reference, the id is referenced and altered based off of the current value of the variables.

**Collisions:**

Checkhit is used in the makefood function which allows the game to know if the head of the snake crashes into the food particle. It is a for loop theat is directly effected by Boolean values.

This section checks the collision into its own body. The crashintobody function takes two parameters x and y, basically it is a for loop that states if the coordinates of the body is equal to a point on the board. The forloop will only begin when the snakesize is larger than 4 or else it wont have any effect. If the head square is contacted with any part of the extended body, then it will return false and the game will end.

Now to check to see if the snake collides with the wall was by far the most complicated part of the entire program for me. hitsomething takes no parameters and is multiple if statements. So if the coordinates of the body collide with the boundaries of the canvas then the score is done, and the level takes the value of You lose!. The instructions at this point turn to tell the user to push the spacebar to play again. At this point it is important to state that the endgame is equal to true clearTimeout allows the loop to stop going at actually end the game. Or else if snakesize is greater than 4 then if the sanke creashes into the body, the game ends.

**The overall big loop of awesomeness:**

SetTimeout will take the loop and refresh it every couple of miliseconds, this allows for the snake to have its speed when the level increases. I’m not too sure if the order of the functions matters but I pretended like they did. After replenish the snake trail is cleared the board is made, food is made, and the snake can move with respect to the properties of the snake, while also taking in consideration if the snake hits something.

**The game is over and you want to try again:**

This last function will allow for the player to try again, it restarts the entire board and variables, speed, it changes back the html. Basically it's the game again like you've never played it in the first place.

**Note from the author:**

I definitely have a lot more javascript coding to do in my life to allow for me to be 100% comfortable with it. I’m lucky to have some previous coding experience, and to have the access to Youtube and the world wide web! =D
