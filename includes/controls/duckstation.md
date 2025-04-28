{% if not btn_hotkey_a %}
{% set btn_hotkey_a = 'SELECT' %}
{% endif %}
### Duckstation ([PSX](../../../systems/psx))

| Button Combo | Action |
| -- | -- |
| ++"{{ btn_hotkey_a }}"+"R1"++ | Save State |
| ++"{{ btn_hotkey_a }}"+"L1"++ | Load State |
| ++"{{ btn_hotkey_a }}"+"R2"++ | Fast-Forward |
| ++"{{ btn_hotkey_a }}"+"{{ btn_north }}"++ | Open Menu |
| ++"{{ btn_hotkey_a }}"+"{{ btn_east }}"++ | Screenshot |
| ++"{{ btn_hotkey_a }}"+"START"++ | Quit Game |

| Supported Bios Files | Path |
| --- | --- |
| [List](https://github.com/stenzek/duckstation/blob/master/src/core/bios.cpp#L32) | `/roms/bios` |
