PREFIX=	/opt/local
SRCS=	${PREFIX}/etc/macports/sources.conf

default: all

all:
	@(cd base; [ ! -f Makefile ] && ./configure --prefix=${PREFIX} ; make all)

install: all
	@(cd base; make install)
	@if egrep -q ^rsync ${SRCS}; then \
	  echo file://`pwd`/dports/ [default] >> ${SRCS}; \
	  sed -i .orig -e 's/^rsync/#rsync/' ${SRCS}; \
	  echo "${SRCS} automatically configured"; \
        fi

clean:
	@(cd base; [ -f Makefile ] && make clean)

