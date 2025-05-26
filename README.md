# Point-Rewarder

# Point-Rewarder

# 🏆 RewardContract

A Cairo 1.0 smart contract for StarkNet that manages a decentralized reward system using user point balances. This contract allows users to earn, claim, and transfer points securely, with event logging for transparency.

---

## 📄 Overview

The `RewardContract` provides a simple way to implement a user-based rewards or loyalty system directly on StarkNet. Each user is identified by their `ContractAddress`, and their point balances are stored and manipulated through safe and permissioned methods.

---

## ✨ Features

- ✅ **Add Points:** Admin or another contract can assign points to a user.
- ✅ **Claim Points:** Users can claim (burn or withdraw) a portion of their points.
- ✅ **Transfer Points:** Users can send points to other users.
- ✅ **Check Balance:** Anyone can query a user’s point balance.
- 📦 **Events:** Emitted for all point-related activities:
  - `PointsAdded`
  - `PointsClaimed`
  - `PointsTransferred`

---

## 🧩 Interface

```cairo
#[starknet::interface]
pub trait IRewardContract<TContractState> {
    fn add_points(ref self: TContractState, user: ContractAddress, points: u256);
    fn claim_points(ref self: TContractState, points: u256);
    fn transfer_points(ref self: TContractState, to: ContractAddress, points: u256);
    fn get_points(self: @TContractState, user: ContractAddress) -> u256;
}
