### Headphones?

### Reading?

## Strudel is a javaScript wrapper for [TidalCycles](https://tidalcycles.org/)
- [Everything is pattern-based](https://tidalcycles.org/docs/reference/cycles)
	- can be unexpected from a conductor's perspective...
- Uses javaScript in the browser (so you don't have to download anything!)
- TidalCycles is a Haskell wrapper for SuperCollider, FYI

## [Strudel](https://strudel.cc/)
- delete welcome shuffle patch!
- play
- update

## mini-tidal starter pattern commands and syntax
`s` = sound

`" "` = what to fit inside one cycle

`~` = silence

`!` = repeat

**starter examples**

`s ("bd")`

`s ("bd hh")`

`s ("bd ~ hh")`

`s ("bd ~ hh!2")`

**everybody now!**

## Strudel
- console
- reference
- sounds
- (but we'll use `bd hh ho sn cp rim` for now!)

## more advanced mini-tidal commands and syntax

`?` = randomly silence

`[]` = nest these within one pulse of the cycle

`[ | ]` = randomly choose sample from this array per cycle

`"< >"` = chose the next one from this list per cycle

`,` = layer these atop one another within one cycle

**more examples**

`s ("hh!16?")`

`s "(bd ~ [hh!2]")`

`s ("[bd | hh | sd]!4")`

`s ("<bd hh sd>!4")`

`s ("bd, ~ hh")`

**everybody now!**

## share a percussion patch

## stacks
- you gotta watch for what the sound source is

`stack(
  "[bd ~ ~ bd] [~ ~ ~ bd] [~ bd bd ~] [~ ~ ~ ~] ",
  "[~ ~ ~ ~] [sd ~ ~ ~] [~ ~ ~ ~] [sd ~ ~ ~] ",
  "[hh ~ hh ~] [hh ~ hh ~] [hh ~ ~ ~] [hh ~ hh ~] ",
  "[~ ~ ~ ~] [ho ~ ~ ~] [~ ~ ho ~] [~ ~ ~ ~] ",
).s()`

## time

- cps

`s("<bd sd>,hh*2").cpm(140/4)`

- fast

`s("bd hh sd hh").fast(sine) `

- slow

`s("bd hh sd hh").slow(2) `

## tidal cycles & its flavors
- tidal cycles: MOST POWERFUL (but needs a lot to get going)
- [estuary: less powerful than strudel but you can play with others](https://estuary.mcmaster.ca/), not covered in this class but you can do it!
- strudel: under development, best when starting, QUITE powerful but you can't play well with others
- in all three of these environments there is a way to run mini-tidal and hydra

### mini-tidal notation comparison
```
// tidal cycles
d1 $ stack[
  s "[bd ~ ~ bd] [~ ~ ~ bd] [~ bd bd ~] [~ ~ ~ ~] ",
  s "[~ ~ ~ ~] [sd ~ ~ ~] [~ ~ ~ ~] [sd ~ ~ ~] ",
  s "[hh ~ hh ~] [hh ~ hh ~] [hh ~ ~ ~] [hh ~ hh ~] ",
  s "[~ ~ ~ ~] [ho ~ ~ ~] [~ ~ ho ~] [~ ~ ~ ~] "
]

// estuary
stack[
  s "[bd ~ ~ bd] [~ ~ ~ bd] [~ bd bd ~] [~ ~ ~ ~] ",
  s "[~ ~ ~ ~] [sd ~ ~ ~] [~ ~ ~ ~] [sd ~ ~ ~] ",
  s "[hh ~ hh ~] [hh ~ hh ~] [hh ~ ~ ~] [hh ~ hh ~] ",
  s "[~ ~ ~ ~] [ho ~ ~ ~] [~ ~ ho ~] [~ ~ ~ ~] "
]

// strudel
stack(
  "[bd ~ ~ bd] [~ ~ ~ bd] [~ bd bd ~] [~ ~ ~ ~] ",
  "[~ ~ ~ ~] [sd ~ ~ ~] [~ ~ ~ ~] [sd ~ ~ ~] ",
  "[hh ~ hh ~] [hh ~ hh ~] [hh ~ ~ ~] [hh ~ hh ~] ",
  "[~ ~ ~ ~] [ho ~ ~ ~] [~ ~ ho ~] [~ ~ ~ ~] ",
).s()

```

## Small assignment for next week! A strudel percussion patch you're proud of.
All in a single markdown file (MD demo)
