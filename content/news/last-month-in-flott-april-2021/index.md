+++
title = "Last Month in Flott - April 2021"
date  = 2021-04-06

[extra]
author = "hannobraun"
+++

This is the monthly newsletter for [Flott](https://flott-motion.org/), the toolkit for motion control software in Rust. Flott aims to make developing motion control software easy, by providing libraries that abstract over hardware commonly used for motion control, like motors, encoders, and other sensors and actuators.

Last months saw a new release of [Stepper], the universal stepper motor interface. I've also published [Stepper Terminal], a new application, built on top of Stepper, for controlling a stepper motor from the command-line on your computer.

<aside>
<p>
    Flott's development is supported by my generous sponsors. Special thanks to <a href="https://github.com/lthiery">Louis Thiery</a> and <a href="https://github.com/ahdinosaur">Mikey</a>, who have started sponsoring me in March!
</p>
<p>
    If you want to support Flott's continued development, please consider <a href="https://github.com/sponsors/hannobraun">sponsoring my work</a> as well.
</p>
</aside>


### Stepper

[Stepper] (formerly known as Step/Dir) is a library that provides a unified interface for controlling stepper motors. March saw continued development of the high-level motion control API, culminating in the release of [version 0.5](https://flott-motion.org/news/stepper-0-5/). This is also the first release under the new name, Stepper.

Highlights:

- [#98] - Change motion control API to accept absolute target position
- [#100] - Support setting step mode for software-motion-controlled driver
- [#107] - Add method for resetting internal position to new value
- [#108] - Remove the need for a custom numeric type
- [#112] - Rename to Stepper
- [#113] - Update documentation
- [#116] - Make `SetDirection`/`Step` errors less weird, more flexible
- [#118] - Implement `SetDirection` and `Step` for `SoftwareMotionControl`

[#98]: https://github.com/flott-motion/step-dir/pull/98
[#100]: https://github.com/flott-motion/step-dir/pull/100
[#107]: https://github.com/flott-motion/step-dir/pull/107
[#108]: https://github.com/flott-motion/step-dir/pull/108
[#112]: https://github.com/flott-motion/step-dir/pull/112
[#113]: https://github.com/flott-motion/step-dir/pull/113
[#116]: https://github.com/flott-motion/step-dir/pull/116
[#118]: https://github.com/flott-motion/step-dir/pull/118

This is just a selection of the pull requests that were merged last month. Check out the [full list](https://github.com/flott-motion/stepper/pulls?q=is%3Apr+is%3Aclosed+created%3A2021-03-01..2021-03-31) on GitHub, if you're interested in all the details.


### Stepper Terminal

[Stepper Terminal] is a CLI and firmware application that saw its [initial release](https://flott-motion.org/news/announcing-stepper-terminal/) in March. It is a tool for manual testing of Stepper, but also serves as a full usage example of the library. Going forward, it will be extended in lock-step with Stepper, as new features are being added.


### What I'm working on

I just came back from vacation (or rather staycation, as they call it these days) and I'm looking forward to getting back into Flott. My next focus area is a high-level guide for [Stepper]. Its API is already fully documented, but there are some crucial pieces of information required to use it and to implement new drivers. That information is currently scattered across a bunch of GitHub issues, if available at all.


### Funding

Right now, Flott is focused on stepper motors, but I want to build it into a full-featured toolkit for motion control software, by abstracting over other kinds of hardware (like encoders, or other motor types), as well as creating more useful building blocks on top of those hardware interfaces.

**Doing this will take a lot of effort. Please consider supporting my work by [sponsoring me](https://github.com/sponsors/hannobraun).**


### Thank you

Thank you for your interest in Flott! If you want to follow its development, feel free to [subscribe to the news feed](/atom.xml). I also plan to set up an email newsletter, but *still* haven't gotten around to it. Again, I'm hoping to have it ready for next month's newsletter.

The next newsletter is expected to arrive in early May. If you have any questions or feedback, please don't hesitate to [contact me](mailto:hanno@braun-odw.eu)!

[Stepper]: https://github.com/flott-motion/stepper
[Stepper Terminal]: https://github.com/flott-motion/stepper-terminal
