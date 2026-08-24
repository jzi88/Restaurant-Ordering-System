# Restaurant-Ordering-System

A full-stack digital restaurant ordering system designed for Italian restaurants.


## visit here

https://jzi88.github.io/Restaurant-Ordering-System/

---

## 📌 Project Overview

 a web-based restaurant ordering system designed to simplify the ordering process inside restaurants.

Instead of relying on traditional paper menus and manually communicating orders to the kitchen, customers can scan a QR code assigned to their table and access the digital menu directly from their phone.

The system consists of:

- 📱 Customer Digital Menu
- 🛒 Shopping Cart
- 👨‍🍳 Kitchen Dashboard
- 🔳 Table QR Codes
- 🗄️ Supabase Database
- ⚙️ Node.js / Express Backend
- 🎨 Responsive Italian-style UI

---

## ✨ Features

### 📱 Digital Menu

Customers can browse the restaurant menu directly from their phone.

The menu includes:

- Product name
- Price
- Category
- Availability
- Category filtering
- Add-to-cart functionality
- Responsive mobile-friendly design

The interface uses an Italian-inspired visual style based on olive, beige, cream, and natural colors.

---

### 🔳 QR Table Ordering

Each restaurant table can have its own QR code.

When a customer scans the QR code, the table number is automatically included in the URL.

The system detects the table number and automatically locks it so the customer cannot accidentally change the table.

---

### 🛒 Shopping Cart

Customers can:

- Add products
- Increase product quantity
- Decrease product quantity
- Remove products
- View the number of items
- View the total price
- Submit the order directly to the kitchen

The total price is calculated automatically based on the selected products and quantities.

---

### 👨‍🍳 Kitchen Dashboard

The kitchen has a dedicated dashboard for managing incoming orders.

Orders are divided into four stages:

```text
🟥 Pending
   ↓
🟧 Preparing
   ↓
🟩 Ready
   ↓
⬜ Completed
```

Kitchen staff can update the order status directly from the dashboard.

The system also supports cancelling orders.

The kitchen dashboard displays:

- Table number
- Order time
- Elapsed time
- Ordered products
- Quantities
- Order total
- Current status

Orders that have been waiting for a longer period are visually highlighted.

The dashboard can automatically refresh to display new orders.

---

## 🗄️ Database

The project uses Supabase with PostgreSQL as the database.

The main database tables are:

### Products

Stores restaurant menu items.

| Column | Description |
|---|---|
| `id` | Product ID |
| `name` | Product name |
| `price` | Product price |
| `category` | Menu category |
| `available` | Product availability |

### Orders

Stores customer orders.

| Column | Description |
|---|---|
| `id` | Order ID |
| `table_id` | Restaurant table number |
| `status` | Current order status |
| `total` | Order total |
| `created_at` | Order creation timestamp |

### Order Items

Stores the individual products inside each order.

| Column | Description |
|---|---|
| `id` | Order item ID |
| `order_id` | Related order |
| `product_id` | Related product |
| `quantity` | Quantity ordered |

The relationships between these tables connect each order with its selected products.

---

## ⚙️ Backend

The backend is built using:

- Node.js
- Express.js
- Supabase JavaScript Client
- CORS
- dotenv

The backend provides REST API endpoints that connect the frontend with the database.

### API Endpoints

#### Get Products

```http
GET /api/products
```

Returns all available products.

#### Create Order

```http
POST /api/orders
```

Creates a new restaurant order.

Example request:

```json
{
  "table_id": "5",
  "items": [
    {
      "product_id": 37,
      "quantity": 2
    }
  ]
}
```

#### Get Orders

```http
GET /api/orders
```

Returns restaurant orders with their associated order items and products.

#### Update Order Status

```http
PUT /api/orders/:id/status
```

Used by the kitchen dashboard to update the order status.

Example:

```json
{
  "status": "preparing"
}
```

Supported statuses:

```text
pending
preparing
ready
completed
cancelled
```

#### Health Check

```http
GET /api/health
```

Used to verify that the backend server is running correctly.

---

## 🎨 Frontend

The frontend uses:

- HTML5
- CSS3
- JavaScript
- Tailwind CSS
- Google Fonts
- Responsive design

The customer interface is optimized for mobile devices because customers primarily access the menu through their phones.

The kitchen dashboard is designed for larger screens such as tablets, laptops, and desktop displays.

---

## 📱 Responsive Design

The system supports:

- 📱 Mobile phones
- 📲 Tablets
- 💻 Laptops
- 🖥️ Desktop screens

The interface automatically adapts to different screen sizes.

---

## 🛡️ Security Considerations

The backend does not trust prices sent from the client.

When an order is submitted, the server retrieves the product prices directly from the database and calculates the final order total.

This helps prevent customers from modifying product prices in the browser before submitting an order.

The backend also validates:

- Table number
- Product IDs
- Product availability
- Product quantities
- Order status values

Sensitive environment variables are stored outside the Git repository.


---



## 🔮 Future Improvements

Possible future improvements include:

- 💳 Online payment integration
- 👤 Customer accounts
- 📊 Admin dashboard
- 📈 Sales analytics
- 🔔 Real-time kitchen notifications
- 📦 Inventory management
- 🧾 Digital receipts
- 🌐 Multiple language support
- 🍕 Product images
- ⭐ Customer reviews
- 🏪 Multi-restaurant support

---



## 👩‍💻 Author

**Aljazi Alghamdi**

Computer Science Student — Taif University

Interested in:

- Cybersecurity
- Web Development
- Artificial Intelligence

---

## 📄 License

This project was developed as a web development project and can be further customized for restaurant use.
