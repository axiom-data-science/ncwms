# ncWMS2

[![Build Status](https://travis-ci.org/axiom-data-science/ncwms.svg?branch=master)](https://travis-ci.org/Reading-eScience-Centre/ncwms)

This is an ncWMS2 fork from [Axiom Data Science](https://axiomdatascience.com). Initially this was forked to add support for using [ehcache and terracotta](http://www.terracotta.org/open-source/). Since ncWMS development has stalled we now use this for testing other integrations.

The main difference are:

1. Automated docker builds available [here](https://hub.docker.com/repository/docker/axiom/ncwms/tags).
1. Automated Docker builds are based off of the Axiom fork of [edal-java](https://github.com/axiom-data-science/edal-java).
1. The `edal-java` source location can be specified when building a ncWMS docker container by specifying a few build arguments:

    * EDAL_SOURCE_ORG (defaults to `axiom-data-science`)
    * EDAL_SOURCE_BRANCH (defaults to `develop`)
    * WEB_CONTEXT (defaults to `ROOT`). Typically, ncWMS is run in the `ncWMS` context (the URL path would be `/ncWMS/...`).

    For example, to build with Axiom's `edal-java` but maintain the `ncWMS` context, you would run

    ```
    docker build \
        -t ncwms2 \
        --build-arg="WEB_CONTEXT=ncWMS" \
        --build-arg="EDAL_SOURCE_ORG=axiom-data-science" \
        --build-arg="EDAL_SOURCE_BRANCH=develop" \
        .
    ```
1. You can enable CORS at the tomcat level by building with `--build-arg="ENABLE_CORS=1"`. By default CORS is not enabled and you should enable it at another level (i.e. nginx).


- [Documentation](https://reading-escience-centre.gitbooks.io/ncwms-user-guide/content/)
- [Source code](https://github.com/Reading-eScience-Centre/ncwms)
- [Issues](https://github.com/Reading-eScience-Centre/ncwms/issues)
- [CHANGELOG](https://github.com/Reading-eScience-Centre/ncwms/blob/master/CHANGELOG)


ncWMS is a [Web Map Service](https://en.wikipedia.org/wiki/Web_Map_Service) for geospatial data that are stored in CF-compliant NetCDF files. The intention is to create a WMS that requires minimal configuration: the source data files should already contain most of the necessary metadata. ncWMS is developed and maintained by the Reading e-Science Centre ([ReSC](http://www.met.reading.ac.uk/resc/home/)) at the University of Reading, UK.

ncWMS v2 is built on top of the [EDAL]((https://reading-escience-centre.gitbooks.io/edal-user-guide/content/)) libraries developed by ReSC

## Licence

```
Copyright (c) 2010 The University of Reading
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions
are met:
1. Redistributions of source code must retain the above copyright
   notice, this list of conditions and the following disclaimer.
2. Redistributions in binary form must reproduce the above copyright
   notice, this list of conditions and the following disclaimer in the
   documentation and/or other materials provided with the distribution.
3. Neither the name of the University of Reading, nor the names of the
   authors or contributors may be used to endorse or promote products
   derived from this software without specific prior written permission.
4. If you wish to use, with or without modification, the Godiva web
   interface, the logo of the Reading e-Science Centre must be retained
   on the web page.

THIS SOFTWARE IS PROVIDED BY THE AUTHOR ``AS IS'' AND ANY EXPRESS OR
IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES
OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED.
IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY DIRECT, INDIRECT,
INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT
NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF
THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

## Authors and Contributors

ncWMS is developed by the [Reading e-Science Centre](http://www.met.reading.ac.uk/resc/home/) and is maintained by [@guygriffiths](https://github.com/guygriffiths).

Contributors:

- [@yosoyjay](https://github.com/yosoyjay)
- [@kwilcox](https://github.com/kwilcox)
