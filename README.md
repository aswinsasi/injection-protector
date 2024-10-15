# SQL and LDAP Query Protection Middleware for Laravel

This package provides **middleware** for Laravel applications to prevent **SQL injection** and **LDAP injection** attacks. It protects your database and directory services by blocking malicious queries, ensuring secure communication between the application and backend services.

## Features
- **SQL Injection Protection:**  
  Validates and sanitizes SQL queries to prevent unauthorized access.
- **LDAP Injection Protection:**  
  Prevents malicious LDAP queries by sanitizing input before querying directory services.
- **Custom Logging:**  
  Suspicious queries are logged for monitoring and further analysis.
- **Easy to Configure:**  
  Configurable middleware with options for logging and handling injection attempts.

---

## Installation

You can install this package via Composer:

```bash
composer require protect/sql-query-protection


php artisan vendor:publish --provider="SqlQueryProtection\SqlQueryProtectionServiceProvider"


# SQL and LDAP Query Protection Middleware for Laravel

This package provides **middleware** for Laravel applications to prevent **SQL injection** and **LDAP injection** attacks. It protects your database and directory services by blocking malicious queries, ensuring secure communication between the application and backend services.

## Features
- **SQL Injection Protection:**  
  Validates and sanitizes SQL queries to prevent unauthorized access.
- **LDAP Injection Protection:**  
  Prevents malicious LDAP queries by sanitizing input before querying directory services.
- **Custom Logging:**  
  Suspicious queries are logged for monitoring and further analysis.
- **Easy to Configure:**  
  Configurable middleware with options for logging and handling injection attempts.

---

## Installation

You can install this package via Composer:

```bash
composer require protect/sql-query-protection
```

```bash
php artisan vendor:publish --provider="SqlQueryProtection\SqlQueryProtectionServiceProvider"
```



---

### SQL Query Protection Package

This package provides SQL injection protection by scanning routes and ensuring middleware is properly applied.  

---

### **Installation**

1. **Require the Package**  
   Install via Composer:  
   ```bash
   composer require your-vendor/package-name
   ```

2. **Publish Configuration**  
   Publish the configuration file to customize settings:  
   ```bash
   php artisan vendor:publish --tag=config
   ```

3. **Clear Config Cache**  
   After publishing, clear the config cache to ensure changes take effect:  
   ```bash
   php artisan config:clear
   ```

---

### **Usage: SQL Protection Command**

The package provides an Artisan command to scan your routes for SQL injection vulnerabilities.  

#### **Command Syntax**
```bash
php artisan sqlprotection:scan
```

#### **Output Example**
```plaintext
Running SQL Protection Scan...
Checking route: api/users
Checking route: api/orders

No SQL injection vulnerabilities detected.
```

If vulnerabilities are found, the output will list the affected routes:  
```plaintext
Potential SQL injection vulnerabilities found in the following routes:
- api/orders
```

---

### **Configuration Options**

The configuration file (`config/sqlqueryprotection.php`) includes the following options:

```php
return [
    'sql_protection_enabled' => true,
    'xss_protection_enabled' => true,
];
```

- **`sql_protection_enabled`**: Enable/Disable SQL protection scanning.
- **`xss_protection_enabled`**: Enable/Disable XSS protection checks.

---

### **Troubleshooting**

If the `sqlprotection:scan` command is not available, ensure the following:

1. **Service Provider**: Make sure the service provider is registered:
   ```php
   SqlQueryProtection\SqlQueryProtectionServiceProvider::class,
   ```

2. **Run `composer dump-autoload`**:
   ```bash
   composer dump-autoload
   ```

3. **Clear Application Cache**:
   ```bash
   php artisan cache:clear
   php artisan config:clear
   ```

---

This will make sure users have all the necessary steps to use your package and command efficiently.
