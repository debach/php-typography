PhpTypography
==============

PhpTypography is based on the [PHP Typography library](http://kingdesk.com/projects/php-typography/) by KINGdesk.

## Installation

Install PhpTypography with [composer](https://getcomposer.org) via

    composer require debach/php-typography:dev-master
    composer install

and then use the class like

    $html       = '...';
    $typography = new Debach\PhpTypography\PhpTypography();
    $prettyHtml = $typography->process($html);
