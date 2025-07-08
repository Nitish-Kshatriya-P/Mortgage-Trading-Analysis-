Mortgage Loan Analysis Power BI Project
The Power BI project analyzes mortgage loans to evaluate the overall profit from selling eligible loans to investors from the month of October. The project uses six Excel files as data sources and consists of five report pages: Loan Status, Loan Balance, Trade Analysis, Trade Execution, and Profit Analysis. This README provides an overview of the data sources, the analysis process, and the calculations performed on each page.
Table of Contents

1.Data Sources
2.Project Overview
3.Report Pages and Calculations
4.Loan Status
5.Loan Balance
6.Trade Analysis
7.Trade Execution
8.Profit Analysis

Here's the more in-depth information of the above list of contents and also on how I carried out the whole project: 

AIM(Assumed): To get the list of loans from the month of october to trade in the markets and compare the best price for each loan. At last, comparing the profits of estimated vs. actual profits made. 

Data Sources
The project uses the following six Excel files as data sources:

1. umbs_prices.xlsx: Contains pricing information for Uniform Mortgage-Backed Securities (UMBS).
2. loan_data.xlsx: Contains detailed information about the mortgage loans, including loan IDs, terms, interest rates, and other relevant attributes.
3. target_profit.xlsx: Contains the company's estimated (target) profit for each loan.
4. loan_bids.xlsx: Contains bid information from investors for each loan, including bidder details and bid amounts.
5. loan_status.xlsx: Contains the status of each loan, used to filter loans eligible for trading.
6. loan_balances.xlsx: Contains the outstanding balance for each loan.

Project Overview
The analysis focuses on mortgage loans for the month of October. The process involves:

Filtering loans eligible for trading based on their status.
Calculating the balance required to clear each loan.
Weighting loans based on their profitability.
Identifying the highest bidder for each loan using bid data.
Calculating profit from selling each loan and comparing the profit with the required company profit.

The results are visualized across five report pages in the Power BI file, each focusing on a specific aspect of the analysis.

Report Pages

Loan Status
Purpose: Displays the status of loans to identify those eligible for trading in October. 'Closed - Ready to Trade' indicates that the loans are ready for trade.
Data Source: loan_status.xlsx
Calculations and Filters:
Filter loans to include only those for October.
Visualize the count compared to the rest of all the loans in the same month.

Loan Balance
Purpose: Calculates and displays the outstanding balance required to clear each eligible loan.
Data Source: loan_balances.xlsx, loan_data.xlsx
Calculations:
Extract the outstanding balance for each loan from loan_balances.xlsx.
Join with loan_data.xlsx to include loan details (e.g., loan ID, interest rate).
Apply a filter to include only loans eligible for trading (from the Loan Status page).
Calculate the total balance to clear all eligible loans.

Trade Analysis
Purpose: Weights loans based on their profitability to prioritize trading decisions.
Data Sources: umbs_prices.xlsx, loan_data.xlsx, target_profit.xlsx
Calculations:
Merge loan data with UMBS pricing to estimate the market value of each loan.
Calculate the expected profit for each loan by subtracting the outstanding balance (loan_balances.xlsx) from the estimated market value (derived from umbs_prices.xlsx).
Weight loans based on their expected profitability.
Sort or rank loans by their profit weight to identify high-priority loans for trading.

Trade Execution
Purpose: Identifies the highest bidder for each eligible loan to maximize profit.
Data Source: loan_bids.xlsx, loan_data.xlsx
Calculations:
For each eligible loan, extract bid data from loan_bids.xlsx.
Identify the highest bid amount for each loan using a measure like:Highest Bid = MAX('loan_bids'[Bid Amount])
Match the highest bid to the corresponding bidder and loan ID.
Calculate the total revenue from selling all loans to the highest bidders:Total Revenue = SUM('loan_bids'[Highest Bid])

Profit Analysis
Purpose: Compares actual profit from selling loans to the company's estimated profit.
Data Sources: loan_bids.xlsx, target_profit.xlsx, loan_balances.xlsx
