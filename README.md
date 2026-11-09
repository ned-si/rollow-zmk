# rollow-zmk

My ZMK config for the Rollow (Barbell Boards) on nice!nano controllers: 36 keys
in use, an EC11 encoder per half and an OLED.

Layout follows the
[unified ZMK config template](https://github.com/zmkfirmware/unified-zmk-config-template),
pinned to ZMK v0.3:

```
build.yaml               build targets (board + shield per half)
boards/shields/rollow/   shield definition: matrix, encoders, OLED
config/west.yml          ZMK version
config/rollow.keymap     keymap, both halves; includes the *.dtsi next to it
config/rollow.conf       Kconfig, both halves (display, encoders)
```

The Rollow is not in upstream ZMK, so its shield definition lives here. The
keymap uses the five-column transform: the outer column of each half is not
mapped.

## Get the firmware

Every push builds both halves in GitHub Actions. Open the run under the
Actions tab and download the `firmware` artifact: it holds
`rollow_left-nice_nano-zmk.uf2` and `rollow_right-nice_nano-zmk.uf2`.

## Flash

For each half: plug it in over USB, double-tap the reset button, and copy that
half's `.uf2` onto the `NICENANO` drive that appears. The drive unmounts on its
own when flashing is done. Flash both halves after a keymap change; the left
half is the central and holds the keymap, but both must run the same version.
