# python-scripts
# 🐍 Python Scripts Collection

A collection of small, useful Python scripts for automation, data handling, and daily tasks.

- `ctl_manager.ipynb` - Manages CTL (Control) files for database releases via Harness. Validates file existence, generates complete CTL files from repository folders, and ensures all database objects are properly listed before deployment.

- `appian_xsd_date_fixer.ipynb` – Fixes Appian XSD type mismatches by converting dateTime to date types for database columns with DATE columnDefinition. Automates XSD corrections for Custom Data Types (CDT) to ensure consistency between database schema and Appian data types.

- `csv_to_sql_inserts.ipynb` – Converts CSV/Excel data to SQL INSERT statements with automatic sequence generation. Perfect for bulk data imports, database migrations, and generating reference data scripts.

- `database_env_comparison.ipynb` – 🔍 Compares database objects between DEV and UAT Oracle environments. Identifies missing or extra tables, procedures, functions, and other objects to ensure environment synchronization before releases.