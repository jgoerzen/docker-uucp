# uucp

**This project is no longer hosted on Github.  See its [new homepage on Salsa](https://salsa.debian.org/jgoerzen/docker-uucp).**

This Docker image provides a base of support for UUCP.  It includes
everything you'll need to set up a UUCP-over-TCP node, whether you use
basic unencrypted commnuication or some other channel like TLS or
SSH.  The info docs for Taylor UUCP are also included.

You can download with:

    docker pull jgoerzen/uucp

And run with something like this:

    docker run -td \
    --stop-signal=SIGRTMIN+3 \
    --tmpfs /run:size=100M --tmpfs /run/lock:size=100M \
    -v /sys/fs/cgroup:/sys/fs/cgroup:ro \
    --hostname=uucp \
    -v /uucp:/var/spool/uucp:rw \
    --name=uucp jgoerzen/uucp

On a more modern host (Debian bullseye or newer), use:

    docker run -td \
    --stop-signal=SIGRTMIN+3 \
    --tmpfs /run:size=100M --tmpfs /run/lock:size=100M \
    -v /sys/fs/cgroup:/sys/fs/cgroup:rw \
    --cgroupns=host \
    --hostname=uucp \
    -v /uucp:/var/spool/uucp:rw \
    --name=uucp jgoerzen/uucp

You will almost certainly want to preserve `/var/spool/uucp` and
possibly also `/etc/uucp` between container builds.  

# Logging

Logging can be done either to Docker or in the container; see `DEBBASE_SYSLOG` as
documented in the [docker-debian-base docs](https://salsa.debian.org/jgoerzen/docker-debian-base).

# Source

This is prepared by John Goerzen <jgoerzen@complete.org> and the source
can be found at https://salsa.debian.org/jgoerzen/docker-uucp

# Security Status

The Debian operating system is configured to automatically apply security patches.

UUCP itself is barely maintained anymore and has a security model from an earlier era.  Do not expect perfect security from it.  For a more modern approach,
you might want my [NNCP docker image](https://salsa.debian.org/jgoerzen/docker-nncp).

# Copyright

Docker scripts, etc. are Copyright (c) 2019-2022 John Goerzen.  
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions
are met:
1. Redistributions of source code must retain the above copyright
   notice, this list of conditions and the following disclaimer.
2. Redistributions in binary form must reproduce the above copyright
   notice, this list of conditions and the following disclaimer in the
   documentation and/or other materials provided with the distribution.
3. Neither the name of the University nor the names of its contributors
   may be used to endorse or promote products derived from this software
   without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE AUTHORS AND CONTRIBUTORS ``AS IS'' AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
ARE DISCLAIMED.  IN NO EVENT SHALL THE REGENTS OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS
OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION)
HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY
OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF
SUCH DAMAGE.

Additional software copyrights as noted.

