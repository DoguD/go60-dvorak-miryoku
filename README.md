# Go60 Dvorak Miryoku

ZMK config for the [MoErgo Go60](https://moergo.com/go60-support): Dvorak base, Miryoku-style 7-layer thumb system. A port of [5-col-corne-dvorak-miryoku](https://github.com/DoguD/5-col-corne-dvorak-miryoku); the layers, home row mods, clipboard and combo behave the same, so see that repo's README for the layout rationale.

## How the Corne layout maps onto the Go60

```
 ·  1  2  3  4  5 |  6  7  8  9  0  ·     number row (BASE; transparent on other layers)
 ·  ┌─────────────┼─────────────┐  ·
 ·  │  Corne 3x5  │  Corne 3x5  │  ·     outer column unused
 ·  └─────────────┼─────────────┘  ·
       ·  ·  ·    |    ·  ·  ·            3-key bottom row unused
          T1 T2 T3 | T3 T2 T1             Corne thumbs, same order
```

Go60 key positions (used by the hold-tap trigger lists and the combo):

```
  0  1  2  3  4  5 |  6  7  8  9 10 11
 12 13 14 15 16 17 | 18 19 20 21 22 23
 24 25 26 27 28 29 | 30 31 32 33 34 35
 36 37 38 39 40 41 | 42 43 44 45 46 47
       48 49 50    |    51 52 53
          54 55 56 | 57 58 59
```

## Differences from the Corne config

- **Number row** on BASE. Home row mods still need a key on the opposite hand, so Cmd+1–5 uses the right-hand Cmd (`T`) and Cmd+6–0 the left-hand Cmd (`E`).
- **Bootloader on both halves** (MEDIA, top pinky keys). The Go60 firmware has to be flashed onto each half, so the right half needs its own key. This replaces the Corne's `&soft_off`, which has no wake-up key defined on the Go60.
- **`BT_CLR`** on MEDIA, right outer column next to `BT_SEL 3`, since there is no separate settings-reset firmware.
- **Touchpads:** MoErgo's defaults. Right pad moves the cursor, left pad scrolls (tap = right click).
- **Debounce:** MoErgo's board defaults (4 ms press / 20 ms release) instead of the Corne's eager 1 / 10 ms.

## Building and flashing

Every push runs the **Build** workflow (Nix + [moergo-sc/zmk](https://github.com/moergo-sc/zmk)). Download `go60.uf2` from the run's artifacts, then flash it onto each half:

1. Hold `Esc` (MEDIA) and tap the top pinky key on the half you want to flash. It mounts as a USB drive.
2. Copy `go60.uf2` onto the drive. Repeat for the other half.

For local builds, start Docker and run `./build.sh`.
