# Intel RealSense for Processing [![Build Status](https://travis-ci.org/cansik/realsense-processing.svg?branch=master)](https://travis-ci.org/cansik/realsense-processing) [![Build status](https://ci.appveyor.com/api/projects/status/nqmgr5d1pfcmco7u?svg=true)](https://ci.appveyor.com/project/cansik/realsense-processing)
Intel RealSense support for [Processing](https://processing.org/)

![Example](readme/example.jpg)

## Introduction

**Intel RealSense for Procesing** is a port of the **[Intel RealSense](https://github.com/IntelRealSense/librealsense)** library for processing. With this library it is possible to use the Intel RealSense D400 camera series within processing.

Supported Intel RealSense Version: [2.17.0](https://github.com/IntelRealSense/librealsense/releases/tag/v2.17.0)

#### ![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Important

- Currently it is still under development and **ONLY** tested on `MacOS`.
- Prebuilt libraries for `MacOS` are in the [nightly build](https://github.com/cansik/realsense-processing/releases/tag/latest).
- `Ubuntu (Unix)` and `MacOS` binaries are bundled in the [pre release v2.17.0.1](https://github.com/cansik/realsense-processing/releases/tag/v2.17.0.1).
- The library is not multithreaded, so there will be performance issues.
- The proof of concept of this library can be found here: [proof-of-concept](https://github.com/cansik/realsense-processing/tree/master/proof-of-concept).

## Example

Here is an example which shows how to use the library. You find more [examples here](https://github.com/cansik/realsense-processing/tree/master/examples).

```java
import ch.bildspur.realsense.*;

RealSenseCamera camera = new RealSenseCamera(this);

void setup()
{
  size(640, 480);

  // width, height, fps, depth-stream, color-stream
  camera.start(640, 480, 30, true, true);
}

void draw()
{
  background(0);

  // read frames
  camera.readFrames();

  // show color image
  image(camera.getColorImage(), 0, 0);
  
  // -- or --
  
  // create grayscale image form depth buffer
  // min and max depth
  camera.createDepthImage(0, 3000);
  
  // show color image
  image(camera.getDepthImage(), 0, 0);
}
```

## About

The processing library is maintained by [@cansik](https://github.com/cansik) and based on the native Intel RealSense [wrapper](https://github.com/cansik/librealsense) developed by [@edwinRNDR](https://github.com/edwinRNDR) and [@cansik](https://github.com/cansik)