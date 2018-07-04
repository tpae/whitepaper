# WLX Coin

## ERC20 - Distributable Token

WLX Coins will be issued according to `ERC20` [1](https://github.com/ethereum/EIPs/issues/20) Standard, which has all the necessary components required to have a successful token distribution. `ERC20` also enables us to interface with other existing `ERC20` Tokens, providing flexibility where it's required.

## ERC865 - Delegated Transfers

We will implement experimental features from `ERC865` [1](https://github.com/ethereum/EIPs/issues/865), which allows delegated transfers that help facilitate token transfers without needing gas. The orders are triggered on off-chain relays, which will execute our smart contract with signed verifiable payload, and will transfer tokens from source to destination.

In order to increase the adoption of our Coins through our mobile app, `ERC865` will reduce the barrier of entry for our users. They will not be required to purchase or own ether, but they will be required to use our WLX Wallet App.

Our WLX Wallet App will be a custom implementation of a wallet, which will have the functionality to sign delegated transfers and trigger off-chain relay to be executed on the blockchain.

### 0x Protocol

Delegated transfers requires a delegate, which will require our Delegate to have access to pool of ETH to facilitate the trade. We can interface with 0x Protocol [1](https://0xproject.com/), which will allow us to execute trades on-chain, interface with our DApp to automate the exchange end-to-end.

### End-to-End Transaction with Only WLX Coins

Using `ERC865` features, we can successfully execute end-to-end transactions without needing gas.

1. `User A` to send `1 WLX` to `User B`
2. `User A` executes off-chain function `transferPreSigned` on `Delegate`
3. `Delegate` verifies `signedPayload` from `User A`
4. `Delegate` executes transfer of `WLX (fee)` from `User A` to `User B` with gas from `DelegateAccount`
5. `Delegate` executes `trade` of `fee` on `0xProtocolExchange` for `ETH` to `DelegateAccount`
6. `DelegateAccount` is replenished for additional transactions

The `fee` will need to be calculated (WLX <> ETH value) prior to executing `transferPreSigned` and should be enough to cover gas price of 2 separate transactions needed to create end-to-end transaction.

# WLXAG Token

Whoslux ecosystem will require interactions with two different tokens, WLX coin is necessary to facilitate the transfer of value across the platform, and WLXAG token is necessary to create transferrable object that represents the Authenticated Good.

## ERC721 - Non-Fungible Token

WLXAG Token will be issued according to `ERC721` Standards for Non-Fungible Tokens, with attributes assigned to each token to represent ownership, Community Authenticator address, goods identifier, and IPFS [1](https://ipfs.io/) address to hold assets and additional metadata.

## Community Authenticators

Each WLXAG Token is issued by the Community Authenticator (CA), and they hold a unique address which can be used to verify the seal of authenticity of the authenticated good. CA's primary objective is to authenticate the goods, in exchange for a fee in WLX.

### Decentralized Autonomous Organization (DAO)

CAs will operate under DAO, with rules defined during the creation of the CA. CAs will have the ability to add/remove members, change authentication consensus, set fee price, payment distribution amongst members, partial refund amount, and manage issued WLXAG Tokens.

CAs will have the authority to revoke issued WLXAG Tokens when necessary. Revoked Tokens will be prevented from circulation. CAs will also have the authority to reinstate revoked Tokens, giving granular control over it's authenticated goods.

CAs can also define validation rules, which will be used to filter incoming authentication requests.

### Issuing WLXAG Tokens

CAs will interface with `Authenticator Smart Contract`, which contains all of necessary functions to issue WLXAG Tokens using WLX Coin.

#### Authenticator Smart Contract

The Authenticator Smart Contract utilizes P2P-based authentication system based on photo recognition and consensus voting system. When a user wants to authenticate the goods, they submit WLX Coin and product metadata, which is available for execution by the CAs.

Authenticator Smart Contract will create an address in IPFS, where user can upload assets and verifiable proofs for CAs to use for authentication.

```
  - For Each Goods (to be authenticated)
    - Authenticate Goods that Pass Initial Validation Criteria (Owner Address, Authentication Fee in WLX, CA Address, IPFS Address, Product Attributes)
    - CA Members
      - Approve Authentication (Pre-authenticated Goods Address)
      - Reject Authentication (Pre-authenticated Goods Address)
  - Approved Authenticated Goods (Reaches Pre-defined Consensus)
    - Issue WLXAG Token (Owner Address, CA Address, IPFS Address, Product Attributes)
    - Distribute Fees to CA Members (CA Address, WLX)
  - Reject Authenticated Goods
    - Issue Partial Refund of Fees (Owner Address, WLX)
```

## Token Features

WLXAG Tokens are non-fungible in nature. They have an authentication authority (CAs), which issues a seal of authentication that is freely interchangeable among users. CAs will have control over the issued WLXAG Tokens, including total number of supply, and are encouraged to maintain the quality of their authenticated goods.

Blockchain also introduces immutability and transparency, with open ledger support for every transaction. WLXAG Tokens offer trust to both parties (buyer and seller) in a transaction, as long as both parties can agree to trust CAs issuing the token. WLXAG Tokens also provide traceability, can follow history of transactions to further verify it's authenticity.

### Trading

WLXAG Tokens can be traded across the platform, and each token represent a authentication seal for the physical goods. WLXAG Tokens can interface with `Marketplace Smart Contract` which provides features for facilitating safe trading.

#### Marketplace Smart Contract

The Marketplace Smart Contract contains features that allows trading on the platform. Marketplace Smart Contract helps facilitate safe trading, with several features to protect both the buyer and the seller.

The basis of the smart contract revolves around a simple feature to transfer ownership.

```
  - Transfer Ownership (WLXAG, Recipient Address)
```

##### Selling a Product to a Trusted User

```
  - Selling a Product to a Trusted User
    - [Seller] List Product for Sale to a User (WLXAG, Buyer Address, Price of Goods in WLX)
    - [Buyer] Pay for Product (WLXAG, WLX)
      - [Seller] Receives WLX
    - [Seller] Transfer Ownership (WLXAG, Buyer Address)
      - [Buyer] Receives WLXAG
```

##### Selling a Product to an User with Trusted Third-party Authorizer

Sometimes we require a third-party to be involved in facilitating the trade. Third-party Authorizers can help verify the transaction on behalf of the buyer and seller, and provide authorization to finalize the trade.

As an example, Third-party Authorizers could be another smart contract that checks shipping tracking number, or a reputable marketplace facilitator that can help resolve disputes.

```
  - Selling a Product to an User with Trusted Third-party Authorizer
    - [Seller] List Product for Sale to a User (WLXAG Token, Buyer Address, Authorizer Address, Authorizer Fee, Price of Goods in WLX)
    - [Buyer] Pay for Product (WLXAG Token, WLX)
    - [Authorizer] Authorize Trade (WLXAG Token)
      - [Seller] Receives WLX
      - [Seller] Transfer Ownership (WLXAG, Buyer Address)
      - [Authorizer] Receives WLX (Fee)
```

##### Listing a Product for Sale with Seller's Approval for Sale

Sellers may choose to list a Product for sale, with a set price, and can authorize execution of the trade. This will require Buyer's interest to pay for the Product. Upon execution from the Seller, items are traded instantly.

There can be multiple offers for the same product, and Seller will decide the Buyer.

```
  - Listing a Product for Sale with Seller's Approval for Sale
    - [Seller] List Product for Sale (WLXAG Token, Price of Goods in WLX)
    - [Buyer] Place Order for Product (WLXAG Token, WLX)
    - [Seller] Accept Order for Product (WLXAG Token, Buyer Address)
      - [Seller] Receives WLX
      - [Seller] Transfer Ownership (WLXAG, Buyer Address)
```

##### Listing a Product for Sale with Trusted Third-party Authorizer

Sellers may choose a Third-party Authorizer to give authority to execute the trade.

```
  - Listing a Product for Sale with Trusted Third-party Authorizer
    - [Seller] List Product for Sale (WLXAG Token, Authorizer Address, Authorizer Fee, Price of Goods in WLX)
    - [Buyer] Place Order for Product (WLXAG Token, WLX)
    - [Authorizer] Authorize Trade (WLXAG Token)
      - [Seller] Transfer Ownership (WLXAG, Buyer Address)
      - [Buyer] Receives WLXAG
      - [Authorizer] Receives WLX (Fee)
```
