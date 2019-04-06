MKR Roll Call
===

```
|\  /| now or
| \/ |  never
```

### What?
* At **23:59 UTC on April 9, 2019**, there will be an MKR voter "snapshot" to collect a list of voting addresses.
* You can set your MKR to vote any time before the snapshot, just be sure to leave it there until April 10. 
* This is optional, but recommended. Consider this the notice to MKR holders that voting has started in earnest. You also get a fun prize:
* You will get to etch a small section of a [slab of ASCII art](https://nmushegian.github.io/slab-of-art/), which will be permanently embedded into the MCD contract.

### How?
* Anyone who is voting for *any set of proposals* at 2019/4/9 23:59:00 UTC will be counted as present.
* We will manually assemble representative addresses for each voter (for example, if you use the ProxyVote contract, we'll take it's "voting key"). 

## ProxyVote contract at vote.makerdao.com

You can use the [vote.makerdao.com](https://vote.makerdao.com) GUI to vote on the next stability fee poll which should become available on Monday, April 8th. Just be sure your MKR is `lock`ed and `vote`ing until April 9th has passed.

## Direct Voting - Metamask + Hardware Wallet

#### Redeem your old MKR, if you haven't already.

There is a GUI available at [makerdao.com/redeem](https://makerdao.com/redeem)

You can use [etherscan for the generic redeemer UI](0x642ae78fafbb8032da552d619ad43f1d81e4dd7c), but the old MKR token cannot be verified due to its archaic source code.

If you use the GUI, be sure to still verify the transactions.

1. `oldMkr.approve(redeemer, balance);`
2. `redeemer.redeem(balance);`

### Voting with [Chief](https://etherscan.io/address/0x8e2a84d6ade1e7fffee039a35ef5f19f13057152)

[Etherscan Chief GUI](https://etherscan.io/address/0x8e2a84d6ade1e7fffee039a35ef5f19f13057152#writeContract)

[Custom GUI](https://chief.makerdao.com)

Whether you use etherscan, or the chief.makerdao GUI, be sure you still verify the generated transactions:

#### Approve the Chief to spend your MKR (and your "MKR IOU"s, while you're at it).

1. `mkr.approve(chief, max_u256);`
2. `iou.approve(chief, max_u256);`

[IOU approval](https://etherscan.io/address/0x9aed7a25f2d928225e6fb2388055c7363ad6727b#writeContract)

[GOV approval](https://etherscan.io/address/0x9f8f72aa9304c8b593d555f12ef6589cc3a579a2#writeContract)


#### `lock` your MKR:

1. `chief.lock(balance);`

[Chief.lock via Etherscan](https://etherscan.io/address/0x8e2a84d6ade1e7fffee039a35ef5f19f13057152#writeContract)

#### `vote` for any roll call slate that includes address `0x0` as a candidate

1. `chief.vote(rollCallSlate)`;

If you don't have a particular other proposal you want to support, you can use the existing ID for `[0x0]`
```
rollCallSlate == 0x290decd9548b62a8d60345a988386fc84ba6bc95484008f6362f93160ef3e563
              == etch([0x0])
```

you can verify this with `chief.slates(rollCallSlate, 0);` and `chief.slates(rollCallSlate, 1)`

[Chief.vote via Etherscan](https://etherscan.io/address/0x8e2a84d6ade1e7fffee039a35ef5f19f13057152#writeContract)

[Chief.slates via Etherscan](https://etherscan.io/address/0x8e2a84d6ade1e7fffee039a35ef5f19f13057152#readContract)

#### If you want to change your vote

1. `vote(different-slate)`.

Create a new slate with `etch([candidate1, candidate2])`, up to 5 candidates. Make sure your list of candidates is lexically ordered and has no repeating candidates, otherwise the contract will reject it.

[Chief.vote, Chief.etch via Etherscan](https://etherscan.io/address/0x8e2a84d6ade1e7fffee039a35ef5f19f13057152#writeContract)

#### When it comes time to move your MKR

1. `chief.free(amount)`.

Don't worry about re-voting, everything is automatically adjusted.

[Chief.free via Etherscan](https://etherscan.io/address/0x8e2a84d6ade1e7fffee039a35ef5f19f13057152#writeContract)

## Contracts referenced in this guide:

#### Old MKR Token

`old_mkr := 0xc66ea802717bfb9833400264dd12c2bceaa34a6d`

Restritced ABI for `balanceOf`+`approve`:
```
[{"constant":true,"inputs":[{"name":"src","type":"address"}],"name":"balanceOf","outputs":[{"name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"name":"guy","type":"address"},{"name":"wad","type":"uint256"}],"name":"approve","outputs":[{"name":"","type":"bool"}],"payable":false,"stateMutability":"nonpayable","type":"function"}]
```

#### MKR Token

`mkr := 0x9f8f72aa9304c8b593d555f12ef6589cc3a579a2`

#### Redeemer

`redeemer:= 0x642ae78fafbb8032da552d619ad43f1d81e4dd7c`

Restricted ABI for `redeem`:
```
[{"constant":false,"inputs":[],"name":"redeem","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"}]
```

#### Maker "chief" contract

`chief := 0x8e2a84d6ade1e7fffee039a35ef5f19f13057152`

#### IOU Token

`iou := 0x9aed7a25f2d928225e6fb2388055c7363ad6727b`

#### Roll Call Slate

`rollCallSlate` is a `bytes32`, not an address
`rollCallSlate := 0x290decd9548b62a8d60345a988386fc84ba6bc95484008f6362f93160ef3e563`


