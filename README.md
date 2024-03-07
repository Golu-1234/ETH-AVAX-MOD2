# Simple Contract Integration with Front-end Dapp

For this project, create a simple contract with 2-3 functions. Then show the values of those functions in frontend of the application and connect with your metamask wallet. 

## Description

The Front-End of a Simple Contract A smart contract that has been deployed on the blockchain can be interacted with using application, a simple web application. To facilitate smooth communication with the contract, the programme establishes a connection with the well-known Ethereum wallet MetaMask.

The application's primary features are as follows:

Connect Wallet: By Clicking you can connect your wallet with front-end application.

Withdraw currency: By clicking a button, users can take 1 to the cryptocurrency value that is kept in the smart contract.

Value of Cryptocurrency: Users can access the most recent price of the cryptocurrency that is stored in the contract and have it displayed on a website.

Deposit Currency: By clicking a button, users can add 1 to the cryptocurrency value that is kept in the smart contract.

## Getting Started

### Installing
1.Clone the repository:
git clone https://github.com/your-username/your-repo.git

2.Install the dependencies:
npm install

#if Using Hardhat Then:-

Run npm i

npx hardhat


### Executing program
Implement your smart contract:

To deploy the smart contract to a blockchain network use Remix.
Record the address on the contract.

*Refresh the contract's address:

Open a text editor and the app.js file.
Put the actual contract address you got from the deployment in place of the placeholder "CONTRACT_ADDRESS."
File saving.

*Launch the programme:

To host the JavaScriptstart a web server or use a development server like Live Server.
Use the correct URL to visit the programme, such as http://127.0.0.1:5500/index.html.

*Link MetaMask:

Check to see if MetaMask is active in your browser and logged into the preferred network.
Give the programme access to connect to your MetaMask account if asked to do so.
```
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.9;

//import "hardhat/console.sol";

contract Assessment {
    address payable public owner;
    uint256 public balance;

    event Deposit(uint256 amount);
    event Withdraw(uint256 amount);

    constructor(uint initBalance) payable {
        owner = payable(msg.sender);
        balance = initBalance;
    }

    function getBalance() public view returns(uint256){
        return balance;
    }

    function deposit(uint256 _amount) public payable {
        uint _previousBalance = balance;
        require(msg.sender == owner, "Not the owner");
        balance += _amount;
        assert(balance == _previousBalance + _amount);
        emit Deposit(_amount);
    }
    error InsufficientBalance(uint256 balance, uint256 withdrawAmount);

    function withdraw(uint256 _withdrawAmount) public {
        require(msg.sender == owner, "Not the owner");
        uint _previousBalance = balance;
        if (balance < _withdrawAmount) {
            revert InsufficientBalance({
                balance: balance,
                withdrawAmount: _withdrawAmount
            });
        }
        balance -= _withdrawAmount;
        assert(balance == (_previousBalance - _withdrawAmount));
        emit Withdraw(_withdrawAmount);
    }
}

```
![Screenshot (181)](https://github.com/Golu-1234/ETH-AVAX-MOD2/assets/161577973/e76a716a-6d2e-434b-b641-bbf3c079cca3)

## Help

```
npm i (please must install node js for running this command)
your Files Should be update
Address must be same as deplyed contracts
```
