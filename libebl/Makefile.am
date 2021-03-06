## Process this file with automake to create Makefile.in
## Configure input file for elfutils.
##
## Copyright (C) 2000, 2001, 2002, 2003, 2004 Red Hat, Inc.
##
## This program is Open Source software; you can redistribute it and/or
## modify it under the terms of the Open Software License version 1.0 as
## published by the Open Source Initiative.
##
## You should have received a copy of the Open Software License along
## with this program; if not, you may obtain a copy of the Open Software
## License version 1.0 from http://www.opensource.org/licenses/osl.php or
## by writing the Open Source Initiative c/o Lawrence Rosen, Esq.,
## 3001 King Ranch Road, Ukiah, CA 95482.
##
DEFS = -D_GNU_SOURCE -DHAVE_CONFIG_H -DOBJDIR=\"$(shell pwd)\"
if MUDFLAP
AM_CFLAGS = -Wall -Wshadow -fpic
else
AM_CFLAGS = -Wall -Werror -Wshadow -fpic
endif
AM_CFLAGS += -DLIBSTR=\"$$(basename $(libdir))\"

INCLUDES = -I$(srcdir) -I$(top_srcdir)/libelf -I$(top_srcdir)/lib -I..
VERSION = 1
PACKAGE_VERSION = @PACKAGE_VERSION@

lib_LIBRARIES = libebl.a
modules = i386 sh mips x86_64 ia64 alpha arm sparc ppc ppc64
noinst_LIBRARIES = libebl_i386_pic.a libebl_sh_pic.a libebl_mips_pic.a \
		   libebl_x86_64_pic.a libebl_ia64_pic.a libebl_alpha_pic.a \
		   libebl_arm_pic.a libebl_sparc_pic.a libebl_ppc_pic.a \
		   libebl_ppc64_pic.a
noinst_PROGRAMS = $(noinst_LIBRARIES:_pic.a=.so)

euincludedir = $(includedir)/elfutils
euinclude_HEADERS = libebl.h

gen_SOURCES = eblopenbackend.c eblclosebackend.c eblstrtab.c \
	      eblreloctypename.c eblsegmenttypename.c \
	      eblsectiontypename.c eblmachineflagname.c \
	      eblsymboltypename.c ebldynamictagname.c eblsectionname.c \
	      eblobjecttypename.c eblsymbolbindingname.c \
	      eblbackendname.c eblshflagscombine.c eblwstrtab.c \
	      eblgstrtab.c eblosabiname.c eblmachineflagcheck.c \
	      eblreloctypecheck.c eblrelocvaliduse.c ebldynamictagcheck.c \
	      eblcorenotetypename.c eblobjnotetypename.c \
	      eblcorenote.c eblobjnote.c ebldebugscnp.c \
	      eblgotpcreloccheck.c

libebl_a_SOURCES = $(gen_SOURCES)

#
# XXX Use --enable-new-dtags as soon as ld.so handles DT_RUNPATH when
# using dlopen correctly.
#	      -Wl,--rpath,\$$ORIGIN/elfutils \
#
i386_SRCS = i386_init.c i386_destr.c i386_symbol.c i386_corenote.c
libebl_i386_pic_a_SOURCES =
am_libebl_i386_pic_a_OBJECTS = $(i386_SRCS:.c=.os)

if MUDFLAP
libelf = ../libelf/libelf.a
libmudflap = -lmudflap
else
libelf = ../libelf/libelf.so
libmudflap =
endif

libebl_i386_so_SOURCES =
libebl_i386.so: libebl_i386_pic.a libebl_i386.map
	$(CC) -shared -o $@ -Wl,--whole-archive,$<,--no-whole-archive \
	      -Wl,--version-script,$(srcdir)/libebl_i386.map \
	      -Wl,-z,defs $(libelf) $(libmudflap)


sh_SRCS = sh_init.c sh_destr.c sh_symbol.c
libebl_sh_pic_a_SOURCES =
am_libebl_sh_pic_a_OBJECTS = $(sh_SRCS:.c=.os)

libebl_sh_so_SOURCES =
libebl_sh.so: libebl_sh_pic.a libebl_sh.map
	$(CC) -shared -o $@ -Wl,--whole-archive,$<,--no-whole-archive \
	      -Wl,--version-script,$(srcdir)/libebl_sh.map \
	      -Wl,-z,defs $(libmudflap)


mips_SRCS = mips_init.c mips_destr.c mips_symbol.c
libebl_mips_pic_a_SOURCES =
am_libebl_mips_pic_a_OBJECTS = $(mips_SRCS:.c=.os)

libebl_mips_so_SOURCES =
libebl_mips.so: libebl_mips_pic.a libebl_mips.map
	$(CC) -shared -o $@ -Wl,--whole-archive,$<,--no-whole-archive \
	      -Wl,--version-script,$(srcdir)/libebl_mips.map \
	      -Wl,-z,defs $(libmudflap)


x86_64_SRCS = x86_64_init.c x86_64_destr.c x86_64_symbol.c
libebl_x86_64_pic_a_SOURCES =
am_libebl_x86_64_pic_a_OBJECTS = $(x86_64_SRCS:.c=.os)

libebl_x86_64_so_SOURCES =
libebl_x86_64.so: libebl_x86_64_pic.a libebl_x86_64.map
	$(CC) -shared -o $@ -Wl,--whole-archive,$<,--no-whole-archive \
	      -Wl,--version-script,$(srcdir)/libebl_x86_64.map \
	      -Wl,-z,defs $(libelf) $(libmudflap)


ia64_SRCS = ia64_init.c ia64_destr.c ia64_symbol.c
libebl_ia64_pic_a_SOURCES =
am_libebl_ia64_pic_a_OBJECTS = $(ia64_SRCS:.c=.os)

libebl_ia64_so_SOURCES =
libebl_ia64.so: libebl_ia64_pic.a libebl_ia64.map
	$(CC) -shared -o $@ -Wl,--whole-archive,$<,--no-whole-archive \
	      -Wl,--version-script,$(srcdir)/libebl_ia64.map \
	      -Wl,-z,defs $(libmudflap)


alpha_SRCS = alpha_init.c alpha_destr.c alpha_symbol.c
libebl_alpha_pic_a_SOURCES =
am_libebl_alpha_pic_a_OBJECTS = $(alpha_SRCS:.c=.os)

libebl_alpha_so_SOURCES =
libebl_alpha.so: libebl_alpha_pic.a libebl_alpha.map
	$(CC) -shared -o $@ -Wl,--whole-archive,$<,--no-whole-archive \
	      -Wl,--version-script,$(srcdir)/libebl_alpha.map \
	      -Wl,-z,defs $(libmudflap)


arm_SRCS = arm_init.c arm_destr.c arm_symbol.c
libebl_arm_pic_a_SOURCES =
am_libebl_arm_pic_a_OBJECTS = $(arm_SRCS:.c=.os)

libebl_arm_so_SOURCES =
libebl_arm.so: libebl_arm_pic.a libebl_arm.map
	$(CC) -shared -o $@ -Wl,--whole-archive,$<,--no-whole-archive \
	      -Wl,--version-script,$(srcdir)/libebl_arm.map \
	      -Wl,-z,defs $(libmudflap)


sparc_SRCS = sparc_init.c sparc_destr.c sparc_symbol.c
libebl_sparc_pic_a_SOURCES =
am_libebl_sparc_pic_a_OBJECTS = $(sparc_SRCS:.c=.os)

libebl_sparc_so_SOURCES =
libebl_sparc.so: libebl_sparc_pic.a libebl_sparc.map
	$(CC) -shared -o $@ -Wl,--whole-archive,$<,--no-whole-archive \
	      -Wl,--version-script,$(srcdir)/libebl_sparc.map \
	      -Wl,-z,defs $(libmudflap)


ppc_SRCS = ppc_init.c ppc_destr.c ppc_symbol.c
libebl_ppc_pic_a_SOURCES =
am_libebl_ppc_pic_a_OBJECTS = $(ppc_SRCS:.c=.os)

libebl_ppc_so_SOURCES =
libebl_ppc.so: libebl_ppc_pic.a libebl_ppc.map
	$(CC) -shared -o $@ -Wl,--whole-archive,$<,--no-whole-archive \
	      -Wl,--version-script,$(srcdir)/libebl_ppc.map \
	      -Wl,-z,defs $(libelf) $(libmudflap)


ppc64_SRCS = ppc64_init.c ppc64_destr.c ppc64_symbol.c
libebl_ppc64_pic_a_SOURCES =
am_libebl_ppc64_pic_a_OBJECTS = $(ppc64_SRCS:.c=.os)

libebl_ppc64_so_SOURCES =
libebl_ppc64.so: libebl_ppc64_pic.a libebl_ppc64.map
	$(CC) -shared -o $@ -Wl,--whole-archive,$<,--no-whole-archive \
	      -Wl,--version-script,$(srcdir)/libebl_ppc64.map \
	      -Wl,-z,defs $(libelf) $(libmudflap)


%.os: %.c %.o
	if $(COMPILE) -c -o $@ -fpic -DPIC -DSHARED -MT $@ -MD -MP \
	  -MF "$(DEPDIR)/$*.Tpo" `test -f '$<' || echo '$(srcdir)/'`$<; \
	then cat "$(DEPDIR)/$*.Tpo" >> "$(DEPDIR)/$*.Po"; \
	     rm -f "$(DEPDIR)/$*.Tpo"; \
	else rm -f "$(DEPDIR)/$*.Tpo"; exit 1; \
	fi

install: install-am
	$(mkinstalldirs) $(DESTDIR)$(libdir)/elfutils
	for m in $(modules); do \
	  $(INSTALL_PROGRAM) libebl_$${m}.so $(DESTDIR)$(libdir)/elfutils/libebl_$${m}-$(PACKAGE_VERSION).so; \
	  ln -fs libebl_$${m}-$(PACKAGE_VERSION).so $(DESTDIR)$(libdir)/elfutils/libebl_$${m}.so; \
	done

uninstall: uninstall-am
	for m in $(modules); do \
	  rm -f $(DESTDIR)$(libdir)/elfutils/libebl_$${m}-$(PACKAGE_VERSION).so; \
	  rm -f $(DESTDIR)$(libdir)/elfutils/libebl_$${m}.so; \
	done
	rmdir --ignore-fail-on-non-empty $(DESTDIR)$(libdir)/elfutils
	rmdir --ignore-fail-on-non-empty $(DESTDIR)$(includedir)/elfutils

noinst_HEADERS = libeblP.h $(noinst_LIBRARIES:%_pic.a=%.h)
EXTRA_DIST = $(noinst_LIBRARIES:%_pic.a=%.map) \
	     $(foreach m,$(modules),$($(m)_SRCS))

CLEANFILES = $(am_libebl_pic_a_OBJECTS) \
	     $(foreach m,$(modules),$(am_libebl_$(m)_pic_a_OBJECTS))
