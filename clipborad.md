
02-12 14:41:14.517  9838  9838 E AndroidRuntime: FATAL EXCEPTION: main
02-12 14:41:14.517  9838  9838 E AndroidRuntime: Process: com.garmin.android.hfservice, PID: 9838
02-12 14:41:14.517  9838  9838 E AndroidRuntime: java.lang.ArrayIndexOutOfBoundsException: length=0;
 index=1
02-12 14:41:14.517  9838  9838 E AndroidRuntime:        at android.util.ArrayMap$1.colGetEntry(Array
Map.java:758)
02-12 14:41:14.517  9838  9838 E AndroidRuntime:        at android.util.MapCollections.toArrayHelper
(MapCollections.java:490)
02-12 14:41:14.517  9838  9838 E AndroidRuntime:        at android.util.MapCollections$ValuesCollect
ion.toArray(MapCollections.java:447)
02-12 14:41:14.517  9838  9838 E AndroidRuntime:        at java.util.ArrayList.<init>(ArrayList.java
:97)
02-12 14:41:14.517  9838  9838 E AndroidRuntime:        at com.garmin.android.handsfree.dbus.Manager
.getAllModems(Manager.java:101)
02-12 14:41:14.517  9838  9838 E AndroidRuntime:        at com.garmin.android.handsfree.dbus.OfonoMa
nager$1.handleMessage(OfonoManager.java:86)
02-12 14:41:14.517  9838  9838 E AndroidRuntime:        at android.os.Handler.dispatchMessage(Handle
r.java:102)
02-12 14:41:14.517  9838  9838 E AndroidRuntime:        at android.os.Looper.loop(Looper.java:148)
02-12 14:41:14.517  9838  9838 E AndroidRuntime:        at android.app.ActivityThread.main(ActivityT
hread.java:5417)
02-12 14:41:14.517  9838  9838 E AndroidRuntime:        at java.lang.reflect.Method.invoke(Native Me
thod)
02-12 14:41:14.517  9838  9838 E AndroidRuntime:        at com.android.internal.os.ZygoteInit$Method
AndArgsCaller.run(ZygoteInit.java:726)
02-12 14:41:14.517  9838  9838 E AndroidRuntime:        at com.android.internal.os.ZygoteInit.main(Z
ygoteInit.java:616)
02-12 14:41:22.464  9282  9501 I ActivityManager: Process com.garmin.android.hfservice (pid 9838) ha
s died

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI3MTEwMDc1OSwxNDM5NTY1NzAwLC02Nz
Y5MDgxNjUsLTYyMzc0OTUxOCwtNTA5NTIyODcxXX0=
-->