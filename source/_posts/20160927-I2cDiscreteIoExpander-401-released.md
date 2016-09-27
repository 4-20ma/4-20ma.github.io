---
title: >-
  I2cDiscreteIoExpander v4.0.1 released
date: 2016-09-27 10:30:00
categories:
  - Arduino
subcategories:
  - I/O Expander
tags:
  - arduino
  - c++
  - dio
  - i2c
  - library
  - pca9535
  - pca9555
  - pcf8574
  - pcf8575
  - pcf8575C
  - texas instruments
  - ti
---

#### Overview

`I2cDiscreteIoExpander` is an Arduino library for the Texas Instruments PCF8575C 16-bit I<sup>2</sup>C I/O expander. Version 4.0.1 was released on 27 Sep 2016 and includes a number of changes.

#### Features
The PCF8575C provides general-purpose remote I/O expansion for most microcontroller families via the I<sup>2</sup>C interface serial clock (SCL) and serial data (SDA).

<!-- more -->

The device features a 16-bit quasi-bidirectional input/output (I/O) port (P07..P00, P17..P10), including latched outputs with high-current drive capability for directly driving LEDs. Each quasi-bidirectional I/O can be used as an input or output without the use of a data-direction control signal. At power on, the I/Os are in 3-state mode. The strong pullup to VCC allows fast-rising edges into heavily loaded outputs. This device turns on when an output is written high and is switched off by the negative edge of SCL. The I/Os should be high before being used as inputs. After power on, as all the I/Os are set to 3-state, all of them can be used as inputs. Any change in setting of the I/Os as either inputs or outputs can be done with the write mode. If a high is applied externally to an I/O that has been written earlier to low, a large current (IOL) flows to GND.

The fixed I<sup>2</sup>C address of the PCF8575C (0x20) is the same as the PCF8575, PCF8574, PCA9535, and PCA9555, allowing up to eight of these devices, in any combination, to share the same I<sup>2</sup>C bus or SMBus.

#### Change log

[Full Changelog](https://github.com/4-20ma/I2cDiscreteIoExpander/compare/v3.0.1...v4.0.1)

IMPROVEMENTS

- \[BREAK\] Update to IDE 1.5 library format v2.1 [\#30](https://github.com/4-20ma/I2cDiscreteIoExpander/pull/30) ([4-20ma](https://github.com/4-20ma))
- Use PlatformIO for Travis CI [\#24](https://github.com/4-20ma/I2cDiscreteIoExpander/pull/24) ([4-20ma](https://github.com/4-20ma))

OTHER

- Update header file caveat [\#40](https://github.com/4-20ma/I2cDiscreteIoExpander/pull/40) ([4-20ma](https://github.com/4-20ma))
- Fix README link, remove \#include [\#38](https://github.com/4-20ma/I2cDiscreteIoExpander/pull/38) ([4-20ma](https://github.com/4-20ma))
- Remove extraneous \#includes [\#36](https://github.com/4-20ma/I2cDiscreteIoExpander/pull/36) ([4-20ma](https://github.com/4-20ma))
- Update LICENSE copyright [\#34](https://github.com/4-20ma/I2cDiscreteIoExpander/pull/34) ([4-20ma](https://github.com/4-20ma))
- Streamline CHANGELOG entries, eliminate dupes [\#32](https://github.com/4-20ma/I2cDiscreteIoExpander/pull/32) ([4-20ma](https://github.com/4-20ma))
- Update CHANGELOG config [\#29](https://github.com/4-20ma/I2cDiscreteIoExpander/pull/29) ([4-20ma](https://github.com/4-20ma))
- Exclude /doc/ from repo, remove deprecated pdf docs [\#22](https://github.com/4-20ma/I2cDiscreteIoExpander/pull/22) ([4-20ma](https://github.com/4-20ma))

#### License

```
Copyright:: 2009-2016 Doc Walker

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

#### Resources

<span class="fa fa-github"> [4-20ma][user] / [I2cDiscreteIoExpander][source]
<span class="fa fa-info-circle"> Source Code [Documentation][docs]
<span class="fa fa-info-circle"> Texas Instruments / [PCF8575C Online datasheet][datasheet]

[user]:       https://github.com/4-20ma
[source]:     https://github.com/4-20ma/I2cDiscreteIoExpander
[docs]:       http://4-20ma.io/I2cDiscreteIoExpander/
[datasheet]:  http://www.ti.com/product/pcf8575c
