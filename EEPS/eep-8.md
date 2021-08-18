---
EEP: 8
title: Time-Bound Permissions
status: Draft
type: Standard
category: Core
author: Corvin Meyer auf der Heide <corvin@liquidstudios.io> <@cmadh>
created: 2021-08-03
---

## Simple Summary

For many use cases, it is useful create **permissions with an expiry date**. 

Especially in applications where even small delays in interaction play a major role, the lowest possible delays are necessary to ensure a smooth user experience. To enable minimal delays and improve the user experience as much as possible, during the interaction with an application that communicates with a smart contract, a **custom permission set on specific actions of one or more smart contracts created with a separate key pair that is used locally by the application to sign transactions could be used instead of one of the common wallets**. However, a permanent permission stored locally and used by an app directly is generally more risky than a permission with an expiry date. 

A good example is interaction-rich games based on EOSIO. Communicating with a wallet reduces the user experience by a lot. Custom permissions that allow signing of **non-value-transferring** ingame actions and the use of internal serialisation and signing can greatly enhance the user experience. However, to minimise the risk, users must remove these custom permissions after finishing playing the game, which is unlikely to be done. Expiring permissions where the expiry date can be set to now + time X would increase security.

## Abstract

I suggest adding an expiry date in the form of an eosio-time (uint32_t) to the permission scheme. This could be set both optionally or by default to uint32_max (Sunday, 7 February 2106).

The implementation should not be very complex and the check of the expiry date during the validation of the signing authority should not play a major role from a performance point of view, as no heavy algorithms are needed to check whether the current time is less or greater than the expiry date.

## Motivation

The motivation comes from the experience we gained during the development of a highly interaction-rich eosio-based game. A specific stack of APIs and libraries, as well as newly developed patterns integrated into traditional game engines to interface with EOSIO-based chains, are necessary to improve the user experience to the highest possible level for both normal consumers and traditional gamers. To reach this target group, further improvements are necessary and the best possible and fastest serialisation and signing of transactions are an elementary component. 

## Specification

I leave a more precise specification to the B1 team or other developers with more detailed insights into the implementation of the permission structure.

## Rationale

## Backwards Compatibility

## Test Cases

## Implementations

## Security Considerations

## Intellectual Property
I hereby agree that this EEP is subject to this copyright waiver and I certify that I have all necessary rights and permissions to make this submission and to agree to such waiver.
