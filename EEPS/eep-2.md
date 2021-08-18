---
EEP: 2
title: Linking Accounts to Web Properties
author: Josh Kauffman <josh@eoscanada.com>, Alexandre Bourget <alex@eoscanada.com>, Marc-Antoine Ross <marc@eoscanada.com>, Stephane Duschesneau <stephane@eoscanada.com>, Matthieu Vachon <matthieu.vachon@eoscanada.com>
status: Draft
type: Standard
category: Core
created: 2018-10-10
---

## Summary

For many use cases, it is useful to an EOS account owner to prove it
owns an account on certain web properties (like social medias, or a
website).

We are proposing a protocol to do verification of such web properties,
along with a contract that a user can use to claim those
verifications, similar to how [Keybase](https://keybase.io) works.

This can be used to increase trust of an account, so that another user
will be more or less likely to enter into a transaction with them.

The goal is to introduce increased trust into the ecosystem. We
envision that Block Explorers will be able to scrape data from this
mechanism to display verified properties.


## Motivation

The original motivation came from seeing ECAF send out messages to user accounts whom they were trying to reach.
Without an easy and verifiable means for another account to verify that this is the *the* ECAF EOS account, there
is no reason to expect trust to be assumed.

## Specification

We hereby specify a smart contract interface and behavior, a data
structure for on-chain storage, and a verification protocol for each
types of web properties (each social media sites accounts, or more
generally a website).

### Proposed smart contract

We propose the `accountsjson` smart contract, which, very similar to
[producerjson](https://github.com/greymass/producerjson) and [regproxyinfo](https://github.com/AlohaEOS/eos-proxyinfo), stores a piece of JSON in the
format specified herein.

* Action `set(account_name owner, string json)`

The `set` action authorized the `owner` to store and pay for RAM of
the storage of the `json` UTF-8 encoded string. It is expected to be a
valid JSON document that follows this specification.

### JSON structure

Example JSON structure:

```
{
  "name": "Long form name",
  "website": "https://example.com",
  "accounts": {
    "twitter": {
      "handle": "example_account",
      "claim": "https://twitter.com/example_account/status/100000000000000000000"
    },
    "github": {
      "handle": "example_account",
      "claim": "https://gist.github.com/example_account/1010101deadbeef1010101"
    },
  },
  "contract": {
    "repo": "https://github.com/organization/repository",
    "rev": "v1.0.0"
  }
}
```

Fields:
* `name` **string** -- would be a long-form, properly capitalized, full name of either the person or organization, like "The ACME Company", or "Albert Einstein".
* `website` **string** -- a full-qualified domain name, with connection scheme and optional path.
* `accounts` **Object** -- holds a map of social media properties, which are to be defined in this specification before added (to avoid collision or conflict).
* `accounts.[site].handle` **string** -- defines the simplest expression of the handle on the social media website. For example, a Twitter would **not** include the proverbial `@` sign.
* `accounts.[site].claim` **string** -- the URL of a claim to link the account specified in the `owner` field of the `set()` action call. Claims are specified according to the _verification protocol_ (see below) and are site specific.
* `contract` **Object** -- holds information about the deployed contract on the `owner` account (specified in `set()`), it can be used to build the code living at the given revision and repository, and to assert that the code living on chain under the `owner` account, corresponds to the source code living in the repository.
* `contract.repo` **string** -- holds a URL to a clonable source code repository
* `contract.rev` **string** -- is the revision of the code in that cloned code repository; it can be a tag, a hash or a branch (provided the latter doesn't move)


### Verification protocol

Verifications can happen for

Note that the path will be stripped for verification.

#### Simple CSV file format

As refered to further down this document, the simple `.csv` file format is comprised of:

* Optionally specified headers, with values: `chain_id_prefix,account_name`

* A list of accounts in the format: `chain_id_prefix,account_name`
  where `chain_id_prefix` is the first 8 characters of the hexadecimal
  representation of the chain_id, followed by a comma `,`, followed by
  an EOSIO name-encoded account name (the famous 12 characters-max
  account name)

Example of account `testtesttest` on the EOS mainnet:
aca376f2,testtesttest


#### Website verification

Website verifications requires the
`/.well-known/eosio-accounts/claims.csv` file to be filled, as a
top-level directory of the domain specified in `website`. Verification
strips any path element specified in the `website` field of the `json`
parameter of the `set` action.

The contents of that `claims.csv` file is defined as the _Simple CSV
file format_ above.

A website becomes verified when:

1. One of the lines in the retrieved `claims.csv` matches the `owner`
   account, equal to the `account_name` field in the CSV (for which we
   saw a `set` action go through), on the chain with the corresponding
   `chain_id`, matching the `chain_id_prefix` specified in the CSV
   file.


#### GitHub handles and claims

Verification for GitHub happens by verifying a **gist** published by
the owner of the account, that includes a file named
`eosio-accounts-claims.csv`; that's plural `accounts` and plural
`claims`, separated by dashes, ending with `.csv`.

The contents of that `eosio-accounts-claims.csv` file is defined as
the _Simple CSV file format_ above.

A claimed GitHub identity becomes verified when all of these are true:

1. One of the lines in retrieved `eosio-accounts-claims.csv` matches
   the `owner` account, equal to the `account_name` field in the CSV
   (for which we saw a `set` action go through), on the chain with the
   corresponding `chain_id`, matching the `chain_id_prefix` specified
   in the CSV file.

2. The GitHub `handle` claimed under `accounts.github` (in the `json`
   parameter of the `set` action) matches the creator of the Gist
   (that would be `owner.login` in the response of the GitHub API).


#### Twitter handles and claims

To be defined, but similar to the othe verification methods, verifying
a Tweet in the format:

```
I own the #eosio account [account_name] on the chain [chain_id_prefix].
```

where, again, the `chain_id_prefix` is the first 8 characters of the
hex representation of the chain's `chain_id`.


####


## References

[eosproxyinfo]: https://github.com/AlohaEOS/eos-proxyinfo published as `eosproxyinfo` on mainnet (`aca376f2`)
[producerjson]: https://github.com/greymass/producerjson published as `producerjson` on `aca376f2`
[Draft Implementation]: https://github.com/eoscanada/accountsjson


## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
