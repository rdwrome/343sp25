# patterns

## samples vs synths

### n vs note
- You can never mix "note" and "n" within a single expression
- With Samples: n means iNdex, so it was which sample from the index you wanted to play
- With Samples: note means: take this one sample but slow/speed it up to pitch it down and up and play the pitches as notes
- With Synths: note and n can mean the same thing, but you still can't mix them within a single expression BUT pitch names == scale degree and ARE interchangeable, e.g.
`note ("0 2 e 6 0 b 6 8")`

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

- scale with rand.range (not in tidal cycles!) and segment (IS in tidal cycles!)
`n(rand.range(0,12).segment(8))
.scale("C:major")
.s("sine")`

**everybody now!**

## share a midi sequence

## sample transformations

- loop at

`samples({ rhodes: 'https://cdn.freesound.org/previews/132/132051_316502-lq.mp3' })
s("rhodes").loopAt(2)`

- begin

`samples({ rave: 'rave/AREUREADY.wav' }, 'github:tidalcycles/dirt-samples')
s("rave").begin("sine").fast(2)`

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
### what are euclidean rhythms?

- linger

`s("lt ht mt cp, [hh oh]*2").linger("<1 .5 .25 .125>")`

- euclid

`note("c3").euclid(3,8)`

## Small assignment for next week! A strudel patch you're proud of.
- All in a single markdown file (MD demo)