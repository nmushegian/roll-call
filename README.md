MKR Roll Call - Preliminary Details, for Whales and Power Users
===

```
|\  /| now or
| \/ |  never
```

* To participate in the roll call, be voting for any slate that includes address `0x0` on **23:59 UTC on April 9, 2019**.
* You will get to etch a small section of a slab of ASCII art, which will be permanently embedded into the MCD contract.
* An announcement will be broadcast on April 2nd.
* This should not interfere with any other voting activity that might happen during that time - just include address `0x0` in any slate you vote for, alongside the thing you actually want passed. (The team can drop enough votes off of `0x0` if something must be passed between April 2 and April 9.)


## Generic steps

### Redeem your old MKR, if you haven't already.

Metamask+HardwareWallet:  [makerdao.com/redeem](https://makerdao.com/redeem)

If you use the GUI, be sure to still verify the transactions.
1) `oldMkr.approve(redeemer, balance);`
2) `redeemer.redeem(balance);`

### Voting with [Chief](https://etherscan.io/address/0x8e2a84d6ade1e7fffee039a35ef5f19f13057152)

A custom GUI is available at [chief.makerdao.com](https://chief.makerdao.com). Whether you use etherscan, or the chief.makerdao GUI, be sure you still verify the generated transactions:

#### Approve the Chief to spend your MKR (and your "MKR IOU"s, while you're at it).
1) `mkr.approve(chief, max_u256);`
2) `iou.approve(chief, max_u256);`

Metamask+HardwareWallet:  [IOU approval](https://etherscan.io/address/0x9aed7a25f2d928225e6fb2388055c7363ad6727b#writeContract)

Metamask+HardwareWallet:  [GOV approval](https://etherscan.io/address/0x9f8f72aa9304c8b593d555f12ef6589cc3a579a2#writeContract)


#### `lock` your MKR:
1) `chief.lock(balance);`

Metamask+HardwareWallet:  [Chief.lock](https://etherscan.io/address/0x8e2a84d6ade1e7fffee039a35ef5f19f13057152#writeContract)

#### `vote` for the roll call slate, which has only the 0x0 account as a candidate *
1) `chief.vote(rollCallSlate)`;

```
rollCallSlate == 0x290decd9548b62a8d60345a988386fc84ba6bc95484008f6362f93160ef3e563
              == etch([0x0])
```

you can verify this with `chief.slates(rollCallSlate, 0);` and `chief.slates(rollCallSlate, 1)`

Metamask+HardwareWallet:  [Chief vote](https://etherscan.io/address/0x8e2a84d6ade1e7fffee039a35ef5f19f13057152#writeContract)

Metamask+HardwareWallet:  [Chief slates](https://etherscan.io/address/0x8e2a84d6ade1e7fffee039a35ef5f19f13057152#readContract)

#### If you want to change your vote
1) `vote(different-slate)`.

Create a new slate with `etch([candidate1, candidate2])`, up to 5 candidates.

Metamask+HardwareWallet:  [Chief.vote, Chief.etch](https://etherscan.io/address/0x8e2a84d6ade1e7fffee039a35ef5f19f13057152#writeContract)

#### When it comes time to move your MKR
1) `chief.free(amount)`.

Don't worry about re-voting, everything is automatically adjusted.

Metamask+HardwareWallet:  [Chief.free](https://etherscan.io/address/0x8e2a84d6ade1e7fffee039a35ef5f19f13057152#writeContract)

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

`iou := 0x9aed7a25f2d928225e6fb2388055c7363ad6727`

#### Roll Call Slate

`rollCallSlate := 0x290decd9548b62a8d60345a988386fc84ba6bc95484008f6362f93160ef3e563`


