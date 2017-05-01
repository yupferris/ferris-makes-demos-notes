# Ep.009 - Engage Breakdown - Notes

Notes on [Ferris Makes Demos Ep.009 - Engage Breakdown][talk] by [ferris][ferris-github].

[Engage][engage] by [Logicoma][LGC], 3rd place in 64k pc demo at Revision 2017 April.

[Listen / download the music track][music-track] from Soundcloud.

[Read ferris on everyweeks](https://everyweeks.com/) for notes on the making.

Many scenes were inspired by [beeple's gfx work][beeple-gfx].

[engage]: http://www.pouet.net/prod.php?which=69658

[ferris-github]: https://github.com/yupferris

[talk]: https://www.youtube.com/watch?v=woqksTHNbvk

[LGC]: http://www.pouet.net/groups.php?which=12638

[enhanced-sphere]: https://scholar.google.com/scholar?q=enhanced+sphere+tracing

[music-track]: https://soundcloud.com/h0ffman/wobble-and-h0ffman-engage

[beeple-gfx]: http://beeple-crap.com/

## Talk TOC

- `00:07:50` tool window overview (preview, profiler, rendering operator graph). The profiler takes time samples from the code at every frame. The post-processing ops chain is the same as in Elysian, but strapped on a raymarcher.
- `prof` operators: profile events, measures start and and end times in a frame. Green line: 16ms (60 fps), dark gray lines: 1ms, red line: 32ms (30 fps).
- `00:11:40` the `text` operator renders a TTF font to a texture unit which can be used in the shader. Uses GDI on Windows to render everything
- `00:12:20` the fonts (typefaces) are custom
- `00:13:20` the TTF is packed in the intro, but the file data is stripped of unused data tables and glyphs
- `00:14:05` both fonts took up 4-5kb in the final intro
- `00:14:30` the tool now can also use *shader include*, pre-processing a `#include` directive in the shader files
- `00:16:00` watch the intro: [Engage][engage]
- `00:24:50` work time on the demo: synth work since November 2016, tool and gfx work since mid-March 2017
- `00:26:30` [music track][music-track] overview
- `00:38:30` `Adultery` plugin test project, playing samples
- `00:43:55` 64k is huge -- talk about the content that fits into 64k and clever ways of optimizing the size.
- `00:48:55` the executable compression is done with **kkrunchy**, not **crinkler** (b/c crinkler works better for the 4-8k range)
- `00:50:20` talk about **no sleep** around Revision
- `00:51:32` story board of the intro, a whole scene was missing before the party
- `00:55:35` the last scene was made at the airport while waiting in a cafe
- `00:57:30` inspiration for the scenes: **Edge of Tomorrow** (movie), **Oblivion** (movie), **beeple** gfx ripoffs
- `01:01:31` first early work-in-progress sceenshots
- `01:02:26` a fisheye projection, a cube, a plane with a procedural texture and bars, a noise field, one reflection bounce on everything
- `01:04:44` raymarching here means sphere tracing ([enhanced sphere tracing][enhanced-sphere] algorithm from 2014 paper by mercury)
- `01:05:50` raymarching technique overview
- `01:22:55` CSG (Constructive Solid Geometry) overview
- `01:30:05` test scenes
- `01:39:10` rendering code overview
- `01:40:23` **beeple tunnel scene**
- `01:55:00` **credit screens**
- `02:03:10` **building and moon scene**
- `02:04:45` change the `fov` (Field of View) from `8.0` to `30.0` to see how it changes the perception of scale to a small scene
- `02:21:15` **robot heads scene**
- `02:24:45` the logicoma logo on the sides is a 2D distance field
- `02:25:45` the 2D field breaks up at grazing angles, so it helped to make it fatter when the camera angle is low
- `02:27:00` WIP shots of developing the robot head
- `02:33:00` **column scene**, repeated polar-rotated robot heads
- `02:36:00` **tunnel scene**, ripoff of beeple's Imagine Dragons
- `02:44:40` WIP shots of the credits
- `02:47:05` move the camera around the spheres to see the reflections
- `02:47:15` no shadow in the demo for performance, just Ambient Occlusion
- `02:50:25` the wild chromatic aberration which is a radial blue with RGB separation
- `02:51:25` **shiny ball and needle scene**
- `02:54:20` **screen content shaders** (radial stripes and code writer)
- `03:11:00` **greeting texts**
- `03:20:00` **ending screen** with merging greetings and logo
- `03:25:00` **needle camera**
- `03:27:10` **eight balls scene**
- `03:32:15` more WIP shots
- `03:45:31` *kkrunchy's* compression techniques

## Optimizations

About 4-5k was saved with optimizations on:

The automation data which changes parameters over time for the tracks. These are a float value 0.0 - 1.0 and a timestamp. It was a big size saver to use a one-byte int for the values instead of four-byte floats.

Delta-encoding the timestamps relative to the previous event, not relative to the beginning of the intro, so that the timestamps can be a smaller value type.

Ableton Live produces double data when copy-pasting, but just clicking again on all the samples removes that.

## Screenshots

- `00:07:50` tool window overview (preview, profiler, rendering operator graph). The profiler takes time samples from the code at every frame. The post-processing ops chain is the same as in Elysian, but strapped on a raymarcher.
- `prof` operators: profile events, measures start and and end times in a frame. Green line: 16ms (60 fps), dark gray lines: 1ms, red line: 32ms (30 fps).

![tool window](./assets/ep009/tool-window.png)

- `00:16:00` watch the intro: [Engage][engage]

![engage start](./assets/ep009/engage-start.png)

- `00:26:30` [music track][music-track] overview

![music track](./assets/ep009/music-track.png)

- `00:51:32` story board of the intro, a whole scene was missing before the party

![storyboard](./assets/ep009/storyboard.png)

- `01:01:31` first early work-in-progress sceenshots

![early wip shots](./assets/ep009/early-wip-shots.png)

- `01:05:50` raymarching technique overview

![raymarching](./assets/ep009/raymarching.png)

- `01:30:05` test scenes

![test scenes](./assets/ep009/test-scenes.png)

- `01:39:10` rendering code overview

![rendering code](./assets/ep009/rendering-code.png)

- `01:40:23` **beeple tunnel scene**

![beeple tunnel](./assets/ep009/beeple-tunnel.png)

- `01:55:00` **credit screens**

![credit screens](./assets/ep009/credit-screens.png)

- `02:03:10` **building and moon scene**

![building moon](./assets/ep009/building-moon.png)

- `02:04:45` change the `fov` (Field of View) from `8.0` to `30.0` to see how it changes the perception of scale to a small scene

![change fov](./assets/ep009/change-fov.png)

- `02:21:15` **robot heads scene**

![robot heads](./assets/ep009/robot-heads.png)

- `02:33:00` **column scene**, repeated polar-rotated robot heads

![column](./assets/ep009/column.png)

- `02:36:00` **tunnel scene**, ripoff of beeple's Imagine Dragons

![tunnel](./assets/ep009/tunnel.png)

- `02:47:05` move the camera around the spheres to see the reflections

![reflections](./assets/ep009/reflections.png)

- `02:50:25` the wild chromatic aberration which is a radial blue with RGB separation

![aberration](./assets/ep009/aberration.png)

- `02:51:25` **shiny ball and needle scene**

![ball needle](./assets/ep009/ball-needle.png)

- `02:54:20` **screen content shaders** (radial stripes and code writer)

![stripes code writer](./assets/ep009/stripes-code-writer.png)

- `03:11:00` **greeting texts**

![greetings](./assets/ep009/greetings.png)

- `03:20:00` **ending screen** with merging greetings and logo

![ending logo](./assets/ep009/ending-logo.png)

- `03:25:00` **needle camera**

![needle camera](./assets/ep009/needle-camera.png)

- `03:27:10` **eight balls scene**

![eight balls](./assets/ep009/eight-balls.png)
