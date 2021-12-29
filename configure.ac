# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([menuconfig], [0.4.18-wmo-1], [andy.koszela@westermo.com])
AC_CONFIG_SRCDIR([src/mconf.c])

AC_CANONICAL_HOST
AC_CANONICAL_BUILD

# Checks for programs.
AC_PROG_CC
AM_INIT_AUTOMAKE([subdir-objects])
AC_PROG_YACC
AC_PROG_LEX

# Checks for libraries.
CROSS_COMPILE=
if test "x$cross_compiling" = "xyes"; then
    case "${host}" in
    *-mingw*)
	AC_CHECK_LIB([gnurx], [regexec])
        ;;
    esac
fi

PKG_CHECK_MODULES([ncurses], [ncurses >= 1.00])

# Checks for library functions.
AC_CHECK_FUNCS([strndup])

AC_CONFIG_FILES([Makefile
                 src/Makefile
                 tests/Makefile])
AC_OUTPUT
