# ERC20-for-ETH-n-AVAX
A solidity smart contract implementing a custom ERC20 token

## Description

Implementing an ERC20 Token contract where owner is able to mint tokens to a provided address, and any user is able to burn and transfer tokens. 

## Getting Started

### Installing

* All necessary installations are pre-installed on Remix online IDE
* Copy the raw file "TokenContract.sol" from this repository
* Launch the Remix online IDE with the url https://remix.ethereum.org

### Executing program

* In Remix, create a new file inside the "contracts" folder on the File explorer displayed on the left
* Paste the raw copy from TokenContract.sol (as below) in the new file you created.


```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.9;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract NewToken is ERC20, Ownable {
    constructor()
        ERC20("NewToken", "NTK")
        Ownable(msg.sender)
    {}

    function mint(address to, uint256 amount) external onlyOwner {
        _mint(to, amount);
    }

    function burn(uint256 amount) public override {
        require(balanceOf(msg.sender) >= amount, "Insufficient balance");
        _burn(msg.sender, amount);
    }

    function transfer(address to, uint256 amount) public override returns (bool) {
        _transfer(_msgSender(), to, amount);
        return true;
    }
}
```
        
* Compile the contract by clicking on the "Solidity Compiler" button on the outermost left menu bar (or use the shortcut "Ctrl + S")
* Just below the "Solidity Compiler" button, find and use the "Deploy and Run transactions" button to deploy the smart contract
* On successful deployment, find and click on the "Deployed Contracts" heading to see a drop down of an interface through which the contract can be interacted with
* Find the provided test accounts under the "ACCOUNTS" field of the interface on the left
* Copy any of the addresses listed in the format 0x5B3...eddC4 (100 ether) for use as input to the interfaces that require an address when interacting with the contract
* Test interact with the various functions of the smart contract

## Help

Ensure that the smart contract file you create is named with a ".sol" file extension

## Author(s)

Name: Adeola David Adelakun

Email: adesdesk@outlook.com


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
