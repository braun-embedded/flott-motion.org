+++
title = "Announcing RampMaker"
date  = 2021-02-02

[extra]
author = "hannobraun"
+++

[RampMaker](https://crates.io/crates/ramp-maker) is a library for creating stepper motor acceleration profiles. You give it a target acceleration, a maximum speed, and a number of steps. From this information, RampMaker will create a series of step delays that constitute an acceleration ramp over that number of steps, with smooth acceleration and deceleration.

``` rust
// Required to call the `ramp` method.
use ramp_maker::AccelerationProfile as _;

// Let's use floating point numbers here to keep the example simple.
// RampMaker also supports fixed-point numbers though.
let target_accel = 1000.0; // meters per second^2
let max_speed = 1500.0; // meters per second
let profile = ramp_maker::Trapezoidal::new(target_accel, max_speed);

let num_steps = 2000;
for delay in profile.ramp(num_steps) {
    // How you handle a delay depends on the platform you're running on
    // (RampMaker works pretty much everywhere). Here, we use a fake `Timer`
    // API, to demonstrate how the delays produced by RampMaker must be
    // used.
    let timer = Timer::start(delay);

    // RampMaker doesn't care how you actually interface with the stepper motor,
    // so we use this fake `step` method to demonstrate the principle. If you
    // haven't settled on a solution, why not check out Step/Dir, another
    // library from the Flott toolkit?
    step();

    // Wait until the delay is over before making the next step.
    timer.wait();
}
```

RampMaker is designed to be used on resource-constrained systems, like microcontrollers. It implements an efficient algorithm to generate approximate trapezoidal acceleration ramps in real-time.


### Why bother?

Motors can't just change their speed instantly. If you try to do that with a stepper motor, you will likely lose steps. Since stepper motors are often driven in an open loop, without feedback about how they actually moved, this will significantly reduce the accuracy you can achieve, or even prevent movement completely.

The solution is to use a controlled acceleration to ramp up to and down from the desired speed. There are many ways to do this. RampMaker currently implements generation of trapezoidal ramps (here's an [overview over different ramp types](https://www.trinamic.com/technology/motion-control-technology/)).


### What's next?

RampMaker has quite a few limitations right now (check out the [GitHub issues](https://github.com/flott-motion/ramp-maker/issues) for a list of known problems). I hope to address everything in due time, but for now, the following points are my priority:

- Integrate RampMaker into the [Step/Dir](https://crates.io/crates/step-dir) library, using it there to provide a more powerful and convenient interface than what is currently available.
- Right now, only movement from and back to stand-still, over a defined number of steps, is supported. To support more use cases, more flexibility is required, like changing the target speed mid-movement.

Both tasks go hand in hand, so I expect to be working on them in parallel.

RampMaker is open source and [developed on GitHub](https://github.com/flott-motion/ramp-maker). If you have any thoughts on what the priorities should be, please open new issues, comment on existing ones, or send a pull request to help out.


### Flott

RampMaker is part of [Flott](https://flott-motion.org/), the open source toolkit for motion control software in Rust. For now, Flott is restricted to interfacing with stepper motors, but I plan to eventually grow it into a comprehensive toolkit that covers all common motion control needs.


### Funding

Creating and maintaining open source software is time-consuming! If you want to support my work on RampMaker and Flott, [please consider sponsoring me](https://github.com/sponsors/hannobraun).
