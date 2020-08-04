# Vmalloc leak
## kernel log
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

## Add log script
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
## log script
	cat vmalloc_info_log.sh
	#!/system/bin/sh


	DATE=$(date "+%Y%m%d%H%M%S")
	LOG_FILE="/sdcard/mtklog/garmin_vmalloc_info_${DATE}.log"
	COMMA=","
	touch ${LOG_FILE}
	chmod 644 ${LOG_FILE}
	while [ true ];
	do
	    date +%Y%m%d%T >> ${LOG_FILE}
	    echo "/proc/meminfo" >> ${LOG_FILE}
	    cat /proc/meminfo >> ${LOG_FILE}
	    echo "/proc/vmallocinfo" >> ${LOG_FILE}
	    cat /proc/vmallocinfo >> ${LOG_FILE}
	    sleep 60
	done
## linux service
	diff --git a/garmin89_tb_ali_kk/init.project.rc b/garmin89_tb_ali_kk/init.project.rc
	index 0a9f902..e5e6cf3 100755
	--- a/garmin89_tb_ali_kk/init.project.rc
	+++ b/garmin89_tb_ali_kk/init.project.rc
	@@ -384,3 +384,5 @@ service restore_mtkbt /system/bin/restore_mtkbt.sh

	 on property:sys.restore_mtkbt=1
	     start restore_mtkbt
	+
	+service vmalloc_info_log /system/bin/vmalloc_info_log.sh
	\ No newline at end of file
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYxNTIyOTU3MiwtMTI2OTQ1NjQzMSwtMT
A5MzQ4MjIxOSwtNTk0MTQwMjI2XX0=
-->