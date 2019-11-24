---
layout: default
title: Welcome to the Hackathon on Securing the Internet of Things
---

# Background

This hackathon focuses on technologies developed in three IETF working groups (WGs), namely RATS, SUIT, and TEEP. The scopes of these three groups are:


- The [RATS WG](https://datatracker.ietf.org/wg/rats/about/) is focused on developing attestation functionality. As an example, the Entity Attestation Token (EAT), an attestation token format, is currently standardized, which can be serialized in JSON and CBOR. For security protection JOSE and COSE is used, respectively.

- The [SUIT WG](https://datatracker.ietf.org/wg/suit/about/) defines a manifest format, which describes meta-data for software/firmware updates. A primary use for such manifests is in context of firmware updates. The manifest format uses CBOR and COSE.

- The [TEEP WG](https://datatracker.ietf.org/wg/teep/about/) develops a protocol for installing, updating and deleting trusted applications on a Trusted Execution Environment like Intel SGX or Arm TrustZone. The TEEP protocol re-uses work from the RATS and the SUIT WGs.

More information can be found in the charter text of these working groups (links above).

In general, these three IETF WGs have their use cases in the Internet of Things environment but the technologies can also be used outside the IoT space. For example, attestation is a technology that is useful also for routers. Firmware updates can also be used for non-IoT devices, such as network storage devices. Trusted execution provisioning can be used for confidential computing on edge gateways and in the cloud environment.


