## homework?

## effected

- pan

`s("[bd hh]*2").pan("<.5 1 .5 0>")`

- gain

`s("hh*8").gain(".4!2 1 .4!2 1 .4 1")`

`note ("c <c d e> e").sound("sawtooth").lpf("<400 500>").gain(1.2)`

- low/high pass filter

`note ("c <c d e> e").sound("sawtooth").lpf("<400 500>")`

- crush

`s("<bd sd>,hh*3").fast(2).crush("<16 8 7 6 5 4 3 2>")`

- vowel

`note ("c <c d e> e").sound("sawtooth").lpf("<400 500>").vowel("<a e i o u>")`

- x fade

`xfade (s("bd*2"), "<0 .25 .5 .75 1>", s("hh*8"))`

- room

`s("bd sd [~ bd] sd").room("<0 .2 .4 .6 .8 1>")`

- evaluation
`
$: n("[0 .. 8]*8/9").scale("C:minor:pentatonic")

// command-/
//$: s("bd*4").bank('RolandTR909')
`

## project

## [strudel + hydra](https://strudel.cc/learn/hydra/)