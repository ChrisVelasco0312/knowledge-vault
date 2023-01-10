rida```
	note (scale "plus" "2 2*4 3 <3 <5 2>>") # s "arpy" # n (irand "5")

```haskell
stack [ every 2 (slow 2)
  $ fast 2
  $ s "glitch:5(4,8) casio:1(3,8)"
  # pan sine
  # speed (cosine + 0.6)
  # gain "0.2"
  + accelerate (-4),
  (slow 4)  $ s "gretsch(8,12)" # speed 0.1 # cut 2 # n (irand 8) # gain "0.4",
  every 2 (striate 2) . every 4 (slow 2) 
  $ n "1 2 3 4 5" # s "numbers" # gain 0.3 # cut 9  # speed "0.3"
]
```