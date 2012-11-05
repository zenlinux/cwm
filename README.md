# cwm - chaos window manager

Linux port of cwm (formerly known was calmwm) from OpenBSD's xenocara.

## Documentation and Bugs
Since this is just a build port of cwm for all information about cwm and it's
configuration please refer to the excellent documentation provided by the man
pages, [here for cwm](http://www.openbsd.org/cgi-bin/man.cgi?query=cwm) and
[here for cwmrc](http://www.openbsd.org/cgi-bin/man.cgi?query=cwmrc)

However, all bugs/crashes/etc should be reported here as they could stem from
differences caused by the porting effort.

## Build and Install
cwm is heavy on the X11 dependencies, which are usually satisfied by the
distributions X11 development packages.

	x11 xcb xrender xft xau xdmcp xinerama xrandr xext freetype2 fontconfig

Building should be as simple as (please report any failure after having satisfied
the library / package dependencies):

	$ make
	# INSTALLPATH=/usr/bin make install
