02-10 14:21:56.084  2950  2950 I PbapService: ACTION_STATE_CHANGE state 1          
02-10 14:21:56.095  2950  2950 W PbapProvider: db create     
02-10 14:21:56.235  2950  2950 D CallbackToFuture: <- org.bluez.obex.Client1.RemoveSession:(o)() [/or
g/bluez/obex]                                                                                        
02-10 14:21:56.343  2950  4220 D CallbackToFuture: -> org.bluez.obex.Client1.RemoveSession() [/org/bl
uez/obex]                                                                                            
02-10 14:21:56.348  2950  5746 E AndroidRuntime: FATAL EXCEPTION: pool-4-thread-1
02-10 14:21:56.348  2950  5746 E AndroidRuntime: Process: com.garmin.android.pbapservice, PID: 2950  
02-10 14:21:56.348  2950  5746 E AndroidRuntime: java.util.ConcurrentModificationException
02-10 14:21:56.348  2950  5746 E AndroidRuntime:        at java.util.ArrayList$ArrayListIterator.next
(ArrayList.java:573)                                                                                 
02-10 14:21:56.348  2950  5746 E AndroidRuntime:        at com.garmin.android.pbap.dbus.ObexManager.g
etInterfaceByPath(ObexManager.java:155)                                                              
02-10 14:21:56.348  2950  5746 E AndroidRuntime:        at com.garmin.android.pbap.dbus.ObexManager.g
etInterface(ObexManager.java:164)                                                                    
02-10 14:21:56.348  2950  5746 E AndroidRuntime:        at com.garmin.android.pbap.dbus.ObexManager.i
nvokeMethod(ObexManager.java:200)                                                                    
02-10 14:21:56.348  2950  5746 E AndroidRuntime:        at com.garmin.android.pbap.dbus.ObexManager.-
wrap0(ObexManager.java)                                                                              
02-10 14:21:56.348  2950  5746 E AndroidRuntime:        at com.garmin.android.pbap.dbus.ObexManager$1
.run(ObexManager.java:234)                                                                           
02-10 14:21:56.348  2950  5746 E AndroidRuntime:        at java.util.concurrent.ThreadPoolExecutor.ru
nWorker(ThreadPoolExecutor.java:1113)                                                                
02-10 14:21:56.348  2950  5746 E AndroidRuntime:        at java.util.concurrent.ThreadPoolExecutor$Wo
rker.run(ThreadPoolExecutor.java:588)                                                                
02-10 14:21:56.348  2950  5746 E AndroidRuntime:        at java.lang.Thread.run(Thread.java:818)
02-10 14:21:56.350  2950  2950 W PbapControlDbus: connnectPbap failed, VIS is not connected.         
02-10 14:21:56.351  2950  2950 I PbapService: ACTION_STATE_CHANGE state 2
02-10 14:21:56.352  2950  2950 I PbapService: ACTION_STATE_CHANGE state 4                            
02-10 14:21:56.353  2950  5754 I PbapService: Starting download phone book

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYyMzc0OTUxOCwtNTA5NTIyODcxXX0=
-->