# ETH-Proof-Project
# Creating a Token

This project demonstrates how to create a custom token on the Ethereum blockchain using Solidity, the primary programming language for smart contracts on Ethereum. The repository includes the Solidity source code, deployment scripts, and comprehensive instructions on how to set up and deploy your own token.

## Description

This project is an in-depth guide to creating a custom token on the Ethereum blockchain using Solidity. It covers the entire process from writing the Solidity code to deploying the token on the Ethereum network. The project aims to provide a clear understanding of the fundamental concepts of smart contracts and token creation, making it easier for developers to create their own tokens for various applications such as Initial Coin Offerings (ICOs), decentralized applications (dApps), and other blockchain-based projects.

## Getting Started

### Prerequisites

To run this program, you will need:

- A web browser
- An internet connection

### Executing the Program

To run this program, you can use Remix, an online Solidity IDE. Follow these steps to get started:

1. **Open Remix:**
   - Go to the Remix website at [https://remix.ethereum.org/](https://remix.ethereum.org/).

2. **Create a New File:**
   - Click on the "+" icon in the left-hand sidebar to create a new file.
   - Save the file with a `.sol` extension (e.g., `MyToken.sol`).
  
   - // SPDX-License-Identifier: MIT
pragma solidity ^0.8.4;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/

contract MyToken {

    // public variables here
    string public name = "Aakashian";
    string public symbol = "Dragon";
    uint256 public supply = 0;

    // mapping variable here
    mapping(address => uint256) public balances;

    // mint function
    function mint(address to, uint256 value) public {
        supply += value;
        balances[to] += value;
    }

    // burn function
    function burn(address from, uint256 value) public {
        require(balances[from] >= value, "Insufficient balance");
       supply = supply - value;
       balances[from] = balances[from] - value;
    }
}
3. **Compile the Contract:**
   - Click on the "Solidity Compiler" tab in the left-hand sidebar.
   - Make sure the "Compiler" option is set to "0.8.4" (or another compatible version), and then click on the "Compile MyToken.sol" button.

4. **Deploy the Contract:**
   - Click on the "Deploy & Run Transactions" tab in the left-hand sidebar.
   - Select the "MyToken" contract from the dropdown menu, and then click on the "Deploy" button.

5. **Interact with the Deployed Contract:**
   - Once the contract is deployed, you can use the deployed contract interface in Remix to call functions like `transfer`, `balanceOf`, etc.

## Authors

Aakash Ojha  
[@Aakash Ojha](https://oaakash14@gmail.com)

## License

This project is licensed under the MIT License - see the LICENSE.md file for details.

