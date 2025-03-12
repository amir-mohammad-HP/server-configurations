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

# setup php

```batch
# .venv\Scripts\php.bat
@echo off
setlocal

REM Define the constant executable path
set "command_exe=.\\.venv\\Lib\\php-8.2.5\\php.exe"

REM Check if the executable exists
if not exist "%command_exe%" (
  echo Error: '%command_exe%' not found.
  exit /b 1
)

REM Execute the executable with all provided arguments
"%command_exe%" %*
```
```bash
# .vnev/bin/php.sh
#!/bin/bash

# Define the constant executable path (can be relative or absolute)
command_exe="./.venv/Lib/php-8.2.5/php"

# Resolve the relative path to an absolute path
command_exe=$(realpath "$command_exe")

# Check if the executable exists
if [ ! -f "$command_exe" ]; then
  echo "Error: '$command_exe' not found."
  exit 1
fi

# Execute the executable with all provided arguments
"$command_exe" "$@"
```

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

