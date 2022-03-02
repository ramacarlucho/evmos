<!--
order: 2
-->

# State

`ClawbackVestingAccounts` are initialized as part of genesis initialization, but can also be created and merged with existing accounts.

### Clawback information type

```protobuf
message ClawbackVestingAccount {
  option (gogoproto.goproto_getters)  = false;
  option (gogoproto.goproto_stringer) = false;

  cosmos.vesting.v1beta1.BaseVestingAccount base_vesting_account = 1 [
    (gogoproto.embed) = true
  ];
  string funder_address = 2;
  google.protobuf.Timestamp start_time = 3 [
    (gogoproto.stdtime) = true,
    (gogoproto.nullable) = false
  ];
  repeated cosmos.vesting.v1beta1.Period lockup_periods = 4 [
    (gogoproto.nullable) = false
  ];
  repeated cosmos.vesting.v1beta1.Period vesting_periods = 5 [
    (gogoproto.nullable) = false
  ];
}
```

ClawbackVestingAccount keeps `base_vesting_account`, `funder_address`, `start_time`, `lockup_periods`, `vesting_periods`.

1. `base_vesting_account` contains all the necessary fields needed for any vesting account implementation.
2. `funder_address` specifies the account which can perform clawback.
3. `start_time` defines the time at which the vesting period begins.
4. `lockup_periods` defines the unlocking schedule relative to the start_time.
5. `vesting_periods` defines the vesting schedule relative to the start_time.



