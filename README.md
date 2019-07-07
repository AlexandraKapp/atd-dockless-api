# dockless-api

Adapted from The [Dockless API of Austin](https://github.com/cityofaustin) for Berlin.
Supplies data for [the interactive interface](https://github.com/AlexandraKapp/atd-dockless-dataviz).

## Table of Contents
* [Installation](#Installation)
* [API Reference](#api-reference)

## Installation

### About the "Database"

The source database for the API is our [Dockless Vehicle Trips](https://data.austintexas.gov/Transportation-and-Mobility/Dockless-Vehicle-Trips/7d8e-dm7r) dataset.

### Option 1: Run w/ Docker (Suggested)

1.  Install [docker](https://www.docker.com/) and start the engine:
    `systemctl start docker`

2.  Clone repo and `cd` into it.
    `git clone https://github.com/cityofaustin/dockless-api.git`

3.  Start the docker server (in the background on port 80)

`./scripts/serve-local.sh`

4.  Make a request:

```shell
curl http://localhost:80/v1/trips?xy=-97.75094341278084,30.276185988411257&flow=destination
```

### Option 2: Run w/ Python 3

1.  Clone repo and `cd` into it.

2.  Install python requirements:

```python
pip install -r requirements.txt
```

3.  Install [libspatialindex](http://libspatialindex.github.io/)

4.  Start the server:

```python
python app/app.py
```

5.  Make a request:

```shell
curl http://localhost:8000/v1/trips?xy=-97.75094341278084,30.276185988411257&flow=destination
```

## Running Docker

```
docker build -f Dockerfile.base -t cityofaustin/dockless-api .
docker tag cityofaustin/dockless-api:latest cityofaustin/dockless-api:latest
docker push cityofaustin/dockless-api

```

## API Reference

[See here](reference.md)
