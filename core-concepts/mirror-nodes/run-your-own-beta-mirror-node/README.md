# Run Your Own Mirror Node

## Overview

A Hedera Mirror Node is a node that receives pre-constructed files from the Hedera Mainnet. These pre-constructed files include **transaction records** and **account balance files**. Transaction records include information about a transaction like the transaction ID, transaction hash, account, etc. The account balance files give you a snapshot of the balances for all accounts at a given timestamp.

In this tutorial, you will run your own Hedera Mirror Node. You will need to create either a Google Cloud Platform (GCP) or Amazon Web Services (AWS) account if you do not have one already. The Hedera Mirror Node object storage bucket, where you will pull the account balance and transaction data from, is stored in GCP or AWS bucket and are configured for [requester pays](https://cloud.google.com/storage/docs/requester-pays). This means the mirror node operator is responsible for the operational costs of reading and retrieving data from the GCP/AWS. A GCP/AWS account will provide the necessary billing information for requesting the data.

{% content-ref url="run-your-own-mirror-node-gcs.md" %}
[run-your-own-mirror-node-gcs.md](run-your-own-mirror-node-gcs.md)
{% endcontent-ref %}

{% content-ref url="run-your-own-mirror-node-s3.md" %}
[run-your-own-mirror-node-s3.md](run-your-own-mirror-node-s3.md)
{% endcontent-ref %}

## Minimum Hardware Requirements & Associated Costs

To run a Hedera Mirror Node, you'll need specific hardware and resources. The recommended minimum requirements for running a Mirror Node, along with the associated costs, are outlined below.&#x20;

### Compute Engine

* **Region:** Iowa
* **Provisioning Model:** Regular
* **Instance Type:** n1-standard-4
* **Operating System / Software:** Free
* **Total hours per month:** 1,460
* **Sustained Use Discount:** Applied (30%)

The estimated cost for the compute engine per month is **USD 194.18**.

### Cloud SQL for PostgreSQL

* **Instance Type:** db-highmem-4
* **Location:** Iowa
* **Number of Instances:** 1
* **Total hours per month:** 730.0
* **SSD Storage:** 200.0 GiB
* **Backup:** 200.0 GiB

The estimated cost for Cloud SQL for PostgreSQL per month is **USD 303.46**.

### Persistent Disk (Accompanying)

* **Product accompanying:** GKE Standard
* **Zonal SSD PD:** 50 GiB (2 x boot disk)

The estimated cost for the persistent disk per month is **USD 17.00**.

Based on these specifications, the total estimated cost to run a Hedera Mirror Node per month is **USD 514.64**.

{% hint style="info" %}
**Please note:** these are estimated costs and actual costs may vary depending on usage and any changes to the pricing of the resources used. Always refer to the most recent price lists from the respective services for accurate costs.
{% endhint %}

Lastly, this setup offers a good balance between cost and performance but you may need to adjust these specifications based on the specific needs and workload of your Mirror Node.
