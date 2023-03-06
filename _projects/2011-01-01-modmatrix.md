---
title: "Modmatrix"
header:
  teaser: /assets/img/Hadron-modmatrix.png
tags: writing dsp
layout: single_tagged
classes: wide
---

Modmatrix is a flexible mapping technique realized as a many-to-many dynamic mapping matrix. Digital sound generation is typically controlled by a large number of parameters and efficient and flexible mapping is necessary to provide expressive control over the instrument. Modmatrix may be seen as a generic and selfmodifying mapping mechanism integrated in a dynamic interpolation scheme. It is implemented efficiently by taking advantage of its inherent sparse matrix structure. Even if the full matrix can allow a large number of inputs and outputs, only the active matrix connections are calculated.   

The origin of the modulation matrix is found in the patch bays of old analogue synthesizers, where patch cords interconnected the various synthesizer modules. In 1969 the English company
Electronic Music Studios (EMS) introduced the VCS3 with a unique matrix patch system to replace the clutter of patch wires (see front left panel in Figure 1 under). Signal routing was accomplished by placing small pins into the appropriate slots in the matrix. 

![EMS-VC3]({{ site.baseurl }}/assets/img/330px-EMS_VCS_3.jpg)  
*The classic EMS VC3 with the modulation  matrix activated by inserting pins into the switchboard*

The modmatrix opcode followed a similar architecture, but uses a gain coefficient matrix instead of the switching pins known from the EMS VC3. This allows independent scaling of each modulator to each parameter. Transforming the gain coefficient matrix then dynamically changes the routing of modulators. The image below shows a simplified example with a reduced-size matrix.  
![modmatrix-2x2]({{ site.baseurl }}/assets/img/modmatrix_simple2x2.png)  
*Dynamic modulation matrix, simplified to 2 parameters and 2 modulators*

Feedback in the moduation matrix can be enabled by also including the modulation parameters as modulation targets. Here the modulation parameters are amplitude and frequency of a low frequency oscillator.  
![modmatrix-2x2]({{ site.baseurl }}/assets/img/modmatrix_simple2x4.png)  
*Dynamic modulation matrixwith feedback*

A full paper on the subject can be found in [A modulation matrix for complex parameter sets](https://www.nime.org/proceedings/2011/nime2011_316.pdf) by &Oslash;yvind Brandtsegg, Sigurd Saue and Thom Johansen.  
The user manual for modmaxtrix can be found in the [official Csound documentation](https://csound.com/docs/manual/modmatrix.html).   



### Background for modmatrix:  
During the work on Hadron Particle synthesizer, I needed a method to efficiently patch a large number of modulators to a large number of synthesis parameters in a dynamic manner. In Hadron, we have 209 synthesis parameters and 52 modulators. To enable the morphing between instrument states (that is a core component of Hadron), we also needed to be able to dynamically morph the modulation matrix, making a gradual transition from one modulation mapping to another. This instiaged the design of modmatrix.
The architecture and functional design of modmatrix was done by myself, and it was implemented by Thom Johansen.
