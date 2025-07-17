# CTL File Management Script

## Description
Script for managing CTL (Control files) used for database releases via Harness.

## Problem
During database releases we have a repository structure with folders:
- `Tbl/` - tables
- `Pro/` - procedures  
- `Trg/` - triggers
- `Fnc/` - functions
- `Vw/` - views
- `Seq/` - sequences
- `Idx/` - indexes

To release objects to higher environments (UAT/PROD), we create a `.ctl` file with a list of files to deploy, e.g.:
```
Tbl/users.tbl
Tbl/products.tbl
Pro/get_user.pro
Pro/update_product.pro
```

## Functionality
1. **CTL file checking** - verifies if all files listed in CTL exist in repo
2. **CTL generation** - automatically creates CTL file with all objects
3. **Path verification** - checks actual paths with case sensitivity

## Usage

### Quick start
1. Open `CTL.ipynb` in VS Code
2. Run cells sequentially (Ctrl+Enter)
3. Change paths in "USAGE EXAMPLES" section
4. Run test examples

### Main functions

#### check_file_existence(base_folder, ctl_file)
```python
# Check if all files from CTL exist
result = check_file_existence("C:\\repo\\my-db-project", "release.ctl")
```

#### generate_ctl_file(base_folder, output_ctl_file, folders_to_include, file_extensions)
```python
# Generate full CTL with all files
generate_ctl_file(
    base_folder="C:\\repo\\my-db-project",
    output_ctl_file="full_release.ctl",
    folders_to_include=['Tbl', 'Pro', 'Trg']
)
```

#### realcase(path)
```python
# Check actual file path
real_path = realcase("C:\\repo\\Tbl\\USER_TABLE.tbl")
```

## Test Examples
In the notebook you'll find ready test examples. Before running:
1. Set correct paths to your repository
2. Create sample CTL files
3. Run tests

## Requirements
- Python 3.x
- `os` module (built-in)
- Jupyter Notebook or VS Code with Python extension