# node-tvdb

[![wercker status](https://app.wercker.com/status/19dcad373ede868e37754a0367d68382/s/master "wercker status")](https://app.wercker.com/project/bykey/19dcad373ede868e37754a0367d68382)

Node.js library for accessing [TheTVDB API](http://www.thetvdb.com/wiki/index.php/Programmers_API). Refactored for [Televiso](https://televi.so/) from [joaocampinhos/thetvdb-api](https://github.com/joaocampinhos/thetvdb-api) to give nicer output and lots of additional features.

Pull requests are always very welcome.

## Features

- Handle errors from API as JavaScript errors
- Only returns relevant data (no need to call response.Data.Series etc.)
- Set language at initialisation or afterwards when needed
- Normalised keys and values
- Empty values parsed as null
- Updates endpoint grouped by type
- Supports both node callback functions and promises
- [Tests with Mocha and Wercker CI](https://app.wercker.com/#applications/53f155d02094f9781d058f98)

## Installation

Install with [npm](http://npmjs.org/):

```
npm install --save node-tvdb
```

And run tests with [Mocha](http://visionmedia.github.io/mocha/):

```
TVDB_KEY=[YOUR API KEY HERE] mocha
```
> _Install mocha with: `npm install -g mocha` (sudo may be required for your setup)_

## Example Usage

To start using this library you first need an API key. You can request one [here](http://thetvdb.com/?tab=apiregister).
Then just follow this simple example that fetches all the shows containing "The Simpsons" in the name.

```
var TVDBClient = require("node-tvdb");
var tvdb       = new TVDBClient("ABC123");

tvdb.getSeries("The Simpsons", function(err, response) {
    // handle error and response
});
```

## API

### var client = new TVDBClient(API_KEY, [language])
```
var TVDBClient = require("node-tvdb");

var tvdb           = new TVDBClient("ABC123"); // language defaults to "en"
var tvdbPortuguese = new TVDBClient("ABC123", "pt");
```

### getLanguages
```
tvdb.getLanguages(function(error, response) {
    // handle error and response
});
```
OR
```
tvdb.getLanguages()
    .then(function(response) { /* handle response */ })
    .catch(function(error) { /* handle error */ });
```

### getLanguage
```
tvdb.getLanguage(); // => "en"
```

### setLanguage
```
tvdb.setLanguage("pt");
```

### getTime
```
tvdb.getTime(function(error, response) {
    // handle error and response
});
```
OR
```
tvdb.getTime()
    .then(function(response) { /* handle response */ })
    .catch(function(error) { /* handle error */ });
```

### getSeries
```
tvdb.getSeries("Breaking Bad", function(error, response) {
    // handle error and response
});
```
OR
```
tvdb.getSeries("Breaking Bad")
    .then(function(response) { /* handle response */ })
    .catch(function(error) { /* handle error */ });
```

### getSeriesById
```
tvdb.getSeriesById(73255, function(error, response) {
    // handle error and response
});
```
OR
```
tvdb.getSeriesById(73255)
    .then(function(response) { /* handle response */ })
    .catch(function(error) { /* handle error */ });
```

### getSeriesByRemoteId
```
tvdb.getSeriesByRemoteId("tt0903747", function(error, response) {
    // handle error and response
});
```
OR
```
tvdb.getSeriesByRemoteId("tt0903747")
    .then(function(response) { /* handle response */ })
    .catch(function(error) { /* handle error */ });
```
> Note: `node-tvdb` automatically selects between remote providers (IMDb and zap2it)

### getSeriesAllById
```
tvdb.getSeriesAllById(73255, function(error, response) {
    // handle error and response
});
```
OR
```
tvdb.getSeriesAllById(73255)
    .then(function(response) { /* handle response */ })
    .catch(function(error) { /* handle error */ });
```

### getEpisodeById
```
tvdb.getEpisodeById(4768125, function(error, response) {
    // handle error and response
});
```
OR
```
tvdb.getEpisodeById(4768125)
    .then(function(response) { /* handle response */ })
    .catch(function(error) { /* handle error */ });
```

### getActors
```
tvdb.getActors(73255, function(error, response) {
    // handle error and response
});
```
OR
```
tvdb.getActors(73255)
    .then(function(response) { /* handle response */ })
    .catch(function(error) { /* handle error */ });
```

### getBanners
```
tvdb.getBanners(73255, function(error, response) {
    // handle error and response
});
```
OR
```
tvdb.getBanners(73255)
    .then(function(response) { /* handle response */ })
    .catch(function(error) { /* handle error */ });
```

### getUpdates
```
tvdb.getUpdates(1400611370, function(error, response) {
    // handle error and response
});
```
OR
```
tvdb.getUpdates(1400611370)
    .then(function(response) { /* handle response */ })
    .catch(function(error) { /* handle error */ });
```

## License

The MIT License (MIT)

Copyright (c) 2014 Edward Wellbrook <edwellbrook@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
