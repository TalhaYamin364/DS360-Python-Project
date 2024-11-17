# Vendor Matching with Fuzzy Logic  

This project automates the process of matching vendor names between two datasets using fuzzy logic. It provides fast and accurate matching options, tailored for different performance and precision requirements.  

---

## Features  
- **Automatic Conversion**: Converts `combined_data.xlsx` to CSV for streamlined processing.  
- **Flexible Matching**: Matches vendor names in `combined_data.csv` against `vendors.csv`.  
- **Two Approaches**:  
  - **Fast Matching**: Optimized for speed with moderate accuracy using `RapidFuzz`.  
  - **Accurate Matching**: Detailed and precise matching, suitable when performance is not a concern.  
- **Output Results**: Saves matched data with vendor names and codes to separate CSV files.  
- **Duplicate Removal**: Ensures no duplicate vendor matches in the output.  

---

## Requirements  

Install the required Python libraries:  
```bash  
pip install pandas rapidfuzz tqdm openpyxl  
```

## File Descriptions  

### Input Files  
- **`combined_data.xlsx`**:  
  Input file containing vendor names to be matched. Ensure the relevant column is named **`Vendor Name`**.  

- **`vendors.csv`**:  
  Reference dataset with the following columns:  
  - **`vendor_name`**: Vendor names to match against.  
  - **`vendor_code`**: Corresponding vendor codes.  

### Scripts  
- **`find_vendors_fast.py`**:  
  Script for fast matching using `RapidFuzz`.  

- **`find_vendors_accurate.py`**:  
  Script for accurate matching by iterating through all rows.  

### Output Files  
- **`result_output.csv`**:  
  Result of the fast matching process.  

- **`result_output_two.csv`**:  
  Result of the accurate matching process.  

---

## Usage  

### Fast Matching  
For faster matching with moderate accuracy, execute:  
```bash
python find_vendors_fast.py
```

---

## Output:

- **`result_output.csv: Contains matched vendor names and codes`**.

### Accurate Matching

 - **`For more precise matching, execute:`**
```bash
python find_vendors_accurate.py
```

## Directory Structure
```plaintext
vendor-matching/
├── combined_data.xlsx       # Input file with vendor names
├── vendors.csv              # Reference file with vendor names and codes
├── find_vendors_fast.py     # Script for fast matching
├── find_vendors_accurate.py # Script for accurate matching
├── result_output.csv        # Output of fast matching
├── result_output_two.csv    # Output of accurate matching
└── README.md                # Project documentation
```

## How the Scripts Work

### Fast Matching (`find_vendors_fast.py`)

1. **File Conversion**: Converts `combined_data.xlsx` into `combined_data.csv`.
2. **Preprocessing**: Cleans and normalizes vendor names from `vendors.csv` (removes whitespace, converts to lowercase).
3. **Fuzzy Matching**: Compares vendor names in `combined_data.csv` against `vendor_name` in `vendors.csv` using RapidFuzz.
4. **Filtering Matches**: Retains matches with a similarity score > 80 and removes duplicates.
5. **Exporting Results**: Saves the matched data to `result_output.csv`.

### Accurate Matching (`find_vendors_accurate.py`)

1. **File Conversion**: Converts `combined_data.xlsx` into `combined_data_two.csv`.
2. **Preprocessing**: Performs the same cleaning and normalization steps as the fast script.
3. **Iterative Matching**: Compares each vendor name in `combined_data_two.csv` against every row in `vendors.csv` using `fuzz.ratio`.
4. **Capturing Matches**: Records all matches with a similarity score > 80 for greater accuracy.
5. **Exporting Results**: Saves the matched data to `result_output_two.csv`.



## Potential Enhancements

- **Error Handling**: Add support for detecting and handling missing or malformed data.
- **Advanced Similarity Metrics**: Incorporate additional similarity metrics for more precise matching.
- **User Interface**: Build a graphical user interface (GUI) to make the tool more user-friendly.
