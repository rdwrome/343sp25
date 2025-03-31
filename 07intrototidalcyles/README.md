# pulsar & hydra
- install [node.js](https://nodejs.org/en/download/) with 'brew' commands
- quit everything and reopen
- install hydra package for pulsar through the command line:
`
git clone https://github.com/hydra-synth/atom-hydra.git
cd atom-hydra
ppm install
ppm link
`
 - quit everything and reopen

# Tidal Cycles Installation

## [Structure of Tidal Cycles](https://tidalcycles.org/docs/getting-started/tidal_start)

## SuperCollider
- Audio Engine is now SuperCollider
- You may now also send out clock information! (but not receive it, sorry)

## Tidal Cycles Dependencies
- [Follow the **Automatic Installation (script)** instructions here](https://tidalcycles.org/docs/getting-started/macos_install)
  - Please let me know if this doesn't work!!!
- Did you have an issue with your Haskell install? Try this instead:
`
curl --proto '=https' --tlsv1.2 -sSf https://get-ghcup.haskell.org | sh
`

## Starting Tidal Cycles
- select your preferred audio output device in AudioMidi Setup
- open SuperCollider
- execute `SuperDirt.start;` with shift, return
- does your preferred audio output device get listed?
- Are they the same sample rate?
- does it say `SuperDirt: listening to Tidal on port 57120`? (this will take a moment)
- open and save a .tidal file in Pulsar
- execute TidalCycles code with shift, return in Pulsar
- monitor in Pulsar and SuperCollider post windows
- (did you already know some sc? SuperDirt the quark boots sc itself, so please don't boot before using the quark)

## The Structure
`d1 $ n "0 2 4 6 0 2 6 8" # sound "cyclo"`

# recording your tc/hydra session in pulsar with OBS advice
## Virtual Audio Interfaces
- [BlackHole](https://existential.audio/blackhole/)
  - uncomplicated, unpowerful
  - Download 16ch
- JACK
  - complicated, powerful
- SoundFlower
  - deprecated, but otherwise perfect

## TidalCycles/SuperCollider Audio > BlackHole > OBS
- ORDER OF OPERATIONS CRITICAL!
- **Audio MIDI Setup**
  - [(Create Multi-Output Device)](https://github.com/ExistentialAudio/BlackHole/wiki/Multi-Output-Device)
  - Input: BlackHole 16ch
  - Output: Multi-Output Device
    - BlackHole 16ch Use box checked!
    - Your MONITOR source (external headphones, etc.) Use box checked!
- **SuperCollider**
  - Input: N/A
  - Output: BlackHole 16ch
  - If you need to change it run this then reboot server:
<pre>
  Server.default.options.outDevice_("BlackHole 16ch");
</pre>
- **OBS**
  - Main Window: Add Source to Scene
    - Audio Input Capture
      - BlackHole 16 ch
