# MyToken Smart Contract

MyToken is an ERC20-compliant token contract built using OpenZeppelin's ERC20 library. The token features include minting, burning, and transferring, with restrictions on minting beyond a defined maximum supply.

## Features
- **Minting Tokens**: Only the admin can mint new tokens, with a maximum supply limit enforced.
- **Burning Tokens**: Any token holder can burn their tokens to reduce the total supply.
- **Transferring Tokens**: Standard ERC20 token transfers are supported.

## Contract Details
- **Token Name**: `MyToken`
- **Symbol**: `MTK`
- **Maximum Supply**: `100,000 MTK`
- **Initial Supply**: Configurable during contract deployment.

## Functions

### `constructor(uint256 initialSupply)`
Initializes the contract with an initial supply of tokens minted to the deployer.

- **Parameters**:
  - `initialSupply` (uint256): The number of tokens to mint at deployment.

### `generateTokens(address recipient, uint256 amount)`
Allows the admin to mint new tokens and send them to a specified recipient.

- **Modifiers**:
  - `onlyAdmin`: Restricts access to the admin.
  - `mintLimit`: Ensures the total supply does not exceed `MAX_SUPPLY`.
- **Parameters**:
  - `recipient` (address): The address to receive the minted tokens.
  - `amount` (uint256): The number of tokens to mint.

### `transferCoins(address to, uint256 amount)`
Transfers tokens from the sender to a specified address.

- **Parameters**:
  - `to` (address): The recipient address.
  - `amount` (uint256): The number of tokens to transfer.

### `destroyTokens(uint256 amount)`
Allows a token holder to burn their own tokens, reducing the total supply.

- **Parameters**:
  - `amount` (uint256): The number of tokens to burn.

### Events
- `TokenMinted(address indexed recipient, uint256 amount)`: Emitted when tokens are minted.
- `TokenBurned(address indexed burner, uint256 amount)`: Emitted when tokens are burned.
