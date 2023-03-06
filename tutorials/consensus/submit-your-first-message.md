# Submit Your First Message

## Summary

With the Hedera Consensus Service, you can develop applications like stock markets, audit logs, stablecoins, or new network services that require high throughput and decentralized trust. This is made possible by having direct access to the stablecoinsnative speed, security, and fair ordering guarantees of the hashgraph consensus algorithm, with the full trust of the Hedera ledger.

## Prerequisites

We recommend you complete the following introduction to get a basic understanding of Hedera transactions. This example does not build upon the previous examples.

<details>

<summary>Developer Quickstart Guide</summary>

### Create Hedera Developer Portal Profile (Faucet)

You will need a Hedera Testnet account. The _**Hedera Testnet**_ account allows you to interact with our APIs and pay for the transaction fees. Visit the [Hedera portal](https://portal.hedera.com/register) to create your _Hedera Testnet_ account and follow the instructions.

<img src="../../.gitbook/assets/portal testnet account.png" alt="" data-size="original">

Once you have completed the instructions, you will receive a _Hedera Testnet_ _**account ID**_ (0.0.x) and your _**private/public key pair**_ on your testnet page. You will need to copy over your _account ID_ and _key pair_ information when you set up your coding environment in the following steps.

<img src="../../.gitbook/assets/portal screenshot.avif" alt="" data-size="original">

_**Note:** Your Hedera Testnet account will be credited with 10,000 test **HBAR** upon creation that can only be utilized on the Hedera test network. Your balance will be topped up daily to 10,000 test **HBAR** when you use your funds._

### Create Project Directory and Initialize Node.js

Open up a terminal window in your IDE and navigate to the folder you want to create this project.&#x20;

```bash
mkdir hedera-first-topic && cd hedera-first-topic
```

Run the following command to initialize a _Node.js_ project:

```bash
npm init -y
```

Install the [JavaScript SDK](https://github.com/hashgraph/hedera-sdk-js) with _`npm`_ or _`yarn,`_ by running the following command:

```bash
// install Hedera's JS SDK with NPM
npm install --save @hashgraph/sdk

// Install with Yarn
yarn add @hashgraph/sdk
```

Navigate to the project root directory and create a _`index.js`_ file by running the following command:&#x20;

```bash
touch index.js
```

Your project structure should look something like this:

<img src="../../.gitbook/assets/image105 (1).png" alt="" data-size="original">

Congrats! You just made my entire year. Now you're ready to move on to Step 1 and set up your Hardhat project.

</details>

We recommend you complete the following introduction to get a basic understanding of Hedera transactions. This example does not build upon the previous examples.

{% content-ref url="../../getting-started/introduction.md" %}
[introduction.md](../../getting-started/introduction.md)
{% endcontent-ref %}

{% content-ref url="../../getting-started/environment-set-up.md" %}
[environment-set-up.md](../../getting-started/environment-set-up.md)
{% endcontent-ref %}

## 1. Create your first topic

To create your first topic, you will use the _<mark style="color:purple;">**`TopicCreateTransaction()`**</mark>_, set its properties, and submit it to the Hedera network. A public topic that anyone can submit messages to does not require any other properties to be set.

If you would like to create a private topic you can optionally set a topic key ([_`setSubmitKey()`_](https://docs.hedera.com/guides/docs/sdks/consensus/create-a-topic#methods)). This means that messages submitted to this topic will require the topic key to sign the message submit transaction. If the topic key does not sign the message submit transaction, the message will not be submitted to the topic.

After submitting the transaction to the Hedera network, you can obtain the new token ID by requesting the receipt.

{% tabs %}
{% tab title="Java" %}
```java
//Create a new topic
TransactionResponse txResponse = new TopicCreateTransaction()
   .execute(client);

//Get the receipt
TransactionReceipt receipt = txResponse.getReceipt(client);
        
//Get the topic ID
TopicId topicId = receipt.topicId;

//Log the topic ID
System.out.println("Your topic ID is: " +topicId);

// Wait 5 seconds between consensus topic creation and subscription creation
Thread.sleep(5000);
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Create a new topic
let txResponse = await new TopicCreateTransaction().execute(client);

//Grab the newly generated topic ID
let receipt = await txResponse.getReceipt(client);
let topicId = receipt.topicId;
console.log(`Your topic ID is: ${topicId}`);

// Wait 5 seconds between consensus topic creation and subscription creation
await new Promise((resolve) => setTimeout(resolve, 5000));
```
{% endtab %}

{% tab title="Go" %}
```go
//Create a new topic
transactionResponse, err := hedera.NewTopicCreateTransaction().
	Execute(client)

if err != nil {
	println(err.Error(), ": error creating topic")
	return
}

//Get the topic create transaction receipt
transactionReceipt, err := transactionResponse.GetReceipt(client)

if err != nil {
	println(err.Error(), ": error getting topic create receipt")
	return
}

//Get the topic ID from the transaction receipt
topicID := *transactionReceipt.TopicID

//Log the topic ID to the console
fmt.Printf("topicID: %v\n", topicID)
```
{% endtab %}
{% endtabs %}

## 2. Subscribe to a topic

After you create the topic, you will want to subscribe to the topic via a Hedera mirror node. Subscribing to a topic via a Hedera mirror node allows you to receive the stream of messages that are being submitted to it.

The _**Hedera Testnet**_ client already establishes a connection to a Hedera mirror node. You can set a custom mirror node by calling _<mark style="color:purple;">**`client.SetMirrorNetwork()`**</mark>_. Please note that you can currently subscribe to Hedera Consensus Service (HCS) topics via [gRPC API](https://docs.hedera.com/guides/docs/mirror-node-api/hedera-consensus-service-api-1) only, so remember to set the mirror node's host and port accordingly.

To subscribe to a topic, you will use _<mark style="color:purple;">**`TopicMessageQuery()`**</mark>_. You will provide it the topic ID to subscribe to, the Hedera mirror node client information, and the topic message contents to return.

{% tabs %}
{% tab title="Java" %}
```java
//Subscribe to the topic
new TopicMessageQuery()
    .setTopicId(topicId)
    .subscribe(client, resp -> {
            String messageAsString = new String(resp.contents, StandardCharsets.UTF_8);
            System.out.println(resp.consensusTimestamp + " received topic message: " + messageAsString);
    });
```
{% endtab %}

{% tab title="JavaScript" %}
<pre class="language-javascript"><code class="lang-javascript"><strong>// Create the query
</strong><strong>new TopicMessageQuery()
</strong>  .setTopicId(topicId)
  .subscribe(client, null, (message) => {
    let messageAsString = Buffer.from(message.contents, "utf8").toString();
    console.log(
      `${message.consensusTimestamp.toDate()} Received: ${messageAsString}`
    );
  });
</code></pre>
{% endtab %}

{% tab title="Go" %}
```go
//Create the query to subscribe to a topic
_, err = hedera.NewTopicMessageQuery().
	SetTopicID(topicID).
	Subscribe(client, func(message hedera.TopicMessage) {
		fmt.Println(message.ConsensusTimestamp.String(), "received topic message ", string(message.Contents), "\r")
   })
```
{% endtab %}
{% endtabs %}

## 3. Submit a message

Now you are ready to submit your first message to the topic. To do this, you will use _<mark style="color:purple;">**`TopicMessageSubmitTransaction().`**</mark>_ For this transaction, you will provide the topic ID and the message to submit to it.

{% tabs %}
{% tab title="Java" %}
```java
//Submit a message to a topic
TransactionResponse submitMessage = new TopicMessageSubmitTransaction()
      .setTopicId(topicId)
      .setMessage("hello, HCS!")
      .execute(client);

//Get the receipt of the transaction
 TransactionReceipt receipt2 = submitMessage.getReceipt(client);

//Prevent the main thread from existing so the topic message can be returned and printed to the console
Thread.sleep(30000);
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
// Send one message
let sendResponse = await new TopicMessageSubmitTransaction({
	topicId: topicId,
	message: "Hello, HCS!",
}).execute(client);

//Get the receipt of the transaction
const getReceipt = await sendResponse.getReceipt(client);

//Get the status of the transaction
const transactionStatus = getReceipt.status
console.log("The message transaction status " + transactionStatus)
```
{% endtab %}

{% tab title="Go" %}
```go
//Send "Hello, HCS!" to the topic
submitMessage, err := hedera.NewTopicMessageSubmitTransaction().
	SetMessage([]byte("Hello, HCS!")).
	SetTopicID(topicID).
	Execute(client)

if err != nil {
	println(err.Error(), ": error submitting to topic")
	return
}

//Get the receipt of the transaction
receipt, err := submitMessage.GetReceipt(client)

//Get the transaction status
transactionStatus := receipt.Status
fmt.Println("The message transaction status " + transactionStatus.String())

//Prevent the program from exiting to display the message from the mirror to the console
time.Sleep(30000)
```
{% endtab %}
{% endtabs %}

## Code Check ✅

{% tabs %}
{% tab title="Java" %}
```java
import com.hedera.hashgraph.sdk.*;
import io.github.cdimascio.dotenv.Dotenv;

import java.nio.charset.StandardCharsets;
import java.util.concurrent.TimeoutException;

public class CreateTopicTutorial {
    public static void main(String[] args) throws TimeoutException, PrecheckStatusException, ReceiptStatusException, InterruptedException {

        //Grab your Hedera testnet account ID and private key
        AccountId myAccountId = AccountId.fromString(Dotenv.load().get("MY_ACCOUNT_ID"));
        PrivateKey myPrivateKey = PrivateKey.fromString(Dotenv.load().get("MY_PRIVATE_KEY"));

        //Build your Hedera client
        Client client = Client.forTestnet();
        client.setOperator(myAccountId, myPrivateKey);

        //Create a new topic
        TransactionResponse txResponse = new TopicCreateTransaction()
                .execute(client);

        //Get the receipt
        TransactionReceipt receipt = txResponse.getReceipt(client);

        //Get the topic ID
        TopicId topicId = receipt.topicId;

        //Log the topic ID
        System.out.println("Your topic ID is: " +topicId);

        // Wait 5 seconds between consensus topic creation and subscription creation
        Thread.sleep(5000);

        //Subscribe to the topic
        new TopicMessageQuery()
                .setTopicId(topicId)
                .subscribe(client, resp -> {
                    String messageAsString = new String(resp.contents, StandardCharsets.UTF_8);
                    System.out.println(resp.consensusTimestamp + " received topic message: " + messageAsString);
                });

        //Submit a message to a topic
        TransactionResponse submitMessage = new TopicMessageSubmitTransaction()
                .setTopicId(topicId)
                .setMessage("hello, HCS!")
                .execute(client);

        //Get the receipt of the transaction
        TransactionReceipt receipt2 = submitMessage.getReceipt(client);

        //Wait before the main thread exits to return the topic message to the console
        Thread.sleep(30000);

    }
}
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
console.clear();
require("dotenv").config();
const {
  AccountId,
  PrivateKey,
  Client,
  TopicCreateTransaction,
  TopicMessageQuery,
  TopicMessageSubmitTransaction,
} = require("@hashgraph/sdk");

// Grab the OPERATOR_ID and OPERATOR_KEY from the .env file
const myAccountId = process.env.MY_ACCOUNT_ID;
const myPrivateKey = process.env.MY_PRIVATE_KEY;

// Build Hedera testnet and mirror node client
const client = Client.forTestnet();

// Set the operator account ID and operator private key
client.setOperator(myAccountId, myPrivateKey);

async function main() {
  //Create a new topic
  let txResponse = await new TopicCreateTransaction().execute(client);

  //Grab the newly generated topic ID
  let receipt = await txResponse.getReceipt(client);
  let topicId = receipt.topicId;
  console.log(`Your topic ID is: ${topicId}`);

  // Wait 5 seconds between consensus topic creation and subscription creation
  await new Promise((resolve) => setTimeout(resolve, 5000));

  //Create the query
  new TopicMessageQuery()
    .setTopicId(topicId)
    .subscribe(client, null, (message) => {
      let messageAsString = Buffer.from(message.contents, "utf8").toString();
      console.log(
        `${message.consensusTimestamp.toDate()} Received: ${messageAsString}`
      );
    });

  // Send one message
  let sendResponse = await new TopicMessageSubmitTransaction({
    topicId: topicId,
    message: "Hello, HCS!",
  }).execute(client);
  const getReceipt = await sendResponse.getReceipt(client);

  //Get the status of the transaction
  const transactionStatus = getReceipt.status;
  console.log("The message transaction status: " + transactionStatus);
}
main();
```
{% endtab %}

{% tab title="Go" %}
```go
package main

import (
	"fmt"
	"os"
	"time"

	"github.com/hashgraph/hedera-sdk-go/v2"
	"github.com/joho/godotenv"
)

func main() {

	//Loads the .env file and throws an error if it cannot load the variables from that file corectly
	err := godotenv.Load(".env")
	if err != nil {
		panic(fmt.Errorf("Unable to load enviroment variables from .env file. Error:\n%v\n", err))
	}

	//Grab your testnet account ID and private key from the .env file
	myAccountId, err := hedera.AccountIDFromString(os.Getenv("MY_ACCOUNT_ID"))
	if err != nil {
		panic(err)
	}

	myPrivateKey, err := hedera.PrivateKeyFromString(os.Getenv("MY_PRIVATE_KEY"))
	if err != nil {
		panic(err)
	}

	//Create your testnet client
	client := hedera.ClientForTestnet()
	client.SetOperator(myAccountId, myPrivateKey)

	//Create a new topic
	transactionResponse, err := hedera.NewTopicCreateTransaction().
		Execute(client)

	if err != nil {
		println(err.Error(), ": error creating topic")
		return
	}

	//Get the topic create transaction receipt
	transactionReceipt, err := transactionResponse.GetReceipt(client)

	if err != nil {
		println(err.Error(), ": error getting topic create receipt")
		return
	}

	//Get the topic ID from the transaction receipt
	topicID := *transactionReceipt.TopicID

	//Log the topic ID to the console
	fmt.Printf("topicID: %v\n", topicID)

	//Create the query to subscribe to a topic
	_, err = hedera.NewTopicMessageQuery().
		SetTopicID(topicID).
		Subscribe(client, func(message hedera.TopicMessage) {
			fmt.Println(message.ConsensusTimestamp.String(), "received topic message ", string(message.Contents), "\r")
		})
        
        //Submit a message to the topic
	submitMessage, err := hedera.NewTopicMessageSubmitTransaction().
		SetMessage([]byte("Hello, HCS!")).
		SetTopicID(topicID).
		Execute(client)

	if err != nil {
		println(err.Error(), ": error submitting to topic")
		return
	}
        
        //Get the transaction receipt
	receipt, err := submitMessage.GetReceipt(client)
        
        //Log the transaction status
	transactionStatus := receipt.Status
	fmt.Println("The transaction message status " + transactionStatus.String())
    
        //Prevent the program from exiting to display the message from the mirror to the console
	time.Sleep(30 * time.Second)
    }
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Have a question? [Ask it on StackOverflow](https://stackoverflow.com/questions/tagged/hedera-hashgraph)
{% endhint %}

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th data-hidden></th><th data-hidden></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td>Author: Hedera Team</td><td></td><td></td><td></td></tr></tbody></table>
