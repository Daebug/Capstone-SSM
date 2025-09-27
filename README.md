# 🏪 Smart Store Manager (SSM)

A comprehensive web-based business management system designed to help business owners efficiently manage their operations, track sales, monitor expenses, and generate insightful reports.

![Smart Store Manager](https://github.com/user-attachments/assets/2c61d183-5e79-41ed-ae6c-70948f3e4e05)

## 📋 Table of Contents

- [Features](#features)
- [System Architecture](#system-architecture)
- [User Roles](#user-roles)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Database Setup](#database-setup)
- [Configuration](#configuration)
- [Usage](#usage)
- [File Structure](#file-structure)
- [API Endpoints](#api-endpoints)
- [Contributing](#contributing)
- [License](#license)

## ✨ Features

### 🔐 Authentication & Authorization
- **Multi-role authentication** (Admin, Owner, Manager)
- **Email verification** system with secure token-based verification
- **Password reset** functionality via email
- **Profile management** with image upload and address validation
- **Session management** and secure logout

### 📊 Business Management
- **Multi-business support** - Owners can manage multiple businesses
- **Branch management** - Create and manage multiple branches per business
- **Product catalog** management with categories and pricing
- **Expense tracking** by type and category
- **Sales monitoring** with detailed transaction history

### 📈 Analytics & Reporting
- **Interactive dashboards** with Chart.js visualizations
- **Sales performance** tracking and analysis
- **Expense analysis** with category breakdown
- **Profit/Loss calculations** and financial insights
- **Custom date range filtering** for all reports
- **Excel export** functionality for all data

### 👥 Team Management
- **Manager assignment** to specific branches
- **Role-based access control** for different user types
- **Activity logging** for audit trails
- **Real-time messaging** between owners and managers

### 📱 Modern UI/UX
- **Responsive design** with Bootstrap 5
- **Interactive particle.js** background effects
- **Sweet Alert** for enhanced user notifications
- **Dynamic forms** with real-time validation
- **Search and filter** capabilities across all modules

## 🏗️ System Architecture

The application follows a **multi-tier architecture**:

```
┌─────────────────┐
│   Presentation  │  ← HTML/CSS/JavaScript (Frontend)
│      Layer      │
├─────────────────┤
│   Application   │  ← PHP Business Logic
│      Layer      │
├─────────────────┤
│   Data Access   │  ← MySQLi Database Connection
│      Layer      │
└─────────────────┘
```

### 🗂️ Database Schema

The system uses a MySQL database (`ssm`) with the following key tables:

- **`owner`** - Business owner accounts and profiles
- **`manager`** - Manager accounts assigned to branches
- **`admin`** - System administrators
- **`business`** - Business information and permits
- **`branch`** - Branch locations and details
- **`product`** - Product catalog and inventory
- **`sales`** - Sales transactions and records
- **`expense`** - Business expense tracking
- **`expense_type`** - Expense categories
- **`activity`** - System activity logs
- **`messages`** - Internal messaging system

## 👤 User Roles

### 🔧 Admin
- Approve/reject business owner registrations
- Manage user accounts and system settings
- View system-wide analytics and reports
- Monitor platform activity

### 🏢 Business Owner
- Register and manage multiple businesses
- Create and manage branch locations
- Assign managers to branches
- Track sales, expenses, and profitability
- Generate comprehensive business reports
- Export data to Excel formats

### 👨‍💼 Manager
- Manage assigned branch operations
- Record sales transactions
- View branch-specific reports
- Communicate with business owners
- Track daily operational metrics

## 🛠️ Technologies Used

### Backend
- **PHP 8.2+** - Server-side scripting
- **MySQL/MariaDB** - Database management
- **MySQLi** - Database connection and queries
- **PHPMailer** - Email functionality
- **PhpSpreadsheet** - Excel file generation

### Frontend
- **HTML5 & CSS3** - Structure and styling
- **JavaScript (ES6+)** - Client-side functionality
- **Bootstrap 5** - Responsive UI framework
- **Chart.js** - Data visualization
- **Particle.js** - Interactive backgrounds
- **SweetAlert2** - Enhanced alerts and modals
- **Font Awesome** - Icon library

### Development Tools
- **Composer** - PHP dependency management
- **Git** - Version control

## 📦 Installation

### Prerequisites
- **XAMPP/WAMP/LAMP** or similar PHP development environment
- **PHP 8.2** or higher
- **MySQL 5.7** or higher
- **Composer** for dependency management

### Step-by-Step Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/smart-store-manager.git
   cd smart-store-manager
   ```

2. **Install PHP dependencies**
   ```bash
   composer install
   ```

3. **Configure your web server**
   - Place the project in your web server's document root (e.g., `htdocs` for XAMPP)
   - Ensure mod_rewrite is enabled

4. **Database setup** (see [Database Setup](#database-setup) section)

5. **Configure environment** (see [Configuration](#configuration) section)

## 🗄️ Database Setup

1. **Create the database**
   ```sql
   CREATE DATABASE ssm CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
   ```

2. **Import the database schema**
   ```bash
   mysql -u root -p ssm < database/ssm_latest2025.sql
   ```

3. **Verify the import**
   - Check that all tables are created properly
   - Ensure sample data is loaded (if included)

## ⚙️ Configuration

### Database Configuration
Edit `conn/conn.php` to match your database settings:

```php
<?php
$host = "localhost";
$username = "your_db_username";
$password = "your_db_password";
$database_name = "ssm";

$conn = new mysqli($host, $username, $password, $database_name);
$conn->set_charset("utf8mb4");
?>
```

### Email Configuration
Configure email settings in your email-related endpoints for:
- **SMTP server** details
- **Email credentials** for sending verification emails
- **From address** and display name

### File Upload Configuration
Ensure the following directories have write permissions:
- `assets/profiles/` - User profile images
- `assets/valid_ids/` - ID verification documents
- `assets/permits/` - Business permits
- `assets/branch_permits/` - Branch permits

## 🚀 Usage

### For Business Owners

1. **Registration**
   - Register with email verification
   - Complete profile with required documents
   - Wait for admin approval

2. **Business Setup**
   - Add business information and permits
   - Create branch locations
   - Set up product catalog

3. **Operations**
   - Record sales transactions
   - Track business expenses
   - Monitor performance through dashboards

### For Managers

1. **Assignment**
   - Get assigned to a branch by the business owner
   - Receive login credentials

2. **Daily Operations**
   - Record sales for assigned branch
   - View branch performance reports
   - Communicate with business owner

### For Administrators

1. **User Management**
   - Review and approve owner registrations
   - Manage user accounts and permissions

2. **System Monitoring**
   - Monitor platform usage and activity
   - Generate system-wide reports

## 📁 File Structure

```
smart-store-manager/
├── admin/                 # Admin panel pages
│   ├── index.php         # Admin dashboard
│   ├── accounts.php      # User account management
│   └── business.php      # Business management
├── manager/              # Manager portal pages
│   ├── index.php         # Manager dashboard
│   ├── viewreports.php   # Reports and analytics
│   └── chatowner.php     # Communication with owners
├── owner/                # Business owner pages
│   ├── index.php         # Owner dashboard
│   ├── managebusiness.php # Business management
│   ├── tracksales.php    # Sales tracking
│   └── manageexpenses.php # Expense management
├── home/                 # Public pages
│   ├── index.php         # Landing page
│   ├── about-us.php      # About page
│   └── privacy-policy.php # Privacy policy
├── endpoints/            # API endpoints
│   ├── sign.php          # Authentication
│   ├── business/         # Business operations
│   ├── sales/            # Sales management
│   └── expenses/         # Expense tracking
├── components/           # Reusable components
│   ├── head_cdn.php      # CSS/JS includes
│   ├── *_sidebar.php     # Navigation sidebars
│   └── footer.php        # Footer component
├── assets/               # Static assets
│   ├── logo.png          # Application logo
│   ├── profiles/         # User profile images
│   └── permits/          # Document uploads
├── css/                  # Stylesheets
│   ├── style.css         # Main styles
│   └── excel.css         # Excel export styles
├── js/                   # JavaScript files
│   ├── chart.js          # Chart configurations
│   ├── particle.js       # Particle effects
│   └── *.js              # Page-specific scripts
├── json/                 # JSON data files
│   ├── refregion.json    # Philippine regions
│   ├── refprovince.json  # Provinces
│   └── ref*.json         # Address reference data
├── database/             # Database files
│   ├── ssm_latest2025.sql # Latest database schema
│   └── ssm (2).sql       # Backup schema
├── conn/                 # Database connection
│   ├── conn.php          # Database configuration
│   └── auth.php          # Authentication helpers
├── vendor/               # Composer dependencies
├── PHPMailer/            # Email library
├── composer.json         # PHP dependencies
└── README.md             # This file
```

## 🔌 API Endpoints

### Authentication
- `POST /endpoints/sign.php` - Login, register, email verification
- `POST /endpoints/reset-password.php` - Password reset
- `GET /endpoints/logout.php` - User logout

### Business Management
- `POST /endpoints/business/` - Business CRUD operations
- `POST /endpoints/product/` - Product management
- `POST /endpoints/branch/` - Branch management

### Sales & Expenses
- `POST /endpoints/sales/` - Sales transaction management
- `POST /endpoints/expenses/` - Expense tracking
- `GET /endpoints/reports/` - Generate reports

### Data Export
- `GET /export_excel.php` - Export various data to Excel
- `POST /import_excel.php` - Import data from Excel

## 🤝 Contributing

We welcome contributions to the Smart Store Manager project! Here's how you can help:

### Development Setup
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Test thoroughly
5. Commit your changes (`git commit -m 'Add amazing feature'`)
6. Push to the branch (`git push origin feature/amazing-feature`)
7. Open a Pull Request

### Coding Standards
- Follow PSR-12 coding standards for PHP
- Use meaningful variable and function names
- Comment complex logic
- Ensure responsive design for all UI changes
- Test across different browsers and devices

### Reporting Issues
- Use the GitHub issue tracker
- Provide detailed steps to reproduce
- Include screenshots for UI issues
- Specify browser and version

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Support

For support and questions:
- Create an issue on GitHub
- Check the existing documentation
- Review the database schema in `/database/`

## 🙏 Acknowledgments

- **Bootstrap** for the responsive UI framework
- **Chart.js** for beautiful data visualizations
- **PHPMailer** for reliable email functionality
- **SweetAlert2** for enhanced user experience
- **Font Awesome** for comprehensive icon library
- **Particle.js** for interactive background effects

---

**Smart Store Manager** - Empowering businesses with intelligent management solutions. 🚀

Built with ❤️ for small and medium businesses.