AC_INIT([menuconfig], [0.4.18-wmo-3], [andy.koszela@westermo.com])
AC_CONFIG_AUX_DIR(build-aux)
AM_INIT_AUTOMAKE([foreign subdir-objects])
AM_SILENT_RULES([yes])

AC_CONFIG_SRCDIR([src/mconf.c])
AC_CONFIG_FILES([Makefile src/Makefile tests/Makefile])

# Checks for programs.
AC_PROG_CC
AC_PROG_YACC
AC_PROG_LEX

AC_CHECK_FUNCS([strndup])

PKG_PROG_PKG_CONFIG
AC_MSG_CHECKING([whether NCURSES_CONFIG_PATH is set])
AC_ARG_VAR(NCURSES_CONFIG_PATH, [Path to ncurses*-config, if available])
AS_IF([test "X$NCURSES_CONFIG_PATH" = "X"], [
    AC_MSG_RESULT([no])
    AC_MSG_NOTICE([checking for ncurses using pkg-config instead])
    PKG_CHECK_MODULES([ncurses], [ncurses >= 1.00])
], [
    AC_MSG_RESULT([yes, $NCURSES_CONFIG_PATH])
    AC_MSG_CHECKING([whether $NCURSES_CONFIG_PATH is executable])
    AS_IF([test ! -x $NCURSES_CONFIG_PATH], [
        AC_MSG_RESULT([no])
        AC_MSG_ERROR([NCURSES_CONFIG_PATH is provided but not executable])
    ], [
        AC_MSG_RESULT([yes])
        ncurses_libs=$($NCURSES_CONFIG_PATH --libs)
        ncurses_cflags=$($NCURSES_CONFIG_PATH --cflags)
        AC_MSG_NOTICE([ncurses cflags: $ncurses_cflags])
        AC_MSG_NOTICE([ncurses libs:   $ncurses_libs])
        ncurses_CFLAGS=$ncurses_cflags
        ncurses_LIBS=$ncurses_libs
    ])
])

AC_OUTPUT
