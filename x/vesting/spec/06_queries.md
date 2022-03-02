<!--
order: 6
-->

# Queries

Vesting module provides queries to check the module's state.

```protobuf
service Query {
    // Retrieves the unvested, vested and locked tokens for a given vesting account
  rpc Balances(QueryBalancesRequest) returns (QueryBalancesResponse) {}
}
```