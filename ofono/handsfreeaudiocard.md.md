HandsfreeAudioManager

	<!DOCTYPE node PUBLIC "-//freedesktop//DTD D-BUS Object Introspection 1.0//EN"
	"http://www.freedesktop.org/standards/dbus/1.0/introspect.dtd">
	<node><interface name="org.freedesktop.DBus.Introspectable"><method name="Introspect"><arg name="xml" type="s" direction="out"/>
	</method></interface><interface name="org.ofono.Manager"><method name="GetModems"><arg name="modems" type="a(oa{sv})" direction="out"/>
	</method><signal name="ModemAdded"><arg name="path" type="o"/>
	<arg name="properties" type="a{sv}"/>
	</signal>
	<signal name="ModemRemoved"><arg name="path" type="o"/>
	</signal>
	</interface><interface name="org.ofono.HandsfreeAudioManager"><method name="GetCards"><arg name="cards" type="a{oa{sv}}" direction="out"/>
	</method><method name="Register"><arg name="path" type="o" direction="in"/>
	<arg name="codecs" type="ay" direction="in"/>
	</method><method name="Unregister"><arg name="path" type="o" direction="in"/>
	</method><signal name="CardAdded"><arg name="path" type="o"/>
	<arg name="properties" type="a{sv}"/>
	</signal>
	<signal name="CardRemoved"><arg name="path" type="o"/>
	</signal>
	</interface><node name="bluetooth"/><node name="card_1"/><node name="hfp"/></node>"

HandsfreeAudioCard 

	<!DOCTYPE node PUBLIC "-//freedesktop//DTD D-BUS Object Introspection 1.0//EN"
	"http://www.freedesktop.org/standards/dbus/1.0/introspect.dtd">
	<node><interface name="org.freedesktop.DBus.Introspectable"><method name="Introspect"><arg name="xml" type="s" direction="out"/>
	</method></interface><interface name="org.ofono.HandsfreeAudioCard"><method name="GetProperties"><arg name="properties" type="a{sv}" direction="out"/>
	</method><method name="Connect"></method><signal name="PropertyChanged"><arg name="name" type="s"/>
	<arg name="value" type="v"/>
	</signal>
	</interface></node>
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY4ODY4NzQzOSwxMzgyNTI1NjI1XX0=
-->