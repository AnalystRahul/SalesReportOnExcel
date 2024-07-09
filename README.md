
# Product Launch Analysis

## Introduction
In the exercise "Product Launch Analysis," the goal is to analyze sales data for Adventure Works. The tasks include:

- Identifying stakeholders interested in sales performance and customer preferences.
- Evaluating the dataset containing product and order information and determining additional data sources for a comprehensive analysis.
- Identifying and cleaning potential errors or inconsistencies in the dataset.

## Step-by-Step Analysis

### Step 1: Identify the Stakeholders
1. **Sales Team:**
   - **Interest:** Understanding sales performance and trends to tailor strategies, identify opportunities for improvement, and maximize sales during the product launch.
   
2. **Marketing Team:**
   - **Interest:** Assessing the effectiveness of marketing strategies and guiding future campaigns to promote the new product line.

### Step 2: Identify and Consider the Data Sources
1. **Dataset Information:**
   - **Product Details:** Contains information about product specifications, aiding in understanding product performance and customer preferences.
   - **Order Details:** Information about orders, including cost, quantity, and status, helping track sales performance and identify trends or issues.
   - **Customer Details:** Tracks individual customer behavior, aiding in understanding customer loyalty and preferences.

2. **Additional Data Sources:**
   - **Customer Demographics:** Provides deeper insights into customer behavior.
   - **Marketing Data:** Correlates marketing efforts with sales performance.
   - **Supply Chain Data:** Understands cost and manages inventory.
   - **Feedback Data:** Offers qualitative insights into customer preferences.
   - **Website Analytics:** Provides insights into online customer behavior.

### Step 3: Data Import and Cleaning

**Identify Missing Values**
```python
missing_values = data.isnull().sum()
missing_values
```

**Clean Product Name (TRIM equivalent)**
```python
data['Product Name'] = data['Product Name'].str.strip()
```

**Standardize Product Category (PROPER equivalent)**
```python
data['Product Category'] = data['Product Category'].str.title()
```

**Standardize Product Size (UPPER)**
```python
data['Product Size'] = data['Product Size'].str.upper()
```

**Remove Rows with Missing Product Descriptions**
```python
data = data.dropna(subset=['Product Description'])
```

**Convert Data Types**
```python
data['Product ID'] = data['Product ID'].astype(int)
data['Product Price'] = data['Product Price'].astype(float)
data['Product Weight'] = data['Product Weight'].astype(float)
data['Order ID'] = data['Order ID'].astype(int)
data['Customer ID'] = data['Customer ID'].astype(int)
data['Order Date'] = pd.to_datetime(data['Order Date'])
data['Order Quantity'] = data['Order Quantity'].astype(int)
data['Order Total'] = data['Order Total'].astype(float)
```

## Step 4: Analyze Sales Trends and Customer Preferences

**Sales Trends**
```python
sales_trends = data.groupby(['Order Date']).agg({'Order Total': 'sum'}).reset_index()
```

**Customer Preferences**
```python
customer_preferences = data.groupby(['Product Category', 'Product Subcategory']).agg({'Order Quantity': 'sum'}).reset_index()
```

### Conclusion
The analysis identifies key stakeholders, evaluates the dataset, cleans the data, and analyzes sales trends and customer preferences. This process helps develop essential data analysis skills, enabling better decision-making and strategy development based on data insights.
