~~~haskell
slow "4 2 5 7 6 4 8" $ iter 3 $ every 5 (jux rev) $ striateBy "8 4 7 4 3" (1/8) $ n (run 26) # s "alphabet:13" #cut 1 #vowel "i i i e e e o o o" #gain 0.8 #hcutoff 1700 #cut 0 #speed (irand 8)

—
stack[
degradeBy 0.9 $ every 8 (jux rev) $ every 2 (stut "<4 8 4 3 4 8 4 5>" "<0.4 0.3 0.4 0.3 0.4 0.1 0.4 0.5>" 0.5) $  s "~ 808bd:1 . 808bd:2 [808bd:4 808bd:1 808bd:1] . 808bd:2 . 808bd:2 " #cut 0 #shape 0.4, 
degradeBy 0.9 $ s " casio:2(4, 16)" #gain 0.8 #hcutoff (range 7000 9000 sine)
]

—
(slow 16) $ s "gretsch:8" #speed 0.1 #cut 1

—
every 7 palindrome $ every 3 (slow 5) $ every 4 (jux rev) $ slow 2 $ striateBy "32 64 128" "<0.125, 0.06125>" $ speed "0.1 .. 0.9" # n (run 16) # s "toys" #gain 0.64 #cut 1

—
slow 8 $ note "< ~ c6'min7 ~!2 . ~ f6'min7 ~!2 >" |< s "padlong" #gain 0.8 #hcutoff (range 100 500 perlin) #cutoff 3000 #delay 0.3 #delaytime 0.1 #delayfeedback 0.9 #cut 1

—
note "0 . ~ . 12" |< s "pebbles" #gain 0.9 #hcutoff (range 100 1000 perlin) #cutoff 1000 #delay 0.3 #delaytime 0.1 #delayfeedback 0.5 #vowel "a e i i i e e i" #begin 0.0 #end 1.0

-----
stack[
every 8 (jux rev) $ every 2 (stut "<4 8 4 3 4 8 4 5>" "<0.4 0.3 0.4 0.3 0.4 0.1 0.4 0.5>" 0.5) $  s "~ 808bd:1 . 808bd:2 [808bd:4 808bd:1 808bd:1] . 808bd:2 . 808bd:2 " #cut 0,

s " casio:2(4, 16)" #gain 0.8 #hcutoff (range 7000 9000 sine)
]

—
(slow 2) $ note "< ~ c3'min7 ~!2 . ~ f3'min7 ~!2 >" |< s "padlong2" #gain 0.8 #hcutoff (range 100 500 perlin) #cutoff 3000 #delay 0.3 #delaytime 0.1 #delayfeedback 0.9 #cut 1

—
(slow 2) $ s "gretsch:8"

—
arpeggiate $ note "~ . ~ . 024?" |< s "tumba*2" #gain 0.9 #hcutoff (range 100 5000 perlin) #cutoff 5000 #delay 0.3 #delaytime 0.1 #delayfeedback 0.5 #vowel "a e i i i e e i"

— 
slice 8 "8 1 3 2 4 6 5 7" $ sound "breath" 

—
iter 3 $ every 5 (jux rev) $ striateBy "8 4 7 4 3" (1/32) $ s "birds:0" #cut 1 #vowel "i i i e e e o o o"

--
stack[
every 8 (jux rev) $ every 2 (stut "<4 8 4 3 4 8 4 5>" "<0.4 0.3 0.4 0.3 0.4 0.1 0.4 0.5>" 0.5) $  s "~ 808bd:1 . 808bd:2 [808bd:4 808bd:1 808bd:1] . 808bd:2 . 808bd:2 " #cut 0,

s " casio:2(4, 16)" #gain 0.8 #hcutoff (range 7000 9000 sine)
]

—
(slow 2) $ note "< ~ c3'min7 ~!2 . ~ f3'min7 ~!2 >" |< s "padlong2" #gain 0.8 #hcutoff (range 100 500 perlin) #cutoff 3000 #delay 0.3 #delaytime 0.1 #delayfeedback 0.9 #cut 1

—
(slow 2) $ s "gretsch:8"

—
arpeggiate $ note "~ . ~ . 024?" |< s "tumba*2" #gain 0.9 #hcutoff (range 100 5000 perlin) #cutoff 5000 #delay 0.3 #delaytime 0.1 #delayfeedback 0.5 #vowel "a e i i i e e i"

— 
slice 8 "8 1 3 2 4 6 5 7" $ sound "breath" 

—
iter 3 $ every 5 (jux rev) $ striateBy "8 4 7 4 3" (1/32) $ s "birds:0" #cut 1 #vowel "i i i e e e o o o"
~~~