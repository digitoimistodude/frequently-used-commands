# Frequently used on CLI

This is a collection of Dude's frequently used commands on servers or command line interfaces by [Digitoimisto Dude Oy](https://www.dude.fi) developer team.

# Table of contents

1. [Let's Encrypt test - test for whether all the certs renew correctly](#lets-encrypt-test---test-for-whether-all-the-certs-renew-correctly)
2. [Find all projects with gravityforms installed](#find-all-projects-with-gravityforms-installed)
3. [Quick backup entire site](#quick-backup-entire-site)
4. [Check WordPress versions in composer.json](#check-wordpress-versions-in-composerjson)
5. [Replace WordPress versions in composer.json (macOS)](#replace-wordpress-versions-in-composerjson-macos)

## SSL

#####  Let's Encrypt test - test for whether all the certs renew correctly

``` bash
/opt/letsencrypt/certbot-auto renew --dry-run
```

##### Find all projects with gravityforms installed

``` bash
grep -R "gravityforms" --include "composer.json" Projects/
```

##### Quick backup entire site

``` bash
wget --cache=off -U "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101 Safari/537.36" --cookies=on --glob=on --tries=3 --proxy=off -e robots=off -x -r --level=1 -p -H -k --quota=100m http://www.example.com/
```

##### Check WordPress versions in composer.json

``` bash
grep -R "johnpbloch/wordpress" ~/Projects/*/composer.json
```

In `~/.bashrc`:

``` bash
alias wpversions='grep -R "johnpbloch/wordpress" ~/Projects/*/composer.json'
```

Restart terminal or run `. ~/.bashrc` for changes to take effect. Then you can just type `wpversions` to see WordPress versions.

#### Replace WordPress versions in composer.json (macOS)

``` bash
find ~/Projects/ -name composer.json -maxdepth 2 -exec sed -i "" 's/4.2.3/4.2.4/g' {} +
```

Bash alias in `~/.bashrc`:

``` bash
alias updateversion='find ~/Projects/ -name composer.json -maxdepth 2 -exec sed -i "" 's/$1/$2/g' {} +'
```

Then you can update any version by typing `updateversion oldversion newversion`, for example WordPress 4.2.3 to WordPress 4.2.4: `updateversion 4.2.3 4.2.4`.

### Footnotes

Under construction, will update constantly.