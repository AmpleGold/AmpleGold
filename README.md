<a href="http://www.amplegold.io/"><img src="https://avatars1.githubusercontent.com/u/69891050?s=460&u=e6aafe70ba1efe2ebdaf7e04e114615433f77d31&v=4" title="AmpleGold" alt="AmpleGold"></a>

# AmpleGold - $AMPLG

AmpleGold (code name AMPLG) is a goldpegged defi protocol that is based on Ampleforths elastic tokensupply model. AMPLG is designed to maintain its base price target of 0.01g of Gold with a progammed inflation adjustment (rebase).

Where Ampleforth rose to a 300m mcap in merely weeks, there were a couple of flaws in their model. We have remodeled and reprogrammed these flaws into a new version of the ample defi protocol.

We are all about decentralization and one thing we distrust most is the current economic fiat system. When the current financial system collapses and the dollar crashes, we strive to remain truly stable by pegging our token to the goldprice. Where 1 AMPLG = 0.01gram of Gold.

Also there were issues with the rebasing protocol. Because its always at a fixed time and date, there was huge volatility right before and after each rebase caused by bots, algorithms and traders. we do this by using a randomized rebase event, that triggers an average of 365 times a year but at at random times.

## Table of Contents

- [Getting Started](#Getting-Started)
- [Mainnet addresses](#Mainnet-addresses)
- [Contracts](#Contracts)
- [Technology](#Technology)
- [Install](#install)
- [Contact](#Contact)
- [License](#license)

## Getting-Started

This repository contains the token contract including their dependencies used on the Ethereum blockchain.

## Mainnet-addresses

The official mainnet addresses of $AMPLG are:

- ERC-20 Token: <a href="https://etherscan.io/token/0x8003c49f6ebacddc493ea47cab45e892d1b638a1">0x8003c49f6ebacddc493ea47cab45e892d1b638a1</a>
- Gold Orchestrator Policy: <a href="https://etherscan.io/address/0x34af6c2e8bd1c58f066b401e9df249c1af128d75">0x34af6c2e8bd1c58f066b401e9df249c1af128d75</a>
- Gold Oracle: <a href="https://etherscan.io/address/0xd015aa88d4d8f75058a3b9bf26290afe872f2642">0xd015aa88d4d8f75058a3b9bf26290afe872f2642</a>
- AMPLG Team Reserve: <a href="https://etherscan.io/address/0x449a26acb90daedb517fded247089f30134ceb09">0x449a26AcB90daeDB517Fded247089f30134cEB09</a>

## Contracts

### AdminProxy.sol

- By design, smart contracts are immutable. On the other hand, software quality heavily depends on the ability to upgrade and patch source code in order to produce iterative releases. Even though blockchain based software profits significantly from the technology’s immutability, still a certain degree of mutability is needed for bug fixing and potential product improvements. OpenZeppelin Upgrades solves this apparent contradiction by providing an easy to use, simple, robust, and opt-in upgrade mechanism for smart contracts that can be controlled by any type of governance, be it a multi-sig wallet, a simple address or a complex DAO.
- https://docs.openzeppelin.com/upgrades/2.7/proxies

### AMPLG_GoldPolicy.sol

-   Parent contract for controlling the smart contract via the gold orchestrator policy.
-   Creates connection to fetch the gold prices and market prices through the Gold Oracle. 
-   Rebasing is pegged to Paxos Gold price. 
-   A randomized lag factor (6-14) is applied based on the current supply, with a
    function to accelerate increase in supply.

Currently under development:

- Integrate Uniswap libraries to connect with Uniswap V2. 

### AMPLG.sol

-   Basic ERC20 Detailed Token with a rebase function, callable by the Gold Orchestrator Policy
-   Contract is Ownable. Owner can be transferred to allow upgrades to finalize the on-chain random rebasing. 
-   Once the code in the contracts is finalized, contract owner will be locked to ensure no party has control and the implementation is completely self governed.

### AMPLG_GoldOracle.sol

- Controls through provider reports the current gold price and market price. 

### AMPLG_TeamReserve.sol

- Smart contract for locking the team tokens of AmpleGold.io

## Technology

### How do rebase events work?

AMPLG’s Elastic token supply defi-protocol has been inspired by AmpleForth’s token model, with some extra features like a randomized rebasing timing and model. AMPLG reaches a supply-price equilibrium with its random rebasing. This means the volatility is in the token supply instead of the token price.

When you Hold AMPLG, you own a percentage of the total supply. Your holdings rise in value when the marketcap rises.

When the price of AMPLG is above the target price. The contract will activate a rebase event to increase AMPLG in circulation and vice versa.

The target price for 1 AMPLG = 0.01g of Gold = $0.63596

To achieve price-supply equilibrium, the protocol expands and contracts supply in one of two ways. Given a price target, Pt and price threshold, δ:

if the exchange rate between AMPLG’s and its target is > Pt + δ, the protocol responds by expanding to coin holders proportionally.

if the exchange rate between AMPLG’s and its target is < Pt − δ, the protocol responds by contracting from coin holders proportionally.

<img src="https://uploads-ssl.webflow.com/5f54b7a65b8274717b693de2/5f58f5f179f4d34481a80e92_amplgprotocol-768x608.jpg">

Above the threshold (Pt + δ) the protocol expands.<br />
Below the threshold (Pt – δ) the protocol contracts.
<br /><br />
Also, a randomized, curved lag factor has been added. This allows the supply to increase faster at a low marketcap. If the supply is high, the lag factor has a bigger chance to be high as well.
<br /><br />
Minimum Lag factor = 6<br />
Maximum lag factor = 14

## Contact

### Official Links:

- Website: https://amplegold.io

- Telegram: https://t.me/amplegold

- Announcement channel: https://t.me/amplegoldannouncements

- Rebase alerts: https://t.me/amplgrebases

- Github: https://github.com/amplegold

- Twitter: https://twitter.com/amplegold

- Medium: https://medium.com/@amplegold

- Youtube: https://youtu.be/MnksEkAW1qA

- Lightpaper: <a href="https://uploads-ssl.webflow.com/5f54b7a65b8274717b693de2/5f55c5cd418da6699b04723e_lightpaper_amplegold_V1_02.pdf">AmpleGold</a>

- UniSwap V2: https://uniswap.info/pair/0x15a6ff0e22404fa28bf1a5dc0688c8b655e798b8

- UniCrypt POL: https://unicrypt.network/uniswap-browser/pair/0x15a6Ff0e22404Fa28BF1A5dc0688c8b655E798B8

### E-mail

Contact us via e-mail:

<a href="mailto:amplegold@protonmail.com">amplegold@protonmail.com</a>

## Install

```bash
# Install project dependencies
npm install

# Install ethereum local blockchain(s) and associated dependencies
npx setup-local-chains
```

### Contribute

To report bugs within this package, create an issue in this repository.
For security issues, please contact amplegold@protonmail.com
When submitting code ensure that it is free of lint errors and has 100% test coverage.

``` bash
# Lint code
npm run lint

# View code coverage
npm run coverage
```

## License

[GNU General Public License v3.0 (c) 2020 AmpleGold.io](./LICENSE)
 
