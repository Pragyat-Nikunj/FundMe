# FundMe Smart Contract Project

A secure, gas-efficient Ethereum smart contract for decentralized crowdfunding, built with [Foundry](https://book.getfoundry.sh/) and Chainlink price feeds. This project demonstrates best practices in Solidity development, automated testing, and deployment scripting.

## Deployed Contract

- **Sepolia:** [Etherscan](https://sepolia.etherscan.io/address/0x23f21e45c9642012db04977fe63d0b5830477fc0#code)

## Features

- **FundMe Contract:**  
  - Accepts ETH contributions from users.
  - Enforces a minimum USD value per contribution (using live Chainlink price feeds).
  - Tracks funders and their contributions.
  - Only the contract owner can withdraw funds.
  - Includes gas-optimized withdrawal logic.

- **Automated Deployment & Interaction Scripts:**  
  - Deploy contracts to any EVM-compatible network.
  - Fund and withdraw from the contract via scripts.

- **Comprehensive Testing:**  
  - Unit and integration tests using Foundry.
  - Mock price feeds for local testing.

## Directory Structure

```
src/         # Solidity contracts
script/      # Deployment and interaction scripts
test/        # Unit and integration tests
test/mocks/  # Mock contracts (e.g., Chainlink price feed)
```

## Prerequisites

- [Foundry](https://book.getfoundry.sh/getting-started/installation)
- Node.js (for npm dependencies)
- RPC URL and private key for deployment to testnets/mainnet

## Getting Started

### 1. Install Dependencies

```sh
forge install
```

### 2. Build Contracts

```sh
forge build
```

### 3. Run Tests

```sh
forge test
```

### 4. Deploy Contracts

Update your RPC URL and private key as needed.

```sh
forge script script/DeployFundMe.s.sol:DeployFundMe --rpc-url <YOUR_RPC_URL> --private-key <YOUR_PRIVATE_KEY> --broadcast
```

### 5. Interact with Contracts

Fund the contract:

```sh
forge script script/Interactions.s.sol:FundFundMe --rpc-url <YOUR_RPC_URL> --private-key <YOUR_PRIVATE_KEY> --broadcast
```

Withdraw funds (owner only):

```sh
forge script script/Interactions.s.sol:WithdrawFundMe --rpc-url <YOUR_RPC_URL> --private-key <YOUR_PRIVATE_KEY> --broadcast
```

## Testing

- **Unit Tests:** Located in `test/unit/`
- **Integration Tests:** Located in `test/integration/`
- **Mocks:** Located in `test/mocks/` for simulating Chainlink price feeds.

## Configuration

- **HelperConfig:** Automatically selects the correct price feed for the current network or deploys a mock for local testing.

## Security

- Only the contract owner can withdraw funds.
- Uses Chainlink oracles for reliable price data.
- Includes thorough test coverage.

## License

This project is licensed under the MIT License.
