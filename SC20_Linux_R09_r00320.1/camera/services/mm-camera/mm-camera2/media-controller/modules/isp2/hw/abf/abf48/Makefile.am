#======================================================================
#makefile for    -lmmcamera_isp_abf48.so for mm-camera2
#======================================================================
EXTRA_CFLAGS =
AM_CFLAGS=
local_ldflags = $(mmcamera_debug_lflags)
AM_CFLAGS =  -DAMSS_VERSION=$(AMSS_VERSION) \
  $(mmcamera_debug_defines) \
  $(mmcamera_debug_cflags)
if !ENABLE_BOARD_QTI_CAMERA_V2
AM_CFLAGS  += -Werror
endif
mmcamerapath = $(srcdir)/../../../../../../
EXTRA_CFLAGS += -I$(srcdir)
EXTRA_CFLAGS += -I$(mmcamerapath)/includes/
EXTRA_CFLAGS += -I$(mmcamerapath)/server-tuning/tuning/
EXTRA_CFLAGS += -I$(mmcamerapath)/media-controller/includes/
EXTRA_CFLAGS += -I$(mmcamerapath)/media-controller/mct/bus/
EXTRA_CFLAGS += -I$(mmcamerapath)/media-controller/mct/controller/
EXTRA_CFLAGS += -I$(mmcamerapath)/media-controller/mct/event/
EXTRA_CFLAGS += -I$(mmcamerapath)/media-controller/mct/module/
EXTRA_CFLAGS += -I$(mmcamerapath)/media-controller/mct/object/
EXTRA_CFLAGS += -I$(mmcamerapath)/media-controller/mct/pipeline/
EXTRA_CFLAGS += -I$(mmcamerapath)/media-controller/mct/port/
EXTRA_CFLAGS += -I$(mmcamerapath)/media-controller/mct/stream/
EXTRA_CFLAGS += -I$(mmcamerapath)/media-controller/mct/tools/
EXTRA_CFLAGS += -I$(mmcamerapath)/media-controller/modules/includes/
EXTRA_CFLAGS += -I$(mmcamerapath)/media-controller/modules/isp2/common/
EXTRA_CFLAGS += -I$(mmcamerapath)/media-controller/modules/isp2/hw/sub_module
EXTRA_CFLAGS += -I$(CAMERAHAL_PATH)/QCamera2/stack/common
EXTRA_CFLAGS += -I$(mmcamerapath)/media-controller/modules/isp2/module/isp48

local_src_files        = module_abf48.c abf48.c
if ENABLE_OEM_CHROMATIX
EXTRA_CFLAGS += -I$(LOCAL_EXTEN_ISP_INCLUDES)
local_src_files  += (shell find $(LOCAL_EXTEN_ISP_INCLUDES) -name 'abf48_ext.c')
AM_CFLAGS += -DOVERRIDE_FUNC=1
endif
local_libadd =    -lcutils \
   # -lmmcamera2_mct \
   # -lmmcamera_isp_sub_module \
   # -lmmcamera2_isp_modules \
    -lmmcamera_dbg
if ENABLE_MM_DEBUG
local_libadd +=    -llog
endif

final_sources=
final_libadd=
if ENABLE_msmcobalt
final_sources+=$(local_src_files)
final_libadd+=$(local_libadd)
endif
if ENABLE_sdm660
final_sources+=$(local_src_files)
final_libadd+=$(local_libadd)
endif
if ENABLE_msm8998
final_sources+=$(local_src_files)
final_libadd+=$(local_libadd)
endif
libsdir = $(prefix)/lib
libs_LTLIBRARIES  =libmmcamera_isp_abf48.la
libmmcamera_isp_abf48_la_SOURCES = $(final_sources)
libmmcamera_isp_abf48_la_LIBADD = $(final_libadd)
libmmcamera_isp_abf48_la_LDFLAGS = -shared
libmmcamera_isp_abf48_la_CFLAGS = ${AM_CFLAGS} ${EXTRA_CFLAGS}
