
# MyToken Solidity
_What's This?_

This is like a digital token machine for Ethereum. It helps create, give, or take away digital tokens.

## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. 

## Features
* Token Metadata: The contract maintains metadata such as the token name, symbol, and total supply.
* Token Creation: The contract creator is initially assigned all tokens specified during contract deployment.
* Token Minting: Allows for the creation of new tokens and assigns them to a specified address.
* Token Burning: Allows for the destruction of tokens held by a specified address.

## Getting Started
### Executing the Program
To run this program, follow these steps:

* Online IDE: Use Remix, an online Solidity IDE. Access the Remix website at Remix Ethereum.

* Create a New File: In Remix, click on the "+" icon in the left-hand sidebar to create a new file. Save the file with a .sol extension (e.g., MyToken.sol).

* Copy and Paste Code: Copy the provided Solidity code and paste it into the newly created file.

``` solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MyToken {
    string public name;                    
    string public symbol;                   
    uint256 public totalSupply;            

    mapping(address => uint256) public balanceOf;

    constructor(string memory _name, string memory _symbol, uint256 _initialSupply) {
        name = _name;
        symbol = _symbol;
        totalSupply = _initialSupply;
        balanceOf[msg.sender] = _initialSupply; // Assign all tokens to the contract creator initially
    }

    // Mint tokens to an address
    function mint(address _to, uint256 _amount) public {
        require(_amount > 0, "Amount must be greater than 0");
        totalSupply += _amount;
        balanceOf[_to] += _amount;
    }

    // Burn tokens from an address
    function burn(address _from, uint256 _amount) public {
        require(balanceOf[_from] >= _amount, "Insufficient balance");
        require(_amount > 0, "Amount must be greater than 0");
        totalSupply -= _amount;
        balanceOf[_from] -= _amount;
    }
}



```

Compile the Code: Navigate to the "Solidity Compiler" tab in the left-hand sidebar. Set the "Compiler" option to "0.8.0" (or another compatible version) and click on the "Compile MyToken.sol" button.

Deploy the Contract: Go to the "Deploy & Run Transactions" tab. Select the MyToken contract from the dropdown menu and click on the "Deploy" button.

Interact with the Contract: Once deployed, you can interact with the contract by minting new tokens, transferring tokens, and burning tokens using the provided functions.

Authors:

Ankita Chaturvedi