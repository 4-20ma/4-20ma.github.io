---
title: >-
  Arduino library for Texas Instruments PCF8575C 16-bit I2C I/O expander
date: 2012-12-31 04:00:00
categories:
- Arduino
subcategories:
- I/O Expander
tags:
- C++
- PCA9535
- PCA9555
- PCF8574
- PCF8575
- PCF8575C
- arduino
- dio
- i2c
- library
- texas instruments
- ti
---

`I2cDiscreteIoExpander` is an Arduino library for the Texas Instruments PCF8575C 16-bit I2C I/O expander.

The PCF8575C provides general-purpose remote I/O expansion for most microcontroller families via the I2C interface serial clock (SCL) and serial data (SDA).

The device features a 16-bit quasi-bidirectional input/output (I/O) port (P07..P00, P17..P10), including latched outputs with high-current drive capability for directly driving LEDs. Each quasi-bidirectional I/O can be used as an input or output without the use of a data-direction control signal. At power on, the I/Os are in 3-state mode. The strong pullup to VCC allows fast-rising edges into heavily loaded outputs. This device turns on when an output is written high and is switched off by the negative edge of SCL. The I/Os should be high before being used as inputs. After power on, as all the I/Os are set to 3-state, all of them can be used as inputs. Any change in setting of the I/Os as either inputs or outputs can be done with the write mode. If a high is applied externally to an I/O that has been written earlier to low, a large current (IOL) flows to GND.

The fixed I2C address of the PCF8575C is the same as the PCF8575, PCF8574, PCA9535, and PCA9555, allowing up to eight of these devices, in any combination, to share the same I2C bus or SMBus.

View Source: <nop class="fa fa-github"> [4-20ma](https://github.com/4-20ma) / [I2cDiscreteIoExpander](https://github.com/4-20ma/I2cDiscreteIoExpander).
