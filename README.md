# 🛒 MarketPlaceFlo

## 📌 Description
**MarketPlaceFlo** is a Solidity-based smart contract that enables users to list, buy, and cancel NFTs using Ether. Compatible with any ERC-721 collection, this marketplace allows secure peer-to-peer trading.

The contract is built using **OpenZeppelin** for security and best practices, and has been thoroughly tested with **Foundry**.

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

---

## 🛠️ How to Use

### 🔧 Prerequisites

- Install **Foundry**: [Installation Guide](https://book.getfoundry.sh/)
- Have a compatible Ethereum wallet (e.g., MetaMask).
- Acquire testnet ETH for testing/deployment (e.g., Goerli, Sepolia).

### 🚀 Deployment Steps

1. Clone the repository.
2. Navigate to the project directory.
3. Install dependencies (if applicable).
4. Run tests using `forge test`.
5. Deploy the contract using Foundry or your preferred deployment tool.

---

## 📄 License

This project is licensed under the **MIT License**. Feel free to use and modify it for your own needs.

---
