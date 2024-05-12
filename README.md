# Smart-Contract-Project (Module 2)

This program is for creating a smart contract project by using withdraw and deposit functions with a front-end app

## Description

Avalanche is a blockchain platform that provides decentralized apps and blockchain networks. Avalanche is designed to address the scalability issues that have conventional blockchain systems. The platform offers exceptional transaction speed and finality in milliseconds because of the consensus protocol, Avalanche. The adaptable architecture of Avalanche complements this scalability by enabling developers to design customized blockchain networks, or subnets, that satisfy particular needs and use cases. 

## Getting Started

### Executing program

To run this program, you can use Visual Studio Code. 

Once you are on the Visual Studio Code, create a new file. Save the file with a .sol extension (e.g., project.sol). Copy and paste the following code into the file:

// SPDX-License-Identifier: GPL-3.0
pragma solidity 0.8.13;

    contract Assessment{
    address payable public cruz;
    uint256 public money;

    event Deposit(uint256 amount);
    event Withdraw(uint256 amount);

    constructor(uint initmoney) payable {
        cruz = payable(msg.sender);
        money = initmoney;
    }

    function getBalance() public view returns(uint256){
        return money;
    }

    function deposit(uint256 _amount) public payable {
        uint _previousBalance = money;

        require(msg.sender == cruz, "You are not the owner of this account!");

        money += _amount;

        assert(money == _previousBalance + _amount);

        emit Deposit(_amount);
    }

    error InsufficientBalance(uint256 balance, uint256 withdrawAmount);

    function withdraw(uint256 _withdrawAmount) public {
        require(msg.sender == cruz, "You are not the owner of this account!");
        uint _previousBalance = money;
        if (money < _withdrawAmount) {
            revert InsufficientBalance({
                balance: money,
                withdrawAmount: _withdrawAmount
            });
        }

        money -= _withdrawAmount;

        assert(money == (_previousBalance - _withdrawAmount));

        emit Withdraw(_withdrawAmount);
    }
}


This file contains only the solidity. It only provides a template to make it easier for the students. If you would like to access the source code, click the link that I have provided.

Original source code from Sir Chris.
https://github.com/MetacrafterChris/SCM-Starter.git

## Authors

Contributors names and contact info

Elissa Mae Cruz


## License

This project is unlicensed.
