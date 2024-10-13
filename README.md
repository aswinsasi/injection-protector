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
composer require your-vendor/sql-query-protection
