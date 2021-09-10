Bash scripts that set intel's cpu governor and turbo boost

Powersave: 
Constantly maintains the cpu's frequency at the base frequecy, regardless of the load
Conservative:
Fluctuates on-demand between the base frequency and the maximum frequency without intel's turbo boost
Performance:
Fluctuates on-demand between the base frequency and the maximum frequency with turbo boost

To monitor frequencies run:
`watch cat /sys/devices/system/cpu/cpu[0-7]*/cpufreq/scaling_cur_freq`

Move the script to /usr/local/bin to run it globally

## Usage:

`cpufreq powersave`
`cpufreq conservative`
`cpufreq performance`
