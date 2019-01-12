Dockerfile for the Cassini mission
===================================

Dockerfile for [Isis3 (USGS)](https://isis.astrogeology.usgs.gov/)
=========================

[![Docker Automated build](https://img.shields.io/docker/automated/seignovert/isis3-cassini.svg)](https://hub.docker.com/r/seignovert/isis3-cassini/)
[![Docker Build Status](https://img.shields.io/docker/build/seignovert/isis3-cassini.svg)](https://hub.docker.com/r/seignovert/isis3-cassini/)
[![GitHub license](https://img.shields.io/github/license/seignovert/docker-usgs-isis3-cassini.svg)](https://github.com/seignovert/docker-usgs-isis3-cassini/blob/master/LICENSE.md)

- Based on the latest (3.6) `seignovert/usgs-isis3`
- Isis3 binaries are installed in `/usgs/isis/bin`
- Isis3 data are installed in `/usgs/data`

Start Isis3 docker container:
```bash
docker run --rm --volumes /path/to/local/cassini/data:/usgs/data/cassini -it seignovert/isis3-cassini
```

Docker compose
------
To (re)build the container:
```bash
docker-compose build
```

To start the container with `PDS_DATA` and `$ISIS3DATA` shared folders:
```bash
docker-compose run --rm isis3-cassini
```

> __Note:__ `PDS_DATA` and `$ISIS3DATA` environment variables can be defined ub `.env` file, at the project root.

Cassini kernels
----------------
To use the SPICE routines, you may need to pull Cassini data (~30Gb) on your local file system.
To retrieve theses data from the USGS `isis` servers you only need to run:
```
rsync_cassini_kernels
```

Notes:
-----
- `testData/` and `kernels/` folders are excluded from `cassini/data` by default.

> __Important:__ I have no affiliation with USGS. The package is provided as is, use at your own risk.