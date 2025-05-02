# sfUSD Proposal

## 1. Objective
We need to implement the sfUSD protocol, with the following features:

Implementation of the sfUSD protocol including the ERC20 token contract with a weight-based reward distribution mechanism based on staking 
Comprehensive testing suite and NatSpec documentation for all Smart Contracts
UI Dashboard for users to monitor and interact with the sfUSD system


## 2. Scope of work
## 2.1. Protocol Implementation 
- The sfUSD protocol will be implemented as a yield-generating RWA token system with the following components:
- Implementation of an ERC20 token with an upgradeable proxy pattern
- Integration with a coefficient-based reward distribution system
- Support for automatic unstacking upon token transfer
- Implementation of permit functionality for gasless approvals
- The core of the system is a coefficient-based reward distribution system that tracks user weight accumulation over time to distribute rewards proportionally. Users receive a sfUSD token, which they can stake to begin receiving rewards. When users transfer tokens, if needed, a portion of them will be automatically unstaked. The rewards will be paid in the USDC token.

The reward distribution will be based on the following formulas:
![SmartContractCalculations2](https://github.com/user-attachments/assets/6d90379b-c657-4841-a28c-1ed89b6e18e4)

![SmartContractCalculation2](https://github.com/user-attachments/assets/31e94e9f-7e52-436a-8e14-2da8b78dd001)


Where:
- target_apy_basis_points is the target annual percentage yield in basis points (1500 for 15%)
- precision is a scaling factor to prevent rounding errors
- b_u is the token balance of user u
- w_u is the accumulated weight for user u
- a is the amount of reward tokens being distributed
- c_w,total and c_r,total are the global weight and reward coefficients

The core idea is to keep track of user actions to be able to distribute rewards with O(1) complexity.

The staking mechanism will be as follows:
- Users will receive sfUSD tokens, which they can stake to start accumulating rewards
- When users transfer tokens, if needed, the portion of them or all will be automatically unstaked.
- Users must explicitly stake their tokens to resume reward accumulation.

This approach ensures that tokens held on DEXes like Uniswap don't receive rewards.

## 2.2. Testing and Documentation
- Implementation of comprehensive unit tests for all contract functions
- Integration tests simulating real-world usage scenarios
- NatSpec documentation for all functions and public variables
- External documentation explaining the mathematical model

## 2.3. UI Dashboard
- The UI dashboard will provide users with a comprehensive interface to interact with the sfUSD protocol with the following features:
- Wallet connection (MetaMask, WalletConnect, etc)
- Account overview showing sfUSD balance
- Real-time display of accumulated rewards
- Interface for staking and unstacking tokens
- Claim rewards functionality
- System statistics (total supply, total staked, current APY, etc.)

## 3. Deliverables
We will provide the following:
- Smart contract repositories with all implementations described above
- Unit and integration tests for all smart contracts
- Deployment scripts for all contracts across test and mainnet environments
- Complete NatSpec documentation for all contracts
- UI Dashboard source code and deployment instructions
- Comprehensive user and developer documentation
