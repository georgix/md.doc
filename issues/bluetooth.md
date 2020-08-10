HFP not recognized by Apple devices
----------------------------------

- project: piranha
- start: 15/07/2019
- end: 23/07/2019

## MFi
[Apple Navigation HFP](https://support.apple.com/en-us/HT204242)

Use bluetoothd to dump device details:

    [IP8]# info RV-BBTK
    Device RV-BBTK not available

    [IP8]# info EC:DB:09:0E:00:D3
    Device EC:DB:09:0E:00:D3
            Name: RV-BBTk
            Alias: RV-BBTk
            Class: 0x240404
            Icon: audio-card
            Paired: no
            Trusted: no
            Blocked: no
            Connected: no
            LegacyPairing: no
            UUID: Headset                   (00001108-0000-1000-8000-00805f9b34fb)
            UUID: Handsfree                 (0000111e-0000-1000-8000-00805f9b34fb)
            UUID: Audio Source              (0000110a-0000-1000-8000-00805f9b34fb)
            UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
            UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
            UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)

    [IP8]# list-attributes EC:DB:09:0E:00:D3
    [CHG] Device 88:19:08:7C:C0:4D Connected: no
    [bluetooth]# list-attributes
    Missing device address argument
    [CHG] Device 88:19:08:7C:C0:4D Connected: yes

    [IP8]# show
    Controller 58:7A:62:0D:51:27
            Name: FusionBT
            Alias: RV-IN1500Z
            Class: 0x040428
            Powered: yes
            Discoverable: no
            Pairable: no
            UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
            UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
            UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
            UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
            UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
            UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
            UUID: Vendor specific           (e8bca34d-fb9e-4192-ac97-78c088ae7c21)
            UUID: Vendor specific           (00000000-deca-fade-deca-deafdecacafe)
            Modalias: usb:v1D6Bp0246d052B
            Discovering: no

# Solution
- Mofify STEREO BT device class to Audio/Video (major) – Car Audio(minor) 
- Ignore virtual call in PND phone app, no incall UI showing
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTExNzc5NjQ1NF19
-->