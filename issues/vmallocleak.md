# Vmalloc leak

diff --git a/drivers/combo/drv_wlan/mt6628/wlan/mgmt/cnm_mem.c b/drivers/combo/drv_wlan/mt6628/wlan/mgmt/cnm_mem.c
index 4836633..d71c22c 100644
--- a/drivers/combo/drv_wlan/mt6628/wlan/mgmt/cnm_mem.c
+++ b/drivers/combo/drv_wlan/mt6628/wlan/mgmt/cnm_mem.c
@@ -363,6 +363,7 @@
 ********************************************************************************
 */
 #include "precomp.h"
+#include "debug.h"

 /*******************************************************************************
 *                              C O N S T A N T S
@@ -639,6 +640,8 @@ cnmMemAlloc (

 #ifdef LINUX
     pvMemory = (PVOID)kalMemAlloc(u4Length, VIR_MEM_TYPE);
+    printk(KERN_WARNING "cnmMemAlloc %p", pvMemory);
+    dump_stack();
 #else
     pvMemory = (PVOID)NULL;
 #endif

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMzNzY1Mzg2NF19
-->