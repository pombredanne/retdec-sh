retdec-sh
=========

Shell scripts for decompiling and analyzing binary files through the
[retdec.com](https://retdec.com) decompilation service by using their public
[REST API](https://retdec.com/api/).

Two scripts are provided:

* **`fileinfo.sh`** - Analyzes the given binary file and prints the obtained
  information to the standard output:

        $ scripts/fileinfo.sh --api-key YOUR-API-KEY file.exe
        Input file               : file.exe
        File format              : PE
        File class               : 32-bit
        File type                : Executable file
        Architecture             : x86 (or later and compatible)
        [..]

* **`decompiler.sh`** - Decompiles the given binary file and downloads the
  decompiled C source code:

        $ scripts/decompiler.sh --api-key YOUR-API-KEY file.exe
        $ cat file.c
		//
		// This file was generated by the Retargetable Decompiler
		// Website: https://retdec.com
		// Copyright (c) 2015 Retargetable Decompiler <info@retdec.com>
		//
        [..]

Development Status
------------------

Although the very basic functionality is there, more features are under
development.

For a list of changes, see the `CHANGELOG` file.

Requirements
------------

* shell (`bash`, `dash`, ...)
* [curl](http://curl.haxx.se/)

The scripts should work with any POSIX shell, although they have been tested
only on `bash` and `dash`.

Installation
------------

Simply copy the scripts from the `scripts` directory to your machine, either
directly or by cloning this repository.

Usage
-----

Since the scripts use the [retdec.com](https://retdec.com) API, **you need to
provide them your API key**. The API key can be obtained by
[registering](https://retdec.com/registration/) at
[retdec.com](https://retdec.com). After [logging
in](https://retdec.com/login/), go to your
[account](https://retdec.com/account/), where you can generate an API key).
After you have an API key, either pass it by using the `-a/--api-key`
parameter, or set the `RETDEC_API_KEY` environment variable.

Synopsis:

    scripts/{fileinfo,decompile}.sh [OPTIONS] FILE

For a detailed list of available options, run the scripts with the `-h/--help`
parameter.

Exit Codes
----------

The scripts may exit with the following codes.

* `0` - everything went OK,
* `1` - either [curl](http://curl.haxx.se/) is not installed or the given
  script parameters are invalid,
* `2` - there was an error during script runtime (e.g. a decompilation failed).

Contributions
-------------

Contributions are welcomed as a pull request. Do not forget to add yourself to
the `AUTHORS.md` file when you have contributed something!

Bug Reporting
-------------

If you have found a bug, please report it by opening an issue.

License
-------

Copyright (c) 2015 Petr Zemek (<s3rvac@gmail.com>) and contributors.

Distributed under the MIT license. See the `LICENSE` file for more details.

Access from Other Languages
---------------------------

If you want to access the [retdec.com](https://retdec.com) decompilation
service from other languages, check out the following projects:

* [retdec-python](https://github.com/s3rvac/retdec-python) - A library and
  tools for accessing the service from Python.
* [retdec-cpp](https://github.com/s3rvac/retdec-cpp) - A library and tools for
  accessing the service from C++.
