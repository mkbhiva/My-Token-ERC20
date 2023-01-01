# Creating My Own Token OGIT

We will be using the ERC20.sol provided by OpenZeppelin Library. This smart contract will be used to mint (create), burn (destroy), and transfer the tokens. In ERC20.sol, some functions are internal (not accessible outside the contract) and need to be called within some external functions of our smart contract.

## Overview

### Base

We are creating a basic smart contract and importing ERC20.sol.

```solidity
//SPDX-License-Identifier: MIT
pragma solidity 0.8.9;
 
import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
 
contract MyToken is ERC20 {
  
}
```

### Implement Constructor

_ERC20.sol takes two parameters in its constructor, the token name and token symbol. To inherit it properly, we need to implement its constructor. Let’s call this token Ogit and symbol “OGT”._


```solidity
contract MyToken is ERC20 {
   constructor() ERC20("Cookie", "CKE") {
      _mint(msg.sender, 10000 * 10 ** decimals());
   }
}
```
This small code creates our Cookie token with a supply of 10000 minted to the msg.sender. However, we can’t mint any more tokens later with this code. For that, we’ll need to add a function for minting additional tokens. Let’s now create a public function to call the internal _mint function of ERC20.sol.

### Usage

**mint**
Privileged accounts will be able to create more supply.

**burn**
Token holders will be able to destroy their tokens.

**pause and unpause**
Privileged accounts will be able to pause the functionality marked as whenNotPaused. Useful for emergency response.

## License

This Contract is released under the [MIT License](LICENSE) and thanks to [OpenZeppelin](https://openzeppelin.com).

