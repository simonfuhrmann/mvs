MVE_ROOT := ../../../mve
PSS_ROOT := ../..
TARGET := libmvs.a
include ${MVE_ROOT}/Makefile.inc

# Position independent code (-fPIC) is required for the UMVE plugin system.
CXXFLAGS += -fPIC -I${MVE_ROOT}/libs -I${PSS_ROOT}/libs ${OPENMP}
LDLIBS += -lpng -ltiff -ljpeg

SOURCES := $(wildcard [^_]*.cc)
${TARGET}: ${SOURCES:.cc=.o}
	$(AR) rcs $@ $^

_test%: _test%.o ${SOURCES:.cc=.o} libmve.a libmve_util.a
	${LINK.cc} -o $@ $^ ${LDLIBS}

clean:
	${RM} ${TARGET} *.o Makefile.dep

.PHONY: clean
