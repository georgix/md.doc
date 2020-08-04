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
## Add log s
	diff --git a/device.mk b/device.mk
	index 1a69373..7a993a7 100644
	--- a/device.mk
	+++ b/device.mk
	@@ -49,6 +49,10 @@ PRODUCT_COPY_FILES += \
	 PRODUCT_COPY_FILES += \
	        vendor/garmin/misc/scripts/restore_mtkbt.sh:/system/bin/restore_mtkbt.sh

	+# GPS on/off test script
	+PRODUCT_COPY_FILES += \
	+       vendor/garmin/misc/scripts/vmalloc_info_log.sh:/system/bin/vmalloc_info_log.sh
	+
	 #
	 # PRODUCT_PACKAGES
	 #
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA2MDgzOTcwMCwtNTk0MTQwMjI2XX0=
-->