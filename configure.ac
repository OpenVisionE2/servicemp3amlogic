AC_INIT([servicemp3], [0.1], [])
AM_INIT_AUTOMAKE([subdir-objects foreign dist-bzip2 no-define tar-pax])
AC_CONFIG_MACRO_DIR([m4])
LT_INIT

AC_PROG_CC
AC_PROG_CXX
AM_PATH_PYTHON
AX_PYTHON_DEVEL
AC_LANG(C++)

PKG_CHECK_MODULES(ENIGMA2, enigma2)
AC_ARG_WITH(gstversion,
	AS_HELP_STRING([--with-gstversion],[use gstreamer version (major.minor)]),
	[GST_MAJORMINOR=$withval],[GST_MAJORMINOR=1.0])

PKG_CHECK_MODULES(GSTREAMER, gstreamer-$GST_MAJORMINOR gstreamer-pbutils-$GST_MAJORMINOR)

AC_ARG_WITH(boxtype,
	[  --with-boxtype=NAME box type [[none,dm800...]]],
	[BOXTYPE="$withval"],[BOXTYPE="dm800"])
AC_SUBST(BOXTYPE)
AC_DEFINE_UNQUOTED(BOXTYPE,"$BOXTYPE",[box type])

AC_ARG_WITH(amlogic,
	AC_HELP_STRING([--with-amlogic], [use amlogic MPEG decoder]),
	[[with_amlogic=$withval]],
	[[with_amlogic=no]]
)
AM_CONDITIONAL(HAVE_AMLOGIC, test x"$with_amlogic" = xyes)
if test x"$with_amlogic" = xyes ; then
	AC_DEFINE(HAVE_AMLOGIC, 1,[Enables AMLOGIC decoder support])
fi

if test "$BOXTYPE" == "alien5"; then
	AC_DEFINE(HAVE_ALIEN5, 1,[enable Alien5 specific hacks])
fi

if test "$BOXTYPE" == "k1plus" -o "$BOXTYPE" == "k1pro" -o "$BOXTYPE" == "k2pro" -o "$BOXTYPE" == "k2prov2" -o "$BOXTYPE" == "k3pro" -o "$BOXTYPE" == "kvim2" -o "$BOXTYPE" == "c300" -o "$BOXTYPE" == "c300pro" -o "$BOXTYPE" == "c400plus" -o "$BOXTYPE" == "alien4"; then
	AC_DEFINE(HAVE_ALIEN5, 1,[enable Alien5 specific hacks])
	AC_DEFINE(HAVE_MECOOL, 1,[enable Mecool devices specific hacks])
fi

AC_DEFINE([DEBUG])

AC_CONFIG_FILES([
Makefile
servicemp3/Makefile
plugin/Makefile
])
AC_OUTPUT
