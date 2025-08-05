# USDtz (USDT.z) – Official Whitepaper
**Decentralized, Multi-Collateral Stablecoin on Ethereum**  
**Version 1.0 – April 2025**  
🌐 Hosted on GitHub: [https://maxrighttalent.github.io](https://maxrighttalent.github.io)

---

## 1. Abstract

**USDtz (USDT.z)** is a next-generation, multi-collateral stablecoin built on **Ethereum**, designed to maintain a stable 1:1 peg to the US Dollar. Unlike traditional stablecoins, USDtz combines **transparent reserve architecture**, **on-chain governance**, and **upgradeable smart contracts** to ensure long-term resilience, decentralization, and trust.

USDtz is governed by its community through the **USDtz Controller**, a UUPS-upgradeable smart contract that allows secure, permissioned upgrades while preserving user balances and ecosystem integrity.

All code is open-source and hosted on GitHub:  
🔗 [https://github.com/Maxrighttalent](https://github.com/Maxrighttalent)

---

## 2. Base Implementation

### Blockchain & Ecosystem
- **Chain**: Ethereum (L1)
- **Token Standard**: Upgradeable ERC-20 (UUPS Proxy)
- **Compiler**: Solidity `^0.8.25`
- **Pattern**: OpenZeppelin Upgradeable Suite

### Contract Address

0x8743d5A6b3F8a7c2C1e9f0d8E2F1aB5cD4e7a7c2

🔗 [View on Etherscan](https://etherscan.io/address/0x8743d5A6b3F8a7c2C1e9f0d8E2F1aB5cD4e7a7c2)

### Audit & Security
- ✅ Audited by **ChainSecurity**
- 🔗 [Full Audit Report](https://usdtz.io/audit)
- All code is open-source and version-controlled on GitHub

---

## 3. Token Mechanics

### Minting & Burning
- **Mint Authority**: `MINTER_ROLE` (Treasury Multisig)
- **Burn Authority**: `BURNER_ROLE` (Staking contracts)
- **Daily Mint Limit**: 1% of total supply
- **Approval**: 3-of-5 multisig required

### Governance
- **Voting Power**: 1 USDT.z = 1 vote
- **Quorum**: 5% of total supply
- **Voting Period**: 72 hours
- **Platform**: [Snapshot – `usdtz.eth`](https://snapshot.org/#/usdtz.eth)

### Fee Distribution
| Allocation | Use Case |
|----------|--------|
| 70% | Reserve Fund (stability buffer) |
| 20% | Stakers (yield) |
| 10% | Treasury (operations) |

---

## 4. Reserve Architecture

### Collateral Strategy
The protocol uses a **phased collateral model**:

| Phase | Strategy | Assets |
|------|---------|--------|
| **Phase 1** | 1:1 Fiat-Backed | USDC, GUSD |
| **Phase 2** | 1.5:1 Over-Collateralized | USDC + stETH |
| **Phase 3** | 2:1 Dynamic | USDC, stETH, tokenized bonds |

### Benefits of Over-Collateralization
- 🛡️ **Stability**: Extra collateral absorbs market shocks
- 🔄 **Trustless Redemption**: Users can always redeem at par
- 📈 **Scalability**: Enables higher borrowing limits

### Reserve Flow
```mermaid
graph LR
    A[User Deposits Stablecoins] --> B(Treasury Multisig)
    B --> C{Reserve Wallet}
    C --> D[Mint USDtz]
    D --> E[User Receives USDT.z]
5. User Operations
Minting Process
An authorized minter deposits USD-equivalent collateral (e.g., 1,000 USDC) into a unique deposit address.
The deposit is verified and swept into the main reserve wallet.
Upon confirmation, 1,000 USDT.z are minted and sent to the minter’s wallet.
Redemption Process
A user burns USDT.z via the redemption portal.
The system verifies the burn and triggers a withdrawal.
The equivalent value in USDC (minus a 0.1% fee) is sent to the user.
🔐 All operations are subject to multisig approval and daily limits. 

6. Token Utility
Holding USDT.z provides more than just stability — it’s a value-accruing asset:

✅
Stable Value
1:1 USD peg for payments and savings
✅
Staking Rewards
Earn yield by locking USDT.z
✅
Governance
Vote on reserve composition and upgrades
✅
DeFi Integration
Use in Uniswap, Aave, Lido, etc.

7. Technical Implementation
Smart Contract Design
Proxy: UUPS (Universal Upgradeable Proxy Standard)
Libraries: OpenZeppelin Upgradeable Suite
Security: ReentrancyGuard, AccessControl, Custom Errors
Gasless Approvals: permit() via ERC20PermitUpgradeable
Key Roles
MINTER_ROLE
Can mint USDT.z
BURNER_ROLE
Can burn USDT.z
UPGRADER_ROLE
Can upgrade logic
DEFAULT_ADMIN_ROLE
Manages role assignments

