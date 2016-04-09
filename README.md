# creof/wkt-parser

[![Code Climate](https://codeclimate.com/github/creof/wkt-parser/badges/gpa.svg)](https://codeclimate.com/github/creof/wkt-parser)
[![Test Coverage](https://codeclimate.com/github/creof/wkt-parser/badges/coverage.svg)](https://codeclimate.com/github/creof/wkt-parser/coverage)
[![Build Status](https://travis-ci.org/creof/wkt-parser.svg?branch=master)](https://travis-ci.org/creof/wkt-parser)

Lexer and parser library for WKT/EWKT spatial object strings.

## Usage

There are two use patterns for the parser. The value to be parsed can be passed into the constructor, then parse()
called on the returned ```Parser``` object:

```php
$input = 'POLYGON((0 0,10 0,10 10,0 10,0 0))';

$parser = new Parser($input);

$value = $parser->parse();
```

If many values need to be parsed, a single ```Parser``` instance can be used:

```php
$input1 = 'POLYGON((0 0,10 0,10 10,0 10,0 0))';
$input2 = 'POINT(0,0)';

$parser = new Parser();

$value1 = $parser->parse($input1);
$value2 = $parser->parse($input2);
```

## Return

The parser will return an array with the keys ```srid```, ```type```, and ```value```.
- ```type``` is the spatial object type (POINT, LINESTRING, etc.)
- ```value``` will contain an array with integer or float values for points, or nested arrays containing these based on spatial object type.
- ```srid``` is the SRID if EWKT value was parsed, null otherwise.

## Exceptions

The ```Lexer``` and ```Parser``` will throw expections implementing interface ```CrEOF\Geo\WKT\Exception\ExceptionInterface```.
