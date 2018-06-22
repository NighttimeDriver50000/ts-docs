AutoTS Installation
-------------------

AutoTS is still quite alpha, but the installer works pretty well. You can
install with AutoTS and then edit files manually, and you shouldn't run into
any issues. If you do encounter issues, please submit them to the
[GitHub project](https://github.com/NighttimeDriver50000/tachibanasite/issues).

To install with AutoTS, go into the directory where you want your site, and
run:

```shell
$ curl -O https://raw.githubusercontent.com/NighttimeDriver50000/tachibanasite/master/_install_ts.sh
$ sh _install_ts.sh
```

Then follow the on-screen instructions.

Manual Installation
-------------------

Enter the directory where you want to put your site:

```sh
cd /<host_path>/<site_url>
```

where `<host_path>` is the path on disk corresponding to the URL `/` on your
server (e.g. `/var/www`), and `<site_url>` is the URL path to your site root
(e.g. `/ts`).

Run:

```sh
git clone https://github.com/NighttimeDriver50000/tachibanasite.git
cd tachibanasite
git submodule update --init --recursive
cd ..
```

Make a directory called <code>[common](../overrides/)</code>, and put a file in
it called <code>[config.ini](../overrides/#config)</code>:

```ini
[TachibanaSite]
local_host_path = "/<host_path>"
install_url = "/<site_url>/tachibanasite"
enable_templates = yes
```

Quick Start
-----------

Create a file <code>common/[header.markdown](../overrides/#header)</code>:

```markdown
# My Site
```

Create a file
<code>common/[navlist.markdown](../overrides/#navlist).[template](../formats/#template)</code>:

```markdown
% import os, configIniUtils
% base = os.path.dirname(configIniUtils.get_install_url())
* [Home]({{base}}/home/)
```

Make a directory called `home`, and put a file in it called `index.php`:

```php
<?php include '../tachibanasite/utils/FindStandardPage.php' ?>
```

You will need a file like this in every [page directory](../structure/) in
order to bootstrap TachibanaSite.

Create a file `home/index.markdown`:

```markdown
*Hello, world!*
```

Create a file `index.php`:

```php
<?php
header('Location: /<site_url>/home/', true, 303);
die();
?>
```

Now go to your site.  You should see a simple page with the default
black-and-white theme, "**My Site**" at the top, and the content "*Hello,
world!*".  If your page doesn't look like [this](/test/), go back and make sure
you input everything correctly.

Bootstrap
---------

To enable Bootstrap, edit your `config.ini`, adding the following lines:

```ini
theme_name = "bootstrap"

[Modules]
mobiletext_disabled = yes
bootstrap_disabled = no
bootstrapify_disabled = no
```

Then rename your `header.markdown` to `header.markdown.template` and edit it:

```markdown
% import os, configIniUtils
% base = os.path.dirname(configIniUtils.get_install_url())
# [My Site]({{base}}/bootstrap/)
```

Your page should now look like [this](/test/bootstrap/).
