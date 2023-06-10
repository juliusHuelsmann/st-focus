Patch for suckless' simple terminal (`st`), which allows the user to specify two distinct opacity
values / background colors; one for the focused- and one for unfocused windows' background.
This enables the user to spot the focused window at a glance.
The patch is based on the [alpha patch](https://st.suckless.org/patches/alpha/); i.e. is to be
applied after applying the alpha patch.

The patch is released [on this release page](https://github.com/juliusHuelsmann/st/releases) and
[on the suckless page](https://st.suckless.org/patches/alpha_focus_highlight/).
Please [leave a star](https://github.com/juliusHuelsmann/st-focus).

## Contributions & Bug Reports
* [Report / Solve Patching issues](https://github.com/juliusHuelsmann/st) with a new version of `st`
* [Contributions and Bug reports](https://github.com/juliusHuelsmann/st-focus)

## Building, customizing and installing the patch
**1. Optional Dependencies**
The opacity functionality of this patch requires an `X composite manager` (e.g. `picom`, `compton`,
`xcompmgr`), which can for instance be installed via `sudo pacman -S picom` on Arch Linux and
launched via `picom -b`.  *The composite manager has to be relaunched after booting*.

**2. Applying the patch**
Apply the patch to `st`'s source code and build code via `patch < [PATCH_NAME]`

**3. Customization**
This patch performs changes in the `config.def.h` file, which need to be manually merged into a
pre-existing custom `config.h` file. The following four variables can be adapted:
- `alpha`/`alphaUnfocused` opacity of the terminal when focused / not focused.
- `bg`/`bgUnfocused` background color when focused / not focused.

**4. Build & install** `make; sudo make install`

## Download
If you want to try out the current version of the patch before patching your own build,
check out [this repository](https://github.com/juliusHuelsmann/st), which contains a
merged version of this patch with a reasonable configuration.

The patch comes
1. merged into the alpha patch (`alpha + focus`) or
2. for patching on top of an already applied alpha patch (`focus`)

I recommend downloading the alpha patch from the
[alpha patch](https://st.suckless.org/patches/alpha/) page and using `Patch: focus`, that way you
make sure that you apply the latest version of the alpha patch.

Note that patch errors can occur when the code in the st repo is updated.
Please report an Issue or contribute a merged patch in that case.

### Patch: alpha + focus

**st-0.9**
- [Version 2(attached)](st-focus-20230610-68d1ad9.diff)
- Most recent release [st-focus-20230610-68d1ad9.diff Github](https://github.com/juliusHuelsmann/st/releases/download/alpha_09/st-focus-20230610-68d1ad9.diff)

**st-0.8.3**
- [Version 1 (attached)](st-focus-20200530-43a395a.diff)
- Most recent release: [st-focus-20200530-43a395a.diff Github](https://github.com/juliusHuelsmann/st/releases/download/v2/st-focus-20200530-43a395a.diff)

---

### Patch: focus

**st-0.8.3**
- [Version 1 (attached)](st-focus-20200530-patch_alpha.diff)
- Most recent release: [st-focus-20200530-patch_alpha.diff (Github)](https://github.com/juliusHuelsmann/st/releases/download/v2/st-focus-20200530-patch_alpha.diff)


## MISC
**Note:** The benefit of the `alpha` patch and the `Alpha Focus Highlight` patch are the ability to
restrict the transparency only to the background color currently in use, hence keeping the font in
the foreground solid and readable.

If the goal is to apply transparency independent on the content, you do not require any patch for
`st`, instead add
`
inactive-opacity = 0.2;
active-opacity = 0.8;
`
to your `picom` configuration file and keep a vanilla `st` build.

If you want to configure `inactive-opacity` and `active-opacity` rules in order to apply opacity to
other applications, but keep the benefits of the st alpha patches, have a look at
[this picom configuration
file](https://github.com/juliusHuelsmann/Config/blob/master/.config/picom/picom.conf),
in which opacity management configured to be performed by `st`.

# Authors / Contributors
* Julius Hülsmann - <juliusHuelsmann [at] gmail [dot] com>
* [Wim Stockman](https://github.com/wimstockman): Fix erroneous color reset
* [glpub](https://github.com/glpub): Fix erroneous color reset
* [Milos Stojanovic](https://github.com/M4444): Code Formatting
* [Yui](https://github.com/yuwui): Fix spelling errors
* Authors of the shipped alpha patch: [Eon S. Jeon](mailto:esjeon@hyunmu.am), [pr](mailto:protodev@gmx.net), [Laslo Hunhold](mailto:dev@frign.de), [Ivan J.](mailto:parazyd@dyne.org), [Matthew Parnell](mailto:matt@parnmatt.co.uk), [Johannes Mayrhofer](mailto:jm.spam@gmx.net), [Àlex Ramírez](mailto:aramirez@posteo.net)
