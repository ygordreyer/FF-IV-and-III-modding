# FF IV modding
 Reverse engineering of FF IV steam version.


 * `.nsbmd`, `.BMD`, or `.BMD0`: 3D models, textures, palettes
 * `.nsbtx`, `.BTX`, or `.BTX0`: textures, palettes
 * `.nsbca`, `.BCA`, or `.BCA0`: joint animations
 * `.nsbtp`, `.BTP`, or `.BTP0`: pattern animations (flipbook-type)
 * `.nsbta`, `.BTA`, or `.BTA0`: material animations (experimental!!)


 So far what I've seen from FF IV files:

 * `.ntxp` = `.BTX`
 * `.nmdp` = `.BMD`
 * `.ncap` = `.BCA`
 * `.namp` = `.BTA`
 * `.nanr` = `.KNBA` - Animation bank
 * `.ncer` and `.nscr` = `.KBEC` - CEII BANK

 * `.ncgr` = `.PNG` (just open as PNG, don't need to remove the header from HEX)

 * `.nmd`  - Are filled with 00 01 11 00 only from what I've seen, so that is a lead I guess



With github.com/scurest/apicula/

* **Scurest's [Apicula](https://github.com/scurest/apicula/blob/master/README.md)**, can be used for working with those models overall.

    Quick command reminder:

        apicula view p00_00.bmd p00_00.btx

    

* **Gericom's [MKDS Course Modifier](https://gbatemp.net/threads/mkds-course-modifier.299444/)**,  can be used for texture edits, exporting and importing as png.
