<!--
order: 5
-->

# Transactions

### MsgCreateClawbackVestingAccount
Defines a message that creates a ClawbackVestingAccount. The account to receive the funds can be an existing `ClawbackVestingAccount` in which case, the funds can be merged.

```protobuf
message MsgCreateClawbackVestingAccount {
  option (gogoproto.equal) = false;

  // from_address specifies the account to provide the funds and sign the
  // clawback request
  string from_address = 1;
  // to_address specifies the account to receive the funds
  string to_address = 2;
  // start_time defines the time at which the vesting period begins
  google.protobuf.Timestamp start_time = 3 [
    (gogoproto.stdtime) = true,
    (gogoproto.nullable) = false
  ];
  // lockup_periods defines the unlocking schedule relative to the start_time
  repeated cosmos.vesting.v1beta1.Period lockup_periods = 4 [
    (gogoproto.nullable) = false
  ];
 // vesting_periods defines thevesting schedule relative to the start_time
  repeated cosmos.vesting.v1beta1.Period vesting_periods = 5 [
    (gogoproto.nullable) = false
  ];
  // merge specifies a the creation mechanism for existing
  // ClawbackVestingAccounts. If true, merge this new grant into an existing
  // ClawbackVestingAccount, or create it if it does not exist. If false,
  // creates a new account. New grants to an existing account must be from the
  // same from_address.
  bool merge = 6;
}
```

### MsgClawback

Perfoms a clawback from the vesting account.

```protobuf
message MsgClawback {
  // funder_address is the address which funded the account
  string funder_address = 1;
  // account_address is the address of the ClawbackVestingAccount to claw back from.
  string account_address = 2;
  // dest_address specifies where the clawed-back tokens should be transferred
  // to. If empty, the tokens will be transferred back to the original funder of
  // the account.
  string dest_address = 3;
}
```