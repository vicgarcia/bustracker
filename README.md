A python module for use with the Chicago Transit Authority BusTracker API

Get an API key and read the documentation at https://www.transitchicago.com/developers/bustracker/

Getting started ...

```
# clone this repository from github
git clone

# setup virtualenv and install dependencies
pipenv install --dev

# add .env file w/ CTA api key
echo 'CTA_API_KEY=CTA-API-KEY' > .env

# run tests
pipenv run python -m pytest (--disable-vcr to bypass vcr and use live api)
```

Usage ...

```
# create the api object
api = BusTrackerApi('CTA-API-KEY')

# get routes
routes = api.get_routes()
pprint(routes)

[{'rt': '1', 'rtclr': '#336633', 'rtdd': '1', 'rtnm': 'Bronzeville/Union Station'},
 {'rt': '2', 'rtclr': '#993366', 'rtdd': '2', 'rtnm': 'Hyde Park Express'},
 ...
 {'rt': '201', 'rtclr': '#996633', 'rtdd': '201', 'rtnm': 'Central/Ridge'},
 {'rt': '206', 'rtclr': '#666600', 'rtdd': '206', 'rtnm': 'Evanston Circulator'}]

# get vehicles
vehicles = api.get_vehicles(rt='76')
pprint(vehicles)

[{'des': 'Logan Square',
  'dly': False,
  'hdg': '89',
  'lat': '41.93177650088356',
  'lon': '-87.72658175513858',
  'pdist': 21595,
  'pid': 4618,
  'rt': '76',
  'tablockid': '76 -455',
  'tatripid': '122292',
  'tmstmp': '20190514 23:21',
  'vid': '1379',
  'zone': ''},
 ...
 {'des': 'Harlem',
  'dly': False,
  'hdg': '268',
  'lat': '41.93132400512695',
  'lon': '-87.74673230307442',
  'pdist': 34823,
  'pid': 4621,
  'rt': '76',
  'tablockid': '76 -409',
  'tatripid': '1075372',
  'tmstmp': '20190514 23:21',
  'vid': '6803',
  'zone': ''}]
```
