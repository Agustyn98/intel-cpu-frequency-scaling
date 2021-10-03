# Change Intel's energy preference
Bash script that sets intel's cpu energy preference and turbo boost.

This script can help laptops get even more battery life than under Windows


## Usage:

**Move the script `cpu` to /usr/local/bin to run it globally**


`cpu power_max` or `cpu 0`

`cpu power` or `cpu 1`

`cpu balance` or `cpu 2`

`cpu performance` or `cpu 3`

`cpu performance_max` or `cpu 4`

To monitor frequencies run:
`watch cat /sys/devices/system/cpu/cpu[0-9]*/cpufreq/scaling_cur_freq`


## Make changes permanent

Move the energy_policy.service to `/etc/systemd/system/`
then run `systemctl enable energy_policy`

Powersave mode is enabled by default, change the default mode by editing ExecStart
`ExecStart=/usr/local/bin/cpu [MODE]`


## Core number

The script is hardcoded for 4 core 8 threads cpus, you might need to adjust the for loop depending on your model
