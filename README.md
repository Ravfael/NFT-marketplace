# NFT Marketplace

This project is a decentralized NFT Marketplace built with Solidity and Hardhat. It allows users to list ERC721 tokens for sale, buy them, update listings, and withdraw proceeds from sales.

## Features

The smart contract `NftMarketplace.sol` provides the following core functionalities:

*   **List Item**: Users can list their NFTs for sale by specifying the NFT contract address, token ID, and price.
*   **Buy Item**: Users can purchase listed NFTs by paying the specified price. The ownership of the NFT is transferred to the buyer, and the funds are stored for the seller.
*   **Cancel Listing**: Sellers can cancel their listings if they no longer wish to sell the NFT.
*   **Update Listing**: Sellers can update the price of their listed NFTs.
*   **Withdraw Proceeds**: Sellers can withdraw the funds they have earned from selling their NFTs.

## Tech Stack

*   **Solidity**: Smart contract programming language.
*   **Hardhat**: Ethereum development environment.
*   **Ethers.js**: Library for interacting with the Ethereum blockchain.
*   **OpenZeppelin**: Standard library for secure smart contracts (ERC721, ReentrancyGuard).

## Prerequisites

*   [Node.js](https://nodejs.org/)
*   [Yarn](https://yarnpkg.com/) or [npm](https://www.npmjs.com/)

## Installation

1.  Clone the repository:
    ```bash
    git clone <repository-url>
    cd nft-marketplace
    ```

2.  Install dependencies:
    ```bash
    yarn install
    ```

## Usage

### Compile Contracts

To compile the smart contracts, run:

```bash
yarn hardhat compile
```

### Deploy

To deploy the contracts to the local Hardhat network:

```bash
yarn hardhat deploy
```

### Run Tests

To run the tests:

```bash
yarn hardhat test
```

### Scripts

The project includes several scripts to interact with the deployed marketplace:

*   `scripts/mint-and-list-item.js`: Mints a basic NFT and lists it on the marketplace.
*   `scripts/buy-item.js`: Buys a listed item.
*   `scripts/cancel-item.js`: Cancels a listing.
*   `scripts/update-listing.js`: Updates the price of a listing.
*   `scripts/get-seller-proceeds.js`: Checks the proceeds of a seller.

To run a script (e.g., mint and list):

first run this one: yarn hardhat node

```bash
yarn hardhat run scripts/mint-and-list-item.js --network localhost
```

## Contract Details

### NftMarketplace.sol

This is the main contract that handles the marketplace logic. It uses `ReentrancyGuard` for security against reentrancy attacks.

*   **Mappings**:
    *   `s_listings`: Maps NFT address and Token ID to a `Listing` struct (price, seller).
    *   `s_proceeds`: Maps seller address to their earned proceeds.

*   **Events**:
    *   `ItemListed`
    *   `ItemCanceled`
    *   `ItemBought`

*   **Modifiers**:
    *   `notListed`: Ensures the item is not already listed.
    *   `isOwner`: Ensures the caller is the owner of the NFT.
    *   `isListed`: Ensures the item is listed.

## License

MIT
