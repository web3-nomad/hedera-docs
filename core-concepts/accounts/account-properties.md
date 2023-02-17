# Account Properties

One Hedera account can be represented by several account addresses. Not all account addresses have the same capabilities when working with Hedera transactions and query requests.

<table data-view="cards"><thead><tr><th align="center"></th></tr></thead><tbody><tr><td align="center"><strong>Account ID</strong></td></tr><tr><td align="center"><strong>Account ID Long Format</strong></td></tr><tr><td align="center"><strong>Account ID Long Zero</strong></td></tr><tr><td align="center"><strong>Ethereum Public Address</strong></td></tr></tbody></table>

#### **Account ID**

Each Hedera account has an **account ID**. The **account ID** is the ID of the account entity that was created by the network. The account entity ID format is `shardId.realmId.accountNumber`. You can use this account ID to specify the account in all Hedera transactions and query requests. The account ID is **immutable** and cannot be changed. The network auto-increments the entity ID as new ones are created. The account ID for a newly created account is returned in the receipt and record confirmations of the transaction.

| Property           | Description                                                                                                                                                                                                                                                                                           | Example    |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| **Shard**          | A shard is a partition of the data received by the nodes that participate in a given shard. The shard ID is the value that represents the shard the account exists in. Today, Hedera operates in only one shared. This value is zero and will remain zero until Hedera operates in more than 1 shard. | **0**.0.10 |
| **Realm**          | The realm ID is the ID of the realm the account exists in within a given shard. Hedera operates in only one realm today. This value is zero and will remain zero until Hedera operates in more than 1 realm.                                                                                          | 0.**0**.10 |
| **Account Number** | The account number is a non-negative number.                                                                                                                                                                                                                                                          | 0.0.**10** |

####
