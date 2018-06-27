# Concept Definition

## Goods Authentication Blockchain

Whoslux is a blockchain implementation that focuses on creating unique identifier for authenticated goods. Luxury goods, or any other authentic goods, are prone to forgery, and require "special attention" in identification. This creates a middle market in the economy, where used luxury goods are sent to the authenticator intermediary company, where they validate and verify the goods before shipping them. The markup is anywhere between 50%~80% depending on the supply and demand. This market alone is currently $120 Billion in the world.

Our primary concept used in our blockchain implementation utilizes a combination of Smart Contracts, and a RESTful interface to fit the growing demand of resale luxury economy.

# How Does It Work?

Series of Smart Contracts that focuses on creating interfaces for authenticating goods.

## Authenticator Smart Contract

The Authenticator Smart Contract utilizes P2P-based authentication system based on image recognition and voting system. When a user wants to authenticate the goods, they pass in WLX and product attributes, which is sent to the Community Authenticators.

Each community authenticator member has the folder address in IPFS, where user uploads images for them to see. After authentication is complete, the community authenticator member casts a vote. Community Authenticators follow a system which forces individual members into voting, or risk stopped payment, where each member of the community can cast a vote to *Reject* or *Accept*. The vote reaches a concensus (80%) of *Accepted* then the product is *Accepted*.

Community Authenticators generate a seal of approval on the item, and the item is now autenticated. Attributions are assigned to the proper owner.

  - For each of the good (to be authenticated)
    - Create a Unique Product Identifier (ETH, WLX, Attributes = {}, State = "Created")
      - Create a folder on a unique IPFS address
      - Show User -> (id, ipfs)
      - Apply Verification (ETH, id, attributes, community, ipfs, State = "Pending or Failed") -> (True/False [based on initial validation])
    - Community Authenticators
      - Receive (WLX, id, ipfs, State = "Pending")
      - Reject (ETH, id, community, State = "Rejected")
      - Approve (ETH, id, community, State = "Accepted")
  - Authenticated Goods
    - Attribute to User (id)

## Marketplace Smart Contract

Marketplace Smart Contract is designed to help users identify and validate the goods, as well as make transactions safely and securely. The digital asset (Attribution to Authenticated Good) transfers to a new user, Blockchain ensures us that transaction is recorded and immutable.

  - For each of the good (already authenticated)
    - Send Product (ETH, user_id, recipient_id, product_id) -> (True/False)
  - To sell a product
    - Create Transaction (ETH, WLX = "Price", user_id, product_id) -> Transaction ID
    - Purchase (ETH, WLX, transaction_id, user_id) -> (True/False, State = "Pending", Purchase ID)
    - Status (ETH, State = ["Shipped", "Received", "Completed"], purchase_id, user_id)
  - To trade a product
    - Create Trade (ETH, user_id, recipient_id)
    - Item (ETH, action = ["Post", "Unpost"], trade_id, user_id, WLX, product_id)
    - Accept Trade (ETH, trade_id, user_id)
    - Reject Trade (ETH, trade_id, user_id)

### Scenarios and Use Cases

Luxury Fashion Brand XYZ wishes to create digitally authenticated signatures for each of their manufactured good. XYZ Brand becomes a Community Authenticators and pre-authenticate their products for fighting physical fake goods. Proof of ownership can be proven with a Blockchain ledger.

Limited Edition Toy User-managed Community has some of the top authenticators. The community becomes a Community Authenticators, and help strengthen limited edition toy market.

#### Different Seals, Different Price, and Different Quality

Seals can carry different weight, and having proper seals can affect the resale value. Seals that are higher priced, higher quality will cost more, but benefit can always outweigh the costs.

# Whoslux (Web/iOS/Android) App

Whoslux App will be broken down into four major sections.
  
  1. WLX Wallet
  2. Product Catalog
  3. Community Network
  4. Community Marketplace

## WLX Wallet

The app will have an interface to buy, sell, trade WLX tokens. The Wallet reflects the balance of WLX, which can be spent for trades and marketplace.

## Product Catalog

Product Catalog section is designed to help user authenticate, trade, and sell. The users can share their Catalog to other members, since they are public in the Blockchain.

## Community Network

Users can join our opt-in community, which links your catalog to your public profile. Our Community Network is ran and managed by Whoslux Team, for better usability and communication.

## Community Marketplace

Community members can participate in the Marketplace, which is a decentralized resale marketplace. The platform will be run as a Smart Contract, providing transparent rules. Trades can take place from the app, and will have trading interface.

# Whoslux API and Developer Community

Whoslux is a technology provider, providing safe, reliable, and transprent service is in our mission. Our goal is to empower the developer community with open source and services.

## Open-Source Smart Contracts

Whoslux Smart Contracts will be managed by the open source community, will receive WLX contributions from Whoslux Team.

## REST API + SDKs

Whoslux will provide a REST API for Product Catalog, allowing the community to contribute with different experiences.

Whoslux will provide mobile SDKs (iOS and Android) for WLX Wallet integration, help bridge in-app transactions with ease.

# Estimated Development Timeline

## Initial Planning, Exploration and Early Development Stage: 2 ~ 4 Weeks

We will start the development of the Smart Contracts, and begin creating core interface for the platform.

## Core Platform Development: 8 ~ 10 Weeks

Core Platform will create the bridge for Smart Contracts, exposing REST API.

## Community Platform Development: 8 ~ 10 Weeks

Community Platform will also create identity services, hosted outside of Blockchain in order to provide seamless experience.

## Marketplace Platform Development: 8 ~ 10 Weeks

Marketplace Platform will have necessary tools to provide secure and reliable transactions.

## Mobile App Development: 8 ~ 10 Weeks

Mobile App will be built with React Native, with reusable components in JavaScript.




