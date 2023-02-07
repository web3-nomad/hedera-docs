# JSON-RPC Relay

The [Hedera JSON-RPC Relay](https://github.com/hashgraph/hedera-json-rpc-relay) is an open-source project that implements the Ethereum JSON-RPC standard. The JSON-RPC relay allows developers to interact with Hedera nodes using familiar Ethereum tools. This allows Ethereum developers and users to deploy, query, and execute contracts as they usually would. Check out the interactable[ OpenRPC Specification](https://playground.open-rpc.org/?schemaUrl=https://raw.githubusercontent.com/hashgraph/hedera-json-rpc-relay/main/docs/openrpc.json\&uiSchema%5BappBar%5D%5Bui:splitView%5D=false\&uiSchema%5BappBar%5D%5Bui:input%5D=false\&uiSchema%5BappBar%5D%5Bui:examplesDropdown%5D=false) and a simple [list of endpoints](https://github.com/hashgraph/hedera-json-rpc-relay/blob/main/docs/rpc-api.md). The Hedera JSON-RPC relay implementation is in beta, offers limited functionality today, and is only available to developers.&#x20;

## HBAR decimal places&#x20;

_The JSON RPC Relay **`msg.value`** uses 18 decimals when it returns HBAR. As a result, the **`gasPrice`** value returns 18 decimal places since it is only utilized from the JSON RPC Relay. Refer to the_ [_HBAR page_](../../sdks-and-apis/sdks/hbars.md) _for a list of Hedera APIs and the decimal places they return._&#x20;

## FAQs

<details>

<summary>How do I run an instance of the relay?</summary>

* ****[**Run locally using `npm`**](https://github.com/hashgraph/hedera-json-rpc-relay#steps)**``**
* ****[**Build and deploy via Docker**](https://github.com/hashgraph/hedera-json-rpc-relay#deployment)****
* ****[**Using the Helm chart**](https://github.com/hashgraph/hedera-json-rpc-relay#helm-chart)****

</details>

<details>

<summary>Are there Community hosted relays?</summary>

* ****[**Hashio**](https://swirldslabs.com/hashio/) ****&#x20;

</details>

<details>

<summary>How many decimals are there in HBAR?</summary>

_Check out the_ [_HBAR page_](../../sdks-and-apis/sdks/hbars.md) _for the full list of Hedera APIs and their decimal representation._&#x20;

</details>

<details>

<summary>How can I contribute feedback or log errors?</summary>

To contribute feedback or log errors, please refer to the [Contributing Guide](../../support-and-community/contributing-guide.md) and submit them as issues in the [GitHub repository](https://github.com/hashgraph/hedera-json-rpc-relay/issues).

</details>
