# Hackathon-Marketplace

## Technologies Used

| Feature               | Technology |
|----------------------|------------|
| **Frontend**         | Next.js  |
| **Styling**          | Tailwind CSS (for fast and responsive UI) |
| **Backend**          | Sanity CMS (Headless CMS for content & product management) |
| **Database**         | Sanity CMS (Manages structured content) |
| **Hosting**          | Vercel (for deployment) |

---

# API Breakdown for Farmers E-Commerce Website

## 1. Authentication & Users API
- **Register a User** → `POST /api/users/register`
- **Login a User** → `POST /api/users/login`
- **Get User Profile** → `GET /api/users/:userId`

## 2. Products API
- **Add a Product (Farmer Only)** → `POST /api/products`
- **Get All Products** → `GET /api/products`
- **Get Single Product by ID** → `GET /api/products/:productId`
- **Update Product (Farmer Only)** → `PUT /api/products/:productId`
- **Delete Product (Farmer Only)** → `DELETE /api/products/:productId`

## 3. Orders API
- **Place an Order (Buyer Only)** → `POST /api/orders`
- **Get Buyer Orders** → `GET /api/orders/:buyerId`
- **Update Order Status (Admin/Farmer)** → `PUT /api/orders/:orderId`

## 4. Categories API
- **Get All Categories** → `GET /api/categories`
- **Add a Category (Admin Only)** → `POST /api/categories`

## 5. Reviews API (Optional)
- **Add a Review** → `POST /api/reviews`
- **Get Reviews for a Product** → `GET /api/reviews/:productId`




# Schema

### Users Table
| Field    | Type   | Description                  |
|----------|--------|-----------------------------|
| userId   | string | Unique identifier for user  |
| name     | string | User's full name            |
| email    | string | User's email address        |
| password | string | Hashed password             |
| role     | string | "farmer" or "buyer"         |
| phone    | string | User's phone number         |
| address  | string | User's address              |

---

### Products Table
| Field       | Type   | Description                                  |
|------------|--------|---------------------------------------------|
| productId  | string | Unique identifier for product              |
| name       | string | Product name                               |
| category   | string | Category (e.g., "seeds", "vegetables")     |
| price      | number | Price of the product                       |
| quantity   | number | Available stock quantity                   |
| sellerId   | string | Reference to `Users.userId` (seller)       |
| description| string | Detailed product description               |

---

### Orders Table
| Field          | Type   | Description                              |
|--------------|--------|-----------------------------------------|
| orderId     | string | Unique identifier for order             |
| buyerId     | string | Reference to `Users.userId` (buyer)     |
| products    | array  | List of ordered products with quantity  |
| totalPrice  | number | Total cost of the order                 |
| status      | string | Order status (e.g., "pending", "completed") |
| deliveryAddress | string | Shipping address                      |

---

### Categories Table
| Field      | Type   | Description                    |
|------------|--------|--------------------------------|
| categoryId | string | Unique identifier for category |
| name       | string | Category name (e.g., "Seeds")  |

---

### Reviews Table (Optional)
| Field      | Type   | Description                              |
|------------|--------|-----------------------------------------|
| reviewId   | string | Unique identifier for review           |
| productId  | string | Reference to `Products.productId`      |
| userId     | string | Reference to `Users.userId` (reviewer) |
| rating     | number | Rating (e.g., 1-5 stars)               |
| comment    | string | Review comment                         |
