# Greetings
I've been very interested in getting back into writing algorithmic electronic music from scratch. Its what I spent a great deal of time on in undergrad
using software like [MaxMSP](https://cycling74.com/products/max/) and [PureData](https://puredata.info/). Heres a piece from my 'senior project' called [Crystal Growth](https://soundcloud.com/nickgideo/crystal-growth).  

When I started with using MaxMSP and PD, I barely knew anything about programming. For instance, Crystal Growth could have easily been 
constructed from a set of loops, but because I didn't understand how to use loops I basically hard-wired everything. 
If you look at the lower right corner of the image below you'll see a daisy-chain of delays. Each delay corresponded to a single
triggering of a note played by an oscillator (an object that makes a single sound). Clearly, this was not a scaleable way to make music!

![Lots of duplicated delays](crystal-growth.jpg)


After graduating, I stumbled into a job where I needed to learn how to organize things in spreadsheets. Google Apps (docs, sheets, etc) 
has a neat feature that lets you write scripts using JavaScript, so I started teaching myself a *real* programming language. I quickly
realized how idiotic I was to not have used loops in my previous programming efforts. Also, In Max and PD, you 'write code' by clicking
and dragging 'wires' that connect object blocks. This is *INCREDIBLY* tedious for a large program (see above) so I hoped that someday I 
could find a way to write algorithmic electronic music using a programming language without having to use a damn mouse! 

Eventually, I discovered [SuperCollider](https://supercollider.github.io/), but I was still too green to understand its wacky syntax 
(more on this later) and I had more to learn about basic programming and comp-sci fundamentals before I could really grok how to use it.
Fast forward a few years to today where I feel ready to start exploring and writing about the journey. 

# First Impressions

As I said before, my first *real* language (if you can call it that) was JavaScript. Its syntax and semeantics feels like *home*, so it's
what I compare to when I learn a new language. Lisp was hard because it felt like everything was upside down and inside out. C++ was full
of pitfalls, and I missed first class functions. Python was like writing prose. SuperCollider so far is.. *"Wat?"*. 

## Variables and Scope and Functions, oh my!

Awesome, so I'm looking at this language now and it looks neat. A little *wierd*, but neat. I boot up the audio-server with CMD-B 
and try to remember how to make a sound. I think I know how it works so lets see. 
The IDE has nice code-execution with SHIFT-ENTER running each line, so I hit that after writing each line below. 
So lets make an oscillator and make a sound
``` SuperCollider
x = SinOsc.ar
x.play
```
Output:
``` console
-> a SinOsc
ERROR: Message 'play' not understood.
...
```
Oh, crap. *Right!* I forgot that you need to put curley brackets around the synth like so:
``` SuperCollider
x = {SinOsc.ar}
x.play
```
``` console
-> a Function
-> Synth('temp__1' : 1000)
```
Sweet! This plays a sine-wave generator (the part that says `-> Synth('temp__1' : 1000)` in the post window) at the default 440hz. 
Hitting CMD-. (ie the command key and a `.`) kills the sound. So whats the deal with the curleys that I needed? As you can see above, 
wrapping statements in curleys turns it into a function (as noted in the post window when it printed `-> a Function` after I evaluated
that line). Since synths don't have a `play` method, but functions do, we need to wrap code up in curleys to make sure we can execute it
as a sound generator. Ok, sure. Thats fine. 

Now I'd like to 
