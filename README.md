# $MILEI Smart Contracts

This repository holds the code for MAGA $MILEI smart contracts.

## Test

```shell
npm run test
npm run test:report-gas
```

Running tests in VS Code: https://hardhat.org/hardhat-runner/docs/advanced/vscode-tests

## Deploy

Deploy to a local Hardhat node.

```shell
npm run compile
npm run node
npm run deploy:local
```

## Create a new project

``` 
npm install --save-dev hardhat
npx hardhat
npx hardhat compile
```
# MAGA $MILEI

MAGA MILEI employs advanced mathematical principles for its tokenomics, ensuring equitable distribution of rewards among all token holders without necessitating token transfers.Utilizing the `reflection` mechanism, MAGA MILEI dynamically adjusts rewards with each transaction, maintaining a fair distribution model.

Distinctively, it abstains from employing `mint` and `burn` methods for token generation or reduction, setting its initial supply at 512 Quadrillion tokens upon deployment, all allocated to the owner.

Despite the fixed supply, MAGA MILEI's token count may increase over time due to reward distributions. These rewards are minted dynamically as transactions occur, facilitated by the `reflection` mechanism.

Additionally, users can effectively burn their tokens by transferring them to the `liquidity pool`, albeit without a designated `burn` function. This mechanism contributes to liquidity while potentially reducing the token supply.

Following each transaction, a portion of tokens is burned as a liquidity fee, while another portion is minted as rewards, all orchestrated through the reflection mechanism.

However, thorough examination of the code revealed require statements in critical methods such as `tokenFromReflection` and `reflectionFromToken`. These constraints likely prevent the token supply from exceeding predefined limits, ensuring the integrity of the project's tokenomics.


## MAGA MILEI structure:
1. `IERC20` interface: Used for ERC-20 tokens.
2. `SafeMath` library: Ensures safe arithmetic operations.
3. `abstract` contract `Context`: Retrieves "msg.sender" and "msg.data".
4. `Address` library: Contains functions related to address types.
5. `Ownable` contract inherits from `Context`: Manages owner-related operations such as `transferOwnership`, `onlyOwner`, `owner`, etc.
6. `IUniswapV2Factory` interface: Creates liquidity pairs with "MAGA MILEI and WBNB".
7. `IUniswapV2Pair` interface: Not utilized in MAGA MILEI, but serves as the template for creating new liquidity pairs.
8. `IUniswapV2Router01` interface: Facilitates the use of the Uniswap function `addLiquidityETH`.
9. `IUniswapV2Router02` is a refinement of `IUniswapV2Router01`: Used for the Uniswap function `swapExactTokensForETHSupportingFeeOnTransferTokens`.
10. `MAGA MILEI` contract inherits from `Context`, `IERC20`, `Ownable`: This contract implements the MAGA MILEI tokenomics.

### Note: To understand the MAGA MILEI project, it is essential to grasp the fundamentals of PancakeSwap (or Uniswap).This repository provides comprehensive explanations of PancakeSwap concepts, along with additional resources for deeper understanding.

## PancakeSwap Introduction Part 1 
This section covers the following topics [link](https://medium.com/@gregshen0925/decentralized-exchange-intro-3ab7c3937041):

- Centralized Exchange (CEX) and Decentralized Exchange (DEX)
- Market Maker
- Automated Market Maker (AMM)
- Constant Product Formula $\( k = x \times y \)$
- PancakeSwap V2 Main Features
    - Token Swap
    - Liquidity Provisioning
        - Providing two tokens to mint LP token
        - Staking LP token
        - Unstaking LP token
        - Burning LP token back to two tokens
    - Oracle
    - Flash Loans

### Architecture of PancakeSwap Smart Contracts
PancakeSwap's architecture comprises two main repositories, each containing two primary smart contracts:

1. **Core**: Responsible for storing values (tokens) and managing them.
   - **Pair**: Implements functionality for swapping, minting, and burning tokens.
   - **Factory**: Facilitates the creation and tracking of pairs.

2. **Periphery**: Contains smart contracts that interact with the Core.
   - **Router**: Facilitates interactions with the Core, providing functionalities such as `swapETHForExactTokens`, `swapExactETHForTokens`, etc.
   - **Library**: Provides functionalities like `getReserves`, `getAmountIn`, `getAmountOut`, etc.

## PancakeSwap Introduction Part 2 
This section elaborates on the following topics [link](https://medium.com/coinmonks/uniswap-introduction-2-c60e66530e68):
- Pair
- Mint
- FeeOn and mintFee
- Burn
- Swap
- Swapping Fee


