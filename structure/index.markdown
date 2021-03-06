## Structure

The typical structure of a TachibanaSite installation:

-   *Site Directory*

    -   <code>[index.php](#autoredir)</code>

    -   [*Page Directories*](#pagedirs)

    -   `common/`

        -   [*Site-Global Overrides*](../overrides/#global)

    -   <code>[tachibanasite/][repo]</code>

        -   `common/`

            -   [*Default Common Override Files*](../overrides/)

        -   `modules/`

            -   [*Module Directories*](../modules)

        -   `pages/`

            -   *Testing and Mail Confirmation Pages*

        -   <code>[php-markdown/][php-markdown]</code>

            -   [*Micelf's PHP Markdown Extra*][PHPME]

        -   `utils/`

            -   *The TachibanaSite Core*

        -   <code>[LICENSE](../tachibanasite/LICENSE)</code>

        -   `README.markdown`

[repo]: https://github.com/NighttimeDriver50000/tachibanasite
[php-markdown]: https://github.com/michelf/php-markdown
[PHPME]:    https://michelf.ca/projects/php-markdown/extra/

### Home Redirect {#autoredir}

Though it is not strictly-speaking necessary, typically you will want to put a
file like this in the site directory:

```php
<?php
header('Location: home/', true, 303);
die();
?>
```

When users navigate to your site directory, they will be redirected to the home
page.

### Page Directories {#pagedirs}

Every page on a TachibanaSite site is a directory. All that is required to make
the directory a page is to put a file called `index.php` in the directory:

<pre><code class="php">&lt;?php include '<em>&lt;Path to TachibanaSite Directory&gt;</em>/utils/FindStandardPage.php' ?></code></pre>

Then you can place override files in that directory (especially
<code>[index.markdown](../overrides/#index)</code>) to fill out the page.
