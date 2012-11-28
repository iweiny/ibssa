
INCLUDES = -I$(includedir)/infiniband

lib_LTLIBRARIES = src/libopensmssa.la

DBGFLAGS = -g

src_libopensmssa_la_CFLAGS = -Wall $(DBGFLAGS) -D_XOPEN_SOURCE=600 -D_BSD_SOURCE=1 -Wno-deprecated-declarations

if HAVE_LD_VERSION_SCRIPT
    libopensmssa_version_script = -Wl,--version-script=$(srcdir)/libopensmssa.map
else
    libopensmssa_version_script =
endif

src_libopensmssa_la_SOURCES = src/ibssa_osm_plugin.c
src_libopensmssa_la_LDFLAGS = -version-info $(libopensmssa_api_version) \
	-export-dynamic $(libopensmssa_version_script)
src_libopensmssa_la_LIBADD = -L$(libdir) -losmcomp
src_libopensmssa_la_DEPENDENCIES = $(srcdir)/libopensmssa.map

# headers are distributed as part of the include dir
EXTRA_DIST = $(srcdir)/libopensmssa.spec.in \
				 $(srcdir)/libopensmssa.map \
				 $(srcdir)/src/*.h \
				 $(srcdir)/config

dist-hook: libopensmssa.spec
	cp libopensmssa.spec $(distdir)
