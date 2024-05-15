# JSON-RPC Relay

The [Hedera JSON-RPC Relay](https://github.com/hashgraph/hedera-json-rpc-relay) is an open-source project implementing the Ethereum JSON-RPC standard. The JSON-RPC relay allows developers to interact with Hedera nodes using familiar Ethereum tools. This allows Ethereum developers and users to deploy, query, and execute contracts as they usually would. Check out the interactive[ OpenRPC Specification](https://playground.open-rpc.org/?schemaUrl=https://raw.githubusercontent.com/hashgraph/hedera-json-rpc-relay/main/docs/openrpc.json\&uiSchema%5BappBar%5D%5Bui:splitView%5D=false\&uiSchema%5BappBar%5D%5Bui:input%5D=false\&uiSchema%5BappBar%5D%5Bui:examplesDropdown%5D=false) and a simple [list of endpoints](https://github.com/hashgraph/hedera-json-rpc-relay/blob/main/docs/rpc-api.md).&#x20;

## HBAR decimal places&#x20;

The Hedera JSON RPC Relay **`msg.value`** uses 18 decimals when it returns HBAR. As a result, the **`gasPrice`** value returns 18 decimal places since it is only utilized from the JSON RPC Relay. Refer to the [HBAR page](../../../sdks-and-apis/sdks/hbars.md) for a list of Hedera APIs and the decimal places they return.&#x20;

## Community Hosted JSON-RPC Relays

Anyone in the community can set up their own JSON RPC relay that applications can use to deploy, query, and execute smart contracts. The endpoints for previewnet, testnet, and mainnet can be found in their associated docs or website. You will find the list of community-hosted Hedera JSON RPC Relays below.&#x20;

<table data-card-size="large" data-view="cards"><thead><tr><th align="center"></th><th data-hidden data-card-cover data-type="files"></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td align="center"><strong>Hashio</strong></td><td><a href="../../../.gitbook/assets/hashio (1).png">hashio (1).png</a></td><td><a href="https://swirldslabs.com/hashio/">https://swirldslabs.com/hashio/</a></td></tr><tr><td align="center"><strong>Arkhia</strong></td><td><a href="../../../.gitbook/assets/arkhia logo.png">arkhia logo.png</a></td><td><a href="https://www.arkhia.io/features/#api-services">https://www.arkhia.io/features/#api-services</a></td></tr><tr><td align="center"><strong>Validation Cloud</strong></td><td><a href="../../../.gitbook/assets/validation cloud logo.png">validation cloud logo.png</a></td><td><a href="https://docs.validationcloud.io/about/hedera/json-rpc-relay-api">https://docs.validationcloud.io/about/hedera/json-rpc-relay-api</a></td></tr><tr><td align="center"><strong>thirdweb</strong></td><td><a href="../../../.gitbook/assets/thirdweb_Logo.jpg">thirdweb_Logo.jpg</a></td><td><a href="https://thirdweb.com/hedera">https://thirdweb.com/hedera</a></td></tr></tbody></table>

{% content-ref url="../../../tutorials/more-tutorials/json-rpc-connections/" %}
[json-rpc-connections](../../../tutorials/more-tutorials/json-rpc-connections/)
{% endcontent-ref %}

{% hint style="info" %}
**Note:** If you want to add your own hosted JSON-RPC relay to this list, please open an issue in the [Hedera docs GitHub repository](https://github.com/hashgraph/hedera-docs). Please be sure to visit the community-hosted websites to review any limitations specific to their instance.&#x20;
{% endhint %}

## FAQ

<details>

<summary>Are there Community hosted relays?</summary>

* [**Hashio**](https://swirldslabs.com/hashio/)&#x20;
* [**Arkhia**](https://www.arkhia.io/features/#api-services)
* [**Validation Cloud**](https://docs.validationcloud.io/about/hedera/json-rpc-relay-api)

</details>

<details>

<summary>How do I connect to the Hedera Network over RPC?</summary>

The configuration guide to connect to the Hedera Network over RPC can be found [here](../../../tutorials/more-tutorials/json-rpc-connections/).

</details>

<details>

<summary>Where can I find the Hedera JSON-RPC relay endpoints?</summary>

The endpoints for previewnet, testnet, and mainnet can be found on [Hashio](https://swirldslabs.com/hashio/), accessible through the [Swirlds Labs](https://swirldslabs.com/) website. Feel free to join the discussion on [Stack Overflow](https://stackoverflow.com/questions/76153239/how-can-i-connect-to-hedera-testnet-over-rpc/76153290#76153290) for more questions.

</details>

<details>

<summary><strong>How does Hedera handle decimals in HBAR and gas prices?</strong></summary>

The JSON-RPC Relay `msg.value` uses 18 decimals when it returns HBAR. The `gasPrice` value also returns 18 decimal places. _Check out the_ [_HBAR page_](../../../sdks-and-apis/sdks/hbars.md) _for the full list of Hedera APIs and their decimal representation._&#x20;

</details>

<details>

<summary>How can I contribute or log errors?</summary>

To contribute or log errors, please refer to the [Contributing Guide](../../../support-and-community/contributing-guide.md) and submit them as issues in the [GitHub repository](https://github.com/hashgraph/hedera-json-rpc-relay/issues).

</details>
