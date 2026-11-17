# Emporium 👜

**An e-commerce website for handbags.** Shoppers can browse and search handbags from brands like ALDO, Michael Kors, Calvin Klein and Kate Spade, add them to a cart, enter shipping details and pay online. Staff get their own login and an analytics dashboard to manage products, customers, orders and warehouses.

Built as a **group project** for the Database Management Systems course in my Master's. I led the UI and user experience and also worked on the code.

🎥 **[Watch the video walkthrough](https://drive.google.com/file/d/1CCx8A_uxuN-d4pf5dSMLIGWpNykHdKow/view?usp=drive_link)**

<img width="1600" height="1023" alt="emporium-screens" src="https://github.com/user-attachments/assets/1e13e5ed-7d0c-4476-9bc0-c6e3c959bcb9" />

## Features

### For shoppers
- **Shop handbags** by type: handbags, sling bags, backpacks and wallets.
- **Sort by price**, low to high or high to low.
- **Search** by name, brand or bag type.
- **Product pages** with several photos of each bag.
- **Cart** that updates as you add or remove items.
- **Checkout:** enter a shipping address, review your items and pay with **Razorpay** (test mode, so no real money is charged).
- **Sign up and log in** to keep your cart and orders.

### For staff
- **Separate employee sign-up and login.**
- **Analytics dashboard** ("Emporium Analytics"): total inventory, customers, revenue and salespeople, plus charts of top-rated bag types and sales by region (Chart.js).
- **Manage the store:** create, view, update and delete products, customers, order items and warehouses.

## Tech stack

| Part | Tools |
|---|---|
| Back end | Python, Django 4.2 |
| Database | SQLite, through Django's ORM and migrations |
| Front end | Django templates, HTML, CSS, JavaScript, Bootstrap 5 |
| Payments | Razorpay (test mode) |
| Charts | Chart.js |

## Database design

The main focus of the course was the database. The data model connects the shop and the business behind it:

| Table | What it stores |
|---|---|
| Customer | Shoppers, linked to their login account |
| Product | Bags: name, brand, bag type, price, rating, stock and store |
| Order / OrderItem | Each cart and the bags in it, with quantities and Razorpay payment details |
| ShippingAddress | Where each order is delivered |
| StoreSalesperson | Sales staff: role, contact and salary |
| StoreTransaction | Sales, linked to the salesperson who made them |
| Region | Sales regions, their managers and total sales |
| StoreWarehouse | Warehouses: address, manager, staff and region |

The dashboard numbers come straight from the database, using queries that add up and average these tables (for example total revenue from transactions, and average rating by bag type).

## Run it locally

You need Python 3.11.

```bash
cd DBMS_PROJECT_ECOMMERCE
python -m venv venv
venv\Scripts\activate          # on Mac: source venv/bin/activate
pip install django==4.2.7 razorpay pillow
python manage.py migrate
python manage.py runserver
```

Then open http://127.0.0.1:8000 in your browser.

## Project structure

```
DBMS_PROJECT_ECOMMERCE/
  ecommerce/            Django project settings and main URLs
  store/models.py       The database tables
  store/views.py        Pages, cart, checkout, payment, dashboard and staff tools
  store/urls.py         All the website's routes
  store/Templates/      HTML pages
  store/static/         CSS, JavaScript and product images
  db.sqlite3            Sample database with products
```

## Team and my role

Built as a group project during my Master's. **My role:** I designed the UI and the shopping experience (the look, layout and flow from browsing to checkout) and worked on the code with the team.
