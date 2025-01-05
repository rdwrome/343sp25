# Tidal Cycles

### starting up refresher
    - select your preferred audio output device in AudioMidi Setup
    - open SuperCollider
    - execute `SuperDirt.start;` with shift, return
    - does your preferred audio output device get listed?
    - are they the same sample rate?
    - does it say `SuperDirt: listening to Tidal on port 57120`? (this will take a moment)
    - open a .tidal file in Pulsar
    - execute TidalCycles code with shift, return in Pulsar
    - monitor in Pulsar and SuperCollider post windows
    - (did you already know a little sc? SuperDirt the quark boots sc itself, so please don't boot before using the quark)

## Tidal Cycles
### [Tutorials](https://tidalcycles.org/docs/patternlib/tutorials/workshop)
### [Reference](https://tidalcycles.org/docs/reference/cycles)
### [Discourse](https://club.tidalcycles.org/)
### [Great Haskell Help](https://learnyouahaskell.com/chapters)

### [MiniTidal/MiniNotation](https://tidalcycles.org/docs/reference/mini_notation)
`s` = sound

`" "` = what to fit inside one cycle

`~` = silence

`!` = replicate

`[ ]` = nest these within one pulse of the cycle

`,` = layer these atop one another within one cycle

`[ | ]` = randomly choose sample from this array per cycle

`?` = randomly silence

`( , )` = spread this many pulses over this many pulses per cycle

now = `< >`, ` / `, `{ }%`

### new to us from minitidal
- [i make money moves: the meaning(s) of `$` and orbits](https://tidalcycles.org/docs/innards/meaning_of_dollar)
- [operators](https://tidalcycles.org/docs/reference/pattern_structure)

## execute
  - shift, return for one line
  - control, return for multiple lines
  - `hush`
  - `# silence`
  - `-- comment`
  - need to change audio output device?: `Server.default.options.outDevice_("External Headphones");`

### mixing and effects
- xfade. orbit name is argument.

`d1 $ s "hh*16?"`

`xfade 1 $ s  "909*16?"`

- djf. lpf/hpf with 0-1 argument.

`d1 $ s "hh*16?" # djf sine`

- hbrick. spectral high pass with 0-1 argument.

`d1 $ s "hh*16?" # hbrick sine`

- lbrick. spectral low pass with 0-1 argument.

`d1 $ s "hh*16?" # lbrick sine`

- shape. parametric amplifier with 0-1 argument.

`d1 $ s "hh*16?" # shape sine`

- crush. bitcrush with 1-16 argument

`d1 $ s "wobble" # crush "[2 | 16]"`

- squiz. weird pitchshifter with arguments in multiples of two.

`d1 $ s "wobble" # squiz "[2 | 16]"`

## For next week:
- Make one TidalCycles patch you're proud of to share with the class.
- Document how you made the patch using the "Documentation outline" in the syllabus. Add that documentation and the patch itself to a Markdown file.
- Submit via your lc repo AND Canvas.
