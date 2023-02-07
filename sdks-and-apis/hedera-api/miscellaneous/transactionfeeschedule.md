# TransactionFeeSchedule

The fees for a specific transaction or query based on the fee data.

| Field                 | Type                                                                                 | Description                                                    |
| --------------------- | ------------------------------------------------------------------------------------ | -------------------------------------------------------------- |
| `hederaFunctionality` | ​[HederaFunctionality](../../../docs/hedera-api/basic-types/hederafunctionality.md)​ | A particular transaction or query                              |
| `feeData`             | ​[FeeData](../../../docs/hedera-api/basic-types/feedata.md)​                         | <p>Resource price coefficients</p><p>[deprecated]</p>          |
| `fees`                | repeated [FeeData](../../../docs/hedera-api/basic-types/feedata.md)                  | Resource price coefficients. Supports subtype price definition |

#### &#x20;<a href="#undefined" id="undefined"></a>
