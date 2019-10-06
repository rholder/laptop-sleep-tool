[![License](https://img.shields.io/badge/license-apache%202.0-brightgreen.svg)](https://github.com/rholder/laptop-sleep-tool/blob/master/LICENSE)
# laptop-sleep-tool

Use `laptop-sleep-tool` to show and optionally set a few sleep mode parameters on modern Linux kernels. I wrote this to quickly diagnose and check the sleep settings on laptops without having to remember which file needs to be manipulated. By itself, it does NOT permanently set the sleep mode so changes made will not persist across reboots. With this tool, one can check the current setting, switch back and forth between settings, and test whether the sleep modes are performing correctly.

It's been tested mostly on a few varieties of Dell XPS 13 laptops that were experiencing high battery drain during sleep using the default settings from Ubuntu 18.04 and the `4.15.x` kernel. It probably works on a bunch of other hardware, too.

## Features
* Show current memory sleep setting
* Set the current memory sleep setting, if run as root, to `deep` or `s2idle`

## Installation
It's a Bash shell script that can go somewhere in your `PATH`. The latest release is available [here](https://github.com/rholder/laptop-sleep-tool/releases).

### Linux
Drop the script into your path, such as `/usr/local/bin`:
```bash
sudo curl -o /usr/local/bin/laptop-sleep-tool -L "https://github.com/rholder/laptop-sleep-tool/releases/download/v1.0.0/laptop-sleep-tool" && \
sudo chmod +x /usr/local/bin/laptop-sleep-tool
```

## Usage
```
Usage: laptop-sleep-tool [OPTION]

  View or update the current laptop sleep settings.

Options:
    -m,  --current-mem-sleep      Print the current mem_sleep state from /sys/power/mem_sleep
    -md, --set-mem-sleep-deep     Set the current mem_sleep state to "deep" (root only)
    -ms, --set-mem-sleep-s2idle   Set the current mem_sleep state to "s2idle" (root only)
    -v,  --version                Print the current version and exit
    -h,  --help                   Print this help text and exit

Examples:
  laptop-sleep-tool --current-mem-sleep
  laptop-sleep-tool --set-mem-sleep-deep

Report bugs and find the latest updates at https://github.com/rholder/laptop-sleep-tool.
```

## References
* There is a permanent battery drain fix noted [here](https://www.reddit.com/r/Dell/comments/8b6eci/xp_13_9370_battery_drain_while_suspended/dx4ftc5/).
* These are the official power states from the [Linux kernel documentation](https://www.kernel.org/doc/Documentation/power/states.txt).

## License
`laptop-sleep-tool` is released under version 2.0 of the [Apache License](http://www.apache.org/licenses/LICENSE-2.0).