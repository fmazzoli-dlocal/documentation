# Issuing Status Codes

### Pending Status

| Status | Status code | Status detail |
| :--- | :--- | :--- |
| `PENDING` | 100 | The operation is pending |
| `PENDING` | 101 | The account is pending |
| `PENDING` | 102 | The KYC process is pending |
| `PENDING` | 103 | The transfer is pending |
| `PENDING` | 104 | The card is pending |

### Waiting for Information

| Status | Status code | Status detail |
| :--- | :--- | :--- |
| `WAITING_FOR_IMAGES` | 200 | Images are required |
| `WAITING_FOR_OTP_EMAIL` | 201 | OTP EMAIL is required |
| `WAITING_FOR_OTP_PHONE` | 202 | OTP PHONE is required |

### Active Status <a id="waiting-for-images-status"></a>

| Status | Status code | Status detail |
| :--- | :--- | :--- |
| `ACTIVE` | 300 | The account is active |
| `ACTIVE` | 301 | Request has been accepted and is being processed |
| `ACTIVE` | 302 | The card is active |
| `ACTIVE` | 303 | The transfer is approved |

### Inactive Status <a id="waiting-for-images-status"></a>

| Status | Status code | Status detail |
| :--- | :--- | :--- |
| `INACTIVE` | 400 | The account is inactive |
| `INACTIVE` | 401 | The card is inactive |

### Rejection Status <a id="waiting-for-images-status"></a>

| Status | Status code | Status detail |
| :--- | :--- | :--- |
| `REJECTED` | 500 | The operation was rejected |
| `REJECTED` | 501 | Rejected by invalid address city |
| `REJECTED` | 502 | Rejected by invalid address state |
| `REJECTED` | 503 | Incorrect address |
| `REJECTED` | 504 | Rejected by zip code |
| `REJECTED` | 505 | Invalid KYC process |
| `REJECTED` | 506 | There is a problem with your request. The image file should not be larger than 1 MB |
| `REJECTED` | 507 | ID cannot be validated |
| `REJECTED` | 508 | Selfie cannot be validated |
| `REJECTED` | 509 | Account already exists |
| `REJECTED` | 510 | User blacklisted |
| `REJECTED` | 511 | Invalid birthdate |
| `REJECTED` | 512 | Document is invalid |
| `REJECTED` | 513 | Password is invalid |
| `REJECTED` | 514 | Card already exists |
| `REJECTED` | 515 | Invalid OTP \(error 5005\) |
| `REJECTED` | 516 | Timeout expired while executing transaction |
| `REJECTED` | 517 | The source account does not exist |
| `REJECTED` | 518 | The source account has no funds |
| `REJECTED` | 519 | The destination account does not exist |
| `REJECTED` | 520 | Amount too large |
| `REJECTED` | 521 | Amount too small |
| `REJECTED` | 522 | Document already exists |
| `REJECTED` | 523 | Rejected by invalid OTP |
| `REJECTED` | 524 | User's  must be over 18 years old |
| `REJECTED` | 525 | Rejected by invalid expedition date |
| `REJECTED` | 526 | Invalid credentials \(error 3001\) |
| `REJECTED` | 527 | Unregistered IP address \(error 3002\) |
| `REJECTED` | 528 | Merchant has no authorization to use this API \(error 3003\) |
| `REJECTED` | 529 | Account not found \(error 4004\) |
| `REJECTED` | 530 | Transfer not found \(error 4004?\) |
| `REJECTED` | 531 | Card not found \(error 4004?\) |
| `REJECTED` | 532 | Invalid request \(error 5000\) |
| `REJECTED` | 533 | Invalid parameter  \(error 5001\) |
| `REJECTED` | 534 | Missing parameter \(error 5002\) |
| `REJECTED` | 535 | Invalid account status \(error 5003\) |
| `REJECTED` | 536 | Invalid card status \(error 5004\) |
| `REJECTED` | 537 | Invalid OTP \(error 5005\) |
| `REJECTED` | 538 | Transfer error due merchant reference already used \(error 5006\) |
| `REJECTED` | 539 | Transfer error due compliance limits \(error 5007\) |
| `REJECTED` | 540 | Transfer error due end beneficiary blacklisted \(error 5008\) |
| `REJECTED` | 541 | Transfer error due Insufficient funds \(error 5009\) |
| `REJECTED` | 542 | Transfer error due to compliance \(error 5010\) |

### Error Status <a id="waiting-for-images-status"></a>

| Status | Status code | Status detail |
| :--- | :--- | :--- |
| `ERROR` | 7000 | Internal error |
| `ERROR` | 7001 | Error in Issuer \(Ex rejected 515\) |



