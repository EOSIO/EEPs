---
EEP: 8
title: Proposed EOS Token Standard
author: Buddy Deck (@deckb)
revision: 0
status: Draft
type: Standard
category: 
created: 2021-07-22
---

## Simple Summary

For the token contract, describe the mandatory and optional tables and actions that can be accessed on an EOSIO chain.

## Abstract

There are many ways to design and implement a token contract. This token standard looks to provide guidelines towards a minimum basic set of mandatory and optional items that make up a token contract.

## Motivation

The first iteration of this standard mirrors the currently implemented eosio.token contract. It will serve as a first step in defining a standard for tokens on EOS and possibly other EOSIO chains. This standard will allow common APIs to be developed to query token contracts and enable validation checks on contracts to ensure a contract meets the standard. This proposal is meant to start a conversation between community members and is expected to be iterated on based on those conversations.

## Proposed Specification

### Tables

#### accounts

##### scope
`name` of the account holder.

##### primary key
`symbol` of the token.

##### columns
balance: `asset` balance of the token holder.

#### stat

##### scope
`symbol` of the token.

##### primary key
`symbol` of the token.

##### columns
supply: 	`asset` holding the current supply of the token.

max_supply: 	`asset` holding the maximum supply of the token.

issuer:		`name` of the account that can create more tokens.


### Actions

#### close
Close the account of the `owner` for the token `symbol`.
##### required authorizer
The `owner` account holder

##### parameters
owner: `name` of the token holder closing the account.

symbol: `symbol` of the token to close.

##### prerequisites
- The `owner` and `symbol` must exist in the accounts table. 
- The `owner` balance must be zero.

##### postcondition
- The `owner` and `symbol` must not exist in the accounts table.

#### create
Allows the `issuer` account to create a token with a maximum supply.

##### required authorizer
token smart contract account

##### parameters
issuer: `name` of the account who can issue tokens. Can be any account name.

maximum_supply: `asset` setting the maximum supply of the token

##### prerequisites
- Token symbol must be valid.
- Token symbol must not exist in stat table.
- maximum_suply has to be smaller than the maximum supply allowed by the system: 2^62 - 1.
- maximum_supply must be positive.
##### postcondition
- symbol must exist in the stat table
- maximum_supply column must equal maximum_supply parameter
- supply column must equal 0.

#### issue
Amount of tokens that will be issued to an account.

##### required authorizer
`issuer` used when the token was created.

##### parameters
to: `name` of the account who can issue the token.
quantity: `asset` amount of the tokens that will be issued.
memo: `string` of characters describing the issuance.

##### prerequisites
- The `memo` is less than 256 bytes.
- The `quantity` `symbol` was created prior to `issue` being called.
- `to` is the `issuer` used in the create call.
- `quantity` must be positive and less than the `maximum_supply` - `current_supply`

##### postcondition
- `accounts` table must have a scope of to and a primary key of `quantity.symbol`
- `balance` must increase by exactly `quantity` for scope of to and primary key of `quantity.symbol`
- `current_supply` in stat must increase by exactly `quantity`

#### open
Open a zero balance token account for owner  with ram_payer paying for the RAM. Must be a no-op if the accounts table row already exists for this owner and symbol.

##### required authorizer
`ram_payer`

##### parameters
owner: 	`name` of the account to hold the zero balance.
symbol:	`symbol` of the token to open a token account.
ram_payer: 	`name` of the account paying for the RAM.

##### prerequisites
- `ram_payer` has enough RAM.
- The `owner` account exists.
- The `symbol` was created prior to `open` being called.
##### postcondition
- `accounts` table must have a scope of to and a primary key of `quantity.symbol`
- `ram_payer` must be payer for the row created in `accounts` with a scope of `symbol` and primary key of `owner`
- `quantity` must be 0 with correct `symbol` if no row existed in `accounts` with a scope of `symbol` and primary key of `owner` prior to this action


#### retire
Remove quantity from the current supply.

##### required authorizer
`issuer` of the token.

##### parameters
quantity:	`asset` to remove from circulation.
memo:		`string` describing the transaction.

##### prerequisites
- `asset.symbol` exists.
- `supply` - `quantity` is greater or equal to 0.
- `memo` is less than 256 bytes.

##### postconditions
- The row of `accounts` with a scope `issuer` and primary key of `quantity.symbol` balance column must decrease by exactly `quantity`
- `stat` column `current_supply` must decrease by exactly `quantity`

#### transfer
Send tokens from the `from` account to the `to` account.

##### required authorizer
`from` account

##### parameters
from		`name` of the account sending the tokens.
to			`name` of the account receiving the tokens.
quantity	`asset` amount to send.
memo		`string` describing the transfer.

##### prerequisites
- The `to` account  exists and is not equal to `from`.
- `quantity` is positive and is a valid `quantity`.
- `memo` is less than 256 bytes.
- `from` liquid balance is greater than `quantity`.
##### postconditions
- The row of `accounts` with a scope `from` and primary key of `quantity.symbol` `balance` column must decrease by exactly `quantity`
- The row of `accounts` with a scope `to` and primary key of `quantity.symbol` `balance` column must increase by exactly `quantity`
- `from` account is notified of transfer using `require_recipient`
- `to` account is notified of transfer using `require_recipient`

#### transferfee (optional)
Send tokens from the `from` account to the `to` account.

##### required authorizer
`from` account

##### parameters
from		`name` of the account sending the tokens.
to			`name` of the account receiving the tokens.
quantity	`asset` amount to send.
fee			`asset` amount to pay as a fee to an account defined by the contract.
memo		`string` describing the transfer.

##### prerequisites
- The `to` account exists and is not equal to `from`.
- `quantity` is positive and is a valid `quantity`.
- `memo` is less than 256 bytes.
- `from` liquid balance is greater than `fee` plus `quantity`.

##### postconditions
- The row of `accounts` with a scope `from` and primary key of `quantity.symbol` `balance` column must decrease by exactly `quantity` + `fee`
- The row of `accounts` with a scope `to` and primary key of `quantity.symbol` `balance` column must increase by exactly `quantity`
- The row of `accounts` with a scope `issuer` and primary key of `quantity.symbol` `balance` column must increase by exactly `fee`
- `from` account is notified of `transfer` using `require_recipient`
- `to` account is notified of `transfer` using `require_recipient`

#### API
This section contains pseudo code describing what an API could look like. 
##### Get Account Balance
reference
https://developers.eos.io/manuals/eos/latest/nodeos/plugins/chain_api_plugin/api-reference/index#operation/get_table_rows 
###### function 
asset getBalance( name code, name account_name, symbol sym ) {
	return get_table_rows( code, “accounts”, account_name, lower_bound=sym, limit=1 ).rows[0].balance
}
##### Get Supply Information
###### reference
https://developers.eos.io/manuals/eos/latest/nodeos/plugins/chain_api_plugin/api-reference/index#operation/get_table_rows

###### function
```
asset getSupply( name code, symbol sym ) {
	return get_table_rows( code, sym, stat, limt=1 ).rows[0].supply
}
```

##### Get Total Supply Information

###### reference
https://developers.eos.io/manuals/eos/latest/nodeos/plugins/chain_api_plugin/api-reference/index#operation/get_table_rows

###### function
```
asset getTotalSupply( name code, symbol sym ) {
	return get_table_rows( code, sym, stat, limit=1 ).rows[0].max_supply
}
```

## Backwards Compatibility

N/A

## Test Cases

# Implementation

[Sample Contract](https://github.com/EOSIO/eosio.token/tree/main/contracts/eosio.token)
