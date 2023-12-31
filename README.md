# BladeFi

## A simplified perpetuals DeFi protocol.

---

### How does it work?

BladeFi is a perpetuals protocol, which allows users (traders) to use leverage for their long/short positions.
</br></br>
The liquidity in the protocol is provided by LPs - liquidity providers, who earn share tokens (vUSDC) with a 1:1 ratio to supplied tokens (USDC).
</br></br>
In this simplified implementation of a protocol, no fees or P&L payouts are calculated. This means that it is not profitable for both LPs and traders.
</br></br>
The realtime value of liquidity pools and open interest are tracked, to ensure no money meant for a beneficiary of a successful trade is taken out of the system before payout.

---

### How to use it?

#### For LPs

You can deposit USDC to provide liquidity by using the `deposit()` function inherited from the ERC4626 Tokenized Vault Standard.</br>

Withdrawal is possible through inherited `withdraw()` function, or by swapping share tokens for the corresponding assets (USDC) using the inherited `redeem()` function. This functionality is limited by the assets meant for the traders - you can't withdraw your liquidity just before a trader sold with profit.

#### For Traders

After providing collateral in USDC, you are eligible to borrow assets. </br>

The leverege on your borrowed tokens must not exceed 20x. </br>

### Warning!

No liquidation mechanism is implemented! </br>

Profit and losses are not realised, only accounted for when LPs are withdrawing liquidity.

---

To implement:

- allow for traders to open a decimal position (for ex. 0.5wbtc)
- reduce potential precision loss
- 