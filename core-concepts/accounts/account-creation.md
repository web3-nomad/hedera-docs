# Account Creation

## Account Creation

Accounts that are created on the Hedera network require the user to pay for the transaction fee to create the account. The transaction fee includes the fees required to use network resources to create the account. This means you will need to use an application like a wallet or portal to create an account for you if you do not have access to an existing Hedera account

The transaction that creates a new account entity on the Hedera network requires you to pay a transaction fee to create the object type. The transaction fee is charged in the native HBAR token. This means that you need to have access to a Hedera account that already exists on the ledger with an HBAR balance to cover the cost of creating the new account. There are ways to get around this since new Hedera developers who are getting ready to develop would not have access to an existing account. Check out the options below to create new accounts.

<table data-view="cards"><thead><tr><th align="center"></th></tr></thead><tbody><tr><td align="center"><strong>Hedera Developer Portal</strong></td></tr><tr><td align="center"><strong>Wallets</strong></td></tr><tr><td align="center"><strong>SDKs</strong></td></tr></tbody></table>

#### **Hedera Developer Portal**

The Hedera Developer Portal creates testnet and previewnet accounts for you. You can use these accounts to create additional testnet and previewnet accounts using the `AccountCreateTransaction` in the SDKs and specifying the previewnet or testnet account provided by the developer portal as the transaction fee payer. Check out this guide \<link to portal guide> to get started. The Hedera Developer Portal _**does not**_ create mainnet accounts. Please see the Hedera supported wallets to create [mainnet accounts](https://docs.hedera.com/hedera/mainnet/mainnet-access).

{% content-ref url="../../networks/testnet/testnet-access.md" %}
[testnet-access.md](../../networks/testnet/testnet-access.md)
{% endcontent-ref %}

#### **Wallets**

A wallet is a piece of software that securely stores your Hedera account and private keys. Most users will interact with distributed applications built on Hedera using a wallet. If you create an account using a supported wallet, the wallet will cover the transaction fee to create the account for you. Please see the list of Hedera [supported wallets](https://docs.hedera.com/hedera/mainnet/mainnet-access) here.

All wallets support creating new accounts on mainnet. They may or may not support creating new accounts on previewnet or testnet.

#### **SDKs**

**Use the** `AccountCreateTransaction`

If you have access to an existing account in any of the networks (previewnet, testnet, mainnet) you can use the SDK to submit an `AccountCreateTransaction` and specify the transaction fee payer with the account you have access to. If you do not already have a Hedera account you will need to create one by using the Hedera Developer Portal or from a supported wallet.

{% content-ref url="../../getting-started/create-an-account.md" %}
[create-an-account.md](../../getting-started/create-an-account.md)
{% endcontent-ref %}

**Auto Account Creation**

Auto account creation is a feature that allows you to use an alias as a virtual account address until the account is created on the Hedera ledger. An alias can be an ECDSA public key, and ED25519 public key, or an Ethereum public address. The official account is created the first time a user transfers HBAR or custom tokens to the alias. Account aliases are free to create. This method of creating accounts can be useful to wallets as the cost of creating the new account on the ledger is charged when the user transfers tokens to the public key address or Ethereum public address.

> **Note:** Please ensure you transfer enough HBAR to cover the account creation fee to avoid transaction failure. Check the fees table [here](https://docs.hedera.com/hedera/mainnet/fees).

→ **Transfer tokens to a public key alias address and create an account**

See examples here:

\<link to examples/other relevant content in docs>\
Reference Hedera Improvement Proposals:

* [HIP-32](https://hips.hedera.com/hip/hip-32)
* [HIP-542](https://hips.hedera.com/hip/hip-542)
