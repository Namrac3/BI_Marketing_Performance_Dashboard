# 📊 BI Martech Dashboard – Marketing Analytics Insights  
**By [Namrata Chavan](https://www.linkedin.com/in/namrata333)**  

This Power BI project — *MarketMindz: BI Martech Dashboard* — provides a comprehensive view of marketing campaign performance, buyer demographics, and purchase drivers.  
It transforms raw marketing data into actionable insights that help optimize campaign strategy, improve ROI, and understand customer behavior across multiple channels.

---

## 🎯 Project Objectives
- Evaluate **marketing campaign performance** by sales, engagement, and product category.  
- Analyze **buyer composition** based on demographics, income, and marital status.  
- Identify **key purchase drivers** influencing campaign success.  
- Provide **data-driven recommendations** for marketing optimization.

---

## 🧠 Dashboard Insights

### 🪩 **Campaign Performance**
![Campaign Performance](Images/Campaign_Performance.png)

- **Campaign 6** achieved the highest purchase count (334) and sales revenue (₹0.33M).  
- **Wine** emerged as the top-selling product with ₹681K in revenue, followed by **Meat (₹374K)**.  
- **In-store purchases** dominated all campaigns, emphasizing strong offline engagement.  
- **Campaigns 5 & 6** yielded the best ROI, combining strong sales and high conversion rates.

---

### 👩‍💼 **Buyer Composition**
![Buyer Composition](Images/Buyer_Composition.png)

- Total customers analyzed: **2.24K**  
- Average income: **₹52.25K** | Average age: **57.19 years**  
- Majority of customers hold **college/university education (1,127)**.  
- **Married customers (1.4K)** accounted for most purchases.  
- As customers age, **wine sales increase** while **meat purchases decline**.  
- Highest sales occurred **in-store (₹12.97K)**, followed by **web (₹9.15K)** and **deals (₹5.21K)**.

---

### 💡 **Purchase Drivers**
![Purchase Drivers](Images/Purchase_Drivers.png)

- Customers with **income > ₹60,585** are **7.8× more likely** to accept Campaign 1.  
- **Low monthly web visits (0–1)** correlate with **higher total sales**, suggesting bulk buyers or loyal customers.  
- Key influencers: **Income level**, **web visit frequency**, and **household composition (kids/teens)**.  
- Purchase drivers vary by product, helping tailor future marketing efforts more precisely.

---

## 📐 Data Model & Schema
![Data Model](Images/Data_Model.png)

The project follows a **star schema** to optimize analytical performance and simplify DAX calculations.

| Table | Description | Key Columns |
|--------|--------------|--------------|
| `marketmindz_research` | Master dataset of demographics, income, age, and campaign acceptance | `ID`, `Age`, `Income`, `Accepted Campaigns` |
| `campaign` | Campaign details with acceptance indicators | `ID`, `Campaign`, `Accepted_Ind` |
| `products` | Product-level sales data | `ID`, `Product`, `Total Sales` |
| `platform` | Distribution of sales across channels | `ID`, `Platform`, `Qty` |
| `Image URL` | Product-image mapping for visuals | `Product`, `URL` |

**Relationships:**
- `marketmindz_research[ID]` → `campaign[ID]` (1:1)  
- `campaign[ID]` → `products[ID]` (1:*)  
- `products[ID]` → `platform[ID]` (1:*)  
- `products[Product]` → `Image URL[Product]` (1:1)

Power Query was used for cleaning and shaping the data, while DAX measures (ROI, Total Sales, Conversion Rate, etc.) enabled deeper performance analytics.

---

## ⚙️ Tools & Technologies
| Tool | Purpose |
|------|----------|
| **Power BI** | Visualization, data modeling, and storytelling |
| **Excel / CSV** | Data preprocessing and cleansing |
| **Power Query & DAX** | Data transformation and KPI creation |
| **Canva / Figma** | Dashboard backgrounds and UI design |

---

## 📈 Key DAX Measures
```DAX
Total Revenue = SUM(Sales[Amount])
ROI = (SUM(Sales[Revenue]) - SUM(Sales[Spend])) / SUM(Sales[Spend])
Conversion Rate = DIVIDE(Total Purchases, Total Reach, 0)
Avg Income = AVERAGE(marketmindz_research[Income])
