# Running Kubuntu

## Touchpad

I could not find definitive info regading KCM's libinput support for touchpad configurations and Plasma 5.12, other than
[this](https://www.reddit.com/r/kde/comments/7qhyft/under_touchpad_settings_certain_options_are/) and [this](https://www.reddit.com/r/kde/comments/5s056t/most_of_the_touchpad_settings_are_disabled/).  Note that the former suggests Plasma 5.12 will support it
but in practice I found that it did not.

For now, went back to synaptics driver (`apt-get install xserver-xorg-input-synaptics`). 

This allowed KDE to control most of the settings (like disable tap-to-click which I despise).  However, two things that
it did not properly give me control over I had to use synclient to manually set:

1. The XPS' touchpad maps the right-bottom area to "right-click".  I had to use:
  ```
  $ synclient RightButtonAreaLeft=0
  $ synclient RightButtonAreaTop=0
  ```
  This disabled it.

2. Palm detection or "disable touchpad while typing".  Setting `synclient PalmDetect=1` improved this a little bit.

I put both sets in my `$HOME/.xsession` to persist them instead of adding an X.org config file in etc.
