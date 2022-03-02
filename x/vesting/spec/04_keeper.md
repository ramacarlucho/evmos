<!--
order: 4
-->

# Keepers

## Keeper functions

Epochs keeper module provides functions perform a clawback.

```go
// Keeper is the interface for lockup module keeper
type Keeper interface {
  // Clawback removes the unvested amount from a ClawbackVestingAccount.
  // The destination defaults to the funder address, but can be overridden.
  Clawback(context.Context,*types.MsgClawback) (*types.MsgClawbackResponse, error)
  
  // Delegation ?

}
```