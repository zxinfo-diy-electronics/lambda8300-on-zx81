# Running Lambda on a ZX81
This repository provides a customized Lambda v1 rom that can be used on a real ZX81. The overlay rom to be used with [OpenSpand](https://codeberg.org/NollKollTroll/OpenSpand) interface to turn your ZX81 into a Lambda 8300.

# WHAT is SUPPORTED
The customized ROMs together with latest OpenSpand firmware 0.51.4 or higher, and they provides together the following features:

## Plain ZX81 only
* Lambda 8300 rom v1 customized for ZX81 hardware (starts up with blinking cursor only), 

## With OpenSpand interface
* Overlay adding support for CAT and LOAD of programs from OpenSpand SD Card storage
* Lambda 8300 beeper support
* Lambda 8300 specific characters, as some of the standard ZX81 has been changed to more gaming oriented.
* Joystick support via OpenSpand

# HOW-TO - with standard ZX81
The CUSTOM.ROM provided is a 16KB ROM (compared to standard 8K ROM), so some modification is needed in order to use it. It has been tested with my own external-rom-interface, which will be improved to get better support. For many cases this setup does not provide the Lambda specific characters - mainly because of 1) On Lambda character bitmaps are provided by ULA 2) The way the ZX81 display system works. Using OpenSpand fixes this anyway.


# HOW-TO - with OpenSpand
In order to prepare your setup for running as a Lambda 8300 using OpenSpand

* Copy the zx81*.rom to your SD Card and rename to CUSTOM.COM
* Copy the zx81*.ovl to your SD Card and rename to CUSTOM.OVL
* Copy LCMDR.P to your SD Card. This is a cut-down Lambda version of ZXPand Commander. It is not recommended for now to rename this to MENU.P, as starting up as a ZX81 with this can lead to unknown disruptions of the setzup.
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
