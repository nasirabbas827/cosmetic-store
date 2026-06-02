# Cosmetic‑store‑final  

A simple, fully‑functional online cosmetics store built with PHP. The repository contains the complete admin panel, buyer utilities (including PHPMailer integration), and the database schema required to run the application locally or on a production server.

---

## Overview  

Cosmetic‑store‑final is a web‑based e‑commerce platform that allows administrators to manage products, categories, orders, and customer feedback, while buyers can browse items, place orders, and receive email notifications. The project showcases a clean separation of concerns between the admin and buyer sections and includes ready‑to‑use SQL scripts, CSS styling, and email handling via PHPMailer.

---

## Features  

| Admin | Buyer |
|-------|-------|
| **Product Management** – Add, edit, delete products (`add_product.php`, `edit_product.php`, `view_products.php`). | **Product Catalog** – Browse products with images stored in `admin/products_images/`. |
| **Category Management** – Create and edit categories (`admin_category.php`, `edit_category.php`). | **Shopping Cart & Checkout** – Simple order placement flow. |
| **Order Management** – View orders, generate reports, update status (`order_report.php`, `update_order_status.php`). | **Order Confirmation Emails** – Sent via PHPMailer (`buyer/PHPMailer/`). |
| **User Management** – Admin login/logout (`admin_login.php`, `logout.php`). | **Contact & Complaints** – View and respond to customer complaints (`view_complaints.php`). |
| **Reviews & Ratings** – View and moderate product reviews (`view_reviews.php`). | **Secure Communication** – PHPMailer configured with placeholders for API keys. |
| **Responsive UI** – Styled with `admin/css/style.css`. | **Responsive UI** – Uses the same CSS assets for consistency. |

---

## Tech Stack  

| Layer | Technology |
|-------|------------|
| **Backend** | PHP 7+ |
| **Database** | MySQL – schema in `Database/cosmetic_db.sql` |
| **Email** | PHPMailer (bundled in `buyer/PHPMailer/`) |
| **Styling** | CSS (`admin/css/style.css`) |
| **Server** | Apache / Nginx (any LAMP/LEMP stack) |

---

## Installation  

1. **Clone the repository**  

   ```bash
   git clone https://github.com/yourusername/Cosmetic-store-final.git
   cd Cosmetic-store-final
   ```

2. **Set up the database**  

   ```bash
   # Log into MySQL and run the script
   mysql -u root -p < Database/cosmetic_db.sql
   ```

3. **Configure the application**  

   - Copy `admin/config.sample.php` to `admin/config.php` (if a sample file exists) or edit `admin/config.php` directly.  
   - Update the following placeholders with your own values:

     ```php
     // admin/config.php
     define('DB_HOST', 'localhost');
     define('DB_NAME', 'cosmetic_db');
     define('DB_USER', 'YOUR_DB_USERNAME');
     define('DB_PASS', 'YOUR_DB_PASSWORD');

     // PHPMailer settings (inside buyer/PHPMailer/get_oauth_token.php or wherever you configure SMTP)
     $mail->Host = 'smtp.example.com';
     $mail->Username = 'YOUR_SMTP_USERNAME';
     $mail->Password = 'YOUR_SMTP_PASSWORD';
     $mail->SMTPSecure = PHPMailer::ENCRYPTION_STARTTLS;
     $mail->Port = 587;
     ```

4. **Install Composer dependencies (PHPMailer)**  

   ```bash
   cd buyer/PHPMailer
   composer install
   ```

5. **Set proper file permissions** (if using Linux)  

   ```bash
   sudo chown -R www-data:www-data .
   sudo chmod -R 755 admin/products_images/
   ```

6. **Configure your web server**  

   - Point the document root to the