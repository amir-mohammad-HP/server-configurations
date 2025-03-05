# Createing Virtual Environment 

to create a virtual environment, you have to create a python virtaual env 

i suggest using `uv` cli tool to create and activate virtual environment

```bash
# Windows Machine
uv venv .venv && .\.venv\Script\activate
```


# download desired php version 

you can download your php version from this source [`https://windows.php.net/downloads/releases/archives/`](https://windows.php.net/downloads/releases/archives/)
and place it inside the `.venv\Lib\`

should be something like this `D:\you-project-path\.venv\Lib\php-8.4.3` where inside `php-8.4.3` folder `php.exe` and `php.ini` exists

# configure composer

if you need specific version of composer inside `Lib` create a composer folder and

## Ubuntu
```bash
# .venv\Lib\composer\composer
#!/bin/sh

dir=$(cd "${0%[/\\]*}" > /dev/null; pwd)

if [ -d /proc/cygdrive ]; then
    case $(which php) in
        $(readlink -n /proc/cygdrive)/*)
            # We are in Cygwin using Windows php, so the path must be translated
            dir=$(cygpath -m "$dir");
            ;;
    esac
fi

php "${dir}/composer.phar" "$@"
```

## Windows
```bat
# .venv\Lib\composer\composer.bat
@echo OFF
:: in case DelayedExpansion is on and a path contains ! 
setlocal DISABLEDELAYEDEXPANSION
php "%~dp0composer.phar" %*
```

and download your desired composer version of `composer.phar`

inside the same directory

here you go, run 

```bash
php -v
```

```bash
composer -v
```

enjoy!

