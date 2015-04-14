---
layout: post
title: Getting quicker with Vim
---

learning vim and practicing for the kata
roman numerals kata
searching for vim shortcuts to cut down on the time

what I am doing to improve for Friday

I will be performing a code kata this Friday for [8LU][1] as mentioned in my previous post.
As I have never used Vim in anger, I have slowly been getting to grips with the editor.

## No mouse
I have set up Tmux and Vim, similar to the other craftsmen and apprentices at 8th Light.
As in Vim you can not really use the mouse and are encouraged to keep you figures on the home keys. The different modes make it interesting when you first start using Vim as you actually need to switch into INSERT mode before getting any characters to appear where you want them.

Navigating around the page is all handled from the key board. H, J, K and L are the basic left, right, up, down character movements but even these should only be used sparingly.

## Slowly learning shortcuts

Repeating the Roman Numerals kata has helped me identify areas that I am slow in Vim. 
When ever I feel like editing is taking longer then I should, I did a quick google to see if there were any better ways of doing it.

Here are a few I've found so far:

### Yanking (copying) lines

This nice [Q and A][2] on StackOverFlow revealed some nice syntax for indicating which lines to copy.

There was also an answer about using ``` gg ``` after typing in the line number to jump directly to the line which was pretty useful.

### Jumping forward or back to the first character on a line

Using ``` f ``` or ``` F ``` to jump forward or back to the character you type helped me make fast edits when I need to change a number on a line.

### Built in auto complete

Using some of the auto complete functions built into Vim as indicated in this [article][3] also helped me speed up the kata.


## Improving with every practice

As I keep repeating the kata I slowly improve my speed and get ideas on what next to look up in regards to advanced Vim topics.
I know Vim is one of the editors that takes years to master. I may not be as fast as in a normal editor at the moment but I'm looking forward to getting faster and more efficient in the coming days, months and years. 


[1]: http://university.8thlight.com/
[2]: http://stackoverflow.com/questions/2023015/vim-yanking-range-of-lines
[3]: https://robots.thoughtbot.com/vim-you-complete-me
