# Create and Mint Token
Creating and minting a token involves deploying a smart contract on a blockchain platform like Ethereum.

## Description
Creating and minting tokens involves gas fees (transaction fees) and requires some familiarity with blockchain development and smart contracts. 

## Getting Started

### Executing the Program

Using Remix IDE, a online development environment for Ethereum smart contracts, execute the provided Solidity smart contract by creating a new file, pasting the code, compiling it using the Solidity Compiler tab, deploying it to a chosen Ethereum network via the Deploy & Run Transactions tab, and subsequently interacting with its functions, allowing us to test and validate the contract's behavior comprehensively.


Code:

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract MyToken is ERC20, Ownable {
    address private _mainOwner;

    constructor(address owner) ERC20("MyToken", "MTK") Ownable(owner) {
        _mainOwner = owner;
        _mint(owner, 700 * (10**uint256(decimals())));
    }

    function mainOwner() public view returns (address) {
        return _mainOwner;
    }

    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }
}

### Author
Name: Mica Ella Gonzaga Santos

Email: 8213946@ntc.edu.ph
