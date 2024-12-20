---

# **SQL and LDAP Query Protection Middleware for Laravel**

This package provides **middleware** for Laravel applications to prevent **SQL injection** and **LDAP injection** attacks. It ensures secure communication by blocking malicious queries, protecting both your **database** and **directory services**.

---

## **Features**  
- **SQL Injection Protection:**  
  Validates and sanitizes SQL queries to prevent unauthorized access.  
- **LDAP Injection Protection:**  
  Prevents malicious LDAP queries by sanitizing input before querying directory services.  
- **Custom Logging:**  
  Logs suspicious queries for monitoring and further analysis.  
- **Easy to Configure:**  
  Configurable middleware with options for logging and handling injection attempts.

---

## **Installation**  

You can install the package via **Composer**.

### **1. Require the Package**  
```bash
composer require protect/sql-query-protection
```
Alternatively, you can install the latest development version:
```bash
composer require protect/sql-query-protection:@dev
```

### **2. Publish the Configuration File**  
```bash
php artisan vendor:publish --provider="SqlQueryProtection\SqlQueryProtectionServiceProvider"
```

### **3. Clear Config Cache**  
After publishing the configuration, clear the config cache:
```bash
php artisan config:clear
```

---
Route Middleware Registration
If you prefer to apply the middleware to specific routes, add the following line to the $routeMiddleware array:

```bash
protected $routeMiddleware = [
    // Other route middleware...
    'sql.protection' => \SqlQueryProtection\Middleware\SqlQueryProtection::class,
];
```
You can then use the middleware in your routes like this:
```bash
Route::middleware(['sql.protection'])->group(function () {
    Route::get('/your-route', 'YourController@yourMethod');
});
```
---
---

## **Usage: SQL Protection Command**

This package provides an **Artisan command** to scan your routes for SQL injection vulnerabilities.

### **Command Syntax**  
```bash
php artisan sqlprotection:scan
```

### **Sample Output:**
```plaintext
Running SQL Protection Scan...
Checking route: api/users
Checking route: api/orders

No SQL injection vulnerabilities detected.
```

If vulnerabilities are detected, they will be listed as follows:
```plaintext
Potential SQL injection vulnerabilities found in the following routes:
- api/orders
```

---

## **Configuration Options**  

The configuration file is located at `config/sqlqueryprotection.php`. You can adjust the following settings:

```php
return [
    'sql_protection_enabled' => true,
    'xss_protection_enabled' => true,
];
```

- **`sql_protection_enabled`**: Enables/Disables SQL injection protection.  
- **`xss_protection_enabled`**: Enables/Disables XSS protection.

---

## **Troubleshooting**  

If the `sqlprotection:scan` command is not recognized or the package does not function as expected, follow these steps:

1. **Ensure the Service Provider is Registered:**  
   Confirm the service provider is registered in `config/app.php`:
   ```php
   'providers' => [
       SqlQueryProtection\SqlQueryProtectionServiceProvider::class,
   ],
   ```

2. **Run `composer dump-autoload`:**  
   ```bash
   composer dump-autoload
   ```

3. **Clear Application Cache:**  
   ```bash
   php artisan cache:clear
   php artisan config:clear
   ```

---

This **README** provides all the necessary steps to install, configure, and use the package effectively, including details about the **Artisan command** and **configuration options**.