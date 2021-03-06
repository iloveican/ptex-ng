#
# Copyright (c) 2014, 2015, 2016, 2017, 2018, 2019 Clerk Ma
#
# You may freely use, modify and/or distribute this file.
#

CC = gcc
CFLAGS = -c -O2
INCLUDES = \
	-I ../texlive/texk/ptexenc/ \
	-I ../texlive/texk/ \
	-I ../texlive/libs/zlib/include \
	-I ../texlive/libs/freetype2/freetype2 \
	-I ../texlive/libs/cairo/cairo \
	-I ../texlive/libs/cairo/cairo-src/src \
	-I ../texlive/texk/web2c/libmd5 \
	-I libotf/src \
	-I mruby/include
LDFLAGS = libdpx.a libcairo-pdf.a libcairo.a libpixman.a libpng.a libpaper.a libz.a libptexenc.a libkpathsea.a libotf.a libfreetype.a libmd5.a libmruby.a -lm

objects = \
	aptex.o \
	aptex-cairo-visual-debug.o \
	aptex-opentype.o \
	aptex-unicode.o \
	aptex-utils.o \
	aptex-mruby.o \
	aptex-src.o

headers = aptex.h aptex-functions.h aptex-macros.h aptex-cairo-visual-debug.h aptex-opentype.h

lsotfea_objects = \
	lsotfea.o \
	lsotfea-stag.o \
	lsotfea-ltag.o \
	lsotfea-ftag.o

all: aptex lsotfea

aptex: $(objects)
	$(CC) -s -o aptex $(objects) $(LDFLAGS)
	cp aptex ptex-ng

lsotfea: lsotfea-src/lsotfea.c lsotfea-src/lsotfea-stag.c lsotfea-src/lsotfea-ltag.c lsotfea-src/lsotfea-ftag.c
	$(CC) -s -O2 -o lsotfea $(INCLUDES) lsotfea-src/lsotfea.c lsotfea-src/lsotfea-stag.c lsotfea-src/lsotfea-ltag.c lsotfea-src/lsotfea-ftag.c libotf.a libfreetype.a

aptex.o: aptex.c $(headers)
	$(CC) $(CFLAGS) $(INCLUDES) aptex.c

aptex-cairo-visual-debug.o: aptex-cairo-visual-debug.c $(headers)
	$(CC) $(CFLAGS) $(INCLUDES) aptex-cairo-visual-debug.c

aptex-opentype.o: aptex-opentype.c $(headers)
	$(CC) $(CFLAGS) $(INCLUDES) aptex-opentype.c

aptex-unicode.o: aptex-unicode.c $(headers)
	$(CC) $(CFLAGS) $(INCLUDES) aptex-unicode.c

aptex-utils.o: aptex-utils.c $(headers)
	$(CC) $(CFLAGS) $(INCLUDES) aptex-utils.c

aptex-mruby.o: aptex-mruby.c $(headers)
	$(CC) $(CFLAGS) $(INCLUDES) aptex-mruby.c

aptex-src.o: aptex-src.c $(headers)
	$(CC) $(CFLAGS) $(INCLUDES) aptex-src.c

.PHONY: clean

clean:
	rm aptex ptex-ng lsotfea *.o
