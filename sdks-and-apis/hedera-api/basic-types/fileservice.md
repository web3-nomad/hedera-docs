# FileService

| RPC              | Request                                                  | Response                                                                 | Comments                                                                |
| ---------------- | -------------------------------------------------------- | ------------------------------------------------------------------------ | ----------------------------------------------------------------------- |
| `createFile`     | [Transaction](../cryptocurrency-accounts/transaction.md) | [TransactionResponse](../cryptocurrency-accounts/transactionresponse.md) | Creates a file                                                          |
| `updateFile`     | [Transaction](../cryptocurrency-accounts/transaction.md) | [TransactionResponse](../cryptocurrency-accounts/transactionresponse.md) | Updates a file                                                          |
| `deleteFile`     | [Transaction](../cryptocurrency-accounts/transaction.md) | [TransactionResponse](../cryptocurrency-accounts/transactionresponse.md) | Deletes a file                                                          |
| `appendContent`  | [Transaction](../cryptocurrency-accounts/transaction.md) | [TransactionResponse](../cryptocurrency-accounts/transactionresponse.md) | Appends the file                                                        |
| `getFileContent` | [Query](../miscellaneous/query.md)                       | [Response](../miscellaneous/response.md)                                 | Retrieves the file content                                              |
| `getFileInfo`    | [Query](../miscellaneous/query.md)                       | [Response](../miscellaneous/response.md)                                 | Retrieves the file information                                          |
| `systemDelete`   | [Transaction](../cryptocurrency-accounts/transaction.md) | [TransactionResponse](../cryptocurrency-accounts/transactionresponse.md) | Deletes a file if the submitting account has network admin privileges   |
| `systemUndelete` | [Transaction](../cryptocurrency-accounts/transaction.md) | [TransactionResponse](../cryptocurrency-accounts/transactionresponse.md) | Undeletes a file if the submitting account has network admin privileges |
