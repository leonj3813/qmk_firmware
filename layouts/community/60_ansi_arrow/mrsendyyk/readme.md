# Sendy YK's 60% ANSI Arrow Layout and Keymap

[https://mr.sendyyk.com](https://mr.sendyyk.com)

## 60% ANSI Arrow Layout

![LAYOUT_60_ansi_arrow](https://raw.githubusercontent.com/mrsendyyk/my_qmk/master/dz60/assets/layout-60-ansi-arrow.png)

## Keymap

### Default Layer

![_BASE](https://raw.githubusercontent.com/mrsendyyk/my_qmk/master/dz60/assets/layout-60-ansi-arrow-keymap---layer-0.png)

### Fn Layer 1

Press and hold *right* **Ctrl** key.

![_FN](https://raw.githubusercontent.com/mrsendyyk/my_qmk/master/dz60/assets/layout-60-ansi-arrow-keymap---layer-1.png)

### Fn Layer 2

Press and hold *right* **Alt** key.

![_SETTINGS](https://raw.githubusercontent.com/mrsendyyk/my_qmk/master/dz60/assets/layout-60-ansi-arrow-keymap---layer-2.png)

### RGB Lighting/LED/Underglow as Caps Lock, Num Lock, Scroll Lock, and Layer Indicator

#### Caps Lock Indicator

```c
    // Caps Lock Indicator
    if (IS_LED_ON(usb_led, USB_LED_CAPS_LOCK)) {
        writePinLow(B2);
        rgblight_setrgb(100, 255, 100);
    }
```

#### Num Lock Indicator

```c
    // Num Lock Indicator
    if (host_keyboard_led_state().num_lock) {
        rgblight_setrgb(225, 8, 0);
    }
```

#### Scroll Lock Indicator
```c
    // Scroll Lock Indicator
    if (host_keyboard_led_state().scroll_lock) {
        rgblight_setrgb(255, 110, 0);
    }
```

#### Layer Indicator

```c
    // Layer Indicator
    else {          
        switch (get_highest_layer(layer_state)) {
            // Fn Layer 1 Indicator
            case _FN:
                rgblight_setrgb(100, 255, 100);
                break;
            // Fn Layer 2 Indicator
            case _SETTINGS:
                rgblight_setrgb(100, 255, 100);
                break;
            // Default Layer Indicator
            case _BASE:
                rgblight_setrgb(0, 0, 0);
                break;
        }
        update_led();
    }
```

## Build The Firmware

You will need to build the firmware. To do so go to your terminal window and run the compile command:

    qmk compile -kb dz60 -km mrsendyyk

See [The Complete Newbs Guide To QMK](https://docs.qmk.fm/#/newbs).
