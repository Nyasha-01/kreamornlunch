
# Lunch Order System

A Flask-based web application for managing lunch orders in organizations. The system allows users to place orders for meals and provides administrators with tools to manage menus, orders, and user accounts.

## Features

### For Users
- **User Registration & Login**: Secure account creation and authentication
- **Weekly Order Management**: Place orders for multiple days of the week
- **Daily Order Submission**: Submit orders for individual days
- **Mobile-Friendly Interface**: Responsive design that works on all devices

### For Administrators
- **Menu Management**: Create and update weekly menus with customizable categories
- **Order Tracking**: View and manage all user orders by date
- **User Management**: Create accounts, reset passwords, and manage admin privileges
- **Category Management**: Add/remove meal categories and set exclusive categories
- **Export Functionality**: Export orders to Excel spreadsheets
- **Pricing Management**: Set and update meal prices
- **Data Cleanup**: Automatic cleanup of old orders (15+ days)

## Installation & Setup

### Web Application (Flask)

1. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

2. **Run the Application**:
   ```bash
   python main.py
   ```

3. **Access the Application**:
   Open your browser and navigate to `http://localhost:5000`

### Mobile Application (Android)

The project includes Buildozer configuration for creating Android APKs:

1. **Install Buildozer**:
   ```bash
   pip install buildozer
   ```

2. **Build APK**:
   ```bash
   buildozer android debug
   ```

## Default Login

When first running the application, a default admin account is created:
- **Username**: admin
- **Password**: admin1234

**Important**: Change this password immediately after first login for security.

## File Structure

```
├── main.py                    # Main Flask application
├── buildozer.spec            # Android build configuration
├── requirements.txt          # Python dependencies
├── templates/                # HTML templates
│   ├── admin.html           # Admin dashboard
│   ├── index.html           # Homepage
│   ├── login.html           # Login page
│   ├── register.html        # Registration page
│   └── weekly_order.html    # Order placement page
├── categories.json          # Meal categories
├── exclusive_categories.json # Exclusive category settings
├── meal_price.json         # Current meal pricing
├── orders.json             # User orders database
├── users.json              # User accounts database
└── weekly_menu.json        # Weekly menu data
```

## Configuration

### Default Categories
The system comes with three default meal categories:
- **proteins**: Main protein items
- **starch**: Carbohydrate options
- **salad**: Fresh salad options

### Adding Custom Categories
Administrators can add custom categories through the admin panel. Categories can be set as "exclusive" - selecting from an exclusive category will disable other category selections.

### Data Storage
All data is stored in JSON files:
- User accounts and authentication data
- Weekly menus and categories
- Order history and tracking
- System configuration settings

### Automatic Cleanup
The system automatically removes order data older than 15 days to prevent storage buildup. This runs as a background task and can also be triggered manually by administrators.

## API Endpoints

### User Routes
- `GET /` - Homepage
- `GET /login` - Login page
- `POST /login` - Process login
- `GET /register` - Registration page
- `POST /register` - Process registration
- `GET /weekly_order` - Weekly order page
- `POST /submit_weekly_order` - Submit weekly orders
- `POST /submit_daily_order` - Submit single day order

### Admin Routes
- `GET /admin` - Admin dashboard
- `POST /update_weekly_menu` - Update menu items
- `POST /admin_place_order` - Place order for user
- `POST /add_category` - Add new meal category
- `POST /remove_category` - Remove meal category
- `POST /toggle_exclusive_category` - Toggle category exclusivity
- `POST /update_meal_price` - Update meal pricing
- `GET /export_orders` - Export orders to Excel

### Utility Routes
- `GET /debug/menu` - Debug menu state (admin only)
- `GET /debug/menu_delivery` - Debug menu delivery (admin only)
- `POST /admin/cleanup` - Manual cleanup trigger

## Security Features

- **Password Hashing**: All passwords are hashed using SHA-256
- **Session Management**: Secure user sessions with Flask sessions
- **Admin Protection**: Admin-only routes with proper authorization
- **Input Validation**: Form validation and sanitization

## Mobile Support

The application includes Buildozer configuration for Android deployment:
- **Target API**: Android API 33
- **Minimum API**: Android API 21
- **Permissions**: Internet access and network state
- **Orientation**: Portrait mode

## Troubleshooting

### Common Issues

1. **Import Errors**: Ensure all dependencies are installed via `pip install -r requirements.txt`
2. **Port Conflicts**: The app runs on port 5000 by default - ensure this port is available
3. **File Permissions**: Ensure the application has write permissions for JSON data files
4. **Mobile Build Issues**: For Android builds, ensure you have the Android SDK and NDK installed

### Debug Features

The application includes debug endpoints for troubleshooting:
- `/debug/menu` - Check current menu state
- `/debug/menu_delivery` - Verify menu data delivery

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is open source and available under the MIT License.
