# 🎵 Semitonal Distance Calculator 🎵

See it live at https://semitonal-distance.surge.sh/

## Usage
The Semitonal Calculator is a straightforward website with a singular purpose: to calculate the amount of semitones leading up to a note from 0.

## What is a semitone? 

A semitone, aka a half-step, is the smallest interval used in classical Western music, equal to a twelfth of an octave.

## Context 📚

In Western music theory the pitch of every note is defined by three qualities: the note's octave, letter, and alter.

**The Octave** An octave is the distance between one pitch and another with is double it's frequency. Every octave is divided into 12 semitones.

**The Musical Alphabet** The Musical Alphabet "A B C D E F G" defines every note in an octave. 

**The Alter** The Alter represents the chromatic alteration of a note in semitones (e.g., -1 for flat, 1 for sharp)

Note that there are only 7 letters in an octave but 12 semitones that make up that octave. In a base scale without sharps or flats the semitones of an octave that aren't decided by the letter are done with chromatic alterations following this pattern: *"A-BC-D-EF-G-"*. The dashes represent the chromatic alteration and are usually assigned a sharp (♯) or flat (♭) symbol depending on the context. 

## How It Works ⚙️

The basic idea behind this calculator is to caculate the total number of semitones in two separate notes and then return the difference between them with an absolute value.

It's easy enough to total the number of semitones in an octave and alter for an individual note but to calculate the total number of semitones leading up to the letter you'll need some kind of context to decide what letter starts the octave. Typically you use C-Major as the base as it is the only major scale without any accidentals, there's a lot of historical reasons behind this but they're beyond the scope of this project. The logic behind this scale and the semitones that make it up are going to have to be hard-coded in as there is no musical alphabet inherent to programming.

This is the basic function I created to find the total number of semitones in an individual note: 

```
	function semitonalCalculator(octave,letter,alter){
		let baseScale = 'C-D-EF-G-A-B';
		//used to determine a value for the letter
		//in calculating semitonal distance it is important that the baseScale used for each note is the same

		let octaveTotal = octave * 12
		//12 semitones in an octave

		let letterTotal = basicScale.indexOf(letter)
		//letter value in semitones
        
		let semitonalTotal = octaveTotal+letterTotal+alter
		return semitonalTotal
	}
```

Then to find the semitonal distance between two different notes you simply find the difference between the total amount of semitones of each note.


