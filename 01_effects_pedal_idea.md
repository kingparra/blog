# An Idea for Another Day

Last night, I had an idea for a guitar effects pedal, inspired by a feature in my app. It's half-baked, but I think the direction is interesting.

In the app, it works like this: you select a chord voicing, turn on "disperse mode," and the chord spreads across fret/string combinations based on a set of constraints—allowed octaves, allowed strings, mandatory pitches. The idea is to change the chord's timbre by changing its physical shape on the fretboard: sparkling highs, muddy lows, dramatic leaps, or tight clusters. There's also a "target" feature that biases the voicing toward a particular fret, which is useful for voice leading.

As I stared half-lidded at the TV, I started wondering: what if that logic lived in a pedal?

Obviously, pedals work with signals, not fret positions. It can't make your amp sound like you're playing a C4 on the high b first fret as opposed to a C4 on the d string 10th fret. It's all just pitches. But it could potentially detect a chord, then spread or compress its voicings in pitch space—biasing toward highs or lows, widening or narrowing the intervals. Harmonizers already exist, but they don't think in terms of voicings. They don't morph a chord's shape while preserving its identity.

The real hook: an expression pedal that lets you sweep a chord from tight to wide in real time. Or a "target mode" that transforms single notes into chord voicings for hands-free voice leading. Maybe it arpeggiates those voicings too.
Pitch detection has gotten pretty good. I'm familiar with single-board computers and Linux, I'm learning a few systems languages, and I've wired up small prototypes before. Why not build something? Maybe it becomes the seed of a homebrew multi-effects unit.

Some other day. For now, it's a nice thought to fall asleep to.
