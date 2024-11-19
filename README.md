# Bitcoin Ordinal Auction

A decentralized auction platform built on top of Bitcoin Ordinals. The auction facilitates the exchange of Bitcoin Ordinals, utilizing the latest technologies to provide a secure and efficient process. This platform supports auctions for Ordinals using Bitcoin's PSBT, UTXO, and WebSocket protocols for seamless operation.

## Features

- **Bitcoin Ordinals**: Auctioning Bitcoin Ordinals (unique satoshis with metadata) using the Ordinals protocol.
- **PSBT**: Partially Signed Bitcoin Transactions to enable multi-party signing for secure transaction creation.
- **UTXO**: Uses Unspent Transaction Outputs for transaction management and bid settlement.
- **WebSocket**: Real-time communication for bid updates, auction status, and other events.

## How It Works

The Bitcoin Ordinal Auction leverages several core components:

### 1. **PSBT (Partially Signed Bitcoin Transactions)**

PSBTs allow for multi-party signing, enabling users to participate in auctions without the need to fully sign transactions themselves. This enhances security by allowing bids and transactions to be prepared and signed incrementally before finalizing. Here's how PSBT is used in the auction:

- Each bid creates a new PSBT that includes the auction participant's offer.
- PSBTs are shared among parties for incremental signing and validation.
- Once the transaction reaches a consensus (all necessary parties have signed), the final transaction is broadcasted to the Bitcoin network to settle the auction.

This method ensures that bids are secure and transactions are only finalized when all parties are in agreement.

### 2. **UTXO (Unspent Transaction Output)**

The auction platform uses the concept of **UTXOs** to handle transactions and bids. A UTXO is essentially an unspent output from a previous Bitcoin transaction. In this platform:

- Each participant in the auction can create bids by referencing available UTXOs they own.
- The UTXOs are tracked, and the platform ensures that bids are placed using unspent outputs that are valid for the auction.
- The final settlement transaction, once the auction ends, is built using the UTXOs from the winning bid.

Using UTXOs guarantees that the platform operates with Bitcoin's native mechanism for transaction validation and ensures that funds are correctly accounted for.

### 3. **WebSocket** 

WebSockets are used to enable real-time communication between the auction platform and participants. This provides a seamless experience where users are instantly notified about the status of the auction, new bids, and other events. Key features include:

- **Real-time updates**: Participants receive immediate updates when bids are placed or when auction statuses change (e.g., bid won, auction ended).
- **Interactive bidding**: Participants can place bids interactively and see the updated status of the auction in real-time without needing to refresh the page.
- **Push notifications**: For key events such as auctions ending or bids being outbid.

WebSockets allow the auction to be more interactive and user-friendly by eliminating delays in bid processing.

## Getting Started

### Prerequisites

- **Node.js** and **npm** for backend development.
- A Bitcoin full node or access to a Bitcoin node that supports PSBTs and UTXO management.
- WebSocket server for real-time bid updates.

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/bitcoin-ordinal-auction.git
   cd bitcoin-ordinal-auction
