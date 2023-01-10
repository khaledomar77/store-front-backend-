 In this document I will show the main API endpoints and the database schema

# API Endpoints

    These are the notes from a meeting with the frontend developer that describe what endpoints the API needs to supply, as well as data shapes the frontend and backend have agreed meet the requirements of the application.
  API Endpoints.
  
  Products.

    Index (GET /products )
    Show (GET /products/:id)
    Create [token required] (POST /product)
    Delete [token required] (DELETE /products/:id)

Users

    Index [token required] (GET /users)
    Show [token required] (GET /users/:id)
    Create (POST users) (POST /user)
    Delete [token required] (DELETE /users/:id)

Orders

    Index [token required] (GET orders)
    Show [token required] (GET orders/:id)
    Create (POST /api/orders)
    Delete [token required] (DELETE orders/:id)

# Database schema 

table1:
    CREATE TABLE users(
    user_id SERIAL PRIMARY KEY,
    username VARCHAR(100) UNIQUE,
    password VARCHAR(100)
);

table2:
    CREATE TABLE products(
    product_id SERIAL PRIMARY KEY,
    product_name VARCHAR(100),
    price NUMERIC,
    description text
);

table3:
    CREATE TABLE orders(
    order_id SERIAL PRIMARY KEY,
    order_name VARCHAR(100),
    quantity integer,
    status VARCHAR(50),
    user_id integer NOT NULL,
    FOREIGN KEY user_id REFERENCES users (user_id)
);

table4:
    CREATE TABLE order_products(
    id SERIAL PRIMARY KEY,
    order_id integer REFERENCES orders (order_id),
    product_id integer REFERENCES products (product_id)
);
