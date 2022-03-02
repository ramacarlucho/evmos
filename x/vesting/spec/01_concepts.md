<!--
order: 1
-->

# Concepts

The purpose of `vesting` module is to create and manage vesting accounts with Clawback option.

## ClawbackVestingAccount
ClawbackVestingAccount implements the VestingAccount interface. It provides an account that can hold contributions subject to  lockup" (like a PeriodicVestingAccount), or vesting which is subject to clawback of unvested tokens, or a combination (tokens vest, but are still locked).

### Clawback

The funder can claim back the coins that have not been vested