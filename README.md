# Pulseaudio-Latency-Utility
A little script to adjust Pulseaudio sink latency. Created so that osu! won't lag.

# Disclaimer
I'm pretty much a newb in bash (and Pulse), so don't expect much :D

# Usage
To adjust latency of the active device, write in the terminal
```
pulse_set_fragments.sh <FRAGMENTS> <FRAGMENT SIZE>
```
In short, fragments define audio buffer size. The bigger its size, the bigger the audio delay is and so will be the audio output consistency. You want to set it as low as possible so that sound won't crackle.
By default <FRAGMENTS> = 1, <FRAGMENT_SIZE> = 1000, which may be not enough.

# Checking latency
I am not certain whether it's the correct method to do it. In terminal write
```
pactl list sinks | grep Latency
```
It will print all sinks with their latency.

# Example
My audio card is Creative Sound Blaster Omni Surround. By default the latency is 100ms, which is unplayable in osu!. With
```
pulse_set_fragments.sh 1 350
```
it becomes becomes 2ms! 
For speakers in monitor BENQ EW2750 I had to use
```
pulse_set_fragments.sh 1 3000
```
which results in 15ms, which is great too.
