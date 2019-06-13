# Frequently used on CLI

This is a collection of Dude's frequently used commands on servers or command line interfaces by [Digitoimisto Dude Oy](https://www.dude.fi) developer team.

# Table of contents

1. [Let's Encrypt test - test for whether all the certs renew correctly](#lets-encrypt-test---test-for-whether-all-the-certs-renew-correctly)
2. [Find all projects with gravityforms installed](#find-all-projects-with-gravityforms-installed)
3. [Quick backup entire site](#quick-backup-entire-site)
4. [Check WordPress versions in composer.json](#check-wordpress-versions-in-composerjson)
5. [Replace WordPress versions in composer.json (macOS)](#replace-wordpress-versions-in-composerjson-macos)
6. [Optimize video for web](#optimize-video-for-web)
7. [Lowercase all in a directory](#lowercase-all-in-a-directory)
8. [Rename all in a directory](#rename-all-in-a-directory)

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

Make complete working offline mirror of a website using `wget`:

``` bash
wget -U 'Mozilla/5.0 (X11; Linux x86_64; rv:30.0) Gecko/20100101 Firefox/30.0' --mirror --convert-links --adjust-extension --page-requisites --cache=off --cookies=on --glob=on --tries=3 --proxy=off -e --robots=off --no-parent http://example.com
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

#### Optimize video for web

For web optimized mp4:

``` bash
HandBrakeCLI -i input.mp4 -o output.mp4 --encoder x264 --vb 900 --ab 128 --maxWidth 640 --maxHeight 480 --two-pass --optimize
```

For web optimized webm:

``` bash
ffmpeg -i input.mp4 -acodec libvorbis -vcodec libvpx output.webm
```

#### Lowercase all in a directory

Useful for example after downloading a pack of fonts that are capitalized

``` bash
rename -f 'y/A-Z/a-z/' *
```

#### Rename all in a directory

Useful for example after downloading a pack of fonts that have useless -webfont appended, or in any case that lots of files are in wrong format.

``` bash
LC_ALL=C find ./ -type f -exec sed -i '' -e 's/foo/bar/g' {} \;
```

Or dry run:

``` bash
rename -nvs searchword replaceword *
```

And the real thing:

``` bash
rename -vs searchword replaceword *
```

### Footnotes

Under construction, will update constantly.