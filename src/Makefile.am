# vim:set et ts=4:
#
# ibus-t9 - The t9 engine for IBus
#
# Copyright (c) 2007-2008 Yu Yuwei <acevery@gmail.com>
# Copyright (c) 2010-2010 microcai  <microcai@fedoraproject.org>
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2, or (at your option)
# any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.

BUILT_SOURCES = icons/ibus_t9.icons.h

icons/ibus_t9.icons.h:
	cd ../icons && $(MAKE) 

libexecdir = ${prefix}/share/ibus/engine

INCLUDES =  @IBUS_CFLAGS@ -DPKGDATADIR=\"$(pkgdatadir)\" -DPREFIX=\"$(prefix)\"

LIBS = @IBUS_LIBS@

libexec_PROGRAMS = ibus-engine-t9

ibus_engine_t9_SOURCES =  main.c 	engine.c 	engine.h decoder.c

component_DATA = ibus-t9.xml 

componentdir = @datadir@/ibus/component

EXTRA_DIST = ibus-t9.xml.in

CLEANFILES = \
	ibus-t9.xml \
	$(NULL)

ibus-t9.xml : ibus-t9.xml.in
	( \
		libexecdir=${libexecdir}; \
		pkgdatadir=${pkgdatadir}; \
		s=`cat $<`; \
		eval "echo \"$${s}\""; \
	) > $@

test: ibus-engine-t9
	./$<  --icon $(top_srcdir)/icons/ --table $(top_srcdir)/tables/table.txt
