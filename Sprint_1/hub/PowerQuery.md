# 1. Open Power Query Editor

* Open Power BI Desktop  
* Import your dataset: Home ➝ Get data  
* Go to Home ➝ Transform Data  
* This opens the Power Query Editor  

---

# 2. Clean Data (Text, Blanks, Nulls, Types)

## 2.1 Trim, Clean, or Uppercase/Lowercase Text

Select the text column → go to Transform tab:

* **Trim** – Transform ➝ Format ➝ Trim (Remove leading/trailing spaces)  
* **Clean** – Transform ➝ Format ➝ Clean (Remove non-printable characters)  
* **Uppercase** – Format ➝ UPPERCASE (Standardize text)  
* **Lowercase** – Format ➝ lowercase (Emails, URLs)  
* **Capitalize Each Word** – Format ➝ Capitalize Each Word (Names, addresses)  


<img width="1878" height="861" alt="image" src="https://github.com/user-attachments/assets/418e564b-e21d-4e54-bdbb-009c7e43c1a6" />

<img width="1901" height="998" alt="image" src="https://github.com/user-attachments/assets/efd811f9-9015-4de1-88ab-e860f21db90a" />

<img width="1890" height="974" alt="image" src="https://github.com/user-attachments/assets/f0df8346-e951-4459-b0bf-b07333d1d2f3" />

<img width="1899" height="991" alt="image" src="https://github.com/user-attachments/assets/3161d0cf-6b94-4d26-ac8b-695c0e039a3b" />

<img width="1897" height="1018" alt="image" src="https://github.com/user-attachments/assets/9e89c699-0f87-44ec-8a87-94e3af0eaec2" />


---

## 2.2 Change Data Types

Important for calculations later.

Steps:

* Select column  
* Transform ➝ Data Type  
* Choose: *Text*, *Whole Number*, *Decimal*, *Date*, *DateTime*, etc.  

<img width="1896" height="993" alt="image" src="https://github.com/user-attachments/assets/2675e15e-de1f-45fb-8c62-09053ad26b2b" />

---

# 3. Add or Remove Rows

## 3.1 Remove Unwanted Rows

Go to Home ➝ Reduce Rows ➝ Remove Rows

Options:

* Remove Top Rows (e.g., headers from messy CSV)  
* Remove Bottom Rows  
* Remove Alternate Rows  
* Remove Blank Rows  
* Remove Duplicates  

Remove duplicates: Home ➝ Remove Rows ➝ Remove Duplicates  

<img width="1918" height="1011" alt="image" src="https://github.com/user-attachments/assets/cd4ccf78-5361-40e3-a2ed-c11e05255eea" />

<img width="1891" height="1052" alt="image" src="https://github.com/user-attachments/assets/acbd2e51-d0ff-497d-aff0-2333ea5d54d8" />

<img width="1891" height="990" alt="image" src="https://github.com/user-attachments/assets/74294f22-92dc-46b0-9805-23e28e246fed" />

<img width="1893" height="977" alt="image" src="https://github.com/user-attachments/assets/52cac467-0228-4de5-8386-992e26ddecc0" />

<img width="1890" height="977" alt="image" src="https://github.com/user-attachments/assets/0d5326e9-d80c-4f4a-b0d0-6ca3d2232dab" />

---

## 3.2 Keep Specific Rows Only

Useful when filtering out noise.

Home ➝ Reduce Rows ➝ Keep Rows

Options:

* Keep Top Rows  
* Keep Bottom Rows  
* Keep Range of Rows  

---

## 3.3 Add Custom Rows

Power Query doesn’t manually "add row" like Excel, but you can:

### Method 1 — Manual Add

* Home ➝ Enter Data  
* Create your row(s)  
* Append to your main table: Home ➝ Append Queries  

### Method 2 — Add a Calculated Column Instead

* Transform ➝ Add Column ➝ Custom Column  

---

# 4. Text Column Transformations (Split, Extract, Format)

## 4.1 Split Column

Select column → Home ➝ Split Column

Options:

* By Delimiter (comma, dash, space)  
* By Number of Characters  
* By Positions  
* Into Rows or Columns  

Example:  
*“John Doe – Sales” → Split by “–”*

---

## 4.2 Extract Text

Select column → Add Column ➝ Extract

Options:

* First characters  
* Last characters  
* Range  
* Text before delimiter  
* Text after delimiter  

Example:  
*Extract first 4 characters of ProductID → Use Extract First Characters*

---

## 4.3 Format Text

Transform ➝ Format

Includes:

* Trim  
* Clean  
* Uppercase/Lowercase  
* Capitalize  
* Add prefix / suffix (Add Column ➝ Format ➝ Add Prefix or Suffix)  

---

## 4.4 Replace Values

* Home ➝ Transform ➝ Replace Values  
* Example: Replace “N/A” with null  

---

# 5. Other Useful Cleaning Tools

## 5.1 Remove Errors

* Home ➝ Reduce Rows ➝ Remove Errors  

---

## 5.2 Fill Down / Fill Up

* Transform ➝ Fill ➝ Down or Up  
* Useful in hierarchical data  

---

## 5.3 Filter Rows

Select column → filter icon.

Common uses:

* Remove blanks  
* Remove 0 values  
* Keep valid ranges only  

---

# 6. Ready for the Markdown Guide?

You can now insert your screenshots wherever needed.
