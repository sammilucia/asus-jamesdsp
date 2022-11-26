# JamesDSP-Linux presets for the ASUS G14 2022 notebooks

These will work on other notebooks. The 2020 G14 has a _similar_ speaker EQ curve, but the 2020 models have some extra peaks and troughs in the mids (1000–6000Hz) and a little different bass resonance (around 300Hz instead of 180Hz).

## Fix for JamesDSP stopping video playback

As at 19-Nov this bug is known and a patch for pipewire is coming (see https://gitlab.freedesktop.org/pipewire/wireplumber/-/merge_requests/450)

For now copy the file in this zip to `/usr/share/wireplumber/scripts/` (and overwrite) [policy-node.zip](https://github.com/sammilucia/asus-jamesdsp/files/10048084/policy-node.zip)

## Why would you want this?

The OS doesn't know about the little speakers, and just outputs sound completely untouched, irrespective of whether it's connected to a big stereo, or little speakers.

Little speakers have a lot of limitations. In Windows ASUS uses Dolby Atmos to try and get the most out of the little speakers. However in Linux we don't have this.

_(Interestingly, based on the performance of Dolby in Windows on the 2022 model, I suspect ASUS are still using the original profiles made by Dolby for the early models in 2020—the 2022 models have quite a different sound response.)_

## What these presets do

They basically try and squeeze as much oompfh out of the little speakers in the ASUS as possible.

## Profiles

While there are a few groups of profiles, there are no rules. Use what you like! Let me know what works for you! I can usually be found on the asus-linux.org Discord 😊

**Critical listening - Flat**
_Good for accurate/critical listening._
Designed to correct EQ problems only, and be as true to the original mix intentions as possible. This is a similar goal to studio monitors. "Plain."

**General use/music/YT - Full Natural Forward**
_Good for general use and music_
This corrects EQ curves and then goes further to widen the stereo image past the edges of the laptop by a sensible amount. That's about it. "Full" refers to "full" frequency spectrum and use of the speakers. I've pushed them about as hard as I can without audible distortion.

**General use/music/YT - Full Natural Stage**
_A more relaxed sounding general use. Comfortable for long-term listening of music/YT/etc. Could also be great for games_
The same, but now we're using the front and back speakers independently, so this is a 4 speaker setup. If you don't have 4 speakers you won't hear it correctly (or if your speakers are wired incorrectly). This is the most full use of laptop speakers.

**Music - Concert**
_Live music experience_
This builds on the full effect of _Full Natural Stage_, however adds some reverb to emulate a well-controlled concert area. I was aiming for great sounding concerts like Kraftwerk _Minimum Maximum_.

**Headphones - Headphones and Sony profiles**
_A set of profiles designed to deal with the binaural nature of headphones_

**Movies/TV - Movie profiles**
_Pofiles designed for the way movie audio/sound/music is mastered, plus intelligibility of speech_

**Gaming - Wide profiles**
_Specifically designed for gaming, and being able to identify where sounds are coming from_

In more detail...

The speakers are actually really good for laptop speakers (but they're still laptop speakers). In my laptop there's some resonance around 180 Hz which I've tried to counter, and while the speakers are very mid heavy, they're nicely consistent, so I've pretty much been able to do a V-shaped EQ curve with some tweaks.

I've then used a mix of convolution, multi-band (well, single band—bass) compression, and mid-side processing to bring the sound out of the laptop and create a surround effect. These tricks, as well as EQ curves very depending on the preset you choose.

I find I prefer certain presets for certain things. **Movies** has worked well for me for movies, **Open** is great for low-battery music, and I like **Wide** for gaming.

There is also a balance of tuning profiles to work with your laptop on a table vs. your lap, etc.

**Headphones** has no EQ at all (because I don't know what headphones you have), but adds some mid-side mixing to turn the binaural signal into "pseudo" stereo (mix the left and right channels a bit).

**Sep 2022 Update:** I've now added two headphone profiles with speaker simulation. This is used when you want to write music on headphones that translates to ("also sounds good on") real world speakers. This is a work in progress, let me know how you go!

## Installing the profiles

Copy the files to your `~./config/jamesdsp` folder. This should already exist after you've run JamesDSP for Linux the first time.

#### OR

```bash
mv ~/.config/jamesdsp ~/.config/jamesdsp.bak
mkdir ~/.config/jamesdsp
git clone https://github.com/sammilucia/asus-jamesdsp
cp -r ./asus-jamesdsp/jamesdsp/* ~/.config/jamesdsp
rm -rf asus-jamesdsp
```

Reboot.

## Updating JamesDSP

To install JamesDSP for Linux, there is a Debian package on the github. If you use Fedora or another distro however you can install the latest version from the copr and update to the newest executable in the Debian package by doing:

```bash
dnf copr enable arrobbins/JDSP4Linux
dnf update
dnf install jamesdsp
```

Download the latest Pipewire or Pulse .deb release from [https://github.com/Audio4Linux/JDSP4Linux](https://github.com/Audio4Linux/JDSP4Linux/releases)

Then do:

```bash
dpkg-deb -xv ./jamesdsp-pipewire_2.4-49994d_linux64.deb ./
chmod +x ./usr/bin/jamesdsp
sudo cp ./usr/bin/jamesdsp /usr/bin
```

## Changes
26-Nov-2022
- General profile fine-tuning
- Renamed _Full Natural Wide_ to _Full Natural Forward_
- Added _Full Natural Stage_, which uses the front and back speakers differently
- Added _Concert_, which is the same as _Full Natural Stage_ but emulates a well-managed concert environment (think: Kraftwork _Minimum Maximum_)
- Added Superwide, which emphasises stereo width

19-Oct-2022
- Matched volume of Movie profiles to other profiles
- Renamed "Wide 3" profile to "Wide Clear"
- Fine tuning of EQ settings
- Added "Full Natural Wide" with slight musical reverberation, it's great for general music
- Added "Full Natural" and "Wide Natural" with similar properties

