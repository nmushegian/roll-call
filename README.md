##### Redeem your old MKR, if you haven't already.
1) `oldMkr.approve(redeemer, balance);`
2) `redeemer.redeem(balance);`

##### Approve the Chief to spend your MKR (and your "MKR IOU"s, while you're at it).
1) `mkr.approve(chief, max_u256);`
2) `iou.approve(chief, max_u256);`

##### `lock` your MKR:
1) `chief.lock(balance);`

##### `vote` for the roll call slate, which has only the 0x0 account as a candidate *
1) `chief.vote(rollCallSlate)`;

* you can verify this with `chief.slates(rollCallSlate, 0);` and `chief.slates(rollCallSlate, 1)`

##### If you want to change your vote
1) `vote(different-slate)`.

Create a new slate with `etch([candidate1, candidate2])`, up to 5 candidates.

##### When it comes time to move your MKR
1) `chief.free(amount)`.

Don't worry about re-voting, everything is automatically adjusted.


Contracts referenced in this guide:

* Old MKR Token, `old_mkr := 0xc66ea802717bfb9833400264dd12c2bceaa34a6d`
* MKR Token, `mkr := 0x9f8f72aa9304c8b593d555f12ef6589cc3a579a2`
* Redeemer, `redeemer:= 0x642ae78fafbb8032da552d619ad43f1d81e4dd7c`
* Maker "chief" contract, `chief := 0x8e2a84d6ade1e7fffee039a35ef5f19f13057152`
* `iou := 0x9aed7a25f2d928225e6fb2388055c7363ad6727`
* `rollCallSlate := 0x290decd9548b62a8d60345a988386fc84ba6bc95484008f6362f93160ef3e563`


