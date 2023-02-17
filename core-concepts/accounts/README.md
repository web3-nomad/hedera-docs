---
description: Hedera accounts
---

# Accounts

Accounts are the central starting point when interacting with the Hedera network. A Hedera account is an entity, a distinct object type stored in the ledger, that holds tokens. The types of tokens an account can hold include the native Hedera fungible token (HBAR), custom fungible, and custom non-fungible tokens (NFTs) created on the Hedera network. \
\
The Hedera native token (HBAR) is a utility token primarily used to pay for transaction and query fees when interacting with the network. You interact with the network by submitting transactions that modify the state of the ledger or queries that read data from the ledger. Most transactions and queries have a [transaction fee](../../networks/mainnet/fees/) that is charged in HBAR. Unlike custom tokens users create on the Hedera network, there is no token ID that represents the native HBAR token. \
\
When an account is created it is stored in state with the Hedera network and its current state can be queried from the ledger and can be viewed in a network explorer. Each account has at least one public and private key pair that is associated with it. The private key(s) on the account are used to sign and authorize transactions that involve the account.

Accounts can be created, updated, or deleted. There are two ways you can create an account either by using an existing account or by using an alias. If you have an existing account, you can use that account to create a new account and to pay for the associated transaction fees in hbar. If you do not have access to an existing account, you can create a testnet account via the [Hedera Developer Portal](https://portal.hedera.com/register) or a mainnet account through one of the options listed [here](../../networks/mainnet/mainnet-access.md). To create an account using an alias, you have to transfer an hbar to that alias. The full balance gets transferred to the new account. The account paying for the transfer transaction is responsible for paying the account creation transaction fee.

##

## Account Properties

### Account Identifiers (Addresses)

One Hedera account can be represented by several account addresses. Not all account addresses have the same capabilities when working with Hedera transactions and query requests.

<table data-view="cards"><thead><tr><th align="center"></th></tr></thead><tbody><tr><td align="center"><strong>Account ID</strong></td></tr><tr><td align="center"><strong>Account ID Long Format</strong></td></tr><tr><td align="center"><strong>Account ID Long Zero</strong></td></tr><tr><td align="center"><strong>Ethereum Public Address</strong></td></tr></tbody></table>

#### **Account ID**

Each Hedera account has an **account ID**. The **account ID** is the ID of the account entity that was created by the network. The account entity ID format is `shardId.realmId.accountNumber`. You can use this account ID to specify the account in all Hedera transactions and query requests. The account ID is **immutable** and cannot be changed. The network auto-increments the entity ID as new ones are created. The account ID for a newly created account is returned in the receipt and record confirmations of the transaction.

| Property           | Description                                                                                                                                                                                                                                                                                           | Example    |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| **Shard**          | A shard is a partition of the data received by the nodes that participate in a given shard. The shard ID is the value that represents the shard the account exists in. Today, Hedera operates in only one shared. This value is zero and will remain zero until Hedera operates in more than 1 shard. | **0**.0.10 |
| **Realm**          | The realm ID is the ID of the realm the account exists in within a given shard. Hedera operates in only one realm today. This value is zero and will remain zero until Hedera operates in more than 1 realm.                                                                                          | 0.**0**.10 |
| **Account Number** | The account number is a non-negative number.                                                                                                                                                                                                                                                          | 0.0.**10** |

#### Account ID Long Format (Alias Key)

Some Hedera accounts have a **long form account ID or alias key**. An account alias key is an ED25519 or ECDSA (secp256k1\*\*)\*\* public key associated with the account only when the account is created using the auto account creation feature. An alias is unique per account. No two accounts can share the same alias. The alias is used for auto account creation (covered above). Otherwise, if an account is created normally, the alias will be null. The Account ID Long is immutable and cannot be changed.

| Property           | Description                                                                                                                                                                                                                                                                                           | Example    |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| **Shard**          | A shard is a partition of the data received by the nodes that participate in a given shard. The shard ID is the value that represents the shard the account exists in. Today, Hedera operates in only one shared. This value is zero and will remain zero until Hedera operates in more than 1 shard. | **0**.0.10 |
| **Realm**          | The realm ID is the ID of the realm the account exists in within a given shard. Hedera operates in only one realm today. This value is zero and will remain zero until Hedera operates in more than 1 realm.                                                                                          | 0.**0**.10 |
| **Account Number** | The account number is a non-negative number.                                                                                                                                                                                                                                                          | 0.0.**10** |

#### Account ID **Long Zero Address**

The Hedera account long zero address is the account ID as an Ethereum-compatible address. The Hedera account ID numbers are hex encoded and the value is prefixed with zeros to form a 20-byte address. This was added to represent all Hedera accounts in an `EVM`conformant manner. All Hedera accounts have a corresponding long zero-form address.

| Property  | Description                                                                                                                                                                                                                                                                                           | Example    |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| **Shard** | A shard is a partition of the data received by the nodes that participate in a given shard. The shard ID is the value that represents the shard the account exists in. Today, Hedera operates in only one shared. This value is zero and will remain zero until Hedera operates in more than 1 shard. | **0**.0.10 |

#### Ethereum Account Address (**Public Address)**

An Ethereum account address is an address that interacts with the Ethereum blockchain. This address is commonly used in wallets like MetaMask. The Ethereum Account Address is the rightmost 20-bytes of the 32-byte `Keccak-256` hash of the `ECDSA` public key of the account. This is calculated on the consensus nodes using the `ECDSA` key provided in the auto create `TransferTransaction`. This EVM address may be either the encoded form of the shard.realm.num or the keccak-256 hash of a ECDSA\_SECP256K1 primitive key. Ethereum native wallets expose the public address as the destination address or source address in transactions. The Ethereum Account Address is immutable and cannot be changed.

<[https://hips.hedera.com/hip/hip-583](https://hips.hedera.com/hip/hip-583)>

In summary, there are four different Hedera account addresses that may represent a single Hedera account — each with differing capabilities.

| Property  | Description                                                                                                                                                                                                                                                                                           | Example    |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| **Shard** | A shard is a partition of the data received by the nodes that participate in a given shard. The shard ID is the value that represents the shard the account exists in. Today, Hedera operates in only one shared. This value is zero and will remain zero until Hedera operates in more than 1 shard. | **0**.0.10 |

### Balances

### Keys

### Automatic Token Associations

Hedera accounts are required to approve custom tokens before they can be transferred into the account by signing the TokenAssociateTransaction. The automatic token association feature allows you to bypass associating the custom token before it is transferred into the account. This feature allows you to approve x number of tokens that can be automatically transferred into your account without having to preauthorize the custom token. Accounts can prepay up to 5,000 token auto associations slots. If an account needs to hold a balance for custom tokens greater than 5,000 the account will need to approve each additional token by using the TokenAssociateTransaction. There is no limit on the total number of tokens that an account can hold.

### Staking

Staking in Hedera is taking an account and associating the HBAR balance to a node in the network. Custom fungible or non-fungible token balances an account holds do not contribute to staking on the network. The purpose of staking accounts to a node on the network is to strengthen the security of the network. To contribute to the security of the network, staked accounts can earn rewards in HBAR. Please see this [guide](https://docs.hedera.com/hedera/core-concepts/staking) \<link to the staking program page> for additional information about the staking rewards program. An account can only stake to one node or one account at any given time.

**Node ID**

An account can optionally elect to stake its HBAR to a node in the Hedera network. The staked node ID is the ID of the node an account can stake to. The full balance of the account is staked to the node. The staked account balance is liquid at all times. This means you can transfer HBAR tokens in and out of the account and your account will continue to be staked to the node without disruption. There is no lock-up period. This means the HBAR tokens in your account are not held for a period of time before you can use them. The node ID for a node can be found [here](https://docs.hedera.com/guides/mainnet) or can be queried from the [nodes REST API](https://testnet.mirrornode.hedera.com/api/v1/docs/#/network/getNetworkNodes).

**Account ID**

An account can optionally elect to stake its HBAR to another account in the Hedera network. This is known as **indirect staking**. The staked account ID is the ID of the account to stake to. The full balance of the account is staked to the specified account. There is no lock-up period and the balance is always liquid just like staking to a node. If account A is staked to account B, account B will need to be staked to a node in order to contribute to network security.

**Decline to Earn Staking Rewards**

Accounts have the option to decline earning staking rewards when they stake to a node or an account that then stakes to a node. The staked account still contributes to the stake calculation of the node, but does not earn rewards or is calculated as part of the rewards payment to the other accounts that have elected to earn rewards. By default, all staked accounts will earn rewards unless this boolean flag is set to true.

Reference: [HIP-406](https://hips.hedera.com/hip/hip-406).

### Account Nonce

Accounts on Hedera are able to submit `EthereumTransaction` types that are processed by the Ethereum Virtual Machine (EVM) on a consensus node. The nonce on the account represents a sequentially incrementing count of the transactions submitted by an account through the `EthereumTransaction` type.

### Receiver Signature Required

Accounts can optionally require the account to sign any transactions that are transferring tokens into the account. If this is set and you do not sign the transactions that transfer tokens to your account the transaction will fail and tokens will not be transferred into the account.

### Account Memo

A memo is like a short note that lives with the account object in state on the ledger and can be viewed on a network explorer when looking up the account. This account memo is limited to 100 characters. Be sure not to use the account memo field for any private information. The memo can be updated or removed from the account at any time.





