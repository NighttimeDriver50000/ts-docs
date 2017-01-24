Installation
------------

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
```

Make a directory called [`common`](../overrides/), and put a file in it called
[`config.ini`](../overrides/#config):

```ini
[TachibanaSite]
local_host_path = "/<host_path>"
install_url = "/<site_url>/tachibanasite"
enable_templates = yes
```

Quick Start
-----------

Create a file `common/`[`header.markdown`](../overrides/#header):

```markdown
# My Site
```

Create a file
`common/`[`navlist.markdown`](../overrides/#navlist)`.`[`template`](../formats/#template):

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
