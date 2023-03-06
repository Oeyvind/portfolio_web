---
title: "Liveconvolver"
header:
  teaser: /assets/img/liveconv-gui.png
tags: writing dsp
layout: single_tagged
classes: wide
---

As part of the project  [Cross adaptive processing as musical intervention](http://crossadaptive.hf.ntnu.no), I collaborated with Sigurd Saue on developing a convolution technique allowing live sampling of the impulse response, meaning that we could do convolution between two realtime audio streams. This enabled realtime improvised cross-adaptive modulation between the sounds coming from two musicians. The ability to *play through the sound of the other* led to the potential for new performative interactions through timbral and rhythmic merging of the instrument sounds.  

Convolution has been used for filtering, reverberation, spatialisation, and as a creative tool for cross-synthesis in a variety of contexts. Common to most of them is that one of the inputs is a time-invariant impulse response (characterising a filter, an acoustic space or similar), allocated, and preprocessed prior to the convolution operation. The time-invariant nature of the impulse response (IR) has inhibited a parametric modulation of the process. Modifying the IR traditionally has implied the need to stop the audio processing, load the new IR, and then re-start processing using the updated IR.   

![Liveconvolver GUI]({{ site.baseurl }}/assets/img/liveconv-gui.png)  
*User interface of the Liveconvolver VST plugin*

By using incremental updates of the filter, the impulse response updates can be done without introducing artefacts in the audio output. The filter is updated at the same rate as it is consumed by the autio input stream. This means that no part of the input audio ever crosses the (incrementally shifting) update point, where we would potneitally find a discontinuity that would create artifacts.  
![Incremental updates]({{ site.baseurl }}/assets/img/liveconv-applsci-08-00103-g004.png)  
*Snapshots of the incremental filter update*


A full paper on the subject can be found in [Live Convolution with Time-Varying Filters](https://www.mdpi.com/2076-3417/8/1/103) by &Oslash;yvind Brandtsegg, Sigurd Saue and Victor Lazzarini.  
The user manual for the liveconv opcode  can be found in the [official Csound documentation](https://csound.com/docs/manual/https://csound.com/docs/manual/liveconv.html).   

