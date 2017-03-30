Audio spectrum heatmap visualization
====================================

This little program continually generates a spectrum from a live audio source (like a microphone or the system audio monitor) and shows it as heapmap. The horizontal axis represents time, the vertical axis represents frequency (with a linear scale by default) and the color represents the amplitude of the harmonic with that frequency at that point of time.

![](http://i.imgur.com/FuCxWIO.png)

<small>The above screenshot is from the Pokemon Ruby Wild Battle song.</small>

Demo
----

A wave generator is useful to test how it works. Here is one that runs in the browser:

* http://js.do/blog/sound-waves-with-javascript/

Chiptune songs are quite interesting to visualize, for instance.

* [Youtube: Pokémon: All Starting Town Themes](https://www.youtube.com/watch?v=a6BNA1_H310&index=2&list=PLYoH_H6bypnkwWeWitN-r5fShyaOTdTmj)
* [Youtube: Pokémon: All Wild Battle Themes](https://www.youtube.com/watch?v=a6BNA1_H310&list=PLYoH_H6bypnkwWeWitN-r5fShyaOTdTmj&index=2)

How to build
------------

This application uses GStreamer, Clutter and GLib, so make sure to install development packages of these first. Also, the CMake build system is needed to build the project.

```
mkdir build && cd build
cmake ..
cmake --build .
./audio_heatmap
```

Technical parameters
--------------------

Sampling frequency: 8000 Hz (therefore the maximum readable frequency is 4000 Hz)
Number of bands: 600 (133.3 Hz each)
Spectrum interval: 10 ms
Minimum harmonic amplitude: -80 dB
Maximum harmonic amplitude: -20 dB

##Color coding

An intensity value between zero and one is generated by scaling the amplitude of the harmonic within its admitted range (-80 dB is zero, -20 dB). Optionally, the result is multiplied by a *gain* value that can be set to better visualize too loud or too quiet audio pieces.

A gradient is then used to color code the result:

* 0.0 is mapped to black (#000000).
* 0.2 is mapped to blue (#0000FF).
* 0.4 is mapped to cyan (#00FFFF).
* 0.6 is mapped to yellow (#FFFF00).
* 1.0 is mapped to white (#FFFFFF).

License
-------

Copyright 2017 Alicia Boya García

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.