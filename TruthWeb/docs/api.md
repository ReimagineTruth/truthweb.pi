# TruthWeb Open-Source API Documentation

Welcome to the TruthWeb Open-Source API! This API allows developers to integrate Pi cryptocurrency into their applications, leveraging TruthWeb’s decentralized ecosystem. Whether you’re building a marketplace, a wallet app, or a custom service, our API provides the tools you need.

## Base URL
All endpoints are relative to the base URL: https://api.truthweb.com/v1/

*Note*: This is a placeholder URL. Replace with your actual deployment URL once the backend is live.

## Authentication
- **API Key**: Required for all requests. Obtain your key by registering at [TruthWeb Developer Portal](#) (coming soon).
- **Header**: Include `Authorization: Bearer <your-api-key>` in all requests.

## Endpoints

### 1. User Profiles
Manage user profiles within the TruthWeb ecosystem.

#### GET /profiles/{username}
Retrieve a user’s public profile information.

- **Method**: `GET`
- **URL**: `/profiles/{username}`
- **Path Parameters**:
  - `username` (string, required): The TruthWeb username (e.g., "pioneer123").
- **Headers**:
  - `Authorization: Bearer <your-api-key>`
- **Response**:
  ```json
  {
    "status": "success",
    "data": {
      "username": "pioneer123",
      "display_name": "Pioneer John",
      "bio": "Pi enthusiast and developer",
      "created_at": "2025-03-05T10:00:00Z"
    }
  }

 
Status Codes:
  
200 OK: Profile retrieved successfully.

404 Not Found: Username not found.

401 Unauthorized: Invalid or missing API key.


2. Wallet
Interact with Pi wallets for transactions and balance checks.
GET /wallet/{username}/balance
Check a user’s Pi balance.
Method: GET

URL: /wallet/{username}/balance

Path Parameters:
username (string, required): The TruthWeb username.

Headers:
Authorization: Bearer <your-api-key>


Response:

{
  "status": "success",
  "data": {
    "username": "pioneer123",
    "balance_pi": 150.75,
    "updated_at": "2025-03-05T12:00:00Z"
  }
}

Status Codes:
200 OK: Balance retrieved successfully.

404 Not Found: User not found.

401 Unauthorized: Invalid or missing API key.


POST /wallet/transfer
Initiate a Pi transfer between users.
Method: POST

URL: /wallet/transfer

Headers:
Authorization: Bearer <your-api-key>

Content-Type: application/json

{
  "from_username": "pioneer123",
  "to_username": "pioneer456",
  "amount_pi": 10.50,
  "description": "Payment for eBook"
}

Body:

{
  "from_username": "pioneer123",
  "to_username": "pioneer456",
  "amount_pi": 10.50,
  "description": "Payment for eBook"
}

Response:

{
  "status": "success",
  "data": {
    "transaction_id": "txn_123456789",
    "from_username": "pioneer123",
    "to_username": "pioneer456",
    "amount_pi": 10.50,
    "timestamp": "2025-03-05T12:05:00Z"
  }
}

Status Codes:
201 Created: Transfer initiated successfully.

400 Bad Request: Invalid parameters (e.g., insufficient balance).

401 Unauthorized: Invalid or missing API key.

3. Marketplace
Access and manage marketplace listings.
GET /marketplace/listings
List available marketplace items.
Method: GET

URL: /marketplace/listings

Query Parameters:
category (string, optional): Filter by category (e.g., "digital", "physical", "services").

limit (integer, optional): Number of results (default: 10).

offset (integer, optional): Pagination offset (default: 0).

Headers:
Authorization: Bearer <your-api-key>

Response:

{
  "status": "success",
  "data": [
    {
      "id": "lst_001",
      "title": "Pi Programming eBook",
      "category": "digital",
      "price_pi": 5.00,
      "seller_username": "pioneer789",
      "created_at": "2025-03-01T09:00:00Z"
    },
    {
      "id": "lst_002",
      "title": "Handmade Pi Mug",
      "category": "physical",
      "price_pi": 15.00,
      "seller_username": "pioneer456",
      "created_at": "2025-03-02T14:00:00Z"
    }
  ],
  "meta": {
    "total": 25,
    "limit": 10,
    "offset": 0
  }
}

Status Codes:
200 OK: Listings retrieved successfully.

401 Unauthorized: Invalid or missing API key.

Error Handling
All endpoints return errors in this format:

{
  "status": "error",
  "message": "Invalid API key",
  "code": 401
}


Rate Limits
Limit: 100 requests per minute per API key.

Response Header: X-RateLimit-Remaining indicates remaining requests.

Getting Started
Register: Sign up at the TruthWeb Developer Portal (#) (coming soon) to get your API key.

Explore: Clone the TruthWeb GitHub repo for sample code.

Contribute: Submit pull requests to enhance the API—it's open-source!

Support
Issues: Report bugs or request features on GitHub Issues.

Contact: Reach out via support@truthweb.com (mailto:support@truthweb.com).

Last Updated: March 05, 2025



---

### Key Features of `api.md`

1. **Overview**:
   - Introduces the API as open-source, tying into your `developers.html#api` description: "Integrate Pi into your apps with our API."
   - Specifies a placeholder base URL (`https://api.truthweb.com/v1/`) for future deployment.

2. **Endpoints**:
   - **User Profiles**: Basic profile retrieval (`GET /profiles/{username}`).
   - **Wallet**: Balance check (`GET /wallet/{username}/balance`) and Pi transfer (`POST /wallet/transfer`), reflecting TruthWeb’s wallet focus.
   - **Marketplace**: Listing retrieval (`GET /marketplace/listings`), aligning with your multi-category marketplace.

3. **Developer-Friendly**:
   - Includes authentication (API key), example requests/responses, status codes, rate limits, and error handling.
   - Links to GitHub for open-source access and contribution.

4. **Future-Proof**:
   - Designed for your Django backend with DRF, which can easily implement these endpoints once live.

---

### Deployment Instructions

1. **Create the Docs Folder**:
   - In your `TruthWeb` repository root, create a `docs/` directory:
     ```bash
     mkdir docs
     ```

2. **Save the File**:
   - Copy the Markdown content into `TruthWeb/docs/api.md`. Use a text editor (e.g., VS Code) or command line:
     ```bash
     echo "# TruthWeb Open-Source API Documentation" > docs/api.md
     # Add the rest of the content manually or via editor
     ```

3. **Push to GitHub**:
   - Add and commit:
     ```bash
     git add docs/api.md
     git commit -m "Add API documentation in docs/api.md"
     git push origin main
     ```

4. **Verify**:
   - Visit `https://github.com/username/TruthWeb/blob/main/docs/api.md` (replace `username`) to view the rendered Markdown.
   - Update the `developers.html` "Get API Docs" link to point to this file (already done in the updated version).

---

### Notes
- **Username**: Replace `username` in `https://github.com/username/TruthWeb` with your actual GitHub username.
- **Placeholder Links**: `#` placeholders (e.g., Developer Portal) should be updated once you have actual URLs.
- **Backend Integration**: When your Django backend is ready, use DRF to implement these endpoints (e.g., `APIView` or `ViewSet` classes) and host them. Update the base URL accordingly.
- **Enhancements**: Add more endpoints (e.g., escrow, instant transactions) or detailed examples (e.g., cURL commands) as your API grows.

