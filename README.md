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
