{%- if not abl_scripts -%}
{%- set abl_scripts = 'root' -%}
{%- endif -%}
[OpenABL](https://github.com/OpenHandheldCollective/OpenABL) is the bootloader used to boot ROCKNIX. Downloads are available from the [OpenABL releases](https://github.com/OpenHandheldCollective/OpenABL/releases) page.

- Once you have written the image to an SD card, insert the card and boot into Android.
- Copy the `openabl` folder from the SD card to the root of Android Internal Storage.
{%- if abl_scripts == 'run_script_as_root' %}
- Navigate to Settings -> Handheld Settings -> Advanced -> Run Script as Root.
- Select the `openabl` folder on the Internal Storage.
- Run the `backup_abl.sh` script to backup your current ABL.
- After backup, run the `flash_abl.sh` script to flash OpenABL.
{%- elif abl_scripts == 'root_scripts' %}
- Launch the 'Handheld Settings' app, navigate to 'Advanced' -> 'Root Scripts' and import the `backup_abl.sh` and `flash_abl.sh` scripts from the `openabl` folder on Internal Storage.
- Navigate to 'Script Management' and run the `backup_abl.sh` script to backup your current ABL.
- After backup, navigate to 'Script Management' and run the `flash_abl.sh` script to flash OpenABL.
{%- else %}
- Execute as root the `backup_abl.sh` script from the Internal Storage to backup your current ABL.
- After backup, execute as root the `flash_abl.sh` script to flash OpenABL.
{%- endif -%}
