BIN = cwm 
SRCS= cwm.c screen.c xmalloc.c client.c menu.c	\
      search.c util.c xutil.c conf.c xevents.c group.c	\
      kbfunc.c mousefunc.c font.c parse.y linux.c
OBJS= cwm.o screen.o xmalloc.o client.o menu.o		\
      search.o util.o xutil.o conf.o xevents.o group.o	\
      kbfunc.o mousefunc.o font.o y.tab.o linux.o


PKGS = x11 xcb xrender xft xau xdmcp xinerama xrandr xext freetype2 fontconfig

CFLAGS	+= -g -Wall
CPPFLAGS+= -I. -D_GNU_SOURCE
LDFLAGS	+= 

PREFIX ?= /usr

# No user serviceable parts below this line.
CPPFLAGS+= $(shell pkg-config --silence-errors --cflags $(PKGS))
LDFLAGS	+= $(shell pkg-config --silence-errors --libs $(PKGS))

all: obj $(BIN)

obj:
	mkdir -p obj

y.tab.c: parse.y
	yacc parse.y

$(BIN): $(OBJS) y.tab.o
	$(CC) $(OBJS) ${LDFLAGS} -o ${BIN}

$(OBJS): %.o: %.c
	$(CC) -c $(CFLAGS) $(CPPFLAGS) $<

install:
	install -d $(PREFIX)/bin
	install -m 0755 $(BIN) $(PREFIX)/bin/cwm

clean:
	-rm -rf $(BIN) *.o *.core

.PHONY: install clean
