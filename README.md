# MCP-CAN-Boot Flash-App

![MCP-CAN-Boot logo](https://raw.githubusercontent.com/crycode-de/mcp-can-boot/main/doc/mcp-can-boot-256.png)

[![NPM version](https://img.shields.io/npm/v/mcp-can-boot-flash-app.svg)](https://www.npmjs.com/package/mcp-can-boot-flash-app)
[![Downloads](https://img.shields.io/npm/dm/mcp-can-boot-flash-app.svg)](https://www.npmjs.com/package/mcp-can-boot-flash-app)
[![Dependency Status](https://img.shields.io/david/crycode-de/mcp-can-boot-flash-app.svg)](https://david-dm.org/crycode-de/mcp-can-boot-flash-app)

[![NPM](https://nodei.co/npm/mcp-can-boot-flash-app.png?downloads=true)](https://nodei.co/npm/mcp-can-boot-flash-app/)

Flash application for **[MCP-CAN-Boot](https://github.com/crycode-de/mcp-can-boot)**, a CAN bus bootloader for **AVR microcontrollers** attached to an **MCP2515** CAN controller.

## The bootloader

More information about the bootloader are available in the official repository: [https://github.com/crycode-de/mcp-can-boot](https://github.com/crycode-de/mcp-can-boot)

## Requirements

* Node.js version 12.x or higher.

* The system where the flash-app is run needs a CAN interface to which the target MCU is connected.

  This may be a Raspberry Pi with an attached MCP2515 CAN controller, for example.

## Usage

No need to install: Just run the flash-app using `npx` (this will take a moment):

```
npx mcp-can-boot-flash-app [...]
```

Or install it globally and run it if you need it more often (recommended):

```
npm install -g mcp-can-boot-flash-app
mcp-can-boot-flash-app [...]
```

## Flash-App parameters

```
--file, -f       Hex file to flash                         [string] [required]
--iface, -i      CAN interface to use               [string] [default: "can0"]
--partno, -p     Specific AVR device like in avrdude       [string] [required]
--mcuid, -m      ID of the MCU bootloader                  [string] [required]
-e               Erase whole flash before flashing new data          [boolean]
-V               Do not verify                                       [boolean]
-r               Read flash and save to given file (no flashing!), optional
                 with maximum address to read until                   [string]
-F               Force flashing, even if the bootloader version missmatched
                                                                     [boolean]
--reset, -R      CAN message to send on startup to reset the MCU
                 (<can_id>#{hex_data})                                [string]
--can-id-mcu     CAN-ID for messages from MCU to remote
                                                [string] [default: 0x1FFFFF01]
--can-id-remote  CAN-ID for messages from remote to MCU
                                                [string] [default: 0x1FFFFF02]
--sff            Use Standad Frame Format (SFF) instead of the default
                 Extended Frame Format (EFF) for the CAN-IDs         [boolean]
--help, -h       Show help                                           [boolean]
```

Examples:

```
npx mcp-can-boot-flash-app -f firmware.hex -p m1284p -m 0x0042
npx mcp-can-boot-flash-app -f firmware.hex -p m1284p -m 0x0042 --reset 020040FF#4201FA
npx mcp-can-boot-flash-app -r -f - -p m328p -m 0x0042
```

## License

**CC BY-NC-SA 4.0**

[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-nc-sa/4.0/)

Copyright (C) 2020-2021 Peter Müller <peter@crycode.de> [https://crycode.de](https://crycode.de)
