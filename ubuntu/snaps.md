# Using snaps

I like zsh and have a whole setup with antigen, etc.  After I switched to zsh snap-installed applications stopped being available in gnome.

Easiest fix for this is to make zsh setup your env the same way that /etc/profile does for bash. (I.e. set the additional bin and desktop paths).

For some reason, Ubuntu does not do this with the zsh package (even though I think it would make sense for them to do so).

Added `emulate sh -c 'source /etc/profile'` to /etc/zsh/zprofile.

See [also](https://askubuntu.com/questions/989871/i-cant-use-snap-packages-even-if-installed/990507)
