# Development Roadmap

## Development Schedule and Timeline
1. Stage 1 - Crowdsale Smart Contract (Completed) - 3 weeks
2. Stage 2 - Tag ID and Authenticator Smart Contract (In Progress) - 4 weeks
3. Stage 3 - Marketplace Smart Contract - 3 weeks
4. Stage 4 - Whoslux API - 4 weeks
5. Stage 5 - Whoslux App (Web/iOS/Android)
   - Stage 5.1 - WLX Wallet - 4 weeks
   - Stage 5.2 - Product Catalog - 4 weeks
   - --- ICO Ready ---
   - Stage 5.3 - Marketplace - 4 weeks
   - Stage 5.4 - Social Network - 3 weeks

## Stage 1 - Crowdsale Smart Contract (Completed) - 3 weeks
In order to get started with Initial Coin Offering (ICO), we need to build a Crowdsale Smart Contract. We will be following close to EOS model, and have already defined the strategies to be developed within the Crowdsale Smart Contract. We will define WLX Coin as a standard ERC-20.

## Stage 2 - Tag ID and Authenticator Smart Contract (In Progress) - 4 weeks
**Tag ID** will need the following:
 - NFC-enabled Tamperproof Tag
   - Type: ICODE SLIX
   - Memory: 896 bytes (need at least 32 bytes for private key)
   - Forum Type: Type 5 (https://nfc.today/learn/nfc-forum-type-5-icode-slix-isoiec-15693-vs-isoiec-14443)
 - QR code (need at least 20 bytes for encrypted public key)
 - Tag ID Generator
   - Key Generator
   - NFC Writer (Hardware)

**Authenticator Smart Contract** will need the following:
 - Network Authenticator Interface
   - DAO
   - WLX Support
 - WLXAG Token Generation (ERC-721)
   - IPFS Support
   - Interface with Tag ID (Signing)
 - Product Verification Framework
   - Interface with Tag ID (Verification)

## Stage 3 - Marketplace Smart Contract - 3 weeks
**Marketplace Smart Contract** will need the following:
 - Transfer Ownership Support
 - Escrow Service
 - Shipment Tracking (Oracle)
 - Interface with Authenticator Smart Contract for Verification

## Stage 4 - Whoslux API - 4 weeks
We will need to create several major components to allow the bridge between Ethereum and the real world:
 - Web3 API Integration
 - Shippo API Integration for Shipment Tracking (Oracle)
 - Delegated Transfer System (DTS) based on ERC-865
 - RESTful Authenticator Interface via DTS
 - RESTful Marketplace Interface via DTS

## Stage 5 - Whoslux App (Web/iOS/Android)
We're going to be building the Whoslux App, which will contain all the features for:
 - WLX Wallet
 - Product Catalog
 - Marketplace
 - Social Network

### Stage 5.1 - WLX Wallet - 4 weeks
The Wallet will be use Whoslux Core API to manage user information. Users will have the flexibility to trade WLX Coins with Bancor Network (buy/sell), also send/receive with any other wallet applications.

We will need to build:
- Whoslux Core API
  - P-II User Data (GDPR Compliance)
  - User Wallets (public and private key)
    - Extended wallet functionalities (trade, buy and sell)

### Stage 5.2 - Product Catalog - 4 weeks
Product Catalog will use the **Authenticator Smart Contract**, and will have features and functionalities to authenticate products.

Product Catalog will be built using:
 - Camera (IPFS integration)
 - RFID Reader API (works natively on iOS and Android)
 - RESTful Authenticator Interface

### Stage 5.3 - Marketplace - 4 weeks
Marketplace will use the **Marketplace Smart Contract**, and will have features and functionalities to buy, sell, trade, and provide safety features.

We will need to build:
- Whoslux Marketplace API
  - List Products for Sale
  - Buyer/Seller Ratings
  - Ban Users

### Stage 5.4 - Social Network - 3 weeks
Social Network will allow users to interact with one another, giving an opportunity to create a community around products.

We will build a place to allow users to share products and pictures.
