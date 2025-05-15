{% if not btn_hotkey_a %}
{% set btn_hotkey_a = 'SELECT' %}
{% endif %}
{% if not btn_hotkey_b %}
{% set btn_hotkey_b = 'START' %}
{% endif %}

### Global Hotkeys

| Button Combo | Action |
| -- | -- |
| ++"L1"+"START"+"SELECT"++ | Exit Emulator / Application |
| ++"{{ btn_hotkey_a }}"+"Vol \+"++ | Brightness Up |
| ++"{{ btn_hotkey_a }}"+"Vol -"++ | Brightness Down |
| ++"{{ btn_hotkey_b }}"+"Vol \+"++ | LED on |
| ++"{{ btn_hotkey_b }}"+"Vol -"++ | LED off |
| ++"{{ btn_hotkey_a }}"+"{{ btn_hotkey_b }}"+"Vol \+"++ | WIFI enable |
| ++"{{ btn_hotkey_a }}"+"{{ btn_hotkey_b }}"+"Vol -"++ | WIFI disable |
