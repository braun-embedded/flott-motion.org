+++
title = "Last Month in Flott - March 2021"
date  = 2021-03-01

[extra]
author = "hannobraun"
+++

This is the monthly newsletter for [Flott](https://flott-motion.org/), the toolkit for motion control software in Rust. Flott aims to make developing motion control software easy, by providing libraries that abstract over hardware commonly used for motion control, like motors, encoders, and other sensors and actuators.

Last month saw lots of progress on [RampMaker] and [Step/Dir], libraries that can be used to control stepper motors.

<aside>
If you want to support Flott's continued development, please consider <a href="https://github.com/sponsors/hannobraun">sponsoring my work</a>.
</aside>


### RampMaker

[RampMaker] is a library that generates acceleration ramps for stepper motors. It saw its initial release in late January. Building on that, lots of work has gone into making it more powerful, flexible, and downright more useful. This has culminated in [version 0.2][RampMaker 0.2] being published.

Highlights:

- [#17] - Rename `AccelerationProfile` to `MotionProfile`
- [#20] - Improve usability of `MotionProfile`
- [#26] - Add reusable testing infrastructure
- [#28] - Improve accuracy of trapezoidal motion profile
- [#30] - Make `MotionProfile` more powerful and flexible
- [#31] - Add additional iterators to `MotionProfile`
- [#32] - Clean up trapezoidal ramp generation
- [#33] - Make trapezoidal ramp generation more flexible

[#17]: https://github.com/flott-motion/ramp-maker/pull/17
[#20]: https://github.com/flott-motion/ramp-maker/pull/20
[#26]: https://github.com/flott-motion/ramp-maker/pull/26
[#28]: https://github.com/flott-motion/ramp-maker/pull/28
[#30]: https://github.com/flott-motion/ramp-maker/pull/30
[#31]: https://github.com/flott-motion/ramp-maker/pull/31
[#32]: https://github.com/flott-motion/ramp-maker/pull/32
[#33]: https://github.com/flott-motion/ramp-maker/pull/33

This is just a selection of pull requests that were merged last month. Check out the [full list](https://github.com/flott-motion/ramp-maker/pulls?q=is%3Apr+is%3Aclosed+created%3A2021-02-01..2021-02-28) on GitHub, if you're interested in all the details.


### Step/Dir

[Step/Dir] is a library that provides a unified interface for controlling stepper motors. Its development took a bit of a back-seat last month, due to the work on RampMaker. Still, some things got done, mostly clean-ups, small improvements, and the addition of a high-level motion control API.

Highlights:

- [#83] - Rename `Driver` to `Stepper`
- [#87] - Clarify nomenclature used by `Stepper`
- [#91] - Make API more flexible by allowing reuse of futures
- [#93] - Make futures more flexible
- [#96] - Add high-level motion control interface

[#83]: https://github.com/flott-motion/step-dir/pull/83
[#87]: https://github.com/flott-motion/step-dir/pull/87
[#91]: https://github.com/flott-motion/step-dir/pull/91
[#93]: https://github.com/flott-motion/step-dir/pull/93
[#96]: https://github.com/flott-motion/step-dir/pull/96

This is just a selection of pull requests that were merged last month. Check out the [full list](https://github.com/flott-motion/step-dir/pulls?q=is%3Apr+is%3Aclosed+created%3A2021-02-01..2021-02-28) on GitHub, if you're interested in all the details.


### What I'm working on

Now that [RampMaker 0.2] is out, I'm focused on integrating it into [Step/Dir] to provide a high-level motion control API for chips that don't support that in hardware. The initial version of that is already done, but it needs some polishing.


### Funding

Right now, Flott is focused on stepper motors, but I want to build it into a full-featured toolkit for motion control software, by abstracting over other kinds of hardware (like encoders, or other motor types), as well as creating more useful building blocks on top of those hardware interfaces.

**Doing this will take a lot of effort. Please consider supporting my work by [sponsoring me](https://github.com/sponsors/hannobraun).**


### Thank you

Thank you for your interest in Flott! If you're interested in following its development, feel free to [subscribe to the news feed](/atom.xml). I also plan to set up an email newsletter, but haven't gotten around to it yet. Next month, hopefully!

The next newsletter is expected to arrive in early April. If you have any questions or feedback, please don't hesitate to [contact me](mailto:hanno@braun-embedded.com)!

[RampMaker]: https://github.com/flott-motion/ramp-maker
[Step/Dir]: https://github.com/flott-motion/step-dir
[RampMaker 0.2]: https://flott-motion.org/news/ramp-maker-0-2/
