# patterns

<!-- N SCALE SYNTH

NOTE PITCH NAME (WITH DEGREE)

ADD OCTAVE info to n scale stuff!!!  

FROM SUPERDIRT:
## N vs Note For Real
- You can never mix "note" and "n" within a single orbit
- With Samples, n meant iNdex, so it was which sample from the index you wanted to play
- With Samples, note meant: take this one sample but slow/speed it up to pitch it down and up and play the pitches as notes
- Now, with Synths: note and n mean the same thing, but you still can't mix them within a single orbit BUT pitch names == scale degree and ARE interchangeable, e.g.
`d3 $ n "0 2 e 6 0 b 6 8" # s "cyclo"`
-->

### samples vs synths

### n vs note
- [`n` is sometimes short for note, sometimes short for 'iNdex', so beware](https://github.com/tidalcycles/strudel/discussions/395)
  - [see also](https://tidalcycles.org/docs/patternlib/tutorials/workshop#difference-between-functions-n-and-note)

## noted

- define by pitch name

`note ("c3").sound("sawtooth")`

- sequence away

`note ("c2 d3 e2").sound("sawtooth")`

- sequence over multiple cycles

`note ("[c3 d3 e3]/4").sound("sawtooth")`

- play one per cycle

`note ("c2 <c 3d e2> e3").sound("sawtooth")`

- scale (use `n`)

`n("0 2 4 6 4 2").scale("C:major").sound("sawtooth")`

**everybody now!**

## share a midi sequence

## [sometimes and its cousins](https://tidalcycles.org/docs/reference/randomness/#the-sometimes-family)
- NEED BETTER DEMO

## sample transformations

- loop at

`samples({ rhodes: 'https://cdn.freesound.org/previews/132/132051_316502-lq.mp3' })
s("rhodes").loopAt(2)`

- begin

`samples({ rave: 'rave/AREUREADY.wav' }, 'github:tidalcycles/dirt-samples')
s("rave").begin("<0 .25 .5 .75>").fast(2)`

## sophisticated pattern transformations

- degradeBy

`s("hh*8").degradeBy(0.2)`

- struct

`note("c,eb,g")
  .struct("x ~ x ~ ~ x ~ x ~ ~ ~ x ~ x ~ ~")
  .slow(2)`

- mask

`note("c [eb,g] d [eb,g]").mask("<1 [0 1]>")`

- palindrome

`note("c d e g").palindrome()`

## sophisticated rhythms

- linger

`s("lt ht mt cp, [hh oh]*2").linger("<1 .5 .25 .125>")`

- euclid

`note("c3").euclid(3,8)`
