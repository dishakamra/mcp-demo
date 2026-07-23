# mcp-demo

## Setup

1. Install dependencies:
   ```bash
   npm install
   ```

2. Verify the project structure:
   ```
   src/
     ├── server.js
     ├── routes/
     │   └── products.js
     ├── services/
     │   └── productService.js
     └── models/
         └── product.js
   tests/
     ├── unit/
     │   └── product.model.test.js
     └── integration/
         └── products.api.test.js
   ```

## Run Commands

Start the development server:
```bash
npm start
```

The server will run on `http://localhost:3000` by default.

## Endpoints

### Health Check

* **GET** `/health`: Check server health status

### Products

* **GET** `/products`: Retrieve all products
* **GET** `/products/:id`: Retrieve a specific product by ID
* **POST** `/products`: Create a new product
* **PUT** `/products/:id`: Update an existing product
* **DELETE** `/products/:id`: Delete a product by ID

## Example Requests and Responses

### Health Check

Get server health status:
```bash
curl http://localhost:3000/health
```

Response (200 OK):
```json
{
  "status": "ok"
}
```

### Products

#### Get all products

Request:
```bash
curl http://localhost:3000/products
```

Response (200 OK):
```json
[
  {
    "id": "1",
    "name": "Keyboard",
    "price": 49.99
  }
]
```

#### Get a specific product by ID

Request:
```bash
curl http://localhost:3000/products/1
```

Response (200 OK):
```json
{
  "id": "1",
  "name": "Keyboard",
  "price": 49.99
}
```

Response (404 Not Found):
```json
{
  "error": "Not found"
}
```

#### Create a new product

Request:
```bash
curl -X POST http://localhost:3000/products \
  -H "Content-Type: application/json" \
  -d '{"name": "Mouse", "price": 19.99}'
```

Response (201 Created):
```json
{
  "id": "1",
  "name": "Mouse",
  "price": 19.99
}
```

Validation Error Response (400 Bad Request):
```json
{
  "error": "Validation failed",
  "details": [
    "name must be a string with at least 2 characters",
    "price must be a number greater than 0"
  ]
}
```

#### Update a product

Request:
```bash
curl -X PUT http://localhost:3000/products/1 \
  -H "Content-Type: application/json" \
  -d '{"name": "Mouse Pro", "price": 29.99}'
```

Response (200 OK):
```json
{
  "id": "1",
  "name": "Mouse Pro",
  "price": 29.99
}
```

Response (404 Not Found):
```json
{
  "error": "Not found"
}
```

#### Delete a product

Request:
```bash
curl -X DELETE http://localhost:3000/products/1
```

Response (204 No Content):
```
(empty body)
```

Response (404 Not Found):
```json
{
  "error": "Not found"
}
```

## Testing

### Unit Tests

Run unit tests:
```bash
npm run test:unit
```

Unit tests are located in `tests/unit/` and test individual components and models.

### Integration Tests

Run integration tests:
```bash
npm run test:integration
```

Integration tests are located in `tests/integration/` and test API endpoints and service interactions.

### Run All Tests

```bash
npm test
```
