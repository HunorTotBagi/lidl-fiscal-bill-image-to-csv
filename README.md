# Lidl Fiscal Bill Image to CSV

The objective was to develop a script capable of scanning an image, specifically a fiscal bill from Lidl. Fortunately, Lidl possesses its own application, which generates high-quality images, thereby simplifying the extraction process.
The outcome have the product name in the first column, accompanied by the formula `=price*amount` in the adjacent column. This particular format is chosen due to its practicality, as it allows for seamless transfer into Excel or Google Sheets.

## Prerequisites

Before running the code, ensure that you have the following dependencies installed: 
- `pytesseract`
- `cv2`

You can install these libraries using `pip`:
```
pip install pytesseract
```

## Data

- The code defines the start and end strings to identify the desired substring that contains the product name and price
- The `find_substring` function is defined to find the index of the first occurrence of a substring within a string
- The start and end indices of the desired substring are found using the `find_substring` function
- The substring containing the products and prices is extracted from the text
- The extracted substring is split into a list of lines using the newline character as the delimiter
- Empty lines are removed from the list of lines
- The `create_df` function is defined to create a pandas DataFrame with two columns: `article name` and `price`
- The lines list is iterated, processing two lines at a time
- The article name is extracted from the first line by splitting it at `/` and taking the first part
- The price is formatted in a way that it can be used for calculations in Excel or Google Sheets
- A dictionary representing a row with the article name and price is created
- The new row is concatenated to the data frame
- The populated data frame is returned
- The `create_df` function is called with the `clean_lines` input, and the resulting data frame is assigned to the variable df
- The resulting data frame is printed
