CC = gcc
AR = ar -ru
RM = rm -f

CFLAGS = -DHAVE_MEMMOVE=1 -DNDEBUG -O3 -I"libxls/include" -I"expat/lib"

INI_OBJS = \
	array.o \
	bsstr.o \
	minIni.o \
	ED_INIFile.o

JSON_OBJS = \
	array.o \
	bsstr.o \
	bsjson.o \
	ED_JSONFile.o

XLS_OBJS = \
	libxls/src/endian.o \
	libxls/src/ole.o \
	libxls/src/xls.o \
	libxls/src/xlstool.o \
	ED_XLSFile.o

XML_OBJS = \
	array.o \
	bsstr.o \
	bsxml.o \
	ED_XMLFile.o

EXPAT_OBJS = \
	expat/lib/xmlparse.o \
	expat/lib/xmlrole.o \
	expat/lib/xmltok.o \
	expat/lib/xmltok_impl.o \
	expat/lib/xmltok_ns.o

ALL_OBJS = $(INI_OBJS) $(JSON_OBJS) $(XLS_OBJS) $(XML_OBJS) $(EXPAT_OBJS)

all: libED_INIFile.a libED_JSONFile.a libED_XLSFile.a libED_XMLFile.a libexpat.a
	cp $^ ../Library/linux64

libED_INIFile.a: $(INI_OBJS)
	$(AR) $@ $(INI_OBJS)

libED_JSONFile.a: $(JSON_OBJS)
	$(AR) $@ $(JSON_OBJS)

libED_XLSFile.a: $(XLS_OBJS)
	$(AR) $@ $(XLS_OBJS)

libED_XMLFile.a: $(XML_OBJS)
	$(AR) $@ $(XML_OBJS)

libexpat.a: $(EXPAT_OBJS)
	$(AR) $@ $(EXPAT_OBJS)

%.o: %.c
	$(CC) -c -o $@ $< $(CFLAGS)

clean:
	$(RM) $(ALL_OBJS)
	$(RM) *.a
	$(RM) ../Library/linux64/linux64.tar.xz
