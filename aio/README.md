Unifield for Linux AIO
----------------------

These are the files needed to build and distribute the
Unifield for Linux AIO, which is based on the Docker hub
and Docker Compose technologies.

The unifield-aio-$VER.tar.gz file is the "distribution"
file, which is shared with the partner who will run this.

Building
--------

Building is simplified by a makefile. Type "make help" to see the
targets.

The version of Unifield is set by the VER variable in the
Makefile. It can be set on the command line as in:

	make build push dist VER=6.1


