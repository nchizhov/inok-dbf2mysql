## DBF to MySQL import

[![License](https://poser.pugx.org/inok/dbf2mysql/license)](https://packagist.org/packages/inok/dbf2mysql)
[![License](https://poser.pugx.org/inok/dbf2mysql/v/stable)](https://packagist.org/packages/inok/dbf2mysql)
[![License](https://poser.pugx.org/inok/dbf2mysql/d/monthly)](https://packagist.org/packages/inok/dbf2mysql)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/nchizhov/inok-dbf2mysql/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/nchizhov/inok-dbf2mysql/?branch=master)

### Description
This package converts DBASE/FoxPro files into MySQL tables. 

### Requires
* [Inok\Dbf](https://packagist.org/packages/inok/dbf)

### Using
```
new \Inok\Dbf2mysql\convert($config);
```
where **$config** is array of parameters

#### Config array parameters
* **db_host** - MySQL Server (default **localhost**)
* **db_port** - MySQL Port (default **3306**)
* **db_username** - MySQL Username (default: **root**)
* **db_password** - MySQL User Password (default: **empty**)
* **db_name** - MySQL Database name: *should exists* (**required**)
* **db_charset** - MySQL Table Charset (default: **utf-8**)
* **dbf_charset** - DBF-file charset for tables without defined encoding (default: **866**)
* **dbf_path** - Path to DBF-files (**required**)
* **dbf_list** - List of import DBF-files: *without extension, case-insensitive*. If **null** - import of all files from directory (default: **null**)
* **table_prefix** - Add prefix for table name (default: **null**) 
* **key_field** - Adds index to MySQL table after import (default: **null**)
* **columns_only** - Imports only columns from DBF-file (default: **false**)
* **deleted_records** - Import marked for deletion records: *creating column with name '**deleted**'* (default: **false**)
* **verbose** - Show import process in console (default: **true**)
* **log_path** - Log-file with import process. If *empty* or *null* - not logging (default: **current script directory**)

#### Notes
1. Empty Dates and TimeDates fields converts to **NULL**
2. General and Picture fields of DBF-files imports into BLOB-fields
3. Logical fields with values: **'t', 'y', 'д'** converts to **'1'**, otherwise - to **'0'**
4. MEMO-fields imports into TEXT-fields
 
#### License

This package is released under the __MIT license__.
