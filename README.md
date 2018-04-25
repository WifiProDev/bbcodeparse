[![Latest Version](https://img.shields.io/github/release/golonka/bbcodeparser.svg?style=flat-square)](https://github.com/golonka/bbcodeparser/releases)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)
[![Build Status](https://img.shields.io/travis/golonka/BBCodeParser/master.svg?style=flat-square)](https://travis-ci.org/golonka/BBCodeParser)
[![Coverage Status](https://img.shields.io/scrutinizer/coverage/g/golonka/bbcodeparser/master.svg?style=flat-square)](https://scrutinizer-ci.com/g/golonka/bbcodeparser/code-structure)
[![Quality Score](https://img.shields.io/scrutinizer/g/golonka/bbcodeparser/master.svg?style=flat-square)](https://scrutinizer-ci.com/g/golonka/bbcodeparser)
[![Total Downloads](https://img.shields.io/packagist/dt/golonka/bbcodeparser.svg?style=flat-square)](https://packagist.org/packages/golonka/bbcodeparser)

The ``Golonka\BBCodeParser`` package will help you with parsing BBCode.

## Install

Via Composer

``` bash
$ composer require golonka/bbcodeparser
```

## Usage
To parse some text it's as easy as this!
``` php
$bbcode = new Golonka\BBCode\BBCodeParser;

echo $bbcode->parse('[b]Bold Text![/b]');
// <strong>Bold Text!</strong>
```
Would like the parser to not use all bbcodes? Just do like this.
``` php
$bbcode = new Golonka\BBCode\BBCodeParser;

echo $bbcode->only('bold', 'italic')
            ->parse('[b][u]Bold[/u] [i]Italic[/i]![/b]');
            // <strong>[u]Bold[/u] <em>Italic</em>!</strong>

echo $bbcode->except('bold')
            ->parse('[b]Bold[/b] [i]Italic[/i]');
            // [b]Bold[/b] <em>Italic</em>
```

## Laravel integration
The integration into Laravel is really easy, and the method is the same for both Laravel 4 and Laravel 5.
Just open your ``app.php`` config file.

In there you just add this to your providers array
``` php
'Golonka\BBCode\BBCodeParserServiceProvider'
```

And this to your facades array
``` php
'BBCode' => 'Golonka\BBCode\Facades\BBCodeParser'
```

The syntax is the same as if you would use it in vanilla PHP but with the ``BBCode::`` before the methods.
Here are some examples.
``` php
// Simple parsing
echo BBCode::parse('[b]Bold Text![/b]');

// Limiting the parsers with the only method
echo BBCode::only('bold', 'italic')
        ->parse('[b][u]Bold[/u] [i]Italic[/i]![/b]');
        // <strong>[u]Bold[/u] <em>Italic</em>!</strong>

// Or the except method
echo BBCode::except('bold')
        ->parse('[b]Bold[/b] [i]Italic[/i]');
        // [b]Bold[/b] <em>Italic</em>
```

## Testing

``` bash
$ phpunit
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

## Credits

- [Joseph Landberg](https://github.com/golonka)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
