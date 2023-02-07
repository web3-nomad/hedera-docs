# ContractDelete

## **ContractDeleteTransactionBody**

Delete a smart contract.

| Field                | Type                                                             | Description                                                |
| -------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------- |
| `contractID`         | [ContractID](../../../docs/hedera-api/basic-types/contractid.md) | The Contract ID instance to delete (this can't be changed) |
| `obtainers`          |                                                                  |                                                            |
| **one of:**          |                                                                  |                                                            |
| `transferAccountID`  | [AccountID](../../../docs/hedera-api/basic-types/accountid.md)   | The account ID which will receive all remaining hbars      |
| `transferContractID` | [ContractID](../../../docs/hedera-api/basic-types/contractid.md) | The contract ID which will receive all remaining hbars     |
