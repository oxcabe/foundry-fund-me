# FundMe

**FundMe** is a minimal crowdfunding platform written in Solidity and targeting the
Ethereum EVM.

## Building from sources

## Requirements

- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
  - You'll know you did it right if you can run `git --version` and you see a response like `git version 2.34.1`.
- [foundry](https://getfoundry.sh/)
  - You'll know you did it right if you can run `forge --version` and you see a response like `forge 0.2.0 (6fcbbd8 2023-12-15T00:23:04.369635679Z`.

## Instructions

```
git clone https://github.com/oxcabe/foundry-fund-me.git
cd foundry-fund-me
forge build
```

## Usage

### Deployment

```
forge script script/DeployFundMe.s.sol
```

### Testing

Run tests:

```
forge test
```

Run specific tests that match some RegEx by running:

```
forge test --mt <regexForMatchingTests>
```

Run tests in Sepolia with:

```
forge test --fork-url <SEPOLIA_RPC_URL>
```

### Test Coverage

```
forge coverage
```

## Deployment to a testnet or mainnet

### 1. Setup environment variables

You'll want to set your `SEPOLIA_RPC_URL` and `PRIVATE_KEY` as environment variables. You can add them to a `.env` file, similar to what you see in `.env.example`.

- `PRIVATE_KEY`: The private key of your account (like from [metamask](https://metamask.io/)). **NOTE:** FOR DEVELOPMENT, PLEASE USE A KEY THAT DOESN'T HAVE ANY REAL FUNDS ASSOCIATED WITH IT.
  - You can [learn how to export it here](https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key).
- `SEPOLIA_RPC_URL`: This is url of the sepolia testnet node you're working with. You can get setup with one for free from [Alchemy](https://alchemy.com/?a=673c802981)

Optionally, add your `ETHERSCAN_API_KEY` if you want to verify your contract on [Etherscan](https://etherscan.io/).

### 2. Get testnet ETH

Head over to [faucets.chain.link](https://faucets.chain.link/) and get some testnet ETH. You should see the ETH show up in your metamask.

### 3. Deploy

```
forge script script/DeployFundMe.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify --etherscan-api-key $ETHERSCAN_API_KEY
```

## Scripts

After deploying to a testnet or local net, you can run the following scripts:

### Fund
```
cast send <FUNDME_CONTRACT_ADDRESS> "fund()" --value 0.1ether --private-key <PRIVATE_KEY>
```

### Withdraw

```
cast send <FUNDME_CONTRACT_ADDRESS> "withdraw()"  --private-key <PRIVATE_KEY>
```

## Formatting


To run code formatting:
```
forge fmt
```


## Thank you, Cyfrin!

Big thanks to Cyfrin for providing free learning resources that allowed me 
to learn Foundry and Solidity development by doing this amazing project ❤️