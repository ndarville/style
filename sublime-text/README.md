Style Guide for Sublime Text
----------------------------

### Installation ###

On **OS X**, move the files in this folder to

    ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/User/

On **Windows**, move the files in this folder to

    %APPDATA%\Sublime Text 3\Packages\User\

### Autoprefixer and Browser Strings ###

To test your browser string, download `browserslist`:

```sh
yarn add browserslist
```

You can see both the coverage of your browser string as well as the affected browsers:

```sh
$ browserslist --coverage "> 5%, last 2 versions, ie 9"
These browsers account for 76.25% of all users globally
```

```sh
$ browserslist "> 5%, last 2 versions, ie 9"
and_chr 49
and_uc 9.9
chrome 50
chrome 49
chrome 48
edge 13
edge 12
firefox 45
firefox 44
ie 11
ie 10
ie 9
ie_mob 11
ie_mob 10
ios_saf 9.0-9.2
ios_saf 8.1-8.4
opera 36
opera 35
safari 9.1
safari 9
```
