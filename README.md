## Rust Music Theory

[![Build Status](https://travis-ci.com/ozankasikci/rust-music-theory.svg?branch=master)](https://travis-ci.com/ozankasikci/rust-music-theory)

A library and executable that provides programmatic implementation of the basis of the music theory.
## Table of Contents

- [Overview](#overview)
- [Usage](#usage)
  * [Usage as a Library](#usage-as-a-library)
  * [Usage as an Executable](#usage-as-an-executable)

## Overview

`Rust Music Theory` is used to procedurally utilize music theory notions like Note, Chord, Scale,
Interval and more.

## Usage
### Usage as a Library
Add `rust_music_theory` as a dependency in your Cargo.toml.
```toml
[dependencies]
rust_music_theory = "0.1"
```

After installing the dependencies, you can use the library as follows.
```rust
extern crate rust_music_theory as rmt;
use rmt::note::{Note, Notes, PitchClass};
use rmt::scale::{Scale, ScaleType, Mode};
use rmt::chord::{Chord, Number as ChordNumber, Quality as ChordQuality};

// to create a Note, specify a pitch class and an octave;
let note = Note::new(PitchClass::As, 4);

// Scale Example;
let scale = Scale::new(
    ScaleType::Diatonic,    // scale type
    PitchClass::C,          // tonic
    4,                      // octave
    Some(Mode::Ionian),     // scale mode
).unwrap();

// returns a Vector of the Notes of the scale
let scale_notes = scale.notes();

// Chord Example;
let chord = Chord::new(PitchClass::C, ChordQuality::Major, ChordNumber::Triad);

// returns a Vector of the Notes of the chord
let chord_notes = chord.notes();

```

This is the simplest form of the usage. For detailed examples, please see the tests folder.


### Usage as an Executable
The binary is implemented as a regex parser cli that returns the notes of the given scale/chord.
To quickly build and run the executable locally;

`git clone http://github.com/ozankasikci/rust-music-theory && cd $`

`cargo run scale D Locrian`
```yaml
Notes:
  1: D
  2: D#
  3: F
  4: G
  5: G#
  6: A#
  7: C
  8: D
```
`cargo run chord C# Dominant Eleventh`
```yaml
Notes:
  1: C#
  2: F
  3: G#
  4: B
  5: D#
  6: G
```

`cargo run scale list`
```yaml
Available Scales:
 - Major|Ionian
 - Minor|Aeolian
 - Dorian
 - Phrygian
 - Lydian
 - Mixolydian
 - Locrian
 - Harmonic Minor
 - Melodic Minor
```


`cargo run chord list`
```yaml
Available chords:
 - Major Triad
 - Minor Triad
 - Suspended2 Triad
 - Suspended4 Triad
 - Augmented Triad
 - Diminished Triad
 - Major Seventh
 - Minor Seventh
 - Augmented Seventh
 - Augmented Major Seventh
 - Diminished Seventh
 - Half Diminished Seventh
 - Minor Major Seventh
 - Dominant Seventh
 - Dominant Ninth
 - Major Ninth
 - Dominant Eleventh
 - Major Eleventh
 - Minor Eleventh
 - Dominant Thirteenth
 - Major Thirteenth
 - Minor Thirteenth
```