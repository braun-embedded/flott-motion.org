+++
title = "Stepper 0.5 (formerly Step/Dir)"
date  = 2021-03-11

[extra]
author = "hannobraun"
+++

[Stepper 0.5.0](https://crates.io/crates/stepper) is now available on crates.io. Stepper is a library for controlling stepper motors. It abstracts over the actual hardware used to control the stepper motor (like a stepper driver or motion control chip) and provides a unified API on top. This library was formerly known as Step/Dir.

The new version introduces a high-level motion control API. Before, you had to tell it when to make each single step, whereas now you have a nice API that lets you make a smooth movement to a target position, without having to take care of the details.

<aside>
Please consider <a href="https://github.com/sponsors/hannobraun">sponsoring my work</a> on Stepper and other open source projects for motion control software in Rust.
</aside>

### Highlights

This section summarizes the highlights of the release. You can find a more complete picture in the [changelog](https://github.com/flott-motion/stepper/blob/main/CHANGELOG.md#v050-2021-03-10).

#### New Name

When I originally started working on Stepper (then known as Step/Dir) I thought I was building a library to abstract over stepper drivers that are controlled via STEP and DIR pins. I expected the higher-level motion control API (and the chips it abstracts over) to live in a separate library.

Turns out reality is a bit messier than that. Not all chips cleanly fall into either category, belonging to both or being something in between. I eventually decided that the best bet for now is to support everything in a single library. The old name directly refers the the STEP an DIR pins and no longer fits the new scope.

Stepper is a more general name, which fits the library's new role as the universal stepper motor interface. But the crate name `stepper` was already used by another library, which provided the capabilities of [`std::iter::StepBy`](https://doc.rust-lang.org/std/iter/struct.StepBy.html), while that was still unstable. `StepBy` has long since been stabilized, and the `stepper` library has fulfilled its original purpose and become obsolete.

Its author, [Saghm Rossi](https://saghm.com/), gracefully allowed me to take over the name and use it as the new name for Step/Dir. Thank you, Saghm! If you're interested, also check out the old library at its [original repository](https://github.com/saghm/stepper).

#### Motion Control API

The old API only abstracted over the ability of stepper drivers to make steps in a given direction, which left it to the user to get the timing right and produce a smooth movement (which is a decidedly non-trivial task).

The new motion control API provides a much higher-level interface, so the caller doesn't have to worry about the details.

``` rust
let max_speed = 1000.0; // steps per second
let target_step = 2000; // 10 revolutions on a typical stepper motor
stepper
    .move_to_position(max_speed, target_step)
    // We could do other work in parallel, but here we just wait until the
    // movement has finished.
    .wait()?; 
```

The API is designed to work with minimal software interaction, if motion control hardware is available, but can also use a software fallback, where hardware support is lacking (see next section). As of now, no motion control chips are supported.

#### RampMaker Integration

The [RampMaker](https://github.com/flott-motion/ramp-maker) library has been integrated to provide a software implementation of the motion control API for all hardware, even if hardware support for motion control is not natively supported.

This makes the motion control API available for all currently supported drivers.


### What's next

The new API makes Stepper much more capable and opens up a whole lot of possibilities. However, the library is still lacking in some key areas:

- **Platform support:** To talk to the platform it's running on, Stepper only uses abstract interfaces that can be implemented basically everywhere. However, the combination of interfaces it uses is not implemented on most platforms.
- **Support for more drivers:** Currently, only two stepper drivers are supported. Support for more stepper drivers and motion control chips is highly desirable.
- **High-level documentation:** The [API Reference](https://docs.rs/stepper) is somewhat extensive, but there is no high-level guide yet. Specifically, documentation on how to address the two previous shortcomings would be very useful.

You can check out the [list of open issues](https://github.com/flott-motion/stepper/issues) for more information on these and other problems.

In due time, I intend to work on all of these issues, but for now, I am going to focus on something else: Providing a complete usage example. I intend to create a microcontroller-based application that controls a motor using Stepper, and accepts commands from a CLI app on the host computer. Besides rounding out the available documentation, this will be helpful for testing.

In the meantime, contributions to these or other areas are highly welcome! Feel free to open issues and submit pull requests on the [GitHub repository](https://github.com/flott-motion/stepper).


### Flott

Stepper is part of [Flott](https://flott-motion.org/), the open source toolkit for motion control software in Rust. For now, Flott is restricted to interfacing with stepper motors, but I plan to eventually grow it into a comprehensive toolkit that covers all common motion control needs.


### Funding

Creating and maintaining open source software is time-consuming! If you want to support my work on Stepper and Flott, [please consider sponsoring me](https://github.com/sponsors/hannobraun).
