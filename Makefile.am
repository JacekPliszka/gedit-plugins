SUBDIRS = help po

ACLOCAL_AMFLAGS = -I m4 ${ACLOCAL_FLAGS}

EXTRA_DIST =			\
	autogen.sh		\
	ChangeLog-20090414	\
	gedit-plugins.doap	\
	intltool-extract.in 	\
	intltool-merge.in 	\
	intltool-update.in

CLEANFILES =
BUILT_SOURCES =

DISTCLEANFILES = 		\
	intltool-extract 	\
	intltool-merge 		\
	intltool-update

MAINTAINERCLEANFILES = 		\
	$(GITIGNORE_MAINTAINERCLEANFILES_TOPLEVEL) \
	$(GITIGNORE_MAINTAINERCLEANFILES_MAKEFILE_IN) \
	$(GITIGNORE_MAINTAINERCLEANFILES_M4_LIBTOOL) \
	ABOUT-NLS		\
	INSTALL			\
	config.rpath		\
	gtk-doc.make		\
	py-compile		\
	test-driver		\
	m4/gnome-doc-utils.m4	\
	m4/gtk-doc.m4		\
	m4/intltool.m4		\
	m4/codeset.m4		\
	m4/fcntl-o.m4		\
	m4/gettext.m4		\
	m4/glibc2.m4		\
	m4/glibc21.m4		\
	m4/iconv.m4		\
	m4/intdiv0.m4		\
	m4/intl.m4		\
	m4/intldir.m4		\
	m4/intlmacosx.m4	\
	m4/intmax.m4		\
	m4/inttypes-pri.m4	\
	m4/inttypes_h.m4	\
	m4/lcmessage.m4		\
	m4/lib-ld.m4		\
	m4/lib-link.m4		\
	m4/lib-prefix.m4	\
	m4/lock.m4		\
	m4/longlong.m4		\
	m4/nls.m4		\
	m4/po.m4		\
	m4/printf-posix.m4	\
	m4/progtest.m4		\
	m4/size_max.m4		\
	m4/stdint_h.m4		\
	m4/threadlib.m4		\
	m4/uintmax_t.m4		\
	m4/visibility.m4	\
	m4/wchar_t.m4		\
	m4/wint_t.m4		\
	m4/xsize.m4		\
	po/Makevars.template	\
	po/Rules-quot		\
	po/*.sed		\
	po/*.header		\
	po/*.sin

DISTCHECK_CONFIGURE_FLAGS = --enable-verify-all
GITIGNOREFILES =				\
	plugins/bookmarks/.deps			\
	plugins/bookmarks/messages/.deps	\
	plugins/drawspaces/.deps		\
	plugins/wordcompletion/.deps

include plugins/Makefile.am

CHANGELOG_START = GEDIT_PLUGINS_2_26_1

dist-hook:
	@if test -d "$(srcdir)/.git"; \
	then \
		echo Creating ChangeLog && \
		(GIT_DIR=$(top_srcdir)/.git \
		  ./missing --run git log $(CHANGELOG_START)^^.. --stat -M -C --name-status  --date=short --no-color) | \
		  fmt --split-only > ChangeLog.tmp \
		&& mv -f ChangeLog.tmp $(top_distdir)/ChangeLog \
		|| ( rm -f ChangeLog.tmp ; \
		  echo Failed to generate ChangeLog >&2 ); \
	else \
		echo A git clone is required to generate a ChangeLog >&2; \
	fi

-include $(top_srcdir)/git.mk
