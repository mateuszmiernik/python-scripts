# CSV to SQL Inserts Generator

Converts CSV/Excel data into SQL INSERT statements with automatic sequence generation.

## 🎯 Problem

You have data in a CSV file and need to import it into a database table. Manually writing INSERT statements is time-consuming and error-prone.

## 🚀 What it does

- Reads CSV files and generates SQL INSERT statements
- Automatically creates sequence names based on table name
- Escapes special characters in text fields
- Creates ready-to-execute SQL scripts

## 🔧 Usage

```python
# Generate INSERT statements
generate_insert_statements(
    csv_file='countries.csv',
    table_name='COUNTRIES',
    output_file='countries_insert.sql'
)

# With custom sequence
generate_insert_statements(
    csv_file='countries.csv',
    table_name='COUNTRIES',
    sequence_name='MY_CUSTOM_SEQ'
)
```

## 📊 Example

**Input CSV:**
```csv
COUNTRY,ALPHA_2_CODE,ALPHA_3_CODE,NUMERIC
United States,US,USA,840
Germany,DE,DEU,276
```

**Generated SQL:**
```sql
INSERT INTO COUNTRIES (ID, COUNTRY, ALPHA_2_CODE, ALPHA_3_CODE, NUMERIC) VALUES (COUNTRIES_SEQ.NEXTVAL, 'United States', 'US', 'USA', 840);
INSERT INTO COUNTRIES (ID, COUNTRY, ALPHA_2_CODE, ALPHA_3_CODE, NUMERIC) VALUES (COUNTRIES_SEQ.NEXTVAL, 'Germany', 'DE', 'DEU', 276);
```

## 📋 Requirements

- Python 3.x
- pandas: `pip install pandas`

## 🧪 Testing

Run the script - it includes sample data for immediate testing.

---

**Use case**: Database migrations, bulk data imports, reference data setup