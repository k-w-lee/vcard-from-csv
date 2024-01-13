# VCard Generator

This is a Python script that generates vCards based on a provided DataFrame and dictionary of column mappings. The script includes various functions to preprocess the data, validate the column mappings, clean and format the contact information, add a prefix to first names, and create and write the vCard entries to a file.

## Requirements

- Python 3.0 or higher
- Pandas library

## Usage

1. Import the required libraries:

   ```python
   import string
   import os
   import pandas as pd
   ```

2. Copy the source code for the VCard Generator functions.

3. Set the necessary constants and create a DataFrame with the contact information. The DataFrame should contain columns corresponding to the valid keys defined in the `VALID_KEYS` set:

   ```python
   df = pd.DataFrame(...)
   ```

4. Specify the column mappings as a dictionary. Each key in the dictionary should correspond to one of the valid keys, and the value should be the column name in the DataFrame that corresponds to that key. Ignore the key value pair if not available:

   ```python
   column_mappings = {
       "last_name": "Last Name Column",
       "first_name": "First Name Column",
       "org": "Organization Column",
       "title": "Title Column",
       "phone": "Phone Column",
       "email": "Email Column",
       "website": "Website Column",
       "street": "Street Column",
       "city": "City Column",
       "p_code": "Postal Code Column",
       "country": "Country Column"
   }
   ```

   Note: Make sure that the column names in the dictionary match the column names in your DataFrame.

5. Call the `vcf_card_generate` function, passing in the DataFrame, column mappings, and any optional parameters:

   ```python
   vcf_card_generate(df, column_mappings, prefix=None, path=None)
   ```

   - `prefix`: A prefix to be added to the first names in the vCards. This is an optional parameter and can be set to `None`.
   - `path`: The path to save the vCard file. This is an optional parameter and can be set to `None`.

6. The vCard entries will be generated based on the provided DataFrame and column mappings. If a prefix is specified, it will be added to the first names. The vCard entries will be written to a file specified by the `path` parameter. If no `path` is provided, the default file name is "result.vcf".

   Example output:

   ```
   Generated vcard. 10 of them. At result.vcf
   ```

## Notes

- The provided DataFrame should include columns corresponding to the valid keys defined in the `VALID_KEYS` set. If any of the required columns are missing, the script will raise an error.

- The script performs preprocessing and cleaning operations on the contact information to ensure the vCard entries are formatted correctly. It removes special characters, spaces, and punctuation, and formats names and phone numbers appropriately.

- The vCard file is written in the vCard 3.0 format, following the mappings defined by the [vCard RDF Specification](https://www.w3.org/TR/vcard-rdf/#Mapping).

- The script uses the Pandas library for data manipulation. Make sure the library is installed before running the script.

- The script prints a success message when the vCard generation is complete. The message includes the total number of vCard entries generated and the file path where the vCard file is saved.
