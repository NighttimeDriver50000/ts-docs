File Formats
------------

### `.markdown` {#markdown}

Most of the files that you will write for your site will be [Markdown][DF]
files.  TachibanaSite uses Michel Fortin's [PHP Markdown Extra][PME].

[DF]:       https://daringfireball.net/projects/markdown/syntax
[PME]:      https://michelf.ca/projects/php-markdown/extra/

### `.template` {#template}

For [certain files](../overrides/) (typically Markdown files), adding the
extension `.template` will enable embedded [Python][] with the BottlePy
[SimpleTemplate syntax][STpl], assuming you have [enabled templates][ETpl].
TachibanaSite uses Python 2.

[Python]:   https://docs.python.org/2/
[STpl]:     http://bottlepy.org/docs/dev/stpl.html#simpletemplate-syntax
[ETpl]:     ../overrides/#config-enable_templates

### `.ini` {#ini}

Configuration files for TachibanaSite are in [php.ini format][ini]. For users,
the only `.ini` file is the overridable file <code>[config.ini][config]</code>.
For developers, TachibanaSite [modules](../modules/) that add CSS or Javascript
need a <code>[module.ini][module]</code>.

[ini]:      https://secure.php.net/manual/en/function.parse-ini-file.php
[config]:   ../overrides/#config
[module]:   ../modules/#module.ini

### `.php` {#php}

Much of TachibanaSite is written in [PHP 5][], but for users, the only relevant
PHP files are the `index.php` files that must be in each [page
directory](../structure/). [Themes][] also need to have a
<code>[StandardPage.php][SP]</code>.

[PHP 5]:    http://php.net/
[SP]:       ../themes/#StandardPage

Formats for Theme, Module, and TS Devs
--------------------------------------

### `.js` and `.css` {#jsandcss}

Both themes and modules can add [JavaScript][JS] and [CSS][] files. For more
details, see [Themes][] and [Modules][].

Note that if you are using <code>[LoadJavascript.php][LJ.php]</code> (as the
default theme does), [jQuery][] and <code>[utils.js][utils.js]</code> are
automatically included.

[JS]:       https://developer.mozilla.org/en-US/docs/Web/JavaScript
[CSS]:      https://developer.mozilla.org/en-US/docs/Web/CSS
[Themes]:   ../themes/
[Modules]:  ../modules/
[LJ.php]:   https://github.com/NighttimeDriver50000/tachibanasite/blob/master/utils/LoadJavascript.php
[jQuery]:   https://jquery.com/
[utils.js]: https://github.com/NighttimeDriver50000/tachibanasite/blob/master/utils/utils.js

### `.py` {#py}

TachibanaSite modules can add [Python][] modules for use in other modules or
template files. For more details, see [Modules][].
