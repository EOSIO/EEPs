---
EEP: 9
title: Exception-safe recover_key intrinsic
author: Jeeyong Um (@conr2d)
status: Draft
type: Standard
category: Core
created: 2021-10-20
---

## Simple Summary

An alternative intrinsic for recovering a key that does not throw an exception with invalid input arguments.

## Abstract

`recover_key` intrinsic throws an exception when given signature is invalid. WASM doesn't support exception handling yet, so it will make a whole transaction fail even when it should not. A new intrinsic `recover_key_safe` does same to `recover_key` but doesn't throw an exception when invalid signature is passed.

## Motivation

`ecrecover` precompiled contract of EVM (Ethereum Virtual Machine) recovers a key (truely address) from the signature like `recover_key` intrinsic of EOSIO. When given signature is invalid, `ecrecover` returns an empty byte array rather than throws an exception, so `recover_key` cannot be used to emulate `ecrecover`. Throwing an exception can be avoided by including libsecp256k1 in WASM binary, but recovering a key in WASM takes up to 80ms with eos-vm-jit or 10ms with eos-vm-oc. This consumes CPU bandwidth too much (not usable in practice), so it needs an alternative exception-safe intrinsic for recovering a key to deploy EVM on WASM.  

## Specification

Add a new intrinsic `recover_key_safe`. User can know when it fails to recover a key by comparing the returned size with 0. This intrinsic is activated by the protocol feature `RECOVER_KEY_SAFE`.

``` c++
int recover_key_safe(const capi_checksum256* digest, const char* sig, size_t siglen, char* pub, size_t publen);
```



## Rationale

It would be simpler to make  `recover_key` not to throw an exception, but it can break existing contract that rely on the current behavior of `recover_key`. (Some contract might not handle invalid signature case, because it made transaction failed automatically.) It would be safer to add a new intrinsic.

## Backwards Compatibility

This needs a consensus upgrade by protocol feature, but will not break backward compatibility in contracts.

## Test Cases

## Implementations

## Security Considerations

## Intellectual Property
I hereby agree that this EEP is subject to this copyright waiver and I certify that I have all necessary rights and permissions to make this submission and to agree to such waiver.
