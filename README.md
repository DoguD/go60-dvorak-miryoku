# Go60 Dvorak Miryoku

ZMK config for the [MoErgo Go60](https://moergo.com/go60-support): Dvorak base with a Miryoku-style thumb-layer core. It started as a port of [5-col-corne-dvorak-miryoku](https://github.com/DoguD/5-col-corne-dvorak-miryoku) and uses the Go60's touchpads and extra keys to drop the MOUSE, MEDIA and FUN layers.

## Base layer

```
 ·    1    2    3    4    5  |  6    7    8    9    0    ·
 ·    '    ,    .    p    y  |  f    g    c    r    l    =
TR    a    o    e    u    i  |  d    h    t    n    s    -
Mgc   /    q    j    k    x  |  b    m    w    v    z    ·
          prev  ⏯  next      |     mute vol− vol+
            Esc  Spc  Tab    |  Ent  Bsp  Del
                 NUM  SYM    |            NAV
```

- Home row mods (CAGS): Ctrl / Alt / Cmd / Shift on `a o e u` and `h t n s`. Positional: they only act as mods with a key on the opposite hand, so Cmd+1–5 uses the right-hand Cmd (`T`) and Cmd+6–0 the left-hand Cmd (`E`).
- `-` and `=` sit where standard Dvorak has them; both are also on NUM.
- Esc, Enter and Backspace are plain keys (no hold), so Backspace repeats when held.
- Both shifts together toggle Caps Lock.

## Layers

| Layer | How | Contents |
|---|---|---|
| NAV | hold Delete | Left hand: inverted-T arrows, Home/End, PgUp/PgDn, Caps Word, clipboard. F1–F12 on the number row. |
| NUM | hold Space | Right-hand number pad, plus `` [ ] ; = \ ` - . `` |
| SYM | hold Tab | Shifted symbols on the right hand |
| TR | tap the left outer home-row key (`TR`), then the letter; or hold it | Turkish letters on their Latin base letters: ç on c, ğ on g, ı on i, ö on o, ş on s, ü on u. Shift gives Ç Ğ Ö Ş Ü, and Shift+ı gives İ (Shift+i on Base already gives I). |
| MAGIC | hold the bottom-left corner (`Mgc`) | MoErgo's default Magic layer: RGB lighting, Bluetooth profiles (tap to select, double-tap to disconnect), clear one / all pairings, USB output, screen brightness, media, reset and bootloader (outer column, second row, each half). Only the factory-test key is left out. Tapping the corner instead shows battery, Bluetooth, layer and Caps Lock status on the left-hand LEDs for 10 s. |
| TOUCH | finger on the right touchpad | Left home row = plain Ctrl / Alt / Cmd / Shift (instant Cmd-click, Shift-click); Esc thumb = right click, Tab thumb = left click (hold to drag). Everything else passes through. |

Turkish letters need the macOS input source set to **ABC – Extended** (System Settings → Keyboard → Input Sources). It types exactly like U.S.; the TR keys send an Option dead key and then the letter (⌥c then s = ş). Unicode Hex Input is not used because it breaks Option+Backspace and Option+arrows. Caps Lock and Caps Word don't capitalize the Turkish letters, so use Shift.

The right touchpad moves the cursor (2× speed). The left touchpad scrolls (tap = right click), inverted to match the Mac trackpad with natural scrolling on.

TOUCH turns on only after 300 ms without typing and stays on for 500 ms after the last touchpad movement. Pressing any key other than its four mods and two clicks turns it off at once, so you can go straight back to typing (except `a o e u`, Esc and Tab within that half second).

## Key positions

```
  0  1  2  3  4  5 |  6  7  8  9 10 11
 12 13 14 15 16 17 | 18 19 20 21 22 23
 24 25 26 27 28 29 | 30 31 32 33 34 35
 36 37 38 39 40 41 | 42 43 44 45 46 47
       48 49 50    |    51 52 53
          54 55 56 | 57 58 59
```

## Building and flashing

Every push runs the **Build** workflow (Nix + [moergo-sc/zmk](https://github.com/moergo-sc/zmk)). Download `go60.uf2` from the run's artifacts, then flash it onto each half:

1. Hold the bottom-left corner (MAGIC) and tap the bootloader key on the half you want to flash (outer column, second row). It mounts as a USB drive.
2. Copy `go60.uf2` onto the drive. Repeat for the other half.

For local builds, start Docker and run `./build.sh`.
