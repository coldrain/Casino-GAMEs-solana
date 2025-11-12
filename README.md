# Solana Casino Games - Coinflip

A decentralized coinflip casino game built on Solana blockchain using Anchor framework.

## Overview

This project implements a coinflip (heads/tails) casino game on Solana. Players can bet SOL and have a chance to win based on slot-based randomness. The game includes different bet amounts with varying win probabilities.

## Features

- **Coinflip Gameplay**: Players choose heads (1) or tails (0) and bet SOL
- **Multiple Bet Amounts**: 
  - 0.05 SOL / 0.1 SOL: 47.5% win rate
  - 0.25 SOL / 0.5 SOL: 40% win rate
  - 1 SOL: 25% win rate
  - 2 SOL: 16.67% win rate
- **Loyalty Fee**: 3% fee on each bet goes to the loyalty wallet
- **Reward System**: Winners can claim their rewards after playing
- **Admin Controls**: Admin can withdraw funds and update settings

## Program Structure

### Main Functions

- `initialize`: Initialize the global authority and reward vault
- `initialize_player_pool`: Create a player pool account for a new player
- `play_game`: Main game function where players place bets
- `claim_reward`: Claim winnings after a successful game
- `update`: Update loyalty fee and wallet (admin only)
- `withdraw`: Withdraw SOL from the reward vault (admin only)

### Accounts

- **GlobalPool**: Stores global game state (admin, loyalty wallet, fees, total rounds)
- **PlayerPool**: Stores individual player data (games played, wins, rewards)
- **RewardVault**: PDA that holds the game's SOL reserves

## Technology Stack

- **Anchor**: 0.29.0
- **Solana Program**: 1.18.12
- **Rust**: Edition 2021

## Setup

### Prerequisites

- Rust and Cargo
- Anchor framework
- Node.js and Yarn
- Solana CLI

### Installation

1. Clone the repository
2. Install dependencies:
   ```bash
   yarn install
   ```

3. Build the program:
   ```bash
   anchor build
   ```

4. Run tests:
   ```bash
   anchor test
   ```

## Configuration

The program is configured for Solana Devnet by default. Update `Anchor.toml` for different networks.

- **Program ID**: `3Sh6Wrj72E7CUJ9EV5g4KPLEo69sxDs6gPZXZd2Tawx1`
- **Loyalty Wallet**: `SERVUJeqsyaJTuVuXAmmko6kTigJmxzTxUMSThpC2LZ`
- **Loyalty Fee**: 3% (30 per mille)

## Game Mechanics

The game uses Solana's slot number for randomness:
- The slot number modulo 2 determines heads (1) or tails (0)
- Additional conditions based on bet amount determine win probability
- Winners receive 2x their bet amount (minus fees)

## Security

- Access control ensures only authorized players can play and claim
- Admin-only functions for withdrawals and updates
- Validation checks for sufficient balances
- Instruction sysvar checking to prevent unauthorized claims

## Contact

**Telegram**: [https://t.me/BlackSky_jose](https://t.me/BlackSky_jose)

**Twitter**: [https://x.com/BlackSky_jose](https://x.com/BlackSky_jose)

## License

This project is provided as-is for educational and development purposes.

