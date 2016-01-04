PhpTypography
==============

PhpTypography is based on the [PHP Typography library](http://kingdesk.com/projects/php-tyography/) by KINGdesk. It is extended to support the PSR-0 autoloading standard.

## Installation

Install PhpTypography with [composer](https://getcomposer.org) via

    composer require debach/php-typography:dev-master
    composer install

and then use the class like

    $html       = '...';
    $typography = new Debach\PhpTypography\PhpTypography();
    $prettyHtml = $typography->process($html);

## What PhpTypography does

PhpTypography enhances the typography of the text on your web pages. The following table shows some examples of HTML texts before and after processing.

<table>
    <thead>
        <tr>
            <th>Before</th>
            <th>After</th>
            <th>Explanation</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>explanation</td>
            <td>ex&amp;shy;pla&amp;shy;na&amp;shy;tion</td>
            <td>Robust hyphenation with soft hyphens <code>&amp;shy;</code>. The browser will hyphenate words automatically based on the current line width. This is especially useful where the line width is rather small, for example in multi-column texts (CSS property <code>column-count</code>).</td>
        </tr>
        <tr>
            <td>I'm waiting for "Peter"</td>
            <td>I’m waiting for “Peter”</td>
            <td>Use correct quotes and apostrophes</td>
        </tr>
        <tr>
            <td>...</td>
            <td>…</td>
            <td>Use the ellipses symbol</td>
        </tr>
        <tr>
            <td>A flock of sparrows - some of them juveniles - alighted and sang.</td>
            <td>A flock of sparrows — some of them juveniles — alighted and sang.</td>
            <td>Use an em-dash instead of a hypen</td>
        </tr>
        <tr>
            <td>14-20 men</td>
            <td>14–20 men</td>
            <td>Use an en-dash instead of a hypen in ranges</td>
        </tr>
        <tr>
            <td><code>Acme Corporation &amp; Partners</code></td>
            <td><code>Acme Corporation &lt;span class="amp"&gt;&amp;&lt;/span&gt; Partners</code></td>
            <td>Ampersands symbols are marked up so that you can choose a different font for them and make them look beatiful. Search the web for “ampersand font” as a start.</td>
        </tr>
    </tbody>
</table>

For more examples, see the [project homepage](http://kingdesk.com/projects/php-typography/).

## How to use PhpTypography

Construct an instance `$typography` of `Debach\PhpTypography\PhpTypography` and call `$typography->process($html)` on it with the HTML text `$html` you want to process:

    $html       = '<p>I\'m waiting for "Peter"...</p>';
    $typography = new Debach\PhpTypography\PhpTypography();
    $prettyHtml = $typography->process($html);
    echo $prettyHtml;

The above code will print (soft hyphens not shown)

    <p>I’m waiting for “Peter”…</p>

By the way, if you’re using the full-stack Symfony framework and Twig, there is also the [TypographyBundle](https://github.com/debach/typography-bundle) which comes with nice little helpers such as the `{% typography %}` tag and the `{{ text|typography }}` filter.

## Configuration

A thorough explanation of the configuration can be found at the [KINGdesk homepage](http://kingdesk.com/projects/php-typography-documentation/). 

Hyphenation depends on the language, which can be set with `set_hyphenation_language($languageCode)`. For example, to set the hyphenation language to French or German, call 

    $typography->set_hyphenation_language('fr'); // set to French
    $typography->set_hyphenation_language('de'); // set to German

The default language is American English. Refer to the filenames in the `lang/` directory for an overview of available languages.
