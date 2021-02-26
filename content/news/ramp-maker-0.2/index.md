+++
title = "RampMaker 0.2"
date  = 2021-02-26

[extra]
author = "hannobraun"
+++

[RampMaker 0.2.0](https://crates.io/crates/ramp-maker) is now available on crates.io. RampMaker is a library for generating motion profiles for stepper motors. Telling a stepper motor to accelerate faster than it is physically able to will result in lost steps, and thus inaccurate movement. A motion profile limits the acceleration required of the motor, helping to achieve an accurate motion.

This release is a huge step forward for RampMaker. After the initial release, which provided very limited capabilities, this new version is more powerful, flexible, accurate, and overall more useful.

<aside>
Please consider <a href="https://github.com/sponsors/hannobraun">sponsoring my work</a> on RampMaker and other open source projects for motion control software in Rust.
</aside>


### Highlights

This section summarizes the highlights of the release. You can find a more complete picture in the [changelog](https://github.com/flott-motion/ramp-maker/blob/main/CHANGELOG.md#v020-2021-02-25).

#### Improved power and flexibility

The previous version only allowed for planning very simple movements, starting and stopping at a stand-still. Now you can adjust the target step of an ongoing motion.

``` rust
// Move 200 steps while staying under the maximum velocity.
let max_velocity = 1000.0; // steps per second
profile.enter_position_mode(max_velocity, 200);

while let Some(delay) = profile.next_delay() {
    // Make a step. This functionality is not part of RampMaker and how it looks
    // exactly depends on your use case. Maybe consider using the Step/Dir
    // library.
    make_step();
    sleep(delay);

    if need_to_move_farther() {
        // Let's move another 1000 steps from this point on. The motion profile
        // will react as necessary, for example by staying at maximum velocity
        // for longer, or accelerating again if it started decelerating already.
        profile.enter_position_mode(max_velocity, 1000);
    }
}
```

Or you can adjust the maximum velocity mid-movement.

``` rust
// Start a long movement at a slow speed.
let mut num_steps = 10_000;
profile.enter_position_mode(200.0, num_steps);

while let Some(delay) = profile.next_delay() {
    // TODO: Make a step.

    if too_slow() {
        // Let's go faster for the rest of the way!
        profile.enter_position_mode(1000.0, num_steps);
    }

    num_steps -= 1;
}
```

This provides a lot more flexibility, opening up more use cases.

#### More accurate trapezoidal profile

RampMaker is designed to run everywhere, even microcontrollers. Since computing an accurate trapezoidal motion profile can be quite expensive, RampMaker employs some clever math to generate an approximated version that is much cheaper to compute.

There are still trade-offs, however. The previous version used a very cheap, but not that accurate algorithm. The new version has been upgraded to generate much more accurate trapezoidal motion profiles, at the cost of additional operations per step (only addition and multiplication though, so nothing too wild).


### What's next

I'm now working on integrating the new version of RampMaker into [Step/Dir](https://crates.io/crates/step-dir), the universal stepper motor interface, where it will be used to provide a high-level motion control API, even it the stepper driver doesn't support that in hardware.

Aside from that, there is a lot more work that can be done: Support for more motion profiles (an s-shaped one would be great), or a velocity mode (when you just want to move at a given velocity without knowing or caring how far). At this point I don't have concrete plans to work on either of those, but contributions are always welcome!


### Flott

RampMaker is part of [Flott](https://flott-motion.org/), the open source toolkit for motion control software in Rust. For now, Flott is restricted to interfacing with stepper motors, but I plan to eventually grow it into a comprehensive toolkit that covers all common motion control needs.


### Funding

Creating and maintaining open source software is time-consuming! If you want to support my work on RampMaker and Flott, [please consider sponsoring me](https://github.com/sponsors/hannobraun).
