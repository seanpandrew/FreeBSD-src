#	@(#)Makefile	8.1 (Berkeley) 6/6/93
# $FreeBSD$

.include <bsd.own.mk>

PROG=	inetd
MAN=	inetd.8
MLINKS=	inetd.8 inetd.conf.5
SRCS=	inetd.c builtins.c

WARNS?=	3
CFLAGS+= -DLOGIN_CAP
#CFLAGS+= -DSANITY_CHECK

.if ${MK_INET6_SUPPORT} != "no"
CFLAGS+= -DINET6
.endif

DPADD+=		${LIBUTIL}
LDADD+=		-lutil

.if ${MK_TCP_WRAPPERS} != "no"
CFLAGS+=	-DLIBWRAP
DPADD+=		${LIBWRAP}
LDADD+=		-lwrap
.endif

# XXX for src/release/picobsd
.if !defined(RELEASE_CRUNCH)
CFLAGS+= -DIPSEC
DPADD+=	${LIBIPSEC}
LDADD+=	-lipsec
.endif

.include <bsd.prog.mk>
