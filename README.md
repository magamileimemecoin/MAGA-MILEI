# Create a new project:

``` 
npm install --save-dev hardhat
npx hardhat
npx hardhat compile
```
# MAGA MILEI [Link to the sourcecode](https://github.com/magamileimemecoin/MAGAMILEI/blob/main/Contracts/maga_milei.sol)

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
6. `IUniswapV2Factory` interface: Creates liquidity pairs with "MAGA MILEI and WETH".
7. `IUniswapV2Pair` interface: Not utilized in MAGA MILEI, but serves as the template for creating new liquidity pairs.
8. `IUniswapV2Router01` interface: Facilitates the use of the Uniswap function `addLiquidityETH`.
9. `IUniswapV2Router02` is a refinement of `IUniswapV2Router01`: Used for the Uniswap function `swapExactTokensForETHSupportingFeeOnTransferTokens`.
10. `MAGA MILEI` contract inherits from `Context`, `IERC20`, `Ownable`: This contract implements the MAGA MILEI tokenomics.
