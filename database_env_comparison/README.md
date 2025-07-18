# Database Environment Comparison Tool

A Python script that compares database objects between DEV and UAT Oracle environments to identify differences and ensure environment synchronization before releases.

## 🎯 Purpose

When deploying database changes from DEV to UAT, it's critical to ensure both environments have the same database objects. This tool helps identify:
- Missing objects in UAT that exist in DEV
- Extra objects in UAT that don't exist in DEV
- Differences in object counts between environments

## 🚀 Features

- **Multi-Environment Support**: Compares DEV and UAT Oracle databases
- **Object Type Detection**: Automatically identifies all object types (tables, procedures, functions, etc.)
- **Detailed Comparison**: Shows exact differences with object names
- **Report Generation**: Creates text reports for documentation
- **Mock Testing**: Includes sample data for immediate testing

## 📋 Requirements

- Python 3.6+
- SQLAlchemy: `pip install sqlalchemy`
- cx_Oracle: `pip install cx_Oracle`

## 🔧 Usage

### Quick Test with Mock Data

```python
# Run this to see how the tool works
create_mock_comparison_test()
```

### Real Database Comparison

```python
# Update connection details
SCHEMA = 'YOUR_SCHEMA_NAME'

# Connect to databases
dev_engine = connect_to_db('dev_user', 'dev_pass', 'dev-host', '1521', 'dev_service')
uat_engine = connect_to_db('uat_user', 'uat_pass', 'uat-host', '1521', 'uat_service')

# Compare environments
dev_objects = fetch_object_names(dev_engine, 'TABLE', is_uat=False)
uat_objects = fetch_object_names(uat_engine, 'TABLE', is_uat=True)
compare_object_names(dev_objects, uat_objects, 'TABLE')
```

## 🧪 Example Output

```
🧪 Running Mock Database Comparison Test
==================================================

=== Testing TABLE Comparison ===
DEV TABLEs: 4 (CUSTOMERS, ORDERS, PRODUCTS, USERS)
UAT TABLEs: 3 (ORDERS, PRODUCTS, USERS)
❌ TABLEs differ between environments
  Only in DEV: CUSTOMERS

=== Testing PROCEDURE Comparison ===
DEV PROCEDUREs: 3 (GET_USER, PROCESS_ORDER, UPDATE_PRODUCT)
UAT PROCEDUREs: 4 (GET_USER, NEW_PROCEDURE, PROCESS_ORDER, UPDATE_PRODUCT)
❌ PROCEDUREs differ between environments
  Only in UAT: NEW_PROCEDURE

✅ Mock test completed!
```

## 🛠️ Functions

### `connect_to_db(user, password, host, port, service_name)`
Establishes connection to Oracle database using SQLAlchemy.

### `fetch_object_types(engine, is_uat)`
Retrieves all distinct object types from database (TABLE, PROCEDURE, FUNCTION, etc.).

### `fetch_object_names(engine, object_type, is_uat)`
Gets all object names for a specific object type.

### `compare_object_names(dev_objects, uat_objects, object_type)`
Compares object lists and identifies differences between environments.

### `generate_comparison_report(dev_engine, uat_engine, output_file)`
Creates comprehensive text report of all differences.

## 📊 What Gets Compared

- **Tables** - Data tables and their structure
- **Procedures** - Stored procedures
- **Functions** - Database functions
- **Triggers** - Database triggers
- **Views** - Database views
- **Sequences** - Auto-increment sequences
- **Indexes** - Database indexes
- **And more** - Any object type found in the schema

## 🔍 Use Cases

- **Pre-Release Validation**: Ensure UAT has all DEV objects before production deployment
- **Environment Auditing**: Regular checks to maintain environment consistency
- **Migration Planning**: Identify what needs to be deployed to UAT
- **DevOps Integration**: Automated environment validation in CI/CD pipelines
- **Database Maintenance**: Track object differences over time

## ⚠️ Configuration

Before running with real databases:

1. **Update Schema Name**: Change `SCHEMA = 'YOUR_SCHEMA_NAME'`
2. **Set Connection Details**: Update database connection parameters
3. **Verify Permissions**: Ensure user has access to `DBA_OBJECTS` (UAT) or `ALL_OBJECTS` (DEV)

## 📝 Report Format

Generated reports include:
- Summary of object types in each environment
- Detailed comparison for each object type
- Lists of objects unique to each environment
- Object counts for quick reference

## 🚨 Important Notes

- **Permissions**: UAT user needs `DBA_OBJECTS` access, DEV user needs `ALL_OBJECTS` access
- **Schema Filtering**: Only compares objects in the specified schema
- **Case Sensitivity**: Oracle object names are case-sensitive
- **Connection Security**: Store credentials securely, don't hardcode passwords

---

**Use case**: Database DevOps, Environment Management, Release Validation  
