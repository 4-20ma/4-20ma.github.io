---
title: >-
  How to automatically test build Arduino libraries
date: 2016-09-19 6:50:00
categories:
  - HOWTO
tags:
  - arduino
  - atmelavr
  - atmelsam
  - due
  - espressif8266
  - genuino101
  - git
  - github
  - huzzah
  - intel_arc32
  - make
  - platformio
  - teensy
  - teensy31
  - travis
  - uno
---

#### Overview

This post describes how to use GitHub, Travis CI, and PlatformIO to automatically test build Arduino libraries.

#### Background

Modern languages and frameworks typically have mature, well-developed facilities for performing unit, integration, and functional testing. The Arduino/C++ platform is not as well-developed in terms of automated testing. Developers traditionally rely on manual testing of libraries (build via Arduino IDE) which is slow, prone to human error, and limit the ability to test against multiple hardware architectures.

``` text User Story
As a project owner
I want my library to compile cleanly for multiple boards
So that it may be used on a wide variety of hardware
```

<!-- more -->

#### Prerequisites

The following are required:

- [GitHub](https://github.com) account
- [Travis CI](https://travis-ci.org) account
  - You can sign in with your GitHub account
- Arduino [library](https://www.arduino.cc/en/Reference/Libraries)
- [PlatformIO](http://platformio.org)
  - Mac OS X: `brew install platformio`  (v3.0.1 used)

#### Example

In the following example, the [ModbusMaster](https://github.com/4-20ma/ModbusMaster) Arduino library code is hosted on GitHub and Travis CI is configured to run for each push to the repository.

GNU `make` is used to build the example sketches included with the library for each of 5 commonly used Arduino boards. During development, the command may be run from the console in order to build against individual boards or the entire set. The `Makefile` in the root directory of the library defines the build process and is configured to parallelize the Travis CI builds for multiple hardware architectures.

`Makefile` settings: adjust, as required; they are identical for all my projects.

- `FIND` - points to bash `find` command
- `DIR` - location of examples to build; this directory will be recursively searched for source files
- `CRITERIA` - search for `*.ino` (newer) or `*.pde` (older) files
- `BUILD` - points to bash `platformio` command
- `LIB` - location of library to include in build

`Makefile` targets: run from the console for all or specific board testing.

- `make all` - runs `make uno`, `make due`, `make huzzah`, `make genuino101`, `make teensy31`
- `make uno` - sets `PLATFORMIO_BOARD=uno` followed by `make build`
- `make due` - sets `PLATFORMIO_BOARD=due` followed by `make build`
- `make huzzah` - sets `PLATFORMIO_BOARD=huzzah` followed by `make build`
- `make genuino101` - sets `PLATFORMIO_BOARD=genuino101` followed by `make build`
- `make teensy31` - sets `PLATFORMIO_BOARD=teensy31` followed by `make build`

`Makefile` targets: call from Travis CI to conduct builds in parallel.

- `make build` - iterates through example directory, building each one in series

{% codeblock Makefile lang:make https://github.com/4-20ma/ModbusMaster/blob/master/Makefile ModbusMaster/Makefile %}
#-------------------------------------------------------------------- settings
FIND          := find
DIR           := $(PWD)/examples
CRITERIA      := \( -name "*.ino" -o -name "*.pde" \)
EACH_EXAMPLE  := $(FIND) $(DIR) $(CRITERIA) -exec
BUILD         := platformio ci
LIB           := .

#--------------------------------------------------------------------- targets
# update .travis.yml if target boards added
all: uno due huzzah genuino101 teensy31

uno due huzzah genuino101 teensy31:
	PLATFORMIO_BOARD=$@ $(MAKE) build

build:
	$(EACH_EXAMPLE) $(BUILD) --board=$(PLATFORMIO_BOARD) --lib=$(LIB) {} \;

.PHONY: all uno due huzzah genuino101 teensy31 build
{% endcodeblock %}

The `.travis.yml` configures Travis CI. In this example, Travis CI will run 5 parallel builds--1 for each `PLATFORMIO_BOARD` setting.

{% codeblock .travis.yml lang:yaml https://github.com/4-20ma/ModbusMaster/blob/master/.travis.yml ModbusMaster/.travis.yml %}
language: python

python:
  - 2.7

sudo: false

cache:
  directories:
    - ~/.platformio

# update Makefile if target boards added
env:
  - PLATFORMIO_BOARD=uno
  - PLATFORMIO_BOARD=due
  - PLATFORMIO_BOARD=huzzah
  - PLATFORMIO_BOARD=genuino101
  - PLATFORMIO_BOARD=teensy31

install:
  - pip install -U platformio

before_script:
  - env
  - echo $HOME
  - echo $TRAVIS_BUILD_DIR
  - ls -al $PWD

script:
  - make build
{% endcodeblock %}

#### Usage

While developing the library, run `make` from the console to build all examples against all boards configured in the `Makefile`.

``` bash
$ make
PLATFORMIO_BOARD=uno /Applications/Xcode.app/Contents/Developer/usr/bin/make build
find examples \( -name "*.ino" -o -name "*.pde" \) -exec platformio ci --board=uno --lib=. {} \;
.
...
.
Processing uno (platform: atmelavr, board: uno, framework: arduino)
.
...
.
Archiving .pioenvs/uno/libFrameworkArduino.a
Archiving .pioenvs/uno/lib/libModbusMaster.a
Indexing .pioenvs/uno/libFrameworkArduino.a
Indexing .pioenvs/uno/lib/libModbusMaster.a
Linking .pioenvs/uno/firmware.elf
Building .pioenvs/uno/firmware.hex
Calculating size .pioenvs/uno/firmware.elf
AVR Memory Usage
----------------
Device: atmega328p

Program:    3496 bytes (10.7% Full)
(.text + .data + .bootloader)

Data:        472 bytes (23.0% Full)
(.data + .bss + .noinit)


========================= [SUCCESS] Took 1.77 seconds =========================
.
...
.
```

When code is pushed to the GitHub repository, Travis CI will automatically build all examples against each hardware architecture. Failed builds will be flagged in Pull Requests / commits so they may be resolved prior to merge.

#### Summary

GitHub, Travis CI, and PlatformIO provide an effective platform for continuous integration test building of Arduino libraries. This integration assures the developer that their library compiles cleanly against selected hardware platforms.

((( <nop class="fa fa-glass"> - <nop class="fa fa-music"> )))

#### Resources

<span class="fa fa-github"> [kyab](https://github.com/kyab) / [travis-test-arduino](https://github.com/kyab/travis-test-arduino) - inspiration for my use of PlatformIO
<span class="fa fa-github"> [4-20ma](https://github.com/4-20ma) / [ModbusMaster](https://github.com/4-20ma/ModbusMaster) - example library illustrating Arduino continuous integration
<span class="fa fa-info-circle"> PlatformIO / [PlatformIO](http://platformio.org) - open source ecosystem for IoT development
<span class="fa fa-info-circle"> Arduino Reference / [Libraries](https://www.arduino.cc/en/Reference/Libraries)
<span class="fa fa-info-circle"> Gnu / [Introduction to Makefiles](https://www.gnu.org/software/make/manual/make.html#Introduction)
<span class="fa fa-info-circle"> Wikipedia / [make](https://en.wikipedia.org/wiki/Make_(software)
<span class="fa fa-info-circle"> Wikipedia / [Makefile](https://en.wikipedia.org/wiki/Makefile)
