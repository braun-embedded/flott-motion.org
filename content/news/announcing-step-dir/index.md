+++
title = "Announcing Step/Dir"
date  = 2021-01-29

[extra]
author = "hannobraun"
+++

Step/Dir is a library that abstracts over stepper motors. It aims to provide a unified interface for controlling stepper motors, no matter which driver or controller chip you use to do that.

Step/Dir has been published for a few months and already went through a few design iterations (the [latest version on crates.io](https://crates.io/crates/step-dir) is 0.4.1). However, its still early days for the library. So far it only supports two stepper motor drivers, and provides a very low-level interface. There's still lots more to do, but its a start.

To learn more about Step/Dir, check out the [repository on GitHub](https://github.com/flott-motion/step-dir) or the [reference documentation](https://docs.rs/step-dir).


### Vision

Step/Dir aims to provide a comprehensive abstraction over stepper driver and controller chips. Those chips are very different in their capabilities. Some have only STEP and DIR pins, to make single steps in a given direction. Others provide a high-level interface and can generate smooth movement over some distance.

My original plan was to write different libraries for driver and controller chips respectively, but it turns out that reality is not so clean-cut. The lines are really blurry, with some driver chips providing varying amounts of controller features. I now believe that trying to write two different libraries would create lots of friction.

Instead, the plan is for Step/Dir to become the one library for controlling stepper motors. It will provide a low-level interface, where available, and a high-level interface everywhere, either directly backed by hardware capabilities or using a software-based fallback.


### Flott

Step/Dir is part of [Flott](https://flott-motion.org/), the toolkit for motion control software in Rust. For now, Flott is restricted to interfacing with stepper motors, but I plan to eventually grow it into a comprehensive toolkit that covers all common motion control needs.

### Funding

I've already spent lots of time working on Step/Dir, and lots more work will be required to realize the vision I laid out above. If you want to support my work on Step/Dir and Flott, [please consider sponsoring me](https://github.com/sponsors/hannobraun).
