# Ubuntu 17.10 on Dell XPS 13 (9360)

Running list of notes I have getting Ubuntu happy on an XPS 13" 9360

The [arch notes](https://wiki.archlinux.org/index.php/Dell_XPS_13_(9360)) are fantastic.

## Scaling on display

By default Ubuntu starts up with the beautiful display at 200% scaling.  Too big for me.  Unfortunately as of right now you can have 100%, 200% or 300%.

I'd like 125% because 100% is too small for my aging eyes.

```
gsettings set org.gnome.mutter experimental-features "['scale-monitor-framebuffer']"
```

_Note: I had to logout and log back in before I had "fractional" scaling settings._

To turn it back off, just set the value of the key to empty string.

As pointed out [here](https://nixaid.com/hidpi-display-on-ubuntu-17-10-and-font-size/) all this seems to do right now is set the resolution lower.
You can check it with xrandr, 125% on the XPS' display:
```
Screen 0: minimum 320 x 200, current 2560 x 1440, maximum 8192 x 8192
XWAYLAND0 connected 2560x1440+0+0 (normal left inverted right x axis y axis) 290mm x 170mm
   2560x1440     59.91*+
```


## Make touchpad right-click not annoying
Credit to the [answer here](https://askubuntu.com/questions/984200/how-to-replace-bottom-right-zone-click-with-two-finger-touch-click-on-clickpad) since most search hits seem to be for older versions of Ubuntu using Xorg.

```
gsettings set org.gnome.desktop.peripherals.touchpad click-method 'fingers'
```

Set it to `default` to go back to the irritating behavior.

## Misc

### apport-gtk spinning a core to 100%

While working with the laptop, I noticed my battery draining fast and one of my cores pegged by `apport-gtk`.  This apparently is the ubuntu crash reporter.  I think it was spinning on a Google Chrome tab process crash report.  I removed all the files in /var/crash and it finally gave up.

[Credit here](https://askubuntu.com/questions/454187/apport-gtk-100-cpu-usage-on-startup-on-ubuntu-14-04-lts)


