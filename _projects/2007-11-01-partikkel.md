---
title: "Partikkel - granular synthesis"
header:
  teaser: /assets/img/Particle-generator.png
tags: writing dsp
layout: single_tagged
classes: wide
---

Partikkel is designed to enable all types of granular synthesis in one single sound generator, with the aim of providing the maximum amount of timbral variation. As a generalized implementation enabling all known varieties of audio particle synthesis in one single generator, it will facilitate new forms of the synthesis technique. To enable the use of such a generalized granular generator in a broader context, it was implemented in an already existent audio processing language. To broaden the context as much as possible it would be preferable to use an open source language with a large library of signal processing routines already in place. The audio processing language would need to have interfaces to common production environments (Digital audio workstations for studio and stage, web applications, embedded computers, ...). To comply with these requirements, we chose to implement the new generator as an opcode for the audio programming language Csound. The opcode was given the name partikkel.  


<audio controls="controls">
  <source type="audio/mp3" src="{{ site.baseurl }}/assets/sound/partikkel_morf.mp3"></source>
  <p>Your browser does not support the audio element.</p>
</audio>
*Audio example of long continuous sound transformation by a single instance of partikkel*

An initial article describing the opcode and its purpose can be found in [Particle synthesis - a unified model for granular synthesis](http://lac.linuxaudio.org/2011/papers/39.pdf) by &Oslash;yvind Brandtsegg, Sigurd Saue and Thom Johansen.  
I also wrote an in-depth chapter on the applications of partikkel to various forms of audio processing in [Granular Synthesis](https://link.springer.com/chapter/10.1007/978-3-319-45370-5_15) in the book [Csound A Sound and Music Computing System](https://link.springer.com/book/10.1007/978-3-319-45370-5) edited by Victor Lazzarini.   
A user manual for the opcode can be found in the [official Csound documentation](https://csound.com/docs/manual/partikkel.html). Other opcodes supporting the operation of partikkel are [partikkelsync](https://csound.com/docs/manual/partikkelsync.html), [partikkelget](https://csound.com/docs/manual/partikkelget.html) and [partikkelset](https://csound.com/docs/manual/partikkelset.html)
 
### Background for partikkel:  
In my doctoral artistic project, I built improvisation software with algorithmic composition techniques. In this context, I needed a very flexible sound generator, as my aims for the improvisation software was that it could immediately react to changes in the musical situation. Software modules would listen to what was played by other performers, and create musically appropriate responses. Obviously, this relates not only to event generation (which notes to play), but also to instrumentation and timbral modulation. This would require the sound generator module to completely change timbre, in extreme cases right in the middle of a held note, to adapt to changes in the musical environment. In order to enable this timbral agility, I needed a sound generator that would enable the widest possible selection of available sounds, all available by parametric changes to one single synthesizer. If we browse the available techniques in the dsp literature, looking for single techniques that allow for extreme sonic flexibility, we find both spectral techniques (FFT, phase vocoder, etc) and granular synthesis. Since the improvisation software was aimed at a realtime application with low latency, and spectral techniques inevitably will come with a latency penalty (related to fft size), I opted for granular processing in time domain. The opcode [partikkel](https://csound.com/docs/manual/partikkel.html) was conceived after reading Curtis Roads' book "Microsound", and the goal was to create an opcode that was capable of all time-domain varieties of granular synthesis described in this book. The idea being that most of the techniques only differ in parameter values, and by having a single opcode that can do all varieties of granular synthesis makes it possible to interpolate between techniques. Granular synthesis is sometimes dubbed particle synthesis, and it was thought apt to name the opcode partikkel to distinguish it from other granular opcodes. The architecture and functional design of partikkel was done by myself, and it was implemented by Thom Johansen and Torgeir Strand Henriksen who were acoustics students at NTNU at the time.
