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

## What I've used so far

* **Scurest's [Apicula](https://github.com/scurest/apicula/blob/master/README.md)**, can be used for working with those models overall.

    Quick command reminder:

        apicula view p00_00.bmd p00_00.btx



* **Gericom's [MKDS Course Modifier](https://gbatemp.net/threads/mkds-course-modifier.299444/)**,  can be used for texture edits, exporting and importing as png.

* **CUE's [Nintendo DS/GBA Compressors](https://gbatemp.net/threads/nintendo-ds-gba-compressors.313278/)**,  can be used for decompress the .lz exention of the files.

* **[Hex Workshop](http://www.hexworkshop.com)**,  It's the Hex Editor that I'm using.

* **[XVI32](http://www.chmaas.handshake.de/delphi/freeware/xvi32/xvi32.htm)**,  I'm using this software to mass edit hex header (remove) from the files. Don't know how to bulk put them back yet tho, so save your backups.

* **[Bulk Rename Utility](https://www.bulkrenameutility.co.uk)**,  This utility can save you a bunch of time renaming extensions.


### Extracting .lz files

With CUE's Nintendo compressors, you can run the command to decompress and compress respectively:

        lzss.exe -d any_boring_name.lz

        lzss.exe -evn any_boring_name.nxtp

Every extension you can change for yourself with Bulk Rename Utility

### Converting the files (.ntxp to .btx, etc...)

This is kinda the annoying part. First of all the easy "1 file edit" way, is open the file with your favorite HEX Editor, and delete everything until the header of the file. (BMD0, BTX0, etc...). Remember to save the header, to put it back in when you are done.

For bulk converting, I've managed to use XVI32 to edit every file on the folder, and delete everything up until the header.

First I've created a BATCH script that runs the script in every file with the extension that I've wanted (any_boring_convert_name.xsc was the name of the xvi32 script): -  /W  parameter is required for tons of files, because it will break if the batch script tries to run every xvi32 script at once... trust me on this one. Save this as any_boring_name.bat

        FOR %%f IN (*.ntxp) DO START /W PATH_TO_FILE\xvi32.exe %%f /S=PATH_TO_FILE\any_boring_convert_name.xsc.xsc

And then I've executed this simples XVI script, that deletes the first 48 bytes of the file (it was the side for the BTX files, can't confirm if is the same size for the other formats), and then verify is the file starts with BTX0 header. It will show a runtime error if it doesn't start with BTX0 header. Save this as any_boring_convert_name.xsc

        DEL 48
        VERIFY 42 54 58 30


### Editing .btx files

This was easy enough. Just open the btx file that you want to edit with MKDS Course Modifier. With this powerful tool you can export to PNG (remember to select the image and the palette). After messing with the png, you can import back and save as btx again.
