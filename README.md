# Change Intel's energy preference
Bash script that set intel's cpu energy preference and turbo boost.
This script can help laptops get even more battery life than under Windows


## Modes:

Each mode adjusts the cpu's frequency range, and how aggressively it scales up under load.

-Maximum powersave:

Sets the energy performance preference to 'power' and disables turbo boost.
Runs almost constantly at the minimum frequency, and scales up very conservatly.


-Powersave:
 
Sets the energy performance preference to 'balance_power' and disables turbo boost, about 10% more performance than maximum powersave mode


-Balance:

Sets the energy performance preference to 'balance_power' and enables turbo boost, about 50% more performance than powersave mode


-Performance:

Sets the energy performance preference to 'balance_performance' and enables turbo boost, about 50% more performance than balance mode.
This mode is the default on most kernels, however it doesn't reach the cpu's maximum frequency under load on computers I've tested it


-Maximum performance:

Sets the energy performance preference to 'performance' and enables turbo boost, about 7% more performance than performance mode.
Constatly runs at the cpu's maximum frequency, regardless of the load, I would only run this mode for short periods of time


## Usage:

**Move the script `cpu` to /usr/local/bin to run it globally**


`cpu power_max` or `cpu 0`

`cpu power` or `cpu 1`

`cpu balance` or `cpu 2`

`cpu performance` or `cpu 3`

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`cpu performance_max` or `cpu 4`

To monitor frequencies run:
`watch cat /sys/devices/system/cpu/cpu[0-7]*/cpufreq/scaling_cur_freq`


## Make changes permanent

Move the energy_policy.service to `/etc/systemd/system/`
then run `systemctl enable energy_policy`

Powersave mode is enabled by default, change the default mode by editing ExecStart
`ExecStart=/usr/local/bin/cpu [MODE]`


## Core number

The script is hardcoded for 4 core 8 threads cpus, you might need to adjust the for loop depending on your model
