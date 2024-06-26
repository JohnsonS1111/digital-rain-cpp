---
layout: post
title: Digital Rain Project Blog
tags: cpp coding project
categories: demo
---
# **Introduction**

<img src="https://raw.githubusercontent.com/JohnsonS1111/digital-rain-cpp/main/docs/assets/images/raining.png">

Greetings, fellow coding enthusiasts!

I would like to present to you my C++ Programming project, which demonstrates a falling matrix effect, something like what can be seen in the movie "The Matrix".
While this project is not up to the standard I would like it to be and it is just a *tad* bit late, I hope you will at the very least enjoy my blog on this project

## Background

**What is a Falling Matrix Effect?** 
This is a piece of code that allows random characters to be printed on the screen in random positions and fall to the bottom of the screen, just like rain. Its pretty cool, and can 
make for a pretty nifty laptop background!

## Research

Before doing this project I had to do some research and see how the falling matrix effect was implemented in different ways and different languages.
One site I looked at indeptly before doing this project was [GeekForGeeks](https://www.geeksforgeeks.org/implementation-falling-matrix/). 
Here they showed in a very simple way how the effect can be created. I also looked many other github repositories, but none of those examples were in C++, so I was not really able to
grasp anything from them.

# **Design and Test**

For the design and testing of the Digital Rain effect, I used Microsoft Visual Studio 2022 as an IDE for writing code and the code was written in Procedural and Object Oriented C++.
To keep it simple, I implemeted simple "getters" and "setters" that allows me to set the screen size (i.e., the area where the rain appears) and the character string, as well as the sleep time (controls the speed at which the rain "falls"). 

Here is My DigitalRain Classs

<img src="https://raw.githubusercontent.com/JohnsonS1111/digital-rain-cpp/main/docs/assets/images/digirain.png">

*Fig. 1 DigitalRain Class in UML Drawing*


Here are the objects I to render the rain

<img src="https://raw.githubusercontent.com/JohnsonS1111/digital-rain-cpp/main/docs/assets/images/Rundigirain.png">

*Fig. 2 Digital Rain Rendering Objects*


## Design : 
The design of the rain was set within the DigitalRain class:

- The width of the rain (the x - axis) determined the maximum distance from the very left of the screen that a character can print.
- the length of the rain (the y - axis) determined the maximum length a character can fall to before being cleared.
- the vector of a string deteremined the characters that could be printed on the screen.
- the sleep time controlled the speed at which a character would wall down the screen.
- the count simply keeps a count of every `DigitalRain` object created.

<img src="https://raw.githubusercontent.com/JohnsonS1111/digital-rain-cpp/main/docs/assets/images/getset.png">

*Fig. 3 DigitalRain class*


## Testing :
Testing and rendereing of the rain was doing in RunDigitalRain. I untilised procedural programming and object oriented programming in RunDigitalRain.

- ClearScreen(): this function is called to clear the screen whenever a print had finished
- DisplayRain(): calls other functions to properly display the rain on the screen.
- InitRain(): Initialises raindrops
- UpdateRain(): updates the positions of the rain droplets on the screen
- RenderRain(): renders rain on the screen and chooses where the next rain droplet should print

<img src="https://raw.githubusercontent.com/JohnsonS1111/digital-rain-cpp/main/docs/assets/images/display.png">

*Fig 4 Rain Display objects*

# **Algorithms**

## Initialisation / Updating

For the most part, the algorithms used were quite simple. I had tried to use more complex algorithms  like `for each` and `sort` to sort through each 
character in the string but was unable to get that code to function the way in wanted it to. In the end I mostly used `if` statements and `for` loops.
In `InitRain()` I used a simple if statement to initialise the raindrops. The struct for this is set in the RunDigitalRain.cpp file. 

<img src="https://raw.githubusercontent.com/JohnsonS1111/digital-rain-cpp/main/docs/assets/images/initrain.png">

*Fig 5*

I decided to used a structure for the rain as 
it made passing and managing raindrops in each function more straightforward.

<img src="https://raw.githubusercontent.com/JohnsonS1111/digital-rain-cpp/main/docs/assets/images/struct.png">

*Fig 6*


In `UpdateRain()` the position of a raindrop is being updated. `raindrops[i].y++` moved the rain drop down the screen. So rather than printing the blank spaces above the character,
the character position on the y - axis was being incremented by 1.

<img src="https://raw.githubusercontent.com/JohnsonS1111/digital-rain-cpp/main/docs/assets/images/updaterain.png">

*Fig 7*


## Rendering

The line `for (const std::string& str : dr.GetCharacterString())` stored the vector of strings into a const string. This is to allow the string to be printed separately. **More about that in Problem Solving**. 
At first, I had planned to use COORD to designate the position at which each character would start at, but i ended up only using the ANSI escape sequence instead.
The raindrops are printed in CYAN. Unfortunately, I was unable to cycle through the defined colors so that each droplet was a diffrent color.

<img src="https://raw.githubusercontent.com/JohnsonS1111/digital-rain-cpp/main/docs/assets/images/render.png">

*Fig 8*


# **Problem Solving**

I faced many problems when doing this project, which came mostly from the using a vector of a string and displaying each character from that vector on the screen.
I was able to access separate characters in the vector but unable to print all of them. I could only print the last character in the string.
I had search online and looked into multiple resources on how to fix this issues but I was unable to find the reason for this. I looked at my algorithms and how I was printing characters on the screen.
In theory, getting the string out of the vector and then separating each character in the string to be printed in succession should work.

<img src="https://raw.githubusercontent.com/JohnsonS1111/digital-rain-cpp/main/docs/assets/images/render2.png">

*Fig 9 Sorting through the vector*

My only guess as to why this could not work is because of the if statement `if (raindrops[i].active = true)`. It could be an issue of the operation never leaves the if statement because `raindrop[i].active` is always true. I tried to manipulate the loop and also used the `std::sort` algorithm, but I was unable to fix that issue.

Originally, I had planned for each character to be printed in a different color, but I was unable to correctly apply that feature.

<img src="https://raw.githubusercontent.com/JohnsonS1111/digital-rain-cpp/main/docs/assets/images/colors.png">

*Fig 10 Defined colors*

As shown above, I already had all the colors I wanted to use defined.

One problem I did overcome was setting the character in a new position. I did not want to move a character down the screen by printing spaces above that character, so instead,
I did that by clearing the screen and reprinted it in a lower area of the screen (`raindrops[i].y++`). This was a major problem which, among other things, contributed to the many problems and bugs I found in my project.

# **Conclusion and Result**

I was able to create a Digital Rain Project using Procedural C++ Programming and Object Oriented Programming to creted multiple DigitalRain objects, pass objects between files and used them. I was able to define a character string, screen length and width and a sleep time to suit my own liking and I was able to make use of algorithms to create a falling matrix effect.

<img src="https://raw.githubusercontent.com/JohnsonS1111/digital-rain-cpp/main/docs/assets/images/Rain.gif">

*Fig 11 Final Product*

## Thank you for Reading this Blog!!!
