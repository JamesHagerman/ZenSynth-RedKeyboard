# Red Keyboard Mod

## The Story

While looking for music toys to circuit bend at an ARC thrift store in Colorado Springs, I came across a $1.49 little red keyboard.

One look, one play, one laugh, many ideas.

### Orignially...

I wanted to make the tiny thing a fat bass synth. Supersaw, PWM sweeps, resonant LPF ramps, hard sync...

### Then...

I got into eurorack years later. And that little red keyboard was still sitting on my shelf. And I had no CV+Gate keyboard...

### So...

I finally, after a lot of thinking, put together a PCB design in Upverter that I could purchase on OSHPark for about $70 for 3x and have at least three little projects.

Due to the price, and the risk of screwing up the first design, I made the thing as modular as possible, while still having a PIC16F690, an MCP4921, a power chip, and some multiplexers broken out.

I also broke out the key pads themselves to their own headers as I knew I'd need to use them again at some point.

## The Code

"As set forth by Morgan and Bartholomew", it's in with a bunch of other projects. Which you've found. Probably.

[https://github.com/JamesHagerman/HardwareProjects/tree/master/PIC%20Work/Red_Keyboard_16f690.X](https://github.com/JamesHagerman/HardwareProjects/tree/master/PIC%20Work/Red_Keyboard_16f690.X)

### PIC16F690

Why I used this chip? Because I had a dev board for it and figured, what the heck, it's probably enough for what I need... I should have used STM32 but, whatever: you **** with the **** you're born with.

I set the thing up to have

### Tuning Process

*Fresh flashes need at least one tuning reset to get things into the ballpark! It should actually be good enough for most purposes...*

This is the fun part (and while I'm finally writing this); there's a bunch of tricks, which I can never remember, to TUNE the silly thing. Here goes:

Hold two highest notes (High E and F) while turning the thing on to enter tuning mode.

Once in tuning mode, these keys do stuff:

```
High C = Pick next Lowest note
High D = Pick next Highest note

High C# = Tune current note DOWN
High D# (Eb) = Tune current note UP

Low C = Reset Tuning to some reasonable settings

Low G = Save tuning and exit tuning mode
```

### Serial output

Yeah, there's a serial console ut on this somewhere... that could help tuning a bit... but you should be able to struggle through it blind... right?
```
    // Setup serial: 9600bps 5v
    TRISBbits.TRISB5 = 1; // RX on pin 12
    TRISBbits.TRISB7 = 1; // TX on pin 10 (this is where you'll see what you're doing...)
```

## The PCB

Since this was the first large project I did on Upverter, it's still there. Mostly since Upverter doesn't have any resonable export tools. I wish I had spent the time learning KiCad instead, but so goes things.

Here's the PCB:

[https://upverter.com/JamesHagerman/4741f7f1c7733770/red-keyboard-simple/](https://upverter.com/JamesHagerman/4741f7f1c7733770/red-keyboard-simple/)