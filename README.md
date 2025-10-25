# pico_input_usb_tester

For testing usb devices on pico and mapping the hid data to struct fields.

The report struct will help me to add support for more devices on my adapters.
Might help other adapters authors too!

The HTML page is ugly but it works. It requires a browser with web hid support. Any Chrome based one should work.

The graphical input tester uses xinput naming and layout (south button is A).

### If you want to help

Wire a usb-a female port to a pico.
- D+ GPIO 0
- D- GPIO 1

- Flash the firmware.
- Connect the pico to a PC.
- Open the HTML file and connect to pico.
- After that, you can connect a game controller to the pico.
- Press some buttons, it should appear on-screen.
- Check the second tab (the ugly green one) for data map.
- Take notes using the comment field. For button names, note the original name (ie: b,a,triangle) or position (ie: top, left). Also the xinput name for that button (a,b,x,y)
- Then click generate C Struct.

Grab this info and post on Discussions:

- Raw HID Descriptor
- Raw HID Data log
- Struct
- USB ID with driver info.

Title should follow the format [VID] [PID] [NAME] [OTHER].<br/>
Ie: `0x0079 0x181C Gulikit Elves 2 Pro Android Mode`

#### About the `Device type` field
- `DRIVER_HID_PARSER` means that there's no mapping for that device.
It's most important to try to get a correct mapping.
- `DRIVER_HID_GENERIC` means that there's already a mapping for that device. You can test to see if it's correct.

There are other drivers that are used for known devices. They should map correctly too.

#### Some screens of the info it shows

![HID descriptor](docs/hid_desc.png)
![HID data log](docs/hid_data.png)
![Data mapping](docs/data_map.png)
![Resulting struct map](docs/struct.png)