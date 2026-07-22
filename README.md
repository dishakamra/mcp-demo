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

### Products

- **GET** `/products` - Retrieve all products
- **GET** `/products/:id` - Retrieve a specific product by ID
- **POST** `/products` - Create a new product
- **PUT** `/products/:id` - Update a product
- **DELETE** `/products/:id` - Delete a product

### Example Requests

Get all products:
```bash
curl http://localhost:3000/products
```

Get a specific product:
```bash
curl http://localhost:3000/products/1
```

Create a new product:
```bash
curl -X POST http://localhost:3000/products \
  -H "Content-Type: application/json" \
  -d '{"name":"Product Name","price":99.99}'
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