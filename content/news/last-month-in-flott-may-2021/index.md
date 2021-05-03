+++
title = "Last Month in Flott - May 2021"
date  = 2021-05-03

[extra]
author = "hannobraun"
+++

This is the monthly newsletter for [Flott](https://flott-motion.org/), the toolkit for motion control software in Rust. Flott aims to make developing motion control software easy, by providing libraries that abstract over hardware commonly used for motion control, like motors, encoders, and other sensors and actuators.

Work last month was focused on documentation, in the form of new high-level guides for [Stepper], and some tweaks and addition to the website.

<aside>
<p>
    Flott's is supported by my generous sponsors. If you want to support Flott's continued development, please consider <a href="https://github.com/sponsors/hannobraun">sponsoring my work</a> as well.
</p>
</aside>

### Highlights

#### Stepper

[Stepper]'s API was already fully documented, but there were some missing pieces of information on how to use it. That's hopefully solved now, with the new guides on [platform support](https://github.com/flott-motion/stepper/blob/main/documentation/platform-support.md) and [how to write a driver](https://github.com/flott-motion/stepper/blob/main/documentation/how-to-write-a-driver.md).

#### Website Tweaks

The website has seen a bit of work this month, with some tweaks to content and design, and most notably, the addition of an email newsletter. If you want to stay up to date on what's happening with Flott, feel free to sign up at the bottom of this page.


### Other work

If you're interested in all the details, here's the full list of pull request that were merged last month.

- [Stepper](https://github.com/flott-motion/stepper/pulls?q=is%3Apr+is%3Aclosed+created%3A2021-04-01..2021-04-30)
- [RampMaker](https://github.com/flott-motion/ramp-maker/pulls?q=is%3Apr+is%3Aclosed+created%3A2021-04-01..2021-04-30) (no work this month)
- [Stepper Terminal](https://github.com/flott-motion/stepper-terminal/pulls?q=is%3Apr+is%3Aclosed+created%3A2021-04-01..2021-04-30)
- [Website](https://github.com/flott-motion/flott-motion.org/pulls?q=is%3Apr+is%3Aclosed+created%3A2021-04-01..2021-04-30)


### What I'm working on

With the documentation work on [Stepper] wrapped up for now, I've turned my attention to testing. Stepper [already has a test stand](https://github.com/flott-motion/stepper/tree/main/test-stand), but that was a bit of a [failed experiment](https://github.com/flott-motion/stepper/issues/49). I want to try and revive it. Automated end-to-end testing would be a great boon for Stepper's further development.


### Funding

Right now, Flott is focused on stepper motors, but I want to build it into a full-featured toolkit for motion control software, by abstracting over other kinds of hardware (like encoders, or other motor types), as well as creating more useful building blocks on top of those hardware interfaces.

**Doing this will take a lot of effort. Please consider supporting my work by [sponsoring me](https://github.com/sponsors/hannobraun).**


### Thank you

Thank you for your interest in Flott! If you want to follow its development, feel free to [subscribe to the news feed](/atom.xml) or sign up for the newsletter using the form below.

The next newsletter is expected to arrive in early June. If you have any feedback or questions, please don't hesitate to [contact me](mailto:hanno@braun-odw.eu)!

[Stepper]: https://github.com/flott-motion/stepper
