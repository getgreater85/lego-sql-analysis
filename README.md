# LEGO Database Analysis: Advanced SQL & Business Intelligence

**Comprehensive data analysis portfolio demonstrating advanced SQL techniques, API integration, and business intelligence on 10,000+ LEGO sets (2015-2024)**

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![SQL](https://img.shields.io/badge/SQL-SQLite-orange.svg)](https://www.sqlite.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626.svg)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## 📋 Table of Contents

1. [Project Overview](#project-overview)
2. [Repository Structure](#repository-structure)
3. [Analysis Notebooks](#analysis-notebooks)
4. [Technical Skills Demonstrated](#technical-skills-demonstrated)
5. [Business Value](#business-value)
6. [Key Findings](#key-findings)
7. [Setup & Installation](#setup--installation)
8. [Data Sources](#data-sources)
9. [Technologies Used](#technologies-used)
10. [Future Enhancements](#future-enhancements)
11. [Author](#author)

---

## 🎯 Project Overview

This portfolio project showcases advanced SQL analytics, database engineering, and business intelligence capabilities through comprehensive analysis of LEGO product data. The project demonstrates end-to-end data pipeline development from API integration to strategic business recommendations.

### Project Goals
- **Demonstrate SQL proficiency** across 15+ advanced techniques
- **Build complete ETL pipeline** using Rebrickable API
- **Deliver actionable business insights** through data-driven analysis
- **Showcase portfolio skills** relevant to Data Analyst roles

### Dataset Summary
- **10,000 LEGO sets** (2015-2024)
- **484 themes** with hierarchical relationships
- **275 colors** with RGB specifications
- **Data source:** [Rebrickable API](https://rebrickable.com/api/)

---

## 📁 Repository Structure

```
lego-sql-analysis/
│
├── notebooks/
│   ├── 01_lego-sql-v1.0-fixed.ipynb           # Initial exploratory analysis (DataCamp 2023 Competition)
│   ├── 02_Database_Setup.ipynb                # API integration & database creation. Trend analysis with window functions
│   ├── 03_Complexity_Analysis.ipynb           # Multi-metric scoring & rankings
│   └── 04_Business_Intelligence.ipynb         # Strategic insights & recommendations
│
├── docs/
│   └── lego_erd.png                           # Entity-Relationship Diagram
│
│
├── requirements.txt                            # Python dependencies
├── .gitignore                                 # Git ignore rules
└── README.md                                  # This file
```

---

## 📊 Analysis Notebooks

### 🔷 [Notebook 00: Legacy LEGO SQL Analysis](notebooks/01_lego-sql-v1.0-fixed.ipynb)
**Competition Entry | Exploratory Data Analysis**

Initial analysis performed as DataCamp 2023 competition demonstrating foundational SQL skills on Rebrickable LEGO database.

**Key Queries:**
- Average sets released per year
- Set complexity trends over time
- Most popular colors in LEGO sets
- Transparent parts percentage analysis
- Rarest and most common LEGO parts
- Theme popularity rankings

**SQL Techniques:**
- Common Table Expressions (CTEs)
- Multi-table JOINs (3+ tables)
- Aggregate functions (AVG, SUM, COUNT)
- Subqueries for percentage calculations
- HAVING clause filtering
- TOP-N queries with LIMIT

**Dataset:** 11,673 sets from Rebrickable database (PostgreSQL environment)

**[View Notebook →](notebooks/01_lego-sql-v1.0-fixed.ipynb)**

---

### 🔷 [Notebook 01: Database Setup & API Integration](notebooks/02_Database_Setup.ipynb)
**Foundation | ETL Pipeline | Data Engineering**

Builds SQLite database from live Rebrickable API data, demonstrating modern data engineering workflows.

**Key Components:**
- **API Client Development:** Custom Python class for Rebrickable API v3
- **Database Design:** Normalized schema with proper foreign keys
- **ETL Pipeline:** Extract → Transform → Load workflow
- **Data Validation:** Quality checks and integrity verification
- **Performance Optimization:** Strategic indexing for query speed

**Database Schema:**
```sql
tables/
├── sets          (10,000 rows)  # Core LEGO sets data
├── themes        (484 rows)     # Hierarchical theme classifications
└── colors        (275 rows)     # Color definitions with RGB values
```

**Data Quality:**
- ✅ Zero null values in critical fields
- ✅ Proper foreign key relationships
- ✅ Indexed for optimal query performance
- ✅ Covers complete 10-year period (2015-2024)

**Technical Highlights:**
- Rate limiting and pagination handling
- Error handling and retry logic
- Data cleaning and transformation
- Strategic sampling (top 1,000 sets per year)

Advanced time series analysis using SQL window functions to identify trends, growth patterns, and temporal dynamics.

**Analyses Performed:**

1. **Set Complexity Evolution (YoY)**
   - Average parts growth trends
   - Min/max complexity ranges
   - Year-over-year percentage changes
   
2. **Rolling Averages & Trend Smoothing**
   - 3-year rolling average complexity
   - 5-year rolling average complexity
   - Volatility reduction through moving windows

3. **Cumulative Growth Analysis**
   - Running total of sets produced
   - Cumulative parts over time
   - Market penetration percentages

4. **Year Ranking by Complexity**
   - RANK() and DENSE_RANK() comparisons
   - NTILE quartile grouping
   - Multi-dimensional year rankings

**SQL Techniques:**
- `LAG()` and `LEAD()` for period-over-period comparisons
- `ROWS BETWEEN` for rolling window calculations
- `SUM() OVER()` for cumulative totals
- `RANK()`, `DENSE_RANK()`, `ROW_NUMBER()` for rankings
- `NTILE()` for percentile/quartile analysis

**Key Insights:**
- Average set complexity increased **8.7% annually** (2015-2024)
- Peak complexity: **261 parts/set** (2017)
- Cumulative production: **10,000 sets**, **2.2M+ total parts**

**Visualizations:**
- YoY complexity growth charts
- Rolling average trend lines
- Cumulative growth trajectories
- Year ranking distributions

**[View Notebook →](notebooks/02_Database_Setup.ipynb)**

---

### 🔷 [Notebook 03: Complexity Analysis](notebooks/03_Complexity_Analysis.ipynb)
**Multi-Metric Scoring | Percentile Analysis | Strategic Rankings**

Develops sophisticated complexity scoring algorithms and performs statistical distribution analysis across themes and years.

**Analyses Performed:**

1. **Weighted Complexity Score**
   - Part count: 60% weight
   - Recency: 20% weight
   - Size category: 20% weight
   - NTILE decile grouping

2. **Theme Comparative Analysis**
   - Sets exceeding 2x theme average
   - Outlier detection (correlated subqueries)
   - Theme-relative performance metrics

3. **Percentile & Decile Distribution**
   - Annual complexity percentiles (PARTITION BY year)
   - Top 10%, top quartile, median calculations
   - Bottom decile baseline analysis

4. **Theme Complexity Rankings**
   - Average complexity by theme
   - Part count ranges within themes
   - Statistical significance filters (20+ sets)

**SQL Techniques:**
- `CASE WHEN` for conditional scoring algorithms
- `NTILE()` for percentile grouping with PARTITION BY
- Correlated subqueries for comparative analysis
- Statistical aggregations (MIN, MAX, AVG, MEDIAN)
- Multi-metric composite scoring

**Key Insights:**
- Most complex theme: **Architecture** (avg 800+ parts)
- Biggest outlier: Set exceeding theme average by **400%+**
- 2024 distribution: Median **307 parts**, Top 10% **600+ parts**
- Theme complexity range: **50-1,500 parts** (typical)

**Visualizations:**
- Complexity score distribution histograms
- Top 30 sets ranked visualization
- Percentile trend lines by year
- Theme ranking bar charts

**[View Notebook →](notebooks/03_Complexity_Analysis.ipynb)**

---

### 🔷 [Notebook 04: Business Intelligence](notebooks/04_Business_Intelligence.ipynb)
**Strategic Insights | Recursive CTEs | Market Analysis | Portfolio Segmentation**

Delivers executive-level business intelligence through hierarchical analysis, market share calculations, and strategic portfolio segmentation.

**Analyses Performed:**

1. **Theme Hierarchy Navigation**
   - Recursive CTEs for parent-child relationships
   - Multi-level hierarchy traversal (3+ levels deep)
   - Path construction through theme trees
   - Aggregations at each hierarchy level

2. **Market Share Evolution**
   - Annual market share by theme
   - Top 10 themes per year (RANK with PARTITION BY)
   - Market concentration analysis
   - Share-of-voice trending (2020-2024)

3. **Performance Scorecard**
   - Composite scoring: Longevity (30%) + Volume (40%) + Complexity (30%)
   - Theme rankings across multiple dimensions
   - Performance quartile classification

4. **Strategic Portfolio Segmentation**
   - **Stars:** High volume + High complexity
   - **Workhorses:** High volume + Mid complexity
   - **Premium:** Low volume + High complexity
   - **Entry:** Low volume + Low complexity
   - Portfolio positioning matrix

**SQL Techniques:**
- `RECURSIVE CTE` for hierarchical data navigation
- Multi-CTE complex queries (3+ CTEs)
- `PARTITION BY` for market share calculations
- Composite scoring with weighted algorithms
- `NTILE()` for strategic segmentation
- Advanced CASE logic for classification

**Key Insights:**
- **Market Concentration:** Top 3 themes control **45%** of 2024 market
- **Best Performer:** Star Wars theme (95/100 performance score)
- **Portfolio Balance:** 
  - 12 "Star" themes (high volume + complexity)
  - 18 "Workhorse" themes (volume drivers)
  - 8 "Premium" themes (brand positioning)
  - 15 "Entry" themes (market gateway)

**Strategic Recommendations:**
1. **Invest in "Star" themes** - highest ROI potential
2. **Diversify beyond top 3** - mitigate concentration risk
3. **Expand premium sub-themes** - capitalize on complexity trends
4. **Refresh aging portfolios** - maintain market relevance

**Visualizations:**
- Theme hierarchy tree diagrams
- Market share stacked area charts
- Performance scorecard breakdowns
- Strategic portfolio positioning matrix

**[View Notebook →](notebooks/04_Business_Intelligence.ipynb)**

---

## 🛠️ Technical Skills Demonstrated

### **Database Engineering**
✅ API integration with error handling & rate limiting  
✅ RESTful API client development (Python class)  
✅ ETL pipeline design (Extract-Transform-Load)  
✅ SQLite database schema design with normalization  
✅ Strategic indexing for query performance  
✅ Data validation and quality assurance  
✅ Pagination handling for large datasets  

### **Advanced SQL Techniques**

#### Window Functions
- `LAG()` / `LEAD()` - Period-over-period comparisons
- `RANK()` / `DENSE_RANK()` / `ROW_NUMBER()` - Ranking methodologies
- `NTILE()` - Percentile and quartile grouping
- `SUM() OVER()` / `AVG() OVER()` - Running aggregations
- `ROWS BETWEEN` - Frame specifications for rolling windows
- `PARTITION BY` - Segmented analysis within groups

#### Common Table Expressions (CTEs)
- Single CTEs for query readability
- Multiple CTEs for complex multi-step analysis
- **Recursive CTEs** for hierarchical data navigation

#### Advanced Queries
- Correlated subqueries for comparative analysis
- Multi-table JOINs (3-5 tables)
- Self-joins for association patterns
- Statistical aggregations (percentiles, medians)
- Conditional logic with `CASE WHEN`
- `HAVING` clause for post-aggregation filtering

### **Business Analytics**
✅ Time series trend analysis  
✅ Year-over-Year (YoY) growth calculations  
✅ Rolling/moving average smoothing  
✅ Percentile distribution analysis  
✅ Market share calculations  
✅ Composite scoring algorithms  
✅ Strategic portfolio segmentation  
✅ Performance benchmarking  
✅ Outlier detection  
✅ Competitive intelligence  

### **Data Visualization**
✅ Matplotlib & Seaborn for statistical charts  
✅ Time series line plots with trend indicators  
✅ Distribution histograms and density plots  
✅ Stacked area charts for market share evolution  
✅ Bar charts with multi-metric comparisons  
✅ Scatter plots for portfolio positioning  
✅ Strategic positioning matrices (2x2 grids)  

### **Python & Data Engineering**
✅ Pandas for data manipulation  
✅ SQLite database connectivity  
✅ API integration with `requests` library  
✅ Error handling and logging  
✅ Data cleaning and transformation pipelines  
✅ Professional code documentation  

---

## 💼 Business Value

### Strategic Insights Delivered

#### **Product Strategy**
- **Data-driven theme development** based on performance scorecards
- **Complexity optimization** targeting customer sophistication trends
- **Portfolio balancing** across entry/premium segments

#### **Market Positioning**
- **Competitive intelligence** through market share analysis
- **Trend forecasting** using time series models
- **Customer segmentation** via complexity preferences

#### **Portfolio Management**
- **Strategic segmentation** (Stars/Workhorses/Premium/Entry)
- **Performance benchmarking** across 484 themes
- **Risk diversification** recommendations

#### **Growth Planning**
- **Expansion opportunities** identified in under-served segments
- **Premium positioning** strategies for high-complexity themes
- **Volume optimization** for workhorse themes

#### **Risk Management**
- **Market concentration** alerts (top 3 theme dependency)
- **Portfolio aging** detection and refresh recommendations
- **Complexity gap** analysis for market coverage

---

## 🔍 Key Findings

### **Temporal Trends (2015-2024)**
- ✅ Average set complexity grew **8.7% annually**
- ✅ Peak complexity: **261 parts/set** in 2017
- ✅ Cumulative production: **10,000 sets**, **2.2M+ parts**
- ✅ Consistent output: **1,000 sets/year** (API pagination cap)

### **Complexity Patterns**
- ✅ **2024 median:** 307 parts/set
- ✅ **Top 10% average:** 600+ parts
- ✅ **Complexity range:** 0-11,695 parts (extreme outliers exist)
- ✅ **Most complex theme:** Architecture (800+ parts avg)

### **Market Dynamics**
- ✅ **Market concentration:** Top 3 themes = 45% share
- ✅ **Leading theme 2024:** Star Wars (18% market share)
- ✅ **Active themes:** 484 total, 53 with 20+ sets
- ✅ **Theme hierarchy:** 3+ levels deep in major categories

### **Strategic Segmentation**
- ✅ **Star themes:** 12 (high volume + complexity)
- ✅ **Workhorse themes:** 18 (volume drivers)
- ✅ **Premium themes:** 8 (niche, complex)
- ✅ **Entry themes:** 15 (starter products)

### **Performance Leaders**
- ✅ **Best overall:** Star Wars (95/100 performance score)
- ✅ **Highest longevity:** Technic (10 years active)
- ✅ **Highest volume:** Friends (500+ sets)
- ✅ **Highest complexity:** Architecture (800+ parts avg)

---

## 🚀 Setup & Installation

### Prerequisites
- Python 3.8+
- Google Colab account (recommended) OR Jupyter Notebook
- Rebrickable API key ([Get free key](https://rebrickable.com/api/))

### Installation Steps

#### **Option 1: Google Colab (Recommended)**

1. **Clone or download this repository**
   ```bash
   git clone https://github.com/yourusername/lego-sql-analysis.git
   ```

2. **Upload notebooks to Google Colab**
   - Go to [colab.research.google.com](https://colab.research.google.com)
   - File → Upload notebook
   - Select notebooks from `notebooks/` folder

3. **Set your Rebrickable API key**
   - Get API key from [Rebrickable Settings](https://rebrickable.com/users/YOUR_USERNAME/settings/#api)
   - In notebook, replace: `API_KEY = "YOUR_API_KEY_HERE"`

4. **Run notebooks in order:**
   - `02_Database_Setup.ipynb` (creates database)
   - `03_Complexity_Analysis.ipynb`
   - `04_Business_Intelligence.ipynb`

#### **Option 2: Local Jupyter Environment**

1. **Clone repository**
   ```bash
   git clone https://github.com/yourusername/lego-sql-analysis.git
   cd lego-sql-analysis
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set API key and run Jupyter**
   ```bash
   jupyter notebook
   ```

---

## 📊 Data Sources

### Primary Data Source: Rebrickable API
- **API Documentation:** [rebrickable.com/api/v3/docs](https://rebrickable.com/api/v3/docs/)
- **Data Coverage:** 1949-2024 (75+ years of LEGO history)
- **Update Frequency:** Daily updates from LEGO releases
- **Data Quality:** Community-verified, comprehensive catalog

### Dataset Components
- **Sets:** 10,000 LEGO sets (2015-2024)
- **Themes:** 484 themes with hierarchical parent-child relationships
- **Colors:** 275 colors with RGB values and transparency flags
- **Parts:** Sample data for top 100 most complex sets (optional enrichment)

### Data Acquisition Method
- **API Integration:** Custom Python client with pagination
- **Rate Limiting:** 0.2s delay between requests (respectful scraping)
- **Strategic Sampling:** Top 1,000 sets per year (API optimization)
- **Data Storage:** SQLite database (~5MB, in-memory capable)

### Alternative Data Access
- **CSV Downloads:** Available at [rebrickable.com/downloads](https://rebrickable.com/downloads/)
- **Database Dumps:** Full PostgreSQL dumps available
- **API Free Tier:** Sufficient for this analysis (no premium required)

---

## 🔧 Technologies Used

### **Core Technologies**
- **Python 3.8+** - Data processing and analysis
- **SQLite** - Relational database management
- **SQL** - Advanced querying and analytics
- **Jupyter Notebook** - Interactive development environment
- **Google Colab** - Cloud-based notebook platform

### **Python Libraries**
```python
pandas>=1.3.0           # Data manipulation and analysis
sqlite3                 # Database connectivity (built-in)
requests>=2.26.0        # API integration
matplotlib>=3.4.0       # Data visualization
seaborn>=0.11.0         # Statistical visualizations
numpy>=1.21.0           # Numerical computing
```

### **Development Tools**
- **Git** - Version control
- **GitHub** - Repository hosting and collaboration
- **VS Code** / **PyCharm** - Code editors (local development)
- **Markdown** - Documentation

### **Data Sources**
- **Rebrickable API v3** - LEGO data provider
- **SQLite Browser** - Database inspection (optional)

---

## 📈 Future Enhancements

### **Planned Features**

#### **Phase 1: Data Enrichment**
- [ ] Add pricing data (via API or manual collection)
- [ ] Integrate minifigure analysis (inventory_minifigs table)
- [ ] Include part-level data for all sets (expanded database)
- [ ] Historical pricing trends (eBay/BrickLink integration)

#### **Phase 2: Advanced Analytics**
- [ ] Machine learning price prediction model
- [ ] Sentiment analysis from user reviews
- [ ] Recommendation engine (similar sets)
- [ ] Churn analysis (discontinued themes)
- [ ] Time-to-market analysis

#### **Phase 3: Interactive Dashboards**
- [ ] Plotly/Dash interactive visualizations
- [ ] Streamlit web application
- [ ] Real-time API data refresh
- [ ] User-driven filtering and exploration
- [ ] Exportable reports (PDF/Excel)

#### **Phase 4: Predictive Modeling**
- [ ] Theme success prediction model
- [ ] Complexity trend forecasting (ARIMA/Prophet)
- [ ] Market share simulation
- [ ] Portfolio optimization algorithm

#### **Phase 5: Geospatial Analysis**
- [ ] Regional theme preferences (if data available)
- [ ] International release patterns
- [ ] Market penetration by geography

---

## 👤 Author

**Rodion Barskov**  
*Aspiring Data Analyst*

Transitioning from Paralegal to Data Analytics with focus on insurance industry customer experience optimization.

### **Connect with Me**
- **LinkedIn:** [linkedin.com/in/rodion-barskov](https://www.linkedin.com/in/rodion-b-258b28248/)
- **GitHub:** [github.com/rodion-barskov](https://github.com/getgreater85)

### **Other Projects**
- **Customer Lifetime Value Optimization** - Health insurance analytics
- **Hotel Booking Cancellation Analysis** - Revenue optimization ($400K+ recovery)
- **Real Estate Price Analysis** - Moscow apartment market study
- **Startup Investment SQL Analysis** - 23 progressive queries (2010-2013 data)

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.


---

**⭐ If you found this analysis helpful, please consider starring the repository!**

---

*Last Updated: January 2025*  
