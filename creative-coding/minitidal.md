# Minitidal learn notes.
[Minitidal guide](https://pdxopen.tech/courses/algomusic-ii-tidalcycles-midi-and-beyond/lessons/e)

**Cycle**: The basic of time in Tidal. It is by default a little more than two seconds.
Pulse of the pattern: The basic underlying rhythm.

[] Square brackets, group together events.

~ Represents a rest.

`s "[~ bd*2] bd*4 ~ bd*8"`

`stack` Used to put patters together in the same pattern, or play multiple sounds at a time.

`stack [s "bd*4", s "hh27*4 hh*2 " , s "~ sn ~ sn"]`

`(1/8 ~>) $ s "hh27*4"` Shift time transformation

**Euclidean rhythms**

```haskell
stack [s "glitch(<5 7>, 8, <0 1 2>)" # n (irand 4),
            s "linnhats*8? <sn sn*8>" ]
```

`n (irand 8)` Randomize the samples declared before

```haskell
stack  [s "bd*4 <industrial coffee(5, 6) [glitch(2, 6, <0 5>) clubkick(6, 7)] <glitch(1, 5) sd*2>> " ,
 s "hh27*4 [sd? sn(5, 8)]"]
```