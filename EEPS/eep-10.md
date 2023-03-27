---
EEP: 10
title: Smart Contract Function Interface of CMChain Digital Collection
author: Siyuan Zhao <zhaosiyuan@chinamobile.com>, Luchun Yang <yangluchun@chinamobile.com>, Shengkun Zhou <zhoushengkun@chinamobile.com>, Lihui Cao <caolihui@chinamobile.com>, Jiayin Li <lijiayinit@chinamobile.com>, Mingjian Zhang <zhangmingjian@chinamobile.com>
status: Draft
type: Standard
category: Interface
created: 2023-3-27
---

## Summary

[ERC721 standard](https://eips.ethereum.org/EIPS/eip-721) and [ERC1155 standard](https://eips.ethereum.org/EIPS/eip-1155) defines the implementation standard of Non-Fungible Token and Multi Token.This contract implements and extends these two standards on the EOS blockchain,providing the idea of the implementing ERC standards on EOS blockchain.

## Abstract

This contract is programmed to provide a complete set of API interfaces of ERC721 and ERC1155 for chain accounts to call.In addition to ERC721 and ERC1155 standard interfaces,the contract expanded functions of batch minting,batch transfer,freezing and destruction of Non-Fungible Tokens and Multi Tokens.

## Specification

The following technical specifications describe the interface of DDC contracts, including mint, burn, transfer, batch mint, batch transfer, freezing, destroy and other functions. The interface of the DDC contract implements the functions of the ERC721 and ERC1155 standards, while expanding the functions of batch mint, batch transfer, freezing, destroy and other functions. 

### Actions

#### mint

`mint(name sender, name to, uint64_t amount, string ddc_uri, uint64 business_type, string memo); `

mint

parameters:

- `sender`:caller of the action
- `to`:receiver of the minted token
- `amount`:amount of minted token
- `ddc_uri`:uri of the minted token
- `business_type`:type of business(`1`means ERC721,`2`means ERC1155)
- `memo`:memo

preconditions:

- `sender`and`to`must be created
- `sender`have the authority of the minting action
- `business_type` is `1` meaning ERC721 or `2` meaning ERC1155
- `amount`has to be equal to `1`if `business_type` is `1`

postconditions:

- The token with `ddc_uri`is minted by `sender` 
- The minted token is owned by `to`



#### batch mint

`mintbatch(name from,name to, vector<uint64> amounts, vector<string> ddc_uris, uint64 business_type, string memo); `

mintbatch

parameters:

- `sender`:caller of the action
- `to`:receiver of the minted tokens
- `amounts`:amount of the minted tokens
- `ddc_uris`:uris of the minted tokens
- `business_type`:type of business(`1`means ERC721,`2`means ERC1155)
- `memo`:memo

preconditions:

- `sender`and`to`must be created
- `sender`have the authority of the batch minting action
- `business_type` is `1` meaning ERC721 or `2` meaning ERC1155
- The members of `amounts` have to be equal to `1` if  `business_type`is `1`(meaning that a ERC721 token can only be minted once with one exact token id)

postconditions:

- Tokens with `ddc_uris`are minted by `sender` 
- The minted tokens are owned by `to`

#### transfer

`transfer(name sender, name from, name to, uint64 ddc_id, uint64 amount, string memo, uint64 business_type); `

transfer

parameters:

- `sender`:caller of the action
- `from`:owner of the token
- `to`:receiver of the transferred token
- `ddc_id`:the unique id of the transferred token
- `amount`:amount of transferred token
- `business_type`:type of business(`1`means ERC721,`2`means ERC1155)
- `memo`:memo

preconditions:

- `sender`,`from`,`to`must be created
- `sender`have the authority of the transfer action
- `from`is the owner of the transferred token
- `ddc_id`is valid meaning that the transferred token exists
- `business_type` is `1` meaning ERC721 or `2` meaning ERC1155
- `amount`has to be equal to `1`if `business_type` is `1`

postconditions:

- The token with `ddc_id`is tranferred from `from` to `to`

#### batch transfer

`batchtrans(name sender,name from, name to, vector<uint64> ddc_ids, vector<uint64> amount, string memo, uint64 business_type); `

batchtrans

parameters:

- `sender`:caller of the action
- `from`:owner of the tokens
- `to`:receiver of the transferred tokens
- `ddc_ids`:the unique ids of the transferred tokens
- `amounts`:amount of transferred tokens
- `business_type`:type of business(`1`means ERC721,`2`means ERC1155)
- `memo`:memo

preconditions:

- `sender`,`from`,`to`must be created
- `sender`have the authority of the transfer action
- `from`is the owner of the transferred tokens
- `ddc_ids`are valid meaning that the transferred tokens exist
- `business_type` is `1` meaning ERC721 or `2` meaning ERC1155
- The members of `amounts` have to be equal to `1` if  `business_type`is `1`(meaning that a ERC721 token can only be minted once with one exact token id)

postconditions:

- The tokens with `ddc_ids`are tranferred from `from` to `to`

#### freezing

`freeze(name sender, uint64 ddc_id, uint64 business_type); `

freeze

Freezed tokens can't be transferred,but can be burned

parameters:

- `sender`:caller of the action
- `ddc_id`:the unique id of the freezed token
- `business_type`:type of business(`1`means ERC721,`2`means ERC1155)

preconditions:

- `sender`must be created
- `sender`have the authority of the freezing action
- `ddc_id`is valid meaning that the freezed token exists
- `business_type` is `1` meaning ERC721 or `2` meaning ERC1155

postconditions:

- The token with `ddc_id`is freezed

#### unfreezing

`unfreeze(name sender, uint64 ddc_id, uint64 business_type); `

unfreeze

parameters:

- `sender`:caller of the action
- `ddc_id`:the unique id of the unfreezed token
- `business_type`:type of business(`1`means ERC721,`2`means ERC1155)

preconditions:

- `sender`must be created
- `sender`have the authority of the unfreezing action
- `ddc_id`is valid meaning that the unfreezed token exists
- `business_type` is `1` meaning ERC721 or `2` meaning ERC1155

postconditions:

- The token with `ddc_id`is unfreezed

#### destroy

`burn(name sender, name owner, uint64 ddc_id, uint64 business_type); `

burn

parameters:

- `sender`:caller of the action
- `owner`:owner of the burned token
- `ddc_id`:the unique id of the burned token
- `business_type`:type of business(`1`means ERC721,`2`means ERC1155)

preconditions:

- `sender`,`owner`must be created
- `sender`have the authority of the burning action
- The burned token belongs to `owner`
- `ddc_id`is valid meaning that the burned token exists
- `business_type` is `1` meaning ERC721 or `2` meaning ERC1155

postconditions:

- The token with `ddc_id`is burned

#### batch destroy

`burnbatch(name sender, name owner, std::vector<uint64_t> ddc_ids, uint64_t business_type); `

burnbatch

parameters:

- `sender`:caller of the action
- `owner`:owner of the burned tokens
- `ddc_ids`:the unique ids of the burned tokens
- `business_type`:type of business(`1`means ERC721,`2`means ERC1155)

preconditions:

- `sender`,`owner`must be created
- `sender`have the authority of the burning action
- The burned tokens belongs to `owner`
- `ddc_ids`is valid meaning that the burned tokens exist
- `business_type` is `1` meaning ERC721 or `2` meaning ERC1155

postconditions:

- The tokens with `ddc_id`are burned

#### approve

`approve(name sender, name to, uint64 ddc_id, uint64 business_type); `

approve

If someone gets a token's approval,he can transfer,freeze or burn the token.

parameters:

- `sender`:caller of the action
- `to`:owner of the approved token
- `ddc_id`:the unique id of the approved token
- `business_type`:type of business(`1`means ERC721,`2`means ERC1155)

preconditions:

- `sender`,`to`must be created
- `sender`have the authority of the approving action
- The approved token belongs to `sender`
- `ddc_id`is valid meaning that the approved token exists
- `business_type` is `1` meaning ERC721 or `2` meaning ERC1155

postconditions:

- `to`gets approval of the approved token which has the id of `ddc_id`

#### batch approve

`approvebatch(name sender, name to, std::vector<uint64_t> ddc_ids, uint64_t business_type); `

approvebatch

If someone gets a token's approval,he can transfer,freeze or burn the token.

parameters:

- `sender`:caller of the action
- `to`:owner of the approved tokens
- `ddc_ids`:the unique ids of the approved tokens
- `business_type`:type of business(`1`means ERC721,`2`means ERC1155)

preconditions:

- `sender`,`to`must be created
- `sender`have the authority of the approving action
- The approved tokens belong to `sender`
- `ddc_id`is valid meaning that the approved tokens exist
- `business_type` is `1` meaning ERC721 or `2` meaning ERC1155

postconditions:

- `to`gets approval of the approved tokens which have the id of `ddc_ids`

## Rationale


The difference between ERC721 and ERC1155 is that ERC721 specifies the uniqueness of the token, while ERC1155 does not have this restriction and can have multiple identical tokens. In DDC, we use global self increasing ddc_id to achieve the irreplaceable nature of token, using business_type to distinguish between two different standard tokens. 
The advantage of this approach is that the ERC721 and ERC1155 tokens can exist simultaneously in DDC, without the need to distinguish between two token contracts. At the same time, doing so can also ensure The uniqueness of ddc_id and avoids the token confusion between ERC721 and ERC1155. 

## Backwards Compatibility

Does not compromise backward compatibility.

## Test Cases

The following are some test cases for the DDC contract.

### Mint

The following content is a mint test case for the DDC contract.

```js
describe('mint', function() {
  let method_name = "mint";
  let business_type = 1;

  it("sender state must be active", async function() {
      await util.exec_contract(contract_name, "updateaccsta", operator1, {
          sender: operator1,
          account: manager1,
          state: 1,
          change_platform_state: 0,
      });
      await expect(async () => {
          await util.exec_contract(contract_name, method_name, manager1, {
              sender: manager1,
              to: consumer1,
              amount: 1,
              ddc_uri: "uri:1",
              business_type: business_type,
              memo: ""
          });
      }).rejects.toThrowError("not active sender");
      await util.exec_contract(contract_name, "updateaccsta", operator1, {
          sender: operator1,
          account: manager1,
          state: 2,
          change_platform_state: 0,
      });
  });

  it("receiver state must be active", async function() {
      await util.exec_contract(contract_name, "updateaccsta", manager1, {
          sender: manager1,
          account: consumer1,
          state: 1,
          change_platform_state: 0,
      });
      await expect(async () => {
          await util.exec_contract(contract_name, method_name, manager1, {
              sender: manager1,
              to: consumer1,
              amount: 1,
              ddc_uri: "uri:1",
              business_type: business_type,
              memo: ""
          });
      }).rejects.toThrowError("not active to user");
      await util.exec_contract(contract_name, "updateaccsta", manager1, {
          sender: manager1,
          account: consumer1,
          state: 2,
          change_platform_state: 0,
      });
  });

  it("function must have permission", async function() {
      await expect(async () => {
          await util.exec_contract(contract_name, method_name, consumer1, {
              sender: consumer1,
              to: consumer3,
              amount: 1,
              ddc_uri: "uri:1",
              business_type: business_type,
              memo: ""
          });
      }).rejects.toThrowError("invalid permission");
      await util.exec_contract(contract_name, "addfunction", operator1, {
          sender: operator1,
          account_role: 3,
          business_type: business_type,
          func_name: "mint",
      });
  });

  it("operator can't mint", async function() {
      await expect(async () => {
          await util.exec_contract(contract_name, method_name, operator1, {
              sender: operator1,
              to: consumer1,
              amount: 1,
              ddc_uri: "uri:1",
              business_type: business_type,
              memo: ""
          });
      }).rejects.toThrowError("Invalid role");
  });

  it("check asset to mint", async function() {
      await util.exec_contract(contract_name, "setfee", operator1, {
          sender: operator1,
          business_type: business_type,
          func_name: "mint",
          value: "1.0000 FEE"
      });
      await expect(async () => {
          await util.exec_contract(contract_name, method_name, consumer1, {
              sender: consumer1,
              to: consumer3,
              amount: 1,
              ddc_uri: "uri:1",
              business_type: business_type,
              memo: ""
          });
      }).rejects.toThrowError("not enough fee to pay");
  });

  it("normal mint", async function() {
      await util.exec_contract(contract_name, "recharge", manager1, {
          from: manager1,
          to: consumer1,
          value: "80.0000 FEE"
      });
      await util.exec_contract(contract_name, method_name, consumer1, {
          sender: consumer1,
          to: consumer1,
          amount: 1,
          ddc_uri: "uri:1",
          business_type: business_type,
          memo: ""
      });
  });
});
```

### Transfer

The following content is a transfer test case for the DDC contract.

```js
describe('transfer', function() {
  let method_name = "transfer";
  let business_type = 1;

  it("sender state must be active", async function() {
      await util.exec_contract(contract_name, "updateaccsta", operator1, {
          sender: operator1,
          account: manager1,
          state: 1,
          change_platform_state: 0,
      });
      await expect(async () => {
          await util.exec_contract(contract_name, method_name, manager1, {
              sender: manager1,
              from: manager1,
              to: consumer1,
              ddc_id: 2,
              amount: 1,
              memo: "",
              business_type: business_type
          });
      }).rejects.toThrowError("not active sender");
      await util.exec_contract(contract_name, "updateaccsta", operator1, {
          sender: operator1,
          account: manager1,
          state: 2,
          change_platform_state: 0,
      });
  });

  it("receiver state must be active", async function() {
      await util.exec_contract(contract_name, "updateaccsta", manager1, {
          sender: manager1,
          account: consumer1,
          state: 1,
          change_platform_state: 0,
      });
      await expect(async () => {
          await util.exec_contract(contract_name, method_name, manager1, {
              sender: manager1,
              from: manager1,
              to: consumer1,
              ddc_id: 2,
              amount: 1,
              memo: "",
              business_type: business_type
          });
      }).rejects.toThrowError("not active to user");
      await util.exec_contract(contract_name, "updateaccsta", manager1, {
          sender: manager1,
          account: consumer1,
          state: 2,
          change_platform_state: 0,
      });
  });

  it("function must have permission", async function() {
      await expect(async () => {
          await util.exec_contract(contract_name, method_name, consumer1, {
              sender: consumer1,
              from: consumer1,
              to: consumer3,
              ddc_id: 2,
              amount: 1,
              memo: "",
              business_type: business_type
          });
      }).rejects.toThrowError("invalid permission");
      await util.exec_contract(contract_name, "addfunction", operator1, {
          sender: operator1,
          account_role: 3,
          business_type: business_type,
          func_name: "transfer",
      });
  });

  it("must use valid ddc id", async function() {
      await expect(async () => {
          await util.exec_contract(contract_name, method_name, consumer1, {
              sender: consumer1,
              from: consumer1,
              to: consumer3,
              ddc_id: 20001,
              amount: 1,
              memo: "",
              business_type: business_type
          });
      }).rejects.toThrowError("invalid ddc id");
  });

  it("ddc must be active", async function() {
      await util.exec_contract(contract_name, "freeze", operator1, {
          sender: operator1,
          ddc_id: 1,
          business_type: business_type,
      });
      await expect(async () => {
          await util.exec_contract(contract_name, method_name, consumer1, {
              sender: consumer1,
              from: consumer1,
              to: consumer3,
              ddc_id: 1,
              amount: 1,
              memo: "",
              business_type: business_type
          });
      }).rejects.toThrowError("ddc id not allowed!");
      await util.exec_contract(contract_name, "unfreeze", operator1, {
          sender: operator1,
          ddc_id: 1,
          business_type: business_type,
      });
  });

  it("must transfer same platform", async function() {
      await expect(async () => {
          await util.exec_contract(contract_name, method_name, consumer1, {
              sender: consumer1,
              from: consumer1,
              to: consumer4,
              ddc_id: 1,
              amount: 1,
              memo: "",
              business_type: business_type
          });
      }).rejects.toThrowError("platform mismatch");
  });

  it("must same person or approve", async function() {
      await expect(async () => {
          await util.exec_contract(contract_name, method_name, consumer3, {
              sender: consumer3,
              from: consumer1,
              to: consumer3,
              ddc_id: 1,
              amount: 1,
              memo: "",
              business_type: business_type
          });
      }).rejects.toThrowError("not approve");
  });

  it("normal transfer", async function () {
      await util.exec_contract(contract_name, method_name, consumer1, {
          sender: consumer1,
          from: consumer1,
          to: consumer3,
          ddc_id: 1,
          amount: 1,
          memo: "",
          business_type: business_type
      });
  });
});
```

## Security Considerations

The deployment of this contract will not temporarily affect EOS security, but the operations involved in the contract, such as transfer, freezing, and destruction, will affect user assets.

## Intellectual Property

I hereby agree that this EEP is subject to this [copyright waiver](https://creativecommons.org/publicdomain/zero/1.0/) and I certify that I have all necessary rights and permissions to make this submission and to agree to such waiver.