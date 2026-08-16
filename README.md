
Powerlifting Meets Data Analysis
📌 Project Overview
This project analyzes a historical dataset of powerlifting meets to understand how recorded competition activity has evolved over time and how it is distributed across federations, countries, and U.S. states.
The analysis focuses on four main dimensions:
•	📈 Growth of recorded powerlifting meets over time
•	🏛️ Federation participation and market concentration
•	🌍 Geographic distribution of meets
•	🇺🇸 U.S. state-level distribution
The objective is to transform raw meet-level data into clear, evidence-based insights using Python and data visualization.
Important: This project analyzes the meets contained in the dataset. It should not be interpreted as a complete measure of worldwide powerlifting activity, because the dataset may have differences in historical coverage, federation coverage, and geographic completeness.
________________________________________
🎯 Objectives
The main questions addressed by this project are:
1.	How has the number of recorded powerlifting meets changed over time?
2.	What is the year-over-year (YoY) growth in recorded meets?
3.	Which federations account for the largest number of meets?
4.	How has federation dominance changed over time?
5.	Which countries host the most recorded meets?
6.	Has the geographic distribution of meets changed across different historical periods?
7.	How concentrated is the U.S. federation landscape?
8.	Which U.S. states host the largest number of recorded meets?
9.	What data-quality limitations need to be considered before interpreting the results?
________________________________________
📂 Dataset
The project uses a CSV dataset containing 8,482 recorded meets and 8 columns.
Dataset columns
Column	Description
MeetID	Unique identifier for the meet
MeetPath	Meet-related path/reference field
Federation	Federation associated with the meet
Date	Date of the meet
MeetCountry	Country where the meet was held
MeetState	State/region where the meet was held, primarily relevant for U.S. records
MeetTown	Town/city where the meet was held
MeetName	Name of the meet
Dataset profile
•	Rows: 8,482
•	Columns: 8
•	Countries represented: 45
•	Federations represented: 60
•	Unique MeetIDs: 8,482
•	Duplicate complete rows: 0
•	Date range: 1974–2018
•	Missing MeetState: 2,986 records (~35.2%)
•	Missing MeetTown: 1,509 records (~17.8%)
The last recorded year in the dataset is 2018, and the data only extends through September 9, 2018. Therefore, 2018 should be treated as a partial year when analyzing annual totals, YoY growth, or year-over-year declines.
________________________________________
🧹 Data Cleaning & Preparation
The cleaning process was designed to preserve valid records rather than automatically removing rows with missing values.
Main cleaning steps
1.	Loaded the raw CSV dataset.
2.	Inspected data types, dimensions, missing values, and duplicates.
3.	Checked the uniqueness of MeetID.
4.	Confirmed that there were no duplicate complete rows.
5.	Converted Date from text to a proper datetime format.
6.	Extracted analytical time fields such as Year.
7.	Standardized categorical text fields by removing unnecessary whitespace and checking category consistency.
8.	Investigated missing geographic information rather than blindly dropping incomplete records.
9.	Treated missing MeetState and MeetTown as a data-quality/coverage issue rather than automatically deleting those observations.
10.	Validated the final dataset before beginning analysis.
Missing-value approach
Missing geographic information was not removed automatically.
This is important because a missing state may be structurally expected for non-U.S. meets rather than being an error. The project therefore investigates missingness by country/federation before deciding how it should be interpreted.
________________________________________
📊 Exploratory Data Analysis
1. Meets over time
The historical trend shows a substantial increase in the number of recorded meets over the dataset's history, especially in the later periods.
The analysis groups meets by year to identify long-term growth and periods of acceleration.
2. Year-over-Year Growth
YoY growth is calculated as:
(Current Year Meets - Previous Year Meets) / Previous Year Meets × 100
This measures the annual change in recorded meet activity.
The project also identifies:
•	Years with the highest positive growth
•	Years with the largest declines
•	Long-term growth trends
•	Potential effects of incomplete years
The final year, 2018, is treated carefully because it is only partially covered in the dataset.
3. Federation analysis
The largest recorded federations in the dataset include:
Federation	Recorded Meets
NSF	2,517
USAPL	976
CPU	969
USPA	864
THSPA	670
PA	493
SPF	480
RPS	334
NZPF	179
NASA	103
These figures describe the distribution of records in the dataset rather than the total real-world activity of each federation.
4. Geographic analysis
The largest host countries in the dataset include:
Country	Recorded Meets
USA	3,894
Norway	2,521
Canada	1,066
Australia	532
New Zealand	195
Together, these countries account for a large share of the recorded meets.
The project also compares geographic patterns across different eras:
•	1980–1999
•	2000–2009
•	2010–2014
•	2015–2018
Because these periods contain different numbers of years, comparisons should use both total meets and average meets per year.
5. Federation dominance by country
A country-by-federation analysis was created to identify whether a country's recorded meets are dominated by one federation or distributed across multiple federations.
Examples from the analysis include:
•	Norway is highly concentrated in NSF.
•	Canada is highly concentrated in CPU.
•	Australia is highly concentrated in PA.
•	New Zealand is highly concentrated in NZPF.
•	The U.S. has a much more fragmented federation landscape.
6. U.S. federation landscape
The U.S. analysis highlights the major federations by recorded meet count.
The largest groups include:
•	USAPL
•	USPA
•	THSPA
•	SPF
•	RPS
This indicates a considerably more fragmented federation structure compared with countries where a single federation dominates most recorded meets.
7. U.S. state analysis
The analysis also identifies the U.S. states with the largest number of recorded meets.
The leading states in the visualization include:
•	Texas
•	California
•	Ohio
•	Pennsylvania
•	New York
•	Florida
•	Tennessee
•	Georgia
•	Illinois
•	Kentucky
This analysis can be extended by calculating state market share and concentration among the top states.
________________________________________
📈 Key Analytical Findings
The current analysis suggests several important patterns.
1. Recorded meet activity increased substantially over time
The number of recorded meets is much higher in the later periods than in the earlier history of the dataset.
This indicates strong growth in recorded competition activity, although this should be interpreted in the context of changing data coverage and federation representation.
2. The geographic center of recorded activity changed over time
Earlier periods in the dataset are strongly represented by Norway, while the United States becomes the dominant host country in the later periods.
This suggests a major shift in the geographic distribution of recorded meets.
3. The United States is the largest host country
The dataset contains 3,894 U.S. meets, making the USA the largest host country in the recorded data.
4. Federation concentration varies significantly by country
Some countries are strongly associated with one federation, while the United States has a much more fragmented federation landscape.
This makes country-level federation concentration an important dimension of the analysis.
5. U.S. meet activity is concentrated in a small group of states
Texas and California stand out significantly in the U.S. state analysis, followed by several other states with substantial recorded activity.
A useful next step is to quantify the percentage of U.S. meets represented by the top 3 and top 10 states.
6. The dataset contains important geographic missingness
MeetState is missing for approximately 35.2% of records and MeetTown for approximately 17.8%.
These missing values should not automatically be interpreted as bad records because geographic fields can be structurally unavailable for certain countries.
________________________________________
📐 Additional Metrics
To make the analysis more rigorous, the project can calculate:
CAGR
Compound Annual Growth Rate can be used to summarize long-term growth:
CAGR = (Ending Value / Beginning Value)^(1 / Number of Years) - 1
Market Share
For a federation or country:
Market Share = Category Meets / Total Meets × 100
Concentration
Federation concentration can be evaluated using:
•	Top-1 market share
•	Top-3 market share
•	Top-5 market share
•	Herfindahl-Hirschman Index (HHI)
These measures provide a more quantitative view of how concentrated or fragmented the federation landscape is.
________________________________________
📊 Visualizations
The project includes visualizations covering:
Historical activity
•	Meets by year
•	YoY growth in meets
•	Era-based meet totals
•	Average meets per year by era
Federation analysis
•	Top federations by number of meets
•	Federation market share
•	Federation trends over time
•	Country vs. dominant federation
•	U.S. federation breakdown
Geographic analysis
•	Top host countries
•	Country distribution by era
•	Top U.S. states
•	Country diversification over time
________________________________________
🛠️ Technologies Used
•	Python
•	Pandas — data cleaning, transformation, aggregation
•	NumPy — numerical calculations
•	Matplotlib — visualization
•	Seaborn — statistical/data visualization
•	Jupyter Notebook — analysis and documentation│________________________________________
🚀 How to Run the Project
1. Clone the repository
git clone https://github.com/YOUR-USERNAME/powerlifting-data-analysis.git
cd powerlifting-data-analysis
2. Create a virtual environment
python -m venv venv
3. Activate the environment
Windows:
venv\Scripts\activate
macOS/Linux:
source venv/bin/activate
4. Install dependencies
pip install -r requirements.txt
5. Launch Jupyter
jupyter notebook
Open the notebooks in the following order:
01_data_cleaning.ipynb
02_eda.ipynb
03_deep_analysis.ipynb
________________________________________
⚠️ Limitations
This project has several limitations that should be considered when interpreting the results.
Dataset coverage
The dataset represents recorded meets available in the source data. It should not automatically be treated as a complete record of every powerlifting meet worldwide.
Historical comparability
The number of recorded meets may be influenced by changes in:
•	Data collection
•	Federation participation
•	Geographic coverage
•	Historical reporting practices
Therefore, growth in recorded meets does not necessarily equal the same percentage growth in the real-world sport.
Partial 2018 data
The dataset ends on September 9, 2018, so 2018 is incomplete.
For this reason, the 2018 annual count should not be compared directly with complete previous years without explicitly accounting for the partial-year coverage.
Missing geographic values
MeetState and MeetTown contain missing values, and the appropriate interpretation can vary by country.
________________________________________
🔮 Future Improvements
Potential extensions include:
•	Build an interactive Power BI or Tableau dashboard
•	Add YoY growth and CAGR analysis
•	Analyze federation growth over time
•	Calculate federation and country concentration metrics
•	Analyze the number of countries represented each year
•	Create a geographic map of meet activity
•	Analyze U.S. state concentration over time
•	Investigate the relationship between federation growth and geographic expansion
•	Add automated data-quality checks
•	Expand the dataset with athlete-level competition data for performance analysis
________________________________________
💡 Conclusion
This project uses historical powerlifting meet data to explore how competitive activity has evolved across time, federations, and geography.
The analysis shows strong growth in recorded meet activity, major changes in geographic dominance, significant differences in federation concentration between countries, and substantial concentration of U.S. activity among specific states and federations.
The main objective is not simply to produce charts, but to demonstrate a complete data-analysis workflow:
Raw Data
   ↓
Data Quality Assessment
   ↓
Data Cleaning
   ↓
Exploratory Data Analysis
   ↓
Statistical Analysis
   ↓
Visualization
   ↓
Insights
   ↓
Dashboard / Storytelling
This project is intended to demonstrate practical skills in data cleaning, exploratory data analysis, aggregation, visualization, analytical reasoning, and data storytelling.
________________________________________
👤 Author
Mohamed Bouzzit
Data Analyst | Python | Pandas | Data Visualization | Exploratory Data Analysis
GitHub: https://github.com/mohamedbouzzit01
LinkedIn: https://www.linkedin.com/in/mohamed-bouzzit/

