# Open303

Open303 is a free and open source emulation of the Roland TB-303 bass synthesizer.

### Credits and Attribution

This repository is a clone and continuation of the original Open303 source code developed by Robin Schmidt ([www.rs-met.com](https://www.google.com/search?q=https://www.rs-met.com)). The original project was hosted at [https://sourceforge.net/projects/open303/](https://sourceforge.net/projects/open303/).

I am not the original author of this software. This fork serves to preserve, update, and improve upon the original work.

### Project Goals

The primary objective of this repository is to modernize the plugin format support. Specifically, this project aims to implement the CLAP plugin standard, as the original VST 2.4 format is now deprecated. This codebase serves as a foundation for learning and implementing the new SDK.

### DSP Improvements and Authenticity

Several updates have been made to the Digital Signal Processing (DSP) core to align the emulation more closely with the behavior of the original analog hardware:

* **Asymmetrical Filter Distortion:** The filter's shaping function has been updated to include a DC bias. This simulates the asymmetrical clipping behavior of the original transistors, introducing even-order harmonics for a warmer sound.
* **Non-Linear Feedback Loop:** The feedback path in the diode ladder filter now processes the signal through a non-linear shaper before re-entering the input. This creates the distinct "squelch" and liquid character associated with the 303 filter resonance.
* **Authentic Passband Attenuation:** The artificial gain compensation found in the original code has been removed. The filter now correctly exhibits a drop in low-frequency volume ("bass drop") when resonance is increased, matching the dynamic behavior of the hardware.
* **Oscillator and Envelope Behavior:** The emulation confirms and maintains specific behaviors such as a free-running oscillator (no phase reset on trigger), cumulative accent "smearing" via a modeled capacitor, and the shortening of decay times on accented notes.

### Building the Project

Please refer to the `Build` directory for project files compatible with your IDE. Note that legacy VST 2.4 support requires the separate VST SDK, which is no longer distributed in this repository.
