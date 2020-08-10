

###
dbus-monitor  --system

### dbus-send

    dbus-send --system --dest=org.freedesktop.DBus --type=method_call --print-reply /org/freedesktop/DBus org.freedesktop.DBus.ListNames
    dbus-send --system --dest=org.freedesktop.DBus --type=method_call --print-reply /org/freedesktop/DBus org.freedesktop.DBus.Introspectable.Introspect
    dbus-send --system --dest=org.bluez --type=method_call --print-reply /org/bluez org.freedesktop.DBus.Introspectable.Introspect
    dbus-send --system --dest=org.ofono --type=method_call --print-reply / org.freedesktop.DBus.Introspectable.Introspect
    dbus-send --system --dest=org.ofono --type=method_call --print-reply /hfp/org/bluez/hci0/dev_88_19_08_7C_C0_4D org.freedesktop.DBus.Introspectable.Introspect

    dbus-send --system --dest=org.ofono --type=method_call --print-reply /hfp/org/bluez/hci0/dev_88_19_08_7C_C0_4D org.ofono.VoiceCallManager.Dial string:'777' string:'default'

    dbus-send --system --dest=org.ofono --type=method_call --print-reply /hfp/org/bluez/hci0/dev_88_19_08_7C_C0_4D org.ofono.CallVolume.SetProperty string:'SpeakerVolume' variant:byte:40

    dbus-send --session --dest=org.bluez.obex --type=method_call --print-reply /org/bluez/obex org.bluez.obex.Client1.CreateSession string:'A8:81:95:8C:31:85' dict:string:string:'Target','pbap'

    dbus-send --session --dest=org.bluez.obex --type=method_call --print-reply /org/bluez/obex org.bluez.obex.Client1.CreateSession string:'88:19:08:7C:C0:4D' dict:string:string:'Target','pbap'

    dbus-send --system --dest=org.bluez --type=method_call --print-reply /org/bluez/hci0 org.freedesktop.DBus.Properties.Get string:org.bluez.Adapter1 string:Discoverable
    method return time=1579271588.837539 sender=:1.18 -> destination=:1.187 serial=1032 reply_serial=2
    variant       boolean false

    dbus-send --system --dest=org.bluez --type=method_call --print-reply /org/bluez/hci0 org.freedesktop.DBus.Properties.Set string:org.bluez.Adapter1 string:Discoverable variant:boolean:true
    Error org.bluez.Error.Failed: Busy

    dbus-send --system --dest=org.bluez --type=method_call --print-reply /org/bluez/hci0 org.freedesktop.DBus.Properties.Set string:org.bluez.Adapter1 string:Discoverable variant:boolean:true
   
### gdbus

    gdbus call -y -d org.freedesktop.DBus -o /org/freedesktop/DBus  -m org.freedesktop.DBus.ListNames
    gdbus introspect -y -d org.freedesktop.DBus -o /org/freedesktop/DBus
    gdbus call -y -d org.freedesktop.DBus -o /org/freedesktop/DBus  -m org.freedesktop.DBus.Introspectable.Introspect

    gdbus call -y -d org.ofono -o /hfp/org/bluez/hci1/dev_88_19_08_7C_C0_4D -m org.ofono.VoiceCallManager.Dial '777' 'default'

### D-feet

"A8:81:95:8C:31:85",{'Target':GLib.Variant('s','PBAP')}
"88:19:08:7C:C0:4D",{'Target':GLib.Variant('s','PBAP')}

"",{'Format':GLib.Variant('s','vcard30')}

(objectpath '/org/bluez/obex/client/session2/transfer3', {'Status': <'queued'>, 'Name': <'telecom/pb.vcf'>, 'Size': <uint64 0>, 'Filename': <'/tmp/obex-client3ESTB0'>, 'Session': <objectpath '/org/bluez/obex/client/session2'>})
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjc0MDcwMjQ1XX0=
-->