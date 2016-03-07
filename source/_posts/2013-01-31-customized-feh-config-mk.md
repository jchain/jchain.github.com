---
layout: post
title: 'Build Feh from source and install to Home directory'
date: 2013-01-31 15:39
comments: true
categories: 
- Linux 
---

[`Feh`][1] is a lightweight image viewer for Linux. Its source code doesn't ship the Autoconf script
and only Makefile. The customization is done by modifying the file `config.mk`. In my case I would
like to install it to my HOME directory. Plus, I have installed the dependency library `giblib` into
HOME directory before so I have to specify the search path for compiler and linker. Here is what
I got so far:

```makefile
PACKAGE ?= feh
VERSION ?= 2.8

# Prefix for all installed files
# PREFIX ?= /usr/local
PREFIX ?= ${HOME}

# Directories for manuals, executables, docs, data, etc.
main_dir = ${DESTDIR}${PREFIX}
man_dir = ${main_dir}/share/man
bin_dir = ${main_dir}/bin
doc_dir = ${main_dir}/share/doc/feh
image_dir = ${main_dir}/share/feh/images
font_dir = ${main_dir}/share/feh/fonts
example_dir = ${main_dir}/share/doc/feh/examples

# default CFLAGS
CFLAGS ?= -g -O2
CFLAGS += -Wall -Wextra -pedantic

curl ?= 1
debug ?= 0
help ?= 0
xinerama ?= 1
exif ?= 0

ifeq (${curl},1)
	CFLAGS += -DHAVE_LIBCURL
	LDLIBS += -lcurl
	MAN_CURL = enabled
else
	MAN_CURL = disabled
endif

ifeq (${debug},1)
	CFLAGS += -DDEBUG -O0
	MAN_DEBUG = . This is a debug build.
else
	MAN_DEBUG =
endif

ifeq (${help},1)
	CFLAGS += -DINCLUDE_HELP
endif

ifeq (${stat64},1)
	CFLAGS += -D_FILE_OFFSET_BITS=64
endif

ifeq (${xinerama},1)
	CFLAGS += -DHAVE_LIBXINERAMA
	LDLIBS += -lXinerama
	MAN_XINERAMA = enabled
else
	MAN_XINERAMA = disabled
endif

ifeq (${exif},1)
	CFLAGS += -DHAVE_LIBEXIF
	LDLIBS += -lexif
	MAN_EXIF = enabled
else
	MAN_EXIF = disabled
endif


# Uncomment this to use dmalloc
#CFLAGS += -DWITH_DMALLOC

# CFLAGS += -DPREFIX=\"${PREFIX}\" \
	-DPACKAGE=\"${PACKAGE}\" -DVERSION=\"${VERSION}\"
CFLAGS += -DPREFIX=\"${PREFIX}\" \
	-DPACKAGE=\"${PACKAGE}\" -DVERSION=\"${VERSION}\" -I${PREFIX}/include

# LDLIBS += -lm -lpng -lX11 -lImlib2 -lgiblib
LDLIBS += -lm -lpng -lX11 -lImlib2 -lgiblib -L${PREFIX}/lib64/
```

[1]: http://feh.finalrewind.org/
