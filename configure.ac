dnl Process this file with autoconf to produce a configure script
AC_INIT([osmo-pcu],
	m4_esyscmd([./git-version-gen .tarball-version]),
	[osmocom-pcu@lists.osmocom.org])

AM_INIT_AUTOMAKE([dist-bzip2])

dnl kernel style compile messages
m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES([yes])])

dnl checks for programs
AC_PROG_MAKE_SET
AC_PROG_CC
AC_PROG_CXX
AC_PROG_INSTALL
LT_INIT

dnl checks for header files
AC_HEADER_STDC

dnl Checks for typedefs, structures and compiler characteristics

dnl checks for libraries
PKG_CHECK_MODULES(LIBOSMOCORE, libosmocore  >= 0.3.9)
PKG_CHECK_MODULES(LIBOSMOVTY, libosmovty)
PKG_CHECK_MODULES(LIBOSMOGSM, libosmogsm >= 0.3.3)
PKG_CHECK_MODULES(LIBOSMOGB, libosmogb >= 0.5.1.4)

AC_MSG_CHECKING([whether to enable sysmocom-bts hardware support])
AC_ARG_ENABLE(sysmocom-bts,
		AC_HELP_STRING([--enable-sysmocom-bts],
				[enable code for sysmocom femto-bts [default=no]]),
		[enable_sysmocom_bts="$enableval"],[enable_sysmocom_bts="no"])
AC_MSG_RESULT([$enable_sysmocom_bts])
AM_CONDITIONAL(ENABLE_SYSMOBTS, test "x$enable_sysmocom_bts" = "xyes")

AC_MSG_CHECKING([whether to enable direct DSP access for PDCH of sysmocom-bts])
AC_ARG_ENABLE(sysmocom-dsp,
		AC_HELP_STRING([--enable-sysmocom-dsp],
				[enable code for sysmocom DSP [default=no]]),
		[enable_sysmocom_dsp="$enableval"],[enable_sysmocom_dsp="no"])
AC_MSG_RESULT([$enable_sysmocom_dsp])
AM_CONDITIONAL(ENABLE_SYSMODSP, test "x$enable_sysmocom_dsp" = "xyes")

AC_OUTPUT(
    src/Makefile
    examples/Makefile
    Makefile)
