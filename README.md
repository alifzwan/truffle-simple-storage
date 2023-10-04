<img src="https://trufflesuite.com/img/truffle-logo-dark.svg" width="200">

[![npm](https://img.shields.io/npm/v/truffle.svg)](https://www.npmjs.com/package/truffle)
[![npm](https://img.shields.io/npm/dm/truffle.svg)](https://www.npmjs.com/package/truffle)
[![GitHub Discussions](https://img.shields.io/static/v1?label=Join&message=Discussions&color=3fe0c5)](https://github.com/trufflesuite/truffle/discussions)
[![Coverage Status](https://coveralls.io/repos/github/trufflesuite/truffle/badge.svg)](https://coveralls.io/github/trufflesuite/truffle)
[![gitpoap badge](https://public-api.gitpoap.io/v1/repo/trufflesuite/truffle/badge)](https://www.gitpoap.io/gh/trufflesuite/truffle)

---

This repository will cover evrything about truffle including:

- [What is Truffle](#what-is-truffle)
  - [Why Truffle](#why-truffle)
  - [Pre-requisite](#pre-requisite)
  - [Truffle Installation](#truffle-installation)
  - [Folder Description](#folder-description)
- [Truffle Operation](#truffle-operation)
  - [Compile](#compile)
  - [Deploy](#deploy)
  - [Migrations Scripts](#migrations-scripts)
- [Ganache](#ganache)
- [Blockchain Deployment](#blockchain-deployment)
- [Alchemy](#alchemy)
- [.env](#.env)
- [Ganache VS Testnet](#ganache-vs-testnet)

## What is Truffle

- Truffle is a tool that helps you to easily **Develop, Compile, Test, and Deploy** your **smart contract** in your development environment.

- Another example like truffle is **Hardhat**

## Why Truffle

- Easy front-end(Dapp) integration with smart contract:

  - To develop Decentralized Application(Dapp), You need 2 things:
    - Front-end (react.js/node.js)
    - Smart contract

- Everything at one place:
  - The front-end code and smart contract will be at the same workplace

## Pre-requisite

- Node.js
- Git

## Truffle installation

```
npm install -g truffle
```

To add `truffle.config`

```
truffle init
```

### Folder Description

- **Contracts** - This file contain all of our smart contract
- **Migrations** - This file is where we write script to deploy the smart contract
- **Test** - This file is for test/debug our smart contract

# Truffle Operation

## Compile

This command will compile all of your smart contract in `contracts` folder.

```
truffle compile
```

- After you compile the smart contract, you will now have `build\contracts` folder which contain your `contract.json` which is your compiled contract

- This `contract.json` contained 2 information:

  - Address
  - ABI

- `contract.json` also known as **artifacts** like in **Hardhat**

## Deploy

- To deploy our smart contract, we need a **migration scripts**

- We need to configure our `truffle-config.js`. We need to tell it which blockchain we want to deploy our smart contract at.

- There's two network where you can deploy your smart contract:

  - **Ganache** - your local network
  - **Testnet** - like sepolia/goerli (Metamask)

- Deployment on **Ganache** :
  ```
  truffle migrate --reset
  ```
- If you don't select which account you want to deploy your smart contract, by default it will choose account 1

- Deployment on **Testnet**:
  ```
  truffle migrate --network sepolia --reset
  ```
  - After deploy you can check your contract address on https://sepolia.etherscan.io/ whether your contract exist or not

### Migration Scripts

- Create file on **migrations folder**.
- Your file must follow your smart contract name.
- For example: `1_contract.json`
- Your contract must be deployed in a sequential manner (In order)
- So your next scripts would be `2_contract.json`

# Ganache

Ganache is local blockchain simulator with the help of which you can run a local blockchain on your system.

- It provides you a wallet that consists of :
  - Account
  - ETH
  - Private Key
- These stuff is used to test your deployment of smart contract

# Blockchain Deployment

## Alchemy

- So let's say you have Your Computer (Centralized) and Ethereum Network (Decentralized):

  - You want to join Ethereum Network, so that you can do transaction on Ethereum Network and deploy your smart contract

  - However, the problem arise where Your Computer is Centralized/Real world while Ethereum Network is in Decentralized/Blockchain

  - You cannot connect Your Computer to Ethereum Network.

  - So how to connect Your Computer to Ethereum Network?

  - There's two approaches:

    - Geth - transform your system to NODE (NOT RECOMMENDED)

    - Alchemy - provide bridge between your system to ethereum network (End-Point)

  - We gonna choose **Alchemy**
    - Alchemy will give us provider link (sepolia) and Project ID (API Key)

## .env

- This file contains an explicit contains that you cannot share with anybody:

  - MNEMONIC - This is your Metamask Private Key
  - PROJECT_ID - This is your Alchemy API Key
  - PROVIDER - This is your ALchemy Project Link

- Install **dotenv**:

```
npm install dotenv
```

- Install **HDWalletProvider**

```
npm install @truffle/hdwallet-provider
```

# Ganache VS Testnet

```
   Ganache (Local Network)                Testnet (Ethereum Network)

 - Centralized System                    - Decentralized System

 - Migration/Deployment time is less     - Migration/Deployment time is more

 - Not Reliable for final testing of     - Reliable for final testing
   Dapp
```
