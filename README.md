# 🛒 MarketPlaceFlo – Decentralized NFT Marketplace (ERC-721)

## 📌 Description
**MarketPlaceFlo** is a Solidity smart contract that enables secure, on-chain peer-to-peer trading of NFTs using Ether on any EVM-compatible blockchain. Fully compatible with all **ERC-721** collections, it allows users to list, purchase, and delist NFTs directly through the contract with no intermediaries.

Built on top of **OpenZeppelin's** trusted libraries, follows industry best practices for smart contract development, ensuring secure and maintainable code. It has been rigorously tested using **Foundry**, covering core functionality and edge cases to guarantee reliability and protection against common vulnerabilities.

---

## 🚀 Features

| **Feature** | **Description** |
|------------|-----------------|
| 🧱 **ERC-721 Support** | Works with any collection that implements the ERC-721 standard. |
| 📝 **NFT Listing** | Users can list their NFTs with a specified price in Ether. |
| 💰 **Purchase with Ether** | Buyers can purchase listed NFTs by sending the exact price. |
| ❌ **Cancel Listings** | Sellers can cancel their listings at any time. |
| 🔒 **Reentrancy Protection** | Secured with `ReentrancyGuard` to prevent reentrancy attacks. |

---

## 📜 Contract Details

### 🏗️ Constructor

| **Component** | **Description** |
|---------------|-----------------|
| `constructor(address owner)` | Initializes the contract by transferring ownership to the specified `owner` address. This enables access control over owner-only functions using OpenZeppelin's `Ownable` module. |

### 📡 Events

| **Event** | **Description** |
|----------|-----------------|
| `NFTListing(address seller, address nftAddress, uint256 tokenId, uint256 price)` | Emitted when an NFT is listed for sale. |
| `cancelNFT(address seller, address nftAddress, uint256 tokenId)` | Emitted when a listing is canceled. |
| `NFTSold(address buyer, address seller, address nftAddress, uint256 tokenId, uint256 price)` | Emitted when an NFT is sold. |

### 🔧 Functions

| **Function** | **Description** |
|-------------|------------------|
| `listNFT(address nftAddress, uint256 tokenId, uint256 price)` | List an NFT with a given price. |
| `buyNFTEther(address nftAddress, uint256 tokenId)` | Purchase a listed NFT by paying the exact price. |
| `cancelList(address nftAddress, uint256 tokenId)` | Cancel an existing listing (only callable by the seller). |

---

## 🧪 Testing with Foundry

The contract has been thoroughly tested using **Foundry**. The test suite covers core functionality, access control, and edge cases.

### ✅ Implemented Tests

| **Test** | **Description** |
|----------|------------------|
| `testMintNFT` | Verifies correct NFT minting in the mock contract. |
| `testPriceZero` | Ensures NFTs cannot be listed with a price of zero. |
| `testNotNFTOwner` | Prevents users who don't own the NFT from listing it. |
| `testListNFT` | Verifies successful listing of NFTs. |
| `testCancelNotOwner` | Ensures only the original lister can cancel a listing. |
| `testCancelListing` | Verifies listings are removed after cancellation. |
| `testBuyUnlistedNFT` | Ensures unlisted NFTs can't be purchased. |
| `testBuyIncorrectPrice` | Ensures purchase fails if price doesn't match. |
| `testBuyNFT` | Full test of the buy flow, including NFT and ETH transfer. |

### 🧪 How to Run Tests

To run the test suite with Foundry:

```bash
forge test

### 📊 Coverage Report

| File                    | % Lines         | % Statements     | % Branches      | % Functions     |
|-------------------------|------------------|-------------------|------------------|------------------|
| `src/MarketPlaceFlo.sol` | 100.00% (21/21) | 100.00% (20/20) | 91.67% (11/12) | 100.00% (3/3)   |

> 🔍 **Note**: Coverage is not 100% for branches due to one specific edge case — the branch that reverts with `"Transaction Error"` on failed Ether transfers. Simulating that revert requires a test using a contract that intentionally rejects Ether. 

---

## 📄 License

This project is licensed under the **MIT License**. Feel free to use and modify it for your own needs.

---
