include ../../ThirdParty/PSCommon/BuildSystem/CommonDefs.mak

BIN_DIR = ../../Bin

INC_DIRS = \
	../../Include \
	../../ThirdParty/PSCommon/XnLib/Include \
	../Drivers/OniFile/Formats

SRC_FILES = \
	*.cpp \
	../Drivers/OniFile/Formats/XnCodec.cpp \
	../Drivers/OniFile/Formats/XnStreamCompression.cpp

ifeq ("$(OSTYPE)","Darwin")
	INC_DIRS += /opt/local/include
	LIB_DIRS += /opt/local/lib
	LDFLAGS += -framework CoreFoundation -framework IOKit
endif

LIB_NAME = OpenNI2

LIB_DIRS = ../../ThirdParty/PSCommon/XnLib/Bin/$(PLATFORM)-$(CFG)
USED_LIBS = XnLib dl pthread jpeg
ifneq ("$(OSTYPE)","Darwin")
        USED_LIBS += rt  
endif

DEFINES += OPENNI2_EXPORT

CFLAGS += -Wall

ifeq ($(shell ld -ljpeg -o /dev/null 1>&2 2> /dev/null; echo $$?), 0)
  USED_LIBS += jpeg
else
  INC_DIRS  += ../../ThirdParty/LibJPEG
  SRC_FILES += ../../ThirdParty/LibJPEG/*.c
endif

include ../../ThirdParty/PSCommon/BuildSystem/CommonCppMakefile
