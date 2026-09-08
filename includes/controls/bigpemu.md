{% if not btn_hotkey_a %}
{% set btn_hotkey_a = 'SELECT' %}
{% endif %}
### BigPEmu ([Atari Jaguar](../../../systems/atarijaguar))

| Button Combo | Action |
| -- | -- |
| ++"{{ btn_hotkey_a }}"+"R1"++ | Quicksave |
| ++"{{ btn_hotkey_a }}"+"L1"++ | Quickload |
| ++"{{ btn_hotkey_a }}"+"{{ btn_north }}"++ | Open Menu |
