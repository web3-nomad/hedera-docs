# Network Response Messages

| Network Response                                              | Description                                                                                                                                        |
| ------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| `INVALID_SCHEDULE_ID`                                         | The Scheduled entity does not exist; or has now expired, been deleted, or been executed                                                            |
| `SCHEDULE_IS_IMMUTABLE`                                       | The Scheduled entity cannot be modified. Admin key was not set during the creation of the Scheduled entity.                                        |
| `INVALID_SCHEDULE_PAYER_ID`                                   | The provided Scheduled Payer does not exist                                                                                                        |
| `INVALID_SCHEDULE_ACCOUNT_ID`                                 | The Schedule Create Transaction TransactionID account does not exist                                                                               |
| `NO_NEW_VALID_SIGNATURES`                                     | The provided sig map did not contain any new valid signatures from required signers of the scheduled transaction                                   |
| `UNRESOLVABLE_REQUIRED_SIGNERS`                               | The required signers for a scheduled transaction cannot be resolved, for example because they do not exist or have been deleted                    |
| `UNPARSEABLE_SCHEDULED_TRANSACTION`                           | The bytes allegedly representing a transaction to be scheduled could not be parsed                                                                 |
| `UNSCHEDULABLE_TRANSACTION`                                   | ScheduleCreate and ScheduleSign transactions cannot be scheduled                                                                                   |
| `SOME_SIGNATURES_WERE_INVALID`                                | At least one of the signatures in the provided sig map did not represent a valid signature for any required signer                                 |
| `TRANSACTION_ID_FIELD_NOT_ALLOWED`                            | The scheduled and nonce fields in the TransactionID may not be set in a top-level transaction                                                      |
| `IDENTICAL_SCHEDULE_ALREADY_CREATED`                          | A schedule already exists with the same identifying fields of an attempted ScheduleCreate (that is, all fields other than scheduledPayerAccountID) |
| `SCHEDULE_ALREADY_DELETED`                                    | A schedule being signed or deleted has already been deleted                                                                                        |
| `SCHEDULE_PENDING_EXPIRATION`                                 | A schedule being signed or deleted has passed it's expiration date and is pending execution if needed and then expiration                          |
| `SCHEDULE_FUTURE_GAS_LIMIT_EXCEEDED`                          | The scheduled transaction could not be created because it would cause the gas limit to be violated on the specified expiration time                |
| `SCHEDULE_FUTURE_THROTTLE_EXCEEDED`                           | The scheduled transaction could not be created because it would cause throttles to be violated on the specified expiration time                    |
| `SCHEDULE_EXPIRATION_TIME_MUST_BE_HIGHER_THAN_CONSENSUS_TIME` | The scheduled transaction could not be created because it's expiration\_time was less than or equal to the consensus time                          |
| `SCHEDULE_EXPIRATION_TIME_TOO_FAR_IN_FUTURE`                  | The scheduled transaction could not be created because it's expiration time was too far in the future                                              |
