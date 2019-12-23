# 2018 12 05 config pulseaudio

[go back to server ToGo](../doc/togo.md#audio)


## Info
* https://wiki.ubuntuusers.de/PulseAudio/
* https://askubuntu.com/questions/767032 \
  "How to enable 5.1 channel playback on a Realtek ALC887-VD chip?"

## Steps
Comment: Maybe first step is unnecessary.

### 1. edit pulseaudio

~~~~~
    $ sudo nano /etc/pulse/daemon.conf
~~~~~

~~~~~
    ... ; remixing-use-all-sink-channels = yes
    ... ; enable-lfe-remixing = no
    >>> ; 2018 12 05 peter: enable 4 channel mode
    >>> enable-lfe-remixing = yes
    ... ; lfe-crossover-freq = 0
    ...

    ... ; alternate-sample-rate = 48000
    ... ; default-sample-channels = 2
    >>> ; 2018 12 05 peter: enable 4 channel mode
    >>> default-sample-channels = 4
    ... ; default-channel-map = front-left,front-right
    ...
~~~~~

### 2. reboot

~~~~~
    $ sudo reboot
~~~~~

### 3. set channel numbers in alsamixer

~~~~~
    $ alsamixer
~~~~~

Control:
* use <right arrow> to select "channel"
* use <up    arrow> to set 4 channels (instead of 2)
* press <esc>

### 4. reboot

~~~~~
    $ sudo reboot
~~~~~
