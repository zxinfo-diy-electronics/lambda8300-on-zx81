# Running Lambda on a ZX81
This repository provides a customized Lambda v1 rom that can be used on a real ZX81. The overlay rom to be used with [OpenSpand](https://codeberg.org/NollKollTroll/OpenSpand) interface to turn your ZX81 into a Lambda 8300.

# WHAT is SUPPORTED
The customized ROMs together with latest OpenSpand firmware 0.51.4 or higher, and they provides together the following features:

## Plain ZX81 only
* Lambda 8300 rom v1 customized for ZX81 hardware (starts up with blinking cursor only). (Lambda 8300 rom v2 might come later)

## With OpenSpand interface
* Overlay adding support for CAT and LOAD of programs from OpenSpand SD Card storage
* SAVE'ing to OpenSpand storage using SAVE command
* Lambda 8300 beeper support
* Lambda 8300 specific characters, as some of the standard ZX81 has been changed to more gaming oriented.
* Joystick support via OpenSpand

# HOW-TO - with standard ZX81
The CUSTOM.ROM provided is a 16KB ROM (compared to standard 8K ROM), so some modification is needed in order to use it. It has been tested with my own external-rom-interface, which will be improved to get better support. For many cases this setup does not provide the Lambda specific characters - mainly because of 1) On Lambda character bitmaps are provided by ULA 2) The way the ZX81 display system works. Using OpenSpand fixes this anyway.


# HOW-TO - with OpenSpand
In order to prepare your setup for running as a Lambda 8300 using OpenSpand

* Copy the zx81*.rom to your SD Card and rename to CUSTOM.COM
* Copy the zx81*.ovl to your SD Card and rename to CUSTOM.OVL
* Copy LCMDR.P to your SD Card. This is a cut-down Lambda version of ZXPand Commander. It is not recommended for now to rename this to MENU.P, as starting up as a ZX81 with this can lead to unknown disruptions of the setup.
* Eventually copy other programs (in P format) to the SD Card.

Now assemble your setup and put the SD Card into the interface and power up. When ready you need to configure OpenSpand for this setup.
* Press 'config' button to activate the CONFIG program.

<table border="0">
 <tr>
    <td valign="top" width="50%">
      <ul>
        <li>A: Audio mode: Make sure to select one with "LAMBDA"</li>
        <li>J: Joystick LAMBDA V1 - to map the joystick interface to Lambda use</li>
        <li>V: If using the OpenSpand composite out, select VIDEO INV / BLACK BORDER for full true experience</li>
        <li>R: ROM CUSTOM (to use the above CUSTOM.ROM & OVL)</li>
        <li>C: CHAR RFSH FROM CHOSEN ROM</li>
      </ul>
      <br>
      Press Q to boot your ZX81 as a Lambda 8300. If you want the setup to be permanent, remember to press 'S' to save SETTINGS.
    </td>
    <td><img width="512" alt="OpenSpand Config" src="https://github.com/user-attachments/assets/e724bc63-c951-49fd-b338-320f6548e717" /></td>
 </tr>
</table>

# My current setup - ZX81, OpenSpand running a game for Lambda 8300
<img width="960" height="1280" alt="IMG_0064 Large" src="https://github.com/user-attachments/assets/be6d4ea6-52fa-48b9-a510-a5d7b6f7470e" />

# ERROR CODES
Lambda 8300 uses two-letter error reporting, these are mapped to the OpenSpand interface to use the corresponding ZX81 one-letter codes:

| ZX81 code | Standard ZX81 report | Lambda 8300 report | OpenSpand error (shown in inverse video) |
|---|---|---|---|
| 1 | NEXT without FOR | `NF` Next without For | Fatal disk error |
| 2 | Variable not found | `UV` Unidentified Variable | Internal error |
| 3 | Subscript wrong | `BS` Bad Subscript | Not ready (no card) |
| 4 | Out of memory | `OM` Out of Memory | Not found |
| 5 | Out of screen | `SF` Screen Full | No path |
| 6 | Number too big (arithmetic overflow) | `OV` OVerflow | Invalid name |
| 7 | RETURN without GOSUB | `RG` RETURN without GOSUB | Write protect |
| 8 | INPUT as a command | `II` Illegal Input | Exists |
| 9 | STOP statement | `ST` STopped | Boot error |
| D | BREAK, CONT repeats | `BK` BreaK | No FS |
| F | No program name supplied | `NA` no program NAme | Timeout |

# TECHNICAL NOTE - Why a 16KB ROM?
As the Lambda 8300 does NOT provide character bitmaps from the ROM, but the ULA, the 512 bytes used for this in the ZX81 has been used for actual code. The 512 bytes table needs to be somewhere in the ROM, in order to display the characters correct. Also the ZX81 needs some additional code during start up to initialize this properly, which has been placed in the upper 8K of the ROM. Doing this the changes to the Lambda rom can be at a minimum, which ensures compatibility with most programs that relies on the ROM content (calling known ROM functions for example).

# REFERENCES
Main source for a lot of inspiration to this work:

* Tynemouth work on getting Lambda rom to run on his [Minstrel 3](https://blog.tynemouthsoftware.co.uk/2019/12/a-minstrel-3-based-clone-of-the-lambda-8300-ZX81-clone.html), including his disassembly of the Lambda v1 rom.
* ZX81 ROM disassembly by [ZXSpectrumVault](https://github.com/ZXSpectrumVault/rom-disassemblies)
* Kio's website with also with [Lambda 8300](https://k1.spdns.de/Vintage/Sinclair/80/Clones/Lambda%208300%2C%20Hong%20Kong/)
* No$Cash documentation, including [Lambda 8300](https://problemkaputt.de/zxdocs.htm)
