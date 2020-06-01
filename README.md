# st-focus
Patch for suckless' simple terminal (`st`), which allows the user to specify two distinct opacity
values / background colors; one for the focused- and one for unfocused windows' background.
This enables the user to spot the focused window at a glance.


## Patch
The patch is released [on this release page](https://github.com/juliusHuelsmann/st/releases) and
[on the suckless page](https://st.suckless.org/patches/alpha_focus_highlight/).

## Building, customizing and installing the patch
### 1. Optional Dependencies
The opacity functionality of this patch requires an `X composite manager` (e.g. `picom`, `compton`, `xcompmgr`), which can for instance be installed via `sudo pacman -S picom` on Arch Linux. **The composite manager has to be launched after booting**.

### 2. Applying the patch 
It can be applied to `st`'s source and build code via `patch < [PATCH_NAME]`

### 3. Customization
This patch performs changes in the `config.def.h` file, which need to be manually merged into a pre-existing custom `config.h` file. The following four variables can be adapted:
- `alpha`/`alphaUnfocused` opacity of the terminal when focused / not focused.
- `bg`/`bgUnfocused` background color when focused / not focused.

### 4. Build & install
```bash
make 
sudo make install
```

## Download
The pre-patched current version of the full vim patch with a reasonable configuration and some
additional patches can be tried out in [this repository](https://github.com/juliusHuelsmann/st),
in which this patches are also ported to new releases of `st`,
and [released](https://github.com/juliusHuelsmann/st/releases).

The patch comes 
1. with the alpha patch pre-applied (st-focus-20200530-43a395a.diff) or 
2. for patching on to of an already applied alpha patch (st-focus-20200530-patch_alpha.diff)




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



# Authors / Contributers
* Julius Hülsmann - <juliusHuelsmann [at] gmail [dot] com>
* [glpub](https://github.com/glpub): Fix: erroneous color reset
* [Milos Stojanovic](https://github.com/M4444): Code Formatting
* [Yui](https://github.com/yuwui): Fix spelling errors

