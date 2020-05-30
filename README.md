# st-focus
Patch for suckless' simple terminal (`st`), which allows the user to specify two distinct opacity
values / background colors; one for the focused- and one for unfocused windows' background.
This enables the user to spot the focused window at a glance.


## Patch
The patch is released [on this release page](https://github.com/juliusHuelsmann/st/releases) and
[on the suckless page](https://st.suckless.org/patches/alpha_focus_highlight/).

## Build the focus patch
This patch requires an `X composite manager` (e.g. `picom`, `compton`, `xcompmgr`).
```bash
sudo pacman -S picom
```
It can be applied to `st`'s source and build code via
```bash
patch < [PATCH_NAME]
make
```
after removing/adapting an existing config.h to contain the changes shipped in the config.def.h.

The pre-patched current version of the full vim patch with a reasonable configuration and some
additional patches can be tried out in [this repository](https://github.com/juliusHuelsmann/st),
in which this patches are also ported to new releases of `st`,
and [released](https://github.com/juliusHuelsmann/st/releases).

## Customization
- `alpha`/`alphaUnfocused` opacity of the terminal when focused / not focused.
- `bg`/`bgUnfocused` background color when focused / not focused.

## MISC
**Note** The benefit of the `alpha` patch and the `Alpha Focus Highlight` patch are the ability to
restrict the transparency only to the background color currently in use, hence keeping the font in
the foreground solid and readable.

If the goal is to apply transparency independent on the content, you do not require any patch for
`st`, instead add
```bash
inactive-opacity = 0.2;
active-opacity = 0.8;
```
to your `picom` configuration file and keep a vanilla `st` build.

If you want to configure `inactive-opacity` and `active-opacity` rules in order to apply opacity to
other applications, but keep the benefits of the st alpha aptches, have a look at
[this picom configuration
file](https://github.com/juliusHuelsmann/Config/blob/master/.config/picom/picom.conf),
in which opacity management configured to be performed by `st`.

