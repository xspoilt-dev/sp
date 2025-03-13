
# Account Management API
 
This API provides endpoints for managing user accounts, including creation, 
balance management, and number changes.

## Base URL
```
https://your-domain.com/api/a.php
```

## Authentication
All requests require an API key parameter (`api_key`).

## General Response Format
All responses are in JSON format with the following structure:
```json
{
  "success": boolean,       // true for successful operations, false otherwise
  "message": string,        // descriptive message about the result
  "data": mixed|null        // operation-specific data or null on error
}
```

## Endpoints

### 1. Create Account
Creates a new user account with initial balance.

**URL:** `https://teamdccs.com/api/spoof/?action=create_account`

**Method:** GET/POST

**Parameters:**
- `action=create_account` (required)
- `api_key=YOUR_API_KEY` (required)
- `number=ACCOUNT_NUMBER` (required)
- `password=ACCOUNT_PASSWORD` (required)
- `balance=INITIAL_BALANCE` (required)

**Example Request:**
```
https://teamdccs.com/api/spoof/?action=create_account&api_key=YOUR_API_KEY&number=12345678901&password=secure123&balance=10
```

**Success Response:**
```json
{
  "success": true,
  "message": "Account created successfully",
  "data": {
    "number": "12345678901",
    "password": "secure123",
    "minutes": 10,
  }
}
```

**Error Responses:**
- `400` Missing required parameters
- `429` Request limit reached
- `402` Insufficient balance
- `500` Failed to create account

### 2. Add Balance
Adds balance to an existing account.

**URL:** `https://teamdccs.com/api/spoof/?action=add_balance`

**Method:** GET/POST

**Parameters:**
- `action=add_balance` (required)
- `api_key=YOUR_API_KEY` (required)
- `number=ACCOUNT_NUMBER` (required)
- `balance=AMOUNT_TO_ADD` (required)

**Example Request:**
```
https://teamdccs.com/api/spoof/?action=add_balance&api_key=YOUR_API_KEY&number=12345678901&balance=5
```

**Success Response:**
```json
{
  "success": true,
  "message": "Balance added successfully",
  "data": {
    "number": "12345678901",
    "added_minutes": 5,
    "new_balance_minutes": 15,
  }
}
```

**Error Responses:**
- `400` Missing required parameters
- `404` Number not found
- `402` Insufficient balance
- `500` Failed to add balance

### 3. Change Number
Changes an account's phone number.

**URL:** `https://teamdccs.com/api/spoof/?action=change_number`

**Method:** GET/POST

**Parameters:**
- `action=change_number` (required)
- `api_key=YOUR_API_KEY` (required)
- `old_number=CURRENT_NUMBER` (required)
- `number=NEW_NUMBER` (required)
- `password=ACCOUNT_PASSWORD` (required)

**Example Request:**
```
https://teamdccs.com/api/spoof/?action=change_number&api_key=YOUR_API_KEY&old_number=12345678901&number=19876543210&password=secure123
```

**Success Response:**
```json
{
  "success": true,
  "message": "Number changed successfully",
  "data": {
    "old_number": "12345678901",
    "new_number": "19876543210"
  }
}
```

**Error Responses:**
- `400` Missing required parameters
- `400` Missing old number
- `404` Number not found
- `500` Failed to change number

### 4. Get Balance
Retrieves the current balance for an account.

**URL:** `https://teamdccs.com/api/spoof/?action=get_balance`

**Method:** GET/POST

**Parameters:**
- `action=get_balance` (required)
- `api_key=YOUR_API_KEY` (required)
- `number=ACCOUNT_NUMBER` (required)
- `password=ACCOUNT_PASSWORD` (required)

**Example Request:**
```
https://teamdccs.com/api/spoof/?action=get_balance&api_key=YOUR_API_KEY&number=12345678901&password=secure123
```

**Success Response:**
```json
{
  "success": true,
  "message": "Balance retrieved successfully",
  "data": {
    "number": "12345678901",
    "minutes": 15,
    
  }
}
```

**Error Responses:**
- `400` Missing required parameters
- `500` Failed to retrieve balance

## Common Error Responses

**Authentication Errors:**
- `401` Missing API key
- `401` Invalid API key
- `503` Failed to authenticate with provider

**Other Errors:**
- `400` Invalid action

@version 1.1
@author API Development Team
@link https://your-domain.com/api/documentation Full API Documentation
