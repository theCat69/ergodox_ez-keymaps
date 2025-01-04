# The cat ergodox ez m32u4 glow configuration

## How to build and flash your ZSA keyboard

In this setup i will not fork the Qmk firmware from zsa to keep things simple and lightweight.
If you like to do so you will have to adapt this walkthrough.

- Go on oryx website to get your latest layout : [https://configure.zsa.io](https://configure.zsa.io).
- Download the source code for your current layout.
- Check the full name for your keyboard. Example for me the hex file is called like so : zsa_ergodox_ez_m32u4_glow_fef-layout_J5evZ_gWKMq.hex my keyboard will be at zsa/ergodox_ez/m32u4/glow.
- Put the source code in a folder (this will be your git repository).
- Change the name of the source file directory : `mv <my_source_directory> <new_name_for_my_keymap>`.
- Check the current QMK firmware version used by ZSA (branch name) : [https://github.com/zsa/qmk_firmware](https://github.com/zsa/qmk_firmware) verify it correspond to the firmware on oryx website.
- Setup QMK on your device (depends on OS) BE CAREFULL TO USE ZSA SETUP FOR THE CORRECT FIRMWARE(on zsa qmk firmware github repo and care for the firmware version because the readme is not always up to date) : [https://docs.qmk.fm/newbs_getting_started](https://docs.qmk.fm/newbs_getting_started).
- If you followed the installation you should find your firmware at ~/qmk_firmware, your origin should be the zsa/qmk github repo and you should be on the branch corresponding to your firmware version.
- You should try to build the default keymap for your keyboard. In my case : `make zsa/ergodox_ez/m32u4/glow:default`.
- If any erros comes up and you are not able to build the default keymap fix the errors until you can build it.
- Create a symlink between your keymap folder inside your project and a the last folder corresponding to your keyboard then keymaps: `ln -s <full_path_to_my_folder> <full_path_to_my_keyboard_in_qmk_firmware>/keymaps`. In my case (i am on windows):  `ln -s C:\dev\c_projects\ergodoxez_zsa_fvd\fvd C:\Users\fef\qmk_firmware\keyboards\zsa\ergodox_ez\m32u4\glow\keymaps\`.
- Build your keymap. In my case : `make zsa/ergodox_ez/m32u4/glow:<new_name_for_my_keymap>`.
- You are all setup to modify the keymap.c file from your layout to compile it again using make.
- Compiled hex file can be found in the root folder of you qmk_firmware folder.
- Flash your keyboard to test your new functionality ! Personally i use keymapp that i downloaded from oryx website but feal free to use anything !

## Notes from ZSA : Building your layout from source

Congratulations on taking the next step, and making use of your keyboard's open-source nature! There's so much power to unlock — this is going to be fun. :)

Here are some initial pointers to get you started:

- Use the documentation at [https://docs.qmk.fm/](https://docs.qmk.fm/) to set up your environment for building your firmware.
- Build your layout against [https://github.com/zsa/qmk_firmware/](https://github.com/zsa/qmk_firmware/) which is our QMK fork (instead of qmk/qmk_firmware). This is what Oryx (the graphical configurator) uses, so it's guaranteed to work.
- Create a folder with a simple name (no spaces!) for your layout inside the qmk_firmware/keyboards/ergodox_ez/glow/keymaps/ folder.
- Copy the contents of the \*\_source folder (in the .zip you downloaded from Oryx) into this folder.
- Make sure you've set up your environment per the [QMK docs](https://docs.qmk.fm/#/newbs_getting_started?id=set-up-your-environment) so compilation would actually work.
- From your shell, make sure your working directory is qmk*firmware, then enter the command `make ergodox_ez/glow:_layout_`, substituting the name of the folder you created for "_layout_".

Good luck on your journey! And remember, if you get stuck, you can always get back to your [original layout](https://configure.zsa.io/ergodox-ez/layouts/J5evZ/gWKMq/0) from Oryx.
