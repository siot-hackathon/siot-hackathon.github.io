---
layout: default
title: Welcome to the Hackathon on Securing the Internet of Things
---

# Preparatory Steps

## RATS

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
 *  This is a rework of attestation code in PSA / TF-M to make it more general, support CWT and
    such
 *  Interface may change; documentation is partial.
 *  Tested as part of PSA / TF-M, but testing of this version is incomplete
 *  Available in [GitHub](https://github.com/laurencelundblade/ctoken). Be sure to look at the example.


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
