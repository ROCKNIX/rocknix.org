{% if not btn_hotkey_a %}
{% set btn_hotkey_a = 'SELECT' %}
{% endif %}
### Xemu ([XBOX](../../../systems/xbox))

| Button Combo | Action |
| -- | -- |
| ++"{{ btn_hotkey_a }}"++ | Open Menu |

| Required Bios Files | Path |
| --- | --- |
| Complex_4627v1.03.bin | `/roms/bios/xemu/bios` |
| mcpx_1.0.bin | `/roms/bios/xemu/bios` |