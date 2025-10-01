# Intro

This shall serve as a reminder and template about how to create a 

- cargo project for embassy and rpico
- set up debugging with vscode for it. 

## Create a cargo project for embassy and rpi pico

The project shall be very simple, a "standalone" project that
does the same as the "blinky" example from embassy.

For details look at the git log. I list the steps from memory:

1: Created an empty default project with cargo new. 

2: Copied (from the rpi blinky example from the embassy repo, https://github.com/embassy-rs/embassy/tree/main/examples/rp ) some files:

- Cargo.toml
- src/blinky.rs
- .cargo/config.toml
- build.rs
- memory.x

3: Modified the Cargo.toml, changed the "path" dependencies to equivalent "git" dependencies. Miraculously, Cargo resolves all the dependencies and starts building! (cargo build)

4: But this wasn't enough. I had to use a nightly compiler and had to install the toolchain. But as i found out a bit later, all the manual changes could be skipped, by adding 

- rust-toolchain.toml

This one is a very simple version, the complete thing is here: https://github.com/embassy-rs/embassy/blob/main/rust-toolchain.toml 

NOW i can build and flash this simple project!

## Setup VSCode for debugging.

Apparently, i need 2 plugins:

- rust-analyzer
- debugger for probe-rs

Ah, and i need to have probe.rs installed. (probably already for the simple flashing above)

From the probe.rs documentation (https://probe.rs/docs/tools/debugger/) i created a launch.json. This allowed my to start debugging, set breakpoints and so on. 

In a second step, i could get the "trace" output (defmt logging they call it) in VSCode. 

Nearly GREAT. But not perfect, i have still trouble to restart the debugger after the first run: After stopping it, modifying the code and then wanting to restart it, everything hangs.

I guess i have to learn one or two things more... 
