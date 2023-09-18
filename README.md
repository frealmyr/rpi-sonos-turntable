# Raspberry Pi USB Sonos Bridge Ansible Playbook

This Ansible playbook is based on https://github.com/basdp/USB-Turntables-to-Sonos-with-RPi/tree/master

> The playbook will optimize the Raspberry Pi for headless operation, such as disabling unused services, moving logs to RAM and disabling swap for less SD card writes.

  - Flash a fresh copy of Raspbian 32-bit on a desired Raspberry Pi device
  - Change `hosts.yaml` to the IP address of the RPi address (use static IP or DHCP resevation)
  - Change the CARD name for the `/etc/asound.conf` configuration in `main.yml`, with your turntable USB card name which can be fetched using the command `aplay -l`
  - Run the playbook using `ansible-playbook main.yml`



## Lossless streaming?

I have given up on getting a decent implementation with lossless streaming using Raspberry Pi RasbianOS, as the quality improvement is most likely negligible. Buying a better input DAC will most likely yield a much better improvement.

Learnings:

  - `liquidsoap` debian package in raspbian is acient, 1.x.x something, upstream is 2.3.x. %ogg(%flac) will not work proplerly with the old 1.x.x version. Not worth the headache to manually manage dependencies and building source.
  - `darkice` only supports lossy formats. Note that the AAC implementation is using a less-than decent encoder, due to licensing. The MP3 encoder in CBR 320 is preferable.

The only sane way to get lossless, is most likely to use `Ubuntu 22.04 LTS` as the base OS. _Might do that one day and update this playbook if i get bored~_
