---
layout: default
title: Welcome to the Hackathon on Securing the Internet of Things
---

# Preparatory Steps

## Attestation / RATS

The Arm Platform Security Architecture (PSA), among other things, defines an attestation API, which uses 
the Entity Attestation Token (EAT). The implement found in Arm Trusted Firmware M (TF-M) uses a number of 
building blocks, namely QCBOR (as an implementation of CBOR), t_cose (as a COSE implementation) and 
ctoken (as an implementation of the EAT token). 

### QCBOR
 *  CBOR encoder / decoder for native C
 *  Mature, tested, commercial code integrated with TF-M and other
 *  Near complete implementation of RFC 7049
 *  Available in [GitHub](https://github.com/laurencelundblade/QCBOR).

### t_cose
 *  COSE Sign1 implementation
     *  Primarily ECDSA signing and verification
     *  Encryption not supported
 *  Small code size, minimal dependency, just on QCBOR and PSA Crypto and/or OpenSSL
 *  Mature, tested, commercial code integrated with TF-M
 *  Available in [GitHub](https://github.com/laurencelundblade/t_cose).

### ctoken
 *  Implementation of CWT, EAT and PSA Initial Attestation 
     *  Doesn't support all the claims defined by EAT and CWT yet.
 *  Small code size, minimal dependency, just on QCBOR and t_cose and PSA Crypto or OpenSSL
 *  This is a rework of attestation code in PSA / TF-M to make it more general, support CWT and such
 *  Interface may change; documentation is partial.
 *  Tested as part of PSA / TF-M, but testing of this version is incomplete
 *  Available in [GitHub](https://github.com/laurencelundblade/ctoken). Be sure to look at the example.

### Example Projects
 * [Attested sensor readings](https://hackmd.io/7d9Ym-w-ScqC0oQp9ji4lQ?view#Attested-sensor-readings)
 * [Journey from IAT to EAT](https://hackmd.io/7d9Ym-w-ScqC0oQp9ji4lQ?view#From-IAT-to-EAT)

## SUIT

### MCUboot

MCUboot is an open-source secure bootloader project for 32-bit microcontrollers. When
integrated with the Trusted Firmware-M codebase, it can also be part of an attested
boot. The trusted firmware implementation uses an earlier draft of RATS for its
attestation tokens. The MCUboot project is also interested in the SUIT manifest to
describe firmware updates.

MCUboot can be built standalone
[mcuboot.com](https://mcuboot.com/mcuboot/readme-zephyr.html) and is
commonly built with Zephyr, and used with projects using Zephyr. There are
numerous supported boards, with the FRDM-K64F being a common example. Any
board with a supported flash driver should be workable with MCUboot,
although there are currently issues with some newer SoCs that have a
minimum write size larger than 8 bytes. It should be possible to build
MCUboot on any platform that is able to build Zephyr applications. The
MCUboot simulator requires Linux or MacOS.

In addition, MCUboot can be included within the trusted firmware TFM image. Docs are
at the dreadful URL
[ci.trustedfirmware.org](https://ci.trustedfirmware.org/job/tf-m-build-test-nightly/lastSuccessfulBuild/artifact/build-docs/tf-m_documents/install/doc/user_guide/html/index.html)

### RIOT

For the SUIT tutorial we will use RIOT, which includes experimental [SUIT support](https://github.com/RIOT-OS/RIOT/tree/master/examples/suit_update).
RIOT is an open source, real-time, multi-threading operating system
which supports a range of devices typically found in the Internet of Things,
based on various 32-bit, 16-bit or 8-bit microcontrollers.

For the SUIT tutorial / hackathon, we suggest you use a preconfigured virtual
machine.
Please download and test-run the VM before the tutorial by following these [instructions & prerequisites](https://github.com/future-proof-iot/RIOT/wiki/SUIT-Tutorial-and-Hackathon-Berlin-2020).

### Manifest Generator

For the tutorial and hackathon, we will use the SUIT manifest generator. This can be [cloned from github](https://github.com/ARMmbed/suit-manifest-generator) and installed using pip, according to the installation [instructions](https://github.com/ARMmbed/suit-manifest-generator#installing). The SUIT manifest generator uses Python 3.6 or later.

### SUIT Manifest Parser Example

For the hackathon, there is a sample parser constructed in a bootloader. This is included in the SUIT Manifest Generator repository. This also requires srec_cat, arm-none-eabi-gcc, and mbed-cli. More detail and requirements are available in the [parser_examples](https://github.com/ARMmbed/suit-manifest-generator/tree/master/parser_examples) directory.

## TEEP

You can either use:

a. Visual Studio on an SGX-capable Windows laptop to code for SGX, or

b. Visual Studio Code on a Windows or Linux laptop to code for ARM TrustZone

### SGX

The prerequisites are listed [here](https://github.com/dthaler/openenclave/blob/feature.vsextension/new_platforms/docs/VisualStudioWindows.md).  To get the VS Extension in the fourth bullet, use the [HACKATHON private](https://1drv.ms/u/s!Aqj-Bj9PNivcnu9rlOlmiAVZz-jOtg?e=QlcO7t) link there rather than the main VS marketplace link since v0.7 is not yet published in the marketplace.

If you need to know whether a machine is SGX1 or SGX1+FLC, you can get just the 'oesgx' tool for Linux and Windows [here](https://1drv.ms/u/s!Aqj-Bj9PNivcnu9uxhIkx-t_VYgHcw?e=bRAudK).

Walkthrough (not required before hackathon):

* See the Walkthrough section [here](https://github.com/dthaler/openenclave/blob/feature.vsextension/new_platforms/docs/VisualStudioWindows.md).

An OTrP prototype with TEEP stubs can be found here:

* GitHub repo: git clone --recursive https://github.com/dthaler/OTrP.git

### Arm TrustZone (for A class)

Prerequisites:

* Install [Visual Studio Code](https://code.visualstudio.com/Download) (for Windows or Linux)

* Install the [Open Enclave extension](https://1drv.ms/u/s!Aqj-Bj9PNivcnu9t-U5vieHQZvzsog?e=3zp70h) private.
  (This update is not yet published in the VS Code marketplace.)

* Followthe other prerequisites listed [here](https://marketplace.visualstudio.com/items?itemName=ms-iot.msiot-vscode-openenclave#requirements)

Walkthrough (not required before hackathon):

* See the Getting Started section [here](https://marketplace.visualstudio.com/items?itemName=ms-iot.msiot-vscode-openenclave).
  If one runs VSCode and the extension on a Windows system, a Linux remote is necessary (WSL, VM, or physical).
