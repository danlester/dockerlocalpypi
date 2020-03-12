## Local Docker container serving pypi
Relevant software:

Bandersnatch - to mirror a list of packages from pypi.org
https://github.com/pypa/bandersnatch

Doesn’t understand dependencies
Downloads all platforms (good?)
Downloads all version (too much?)

Pypiserver - a very simple server to act as an index, maybe based on pypi packages downloaded above
https://github.com/pypiserver/pypiserver#sources

Pip2pi
https://github.com/wolever/pip2pi
Builds a pypi compatible folder repo which can be served over pypiserver
A bit like bandersnatch BUT only works on versions installed and for current (build) platform - no windows etc (Might be possible with --platform=win32 flag but not sure)

Maybe try pip2pi and pypiserver to start with. Although then will only really work for a Docker container


DevPi could be useful, but maybe too much
https://devpi.net/docs/devpi/devpi/5.2/+d/index.html


Best combination would be something like:

https://github.com/chriscowley/docker-pypi-mirror

But would need to work out the dependency tree to whitelist all relevant packages

Linux Only

docker run -p 8080:8080 ideonate/dockerlocalpypi:linuxonly

Then in another container:

docker run -it python:3.7 /bin/bash

pip install --index-url http://host.docker.internal:8080 --trusted-host host.docker.internal numpy




