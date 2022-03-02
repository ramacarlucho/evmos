<!--
order: 0
title: "Vesting Overview"
parent:
  title: "vesting"
-->

# `vesting`

## Abstract

The `x/vesting` module manages the vesting account logic.

Vesting account can be defined at genesis or created on a later date with a `NewClawbackVestingAccount` transaction.

A vesting account may be initialized with a vesting start time `ST` and a number of vesting periods `P`, and locking period `L`. The vesting and locking periods will not begin until start time is reached. If vesting periods are included, the vesting will occur over the specified number of periods. If locking periods are included, each period will unlock the defined amount of coins to the account.

For all vesting accounts, the owner of the vesting account is only able to delegate and undelegate from validators once the coins have been vested. 
They cannot transfer coins to another account until those coins are vested and unlocked and they cannot interact with the `evm` while it still has locked coins.

## Contents

1. **[Concept](01_concepts.md)**
2. **[State](02_state.md)**
3. **[Events](03_events.md)**
4. **[Keeper](04_keeper.md)**
5. **[Transactions](05_transactions.md)**
6. **[Queries](06_queries.md)**
