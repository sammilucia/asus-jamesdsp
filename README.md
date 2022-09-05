# JamesDSP-Linux presets for the ASUS G14 2022 notebooks

These will work on other notebooks. The 2020 G14 has a _similar_ speaker EQ curve, but the 2020 models have some extra peaks and troughs in the mids (1000–6000Hz) and a little different bass resonance (around 300Hz instead of 180Hz).

## Why would you want this?

The OS doesn't know about the little speakers, and just outputs sound completely untouched, irrespective of whether it's connected to a big stereo, or little speakers.

Little speakers have a lot of limitations. In Windows ASUS uses Dolby Atmos to try and get the most out of the little speakers. However in Linux we don't have this.

_(Interestingly, based on the performance of Dolby in Windows on the 2022 model, I suspect ASUS are still using the original profiles made by Dolby for the early models in 2020—the 2022 models have quite a different sound response.)_

## What these presets do

They basically try and squeeze as much oompfh out of the little speakers in the ASUS as possible.

## Proifiles

In more detail...

The speakers are actually really good for laptop speakers (but they're still laptop speakers). In my laptop there's some resonance around 180 Hz which I've tried to counter, and while the speakers are very mid heavy, they're nicely consistent, so I've pretty much been able to do a V-shaped EQ curve with some tweaks.

I've then used a mix of convolution, multi-band (well, single band—bass) compression, and mid-side processing to bring the sound out of the laptop and create a surround effect. These tricks, as well as EQ curves very depending on the preset you choose.

I find I prefer certain presets for certain things. **Movies** has worked well for me for movies, **Open** is great for low-battery music, and I like **Wide** for gaming.

**Headphones** has no EQ at all (because I don't know what headphones you have), but adds some mid-side mixing to turn the binaural signal into "pseudo" stereo (mix the left and right channels a bit).

There is also a balance of tuning profiles to work with your laptop on a table vs. your lap, etc.

## Installation

1. Install JamesDSP for Linux from https://github.com/Audio4Linux/JDSP4Linux 
1. Copy the files to your `~./config/jamesdsp` folder. There should

## OR

```bash
mv ~/.config/jamesdsp ~/.config/jamesdsp.bak
mkdir ~/.config/jamesdsp
git clone https://github.com/sammilucia/asus-jamesdsp
cp -r ./asus-jamesdsp/jamesdsp/* ~/.config/jamesdsp
rm -rf asus-jamesdsp
```

3. Reboot.

