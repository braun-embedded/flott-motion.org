+++
+++

<strong class="why">Developing motion control software in Rust should be easy!</strong> Flott aims to make this a reality, by providing libraries that abstract over hardware commonly used for motion control, like motors, encoders, and other sensors and actuators.

## Libraries

It's still early days for Flott, and work to build up the ecosystem is ongoing. So far, the following libraries are available:
- **[Step/Dir](https://github.com/flott-motion/step-dir) - Universal Stepper Motor Interface**
- **[RampMaker](https://github.com/flott-motion/ramp-maker) - Stepper Acceleration Ramp Generator**

Long-term, Flott aims to become a comprehensive toolkit that covers all common motion control needs.

## Vision

The development of Flott is guided by the following principles:

- **Open source, permissive license**: Whether you use Flott for a hobby project or something you are going to sell, there won't be any legal restrictions standing in your way.
- **Open community**: Everyone is welcome to contribute to Flott. Its creator accepts funding and wants to work on it full-time, but the project's policy is to promote all project maintainers that want to do this.
- **Portable**: If you want to position a tool at specific coordinates, then write code to do just that. Whether using stepper or linear motors, open- or closed-loop control, a gantry mill or a delta robot; your code stays the same. Write your code once, and adapt to changes in the hardware by re-arranging and re-configuring the building blocks provided by Flott.
- **Flexible**: Replace the code that generates acceleration ramps with your own implementation, or reach down to access the unique features of a specific stepper driver. Whenever you need to leave the beaten path, Flott won't stand in your way.
- **Portable, again**: Flott is designed to run on microcontrollers, with little to no overhead. But the abstract interfaces it builds on can be implemented for all kinds of platforms, large or small.

## Funding

If you're getting value out of Flott, please consider supporting us financially. Your sponsorship helps to keep the project healthy and moving forward.

[Hanno Braun], the creator of Flott, is [accepting sponsorship](https://github.com/sponsors/hannobraun).

[Hanno Braun]: https://github.com/hannobraun
