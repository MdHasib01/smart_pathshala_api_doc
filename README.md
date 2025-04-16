# Smart Pathshala Payment API Documentation

This documentation outlines the API endpoints for the Smart Pathshala Payment system, specifically focusing on bKash payment integration.

---

## API Endpoints

### bKash Payment

The following endpoints are available for bKash payment processing:

---

### 1. Get Bill Information

Retrieves bill information for a specific student and billing period.

- **Endpoint:** `/invoices/ussd/bkash/get-bill`
- **Method:** `POST`
- **Content-Type:** `multipart/form-data`

#### Request Parameters

| Parameter | Description                                     |
| --------- | ----------------------------------------------- |
| data      | JSON string containing student and billing info |

#### JSON Data Structure

```json
{
  "institute_id": "XXXX XXX XX",
  "student_username": "XXXXXXX",
  "billing_month": 202504
}
```

| Field            | Description                                                      |
| ---------------- | ---------------------------------------------------------------- |
| institute_id     | The identifier for the institution (e.g., "XXXX XXX XX")         |
| student_username | Student's unique username (e.g., "XXXXXXX")                      |
| billing_month    | The billing month in YYYYMM format (e.g., 202504 for April 2025) |

#### Success Response

The endpoint returns bill information for the specified student.

---

### 2. Accept Payment

Processes a payment for a student's bill.

- **Endpoint:** `/invoices/ussd/bkash/accept-payment`
- **Method:** `POST`
- **Content-Type:** `multipart/form-data`

#### Request Parameters

| Parameter | Description                         |
| --------- | ----------------------------------- |
| data      | JSON string containing payment info |

#### JSON Data Structure

```json
{
  "institute_id": "XXXX XXX XX",
  "student_username": "XXXXXXX",
  "billing_month": 202504,
  "total_amount": 10000,
  "user_wallet_number": "01XXXXXXXXX",
  "trxid": "TRXxxxxxx",
  "paid_at": 20250407123045
}
```

| Field              | Description                                |
| ------------------ | ------------------------------------------ |
| institute_id       | The identifier for the institution         |
| student_username   | Student's unique username                  |
| billing_month      | The billing month in YYYYMM format         |
| total_amount       | Payment amount (in smallest currency unit) |
| user_wallet_number | bKash wallet number used for payment       |
| trxid              | Unique transaction ID                      |
| paid_at            | Payment timestamp in YYYYMMDDHHmmss format |

#### Success Response

The endpoint confirms successful payment processing.

---

### 3. Check Payment Status

Verifies the status of a previously submitted payment.

- **Endpoint:** `/invoices/ussd/bkash/check-payment-status`
- **Method:** `POST`
- **Content-Type:** `multipart/form-data`

#### Request Parameters

| Parameter | Description                             |
| --------- | --------------------------------------- |
| data      | JSON string containing transaction info |

#### JSON Data Structure

```json
{
  "institute_id": "XXXX XXX XX",
  "trxid": "TRXxxxxxx"
}
```

| Field        | Description                        |
| ------------ | ---------------------------------- |
| institute_id | The identifier for the institution |
| trxid        | Transaction ID to check            |

#### Success Response

The endpoint returns the current status of the payment transaction.

---

## Important Notes

1. All requests must include the Basic Authentication credentials.
2. All data must be sent as a JSON string in the `data` field of a form-data request.
3. The `trxid` should be unique for each payment.
4. The `billing_month` format is `YYYYMM` (e.g., `202504` for April 2025).
5. The `paid_at` timestamp format is `YYYYMMDDHHmmss`.

---

## Support

For any issues or questions regarding this API integration, please contact Smart Pathshala support.

---

Let me know if you'd like this in a downloadable format (Markdown, PDF, etc.) or styled for developer documentation.
