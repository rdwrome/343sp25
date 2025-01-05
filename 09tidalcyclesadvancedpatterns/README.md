# SuperDirt

## N vs Note For Real
- You can never mix "note" and "n" within a single orbit
- With Samples, n meant iNdex, so it was which sample from the index you wanted to play
- With Samples, note meant: take this one sample but slow/speed it up to pitch it down and up and play the pitches as notes
- Now, with Synths: note and n mean the same thing, but you still can't mix them within a single orbit BUT pitch names == scale degree and ARE interchangeable, e.g.
`d3 $ n "0 2 e 6 0 b 6 8" # s "cyclo"`

## yes, you can change bps
`setcps (115/60/4)`

### samples

### selecting specific samples in a group

- striate. cuts sample into the parameter, plays progressive cut per loop. (can't use with pattern, but we'll get to that with "slice").

`d5 $ striate 3 $ s "print:0 print:1 print:2"`

- begin. where to begin in sample.

`d6 $ s "bev" # begin 0.5`

- end. where to end in sample.

`d6 $ s "bev" # begin 0.5 # end 0.65`

- loop. argument is to stretch the sample over these many patterns, then start again.

`d6 $ loopAt 8 $ s "bev"`

- slice. first argument is how many slices to make of the sample, second argument is which sample to choose per pattern.

`d6 $ slice 16 "[2|4|8|16]" $ s "bev"`

- random slice. argument is how many slices to make of the sample, which one is random.

`d6 $ randslice 8 $ s "bev"`

### advanced pattern transformation

- one hit. NO ORBIT!

`once $ s "xmas"`

- arp, slow, hurry

`d2 $ slow 2 $ note (arp "<converge diverge pinkyup pinkyupdown thumbup thumbupdown>" "<d'major a'major>") # s "newnotes"`

- [sometimes and it's cousins](https://tidalcycles.org/docs/reference/randomness/#the-sometimes-family)

- palindrome. reverses pattern every other cycle.

`d2 $ palindrome $ note (arp "<converge diverge pinkyup pinkyupdown thumbup thumbupdown>" "<d'major a'major>") # s "newnotes"`

`d2 $ sometimes (palindrome) $ note (arp "<converge diverge pinkyup pinkyupdown thumbup thumbupdown>" "<d'major a'major>") # s "newnotes"` !-->

- degrade. randomly removes events from a pattern half the time.

`d2 $ degrade $ note (arp "<converge diverge pinkyup pinkyupdown thumbup thumbupdown>" "<d'major a'major>") # s "newnotes"`

`d2 $ sometimes (degrade) $ degrade $ note (arp "<converge diverge pinkyup pinkyupdown thumbup thumbupdown>" "<d'major a'major>") # s "newnotes"`

- degradeBy. randomly removes events from a pattern a specified percentage of the time.

`d3 $ degradeBy 0.3 $ "reverbkick*4"`

- linger. truncates a pattern then repeats the truncation.

`d2 $ linger "[0.25 0.5 0.75]" $ degrade $ note (arp "<converge diverge pinkyup pinkyupdown thumbup thumbupdown>" "<d'major a'major>") # s "newnotes"`

- [chunk'. divides a pattern into parts, applies function to each part, reverses some(that's what the apostrophe at the end is about)](https://tidalcycles.org/docs/reference/alteration/#chunk-1)

`d5 $ chunk' 3 (hurry 2) $ n ("7 2 [3 2] ~") # s "print"`  

- operators a la rachelle with samples (pentatonic clusters + just a *touch* of randomness)

`d5 $ n ("1 ~ 2 [3 2] ~" |+ irand 11) # s "print"`

## Recording
```SuperCollider
s.record;
s.stopRecording;
```

## [Sending Clock](https://tidalcycles.org/docs/configuration/MIDIOSC/midi/#synchronising-midi-clock)

## [Multichannel](https://tidalcycles.org/docs/configuration/AudioConfig/audio_outputs/)
```SuperCollider
(
s.options.numBuffers = 1024 * 256;
s.options.memSize = 8192 * 32;
s.options.maxNodes = 1024 * 32;
s.options.numOutputBusChannels = 4; // total number of channels output
s.options.numInputBusChannels = 2;

s.waitForBoot {
~dirt = SuperDirt(4, s); // pan across four channels
~dirt.loadSoundFiles;
~dirt.start(57120, 0 ! 12); // start superdirt, listening on port 57120, create twelve orbits each sending audio to channel 0
};
s.latency = 0.3;
);
s.record(numChannels:4); // output channels again
s.stopRecording;
```

## So you want your own samples...
```SuperCollider
(
s.options.numBuffers = 1024 * 256;
s.options.memSize = 8192 * 32;
s.options.maxNodes = 1024 * 32;
s.options.numOutputBusChannels = 2; // total number of output channels
s.options.numInputBusChannels = 2;

s.waitForBoot {
    ~dirt = SuperDirt(2, s); // total number of output channels
	~dirt.loadSoundFiles;
    ~dirt.loadSoundFiles("/Users/rrome/Documents/GitHub/mehetabel/Dirt/samples/**"); // specify sample folder to load THIS IS THE RACHEL PATH
    s.sync; // wait for supercollider to finish booting up
    ~dirt.start(57120, 0 ! 12); // start superdirt, listening on port 57120, create twelve orbits each sending audio to channel 0
};
);
```

## For next week:
- Make one TidalCycles patch you're proud of to share with the class.
- Document how you made the patch using the "Documentation outline" in the syllabus. Add that documentation and the patch itself to a Markdown file.
- Submit via your lc repo AND Canvas.
