# Rentium - Rental Management System

A comprehensive rental management system built with Laravel, Livewire, and Tailwind CSS. Rentium provides a modern, efficient solution for managing rental properties, tenants, payments, and maintenance requests.

## 🚀 Features

### Property Management
- **Property Listings**: Add, edit, and manage rental properties with detailed information
- **Property Categories**: Organize properties by type (apartment, house, commercial, etc.)
- **Media Management**: Upload and manage property photos and documents
- **Property Status Tracking**: Available, occupied, maintenance, etc.
- **Location Management**: GPS coordinates and address validation

### Tenant Management
- **Tenant Profiles**: Comprehensive tenant information and contact details
- **Lease Agreements**: Digital lease creation and management
- **Tenant Communication**: Built-in messaging system
- **Document Storage**: Store tenant documents securely
- **Tenant History**: Track rental history and references

### Financial Management
- **Rent Collection**: Automated rent tracking and collection
- **Payment Processing**: Multiple payment method support
- **Invoice Generation**: Automated invoice creation and delivery
- **Financial Reports**: Detailed financial analytics and reporting
- **Late Fee Management**: Automatic late fee calculation
- **Security Deposits**: Track and manage security deposits

### Maintenance & Support
- **Maintenance Requests**: Tenant-submitted maintenance requests
- **Work Order Management**: Assign and track maintenance tasks
- **Vendor Management**: Maintain contractor and vendor databases
- **Maintenance Scheduling**: Schedule routine maintenance
- **Cost Tracking**: Track maintenance expenses

### Dashboard & Analytics
- **Real-time Dashboard**: Overview of all system metrics
- **Revenue Analytics**: Income tracking and forecasting
- **Occupancy Reports**: Vacancy and occupancy statistics
- **Performance Metrics**: Property performance analysis
- **Custom Reports**: Generate custom business reports

## 🛠️ Technology Stack

- **Backend**: Laravel 12.x
- **Frontend**: Livewire 3.x
- **Styling**: Tailwind CSS 3.x
- **Database**: MySQL 8.0+ / PostgreSQL 13+
- **Cache**: Redis (optional)
- **Queue**: Laravel Queues
- **Storage**: Local / AWS S3 / Google Cloud Storage
- **Authentication**: Laravel Sanctum
- **Email**: SMTP / Mailgun / AWS SES

## 📋 Requirements

- PHP 8.1 or higher
- Composer 2.x
- Node.js 16+ and npm
- MySQL 8.0+ or PostgreSQL 13+
- Redis (optional, for caching and queues)

### PHP Extensions Required
- BCMath
- Ctype
- Fileinfo
- JSON
- Mbstring
- OpenSSL
- PDO
- Tokenizer
- XML
- GD or Imagick (for image processing)

## 🚀 Installation

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/rentium.git
cd rentium
```

### 2. Install Dependencies
```bash
# Install PHP dependencies
composer install

# Install Node.js dependencies
npm install
```

### 3. Environment Configuration
```bash
# Copy environment file
cp .env.example .env

# Generate application key
php artisan key:generate
```

### 4. Configure Environment Variables
Edit the `.env` file with your configuration:

```env
APP_NAME=Rentium
APP_ENV=local
APP_KEY=base64:your-generated-key
APP_DEBUG=true
APP_URL=http://localhost

# Database Configuration
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=rentium
DB_USERNAME=your_username
DB_PASSWORD=your_password

# Mail Configuration
MAIL_MAILER=smtp
MAIL_HOST=your-smtp-host
MAIL_PORT=587
MAIL_USERNAME=your-email
MAIL_PASSWORD=your-password
MAIL_ENCRYPTION=tls

# File Storage
FILESYSTEM_DISK=local
# For AWS S3 (optional)
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_DEFAULT_REGION=
AWS_BUCKET=

# Cache & Session
CACHE_DRIVER=file
SESSION_DRIVER=file
QUEUE_CONNECTION=sync

# Redis (optional)
REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379
```

### 5. Database Setup
```bash
# Run database migrations
php artisan migrate

# Seed the database with sample data (optional)
php artisan db:seed
```

### 6. Storage Setup
```bash
# Create symbolic link for storage
php artisan storage:link

# Set proper permissions
chmod -R 775 storage bootstrap/cache
```

### 7. Build Frontend Assets
```bash
# Development build
npm run dev

# Production build
npm run build
```

### 8. Start the Application
```bash
# Start Laravel development server
php artisan serve

# In another terminal, start Vite (for development)
npm run dev
```

The application will be available at `http://localhost:8000`

## 🔧 Configuration

### Queue Configuration
For production environments, configure queues for better performance:

```bash
# Set queue driver in .env
QUEUE_CONNECTION=redis

# Process queues
php artisan queue:work
```

### Task Scheduling
Add to your crontab for automated tasks:
```bash
* * * * * cd /path-to-your-project && php artisan schedule:run >> /dev/null 2>&1
```

### Performance Optimization
```bash
# Cache configuration
php artisan config:cache

# Cache routes
php artisan route:cache

# Cache views
php artisan view:cache

# Optimize autoloader
composer install --optimize-autoloader --no-dev
```

## 👤 Default Users

After seeding, you can use these default accounts:

**Admin User:**
- Email: admin@rentium.com
- Password: password

**Property Manager:**
- Email: manager@rentium.com
- Password: password

**Tenant:**
- Email: tenant@rentium.com
- Password: password

## 📱 API Documentation

Rentium includes a RESTful API for mobile applications and third-party integrations.

### Authentication
The API uses Laravel Sanctum for authentication. Include the bearer token in your requests:
```
Authorization: Bearer your-api-token
```

### Key Endpoints
- `GET /api/properties` - List all properties
- `GET /api/properties/{id}` - Get property details
- `GET /api/tenants` - List all tenants
- `POST /api/maintenance-requests` - Submit maintenance request
- `GET /api/payments` - List payments
- `POST /api/payments` - Process payment

Full API documentation is available at `/api/documentation` when the application is running.

## 🧪 Testing

```bash
# Run all tests
php artisan test

# Run with coverage
php artisan test --coverage

# Run specific test suite
php artisan test --testsuite=Feature
```

## 📊 Monitoring & Logging

### Logging
Logs are stored in `storage/logs/`. Configure log channels in `config/logging.php`.

### Error Tracking
For production, consider integrating with services like:
- Sentry
- Bugsnag
- Rollbar

## 🚀 Deployment

### Production Checklist
- [ ] Set `APP_ENV=production` and `APP_DEBUG=false`
- [ ] Configure proper database credentials
- [ ] Set up SSL certificate
- [ ] Configure mail service
- [ ] Set up queue workers
- [ ] Configure cron jobs
- [ ] Set up backup system
- [ ] Configure monitoring

### Server Requirements
- Web server (Apache/Nginx)
- PHP-FPM
- MySQL/PostgreSQL
- Redis (recommended)
- SSL certificate
- Regular backups

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines
- Follow PSR-12 coding standards
- Write tests for new features
- Update documentation as needed
- Use meaningful commit messages

## 🔒 Security

### Security Features
- CSRF protection
- SQL injection prevention
- XSS protection
- Authentication & authorization
- Rate limiting
- Input validation
- Secure file uploads

### Reporting Security Issues
Please report security vulnerabilities to security@rentium.com

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- **Documentation**: [docs.rentium.com](https://docs.rentium.com)
- **Issues**: [GitHub Issues](https://github.com/yourusername/rentium/issues)
- **Email**: support@rentium.com
- **Community**: [Discord](https://discord.gg/rentium)

## 🔄 Changelog

### Version 1.0.0 (Latest)
- Initial release
- Property management system
- Tenant management
- Payment processing
- Maintenance requests
- Dashboard and analytics

## 🚧 Roadmap

- [ ] Mobile application (React Native)
- [ ] Advanced reporting and analytics
- [ ] Integration with accounting software
- [ ] Multi-language support
- [ ] White-label solution
- [ ] AI-powered insights
- [ ] Automated lease renewals
- [ ] Advanced tenant screening

## 🙏 Acknowledgments

- Laravel community for the amazing framework
- Livewire team for reactive components
- Tailwind CSS for utility-first styling
- All contributors and testers

---

**Made with ❤️ by the Rentium Team**
