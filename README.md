# Financial-Planner-for-Emergencies-and-Retirement-funds
# Background

I have decided to start a fintech consulting firm that focuses on projects to benefit local communities. I just won my first contract with a large credit union. The project entails building a tool to help credit union members evaluate their financial health. Specifically, the credit union board wants the members to be able to do two things. First, they should be able to assess their monthly budgets. Second, they should be able to forecast a reasonably effective retirement plan based on their current holdings of cryptocurrencies, stocks, and bonds. The chief technology officer (CTO) of the credit union wants me to develop a prototype application to present at its next assembly.

# My objectives

 I have to create two financial analysis tools with a single Jupyter notebook:
* A financial planner for emergencies. The members will be able to use this tool to visualise their current savings. The members can then determine if they have enough reserves for an emergency fund.
 * A financial planner for retirement. This tool will forecast the performance of their retirement portfolio in 30 years. To do this, the tool will make an Alpaca API call via the Alpaca SDK to get historical price data for use in Monte Carlo simulations.

# My Approach

## Create a Financial Planner for Emergencies

For this section, I created a personal financial planner for emergencies. To develop the prototype, I assumed the following:
* The average monthly household income for each credit union member is $12,000.
* Each credit union member has a savings portfolio that consists of a cryptocurrency wallet, stocks, and bonds.

### Evaluate the Cryptocurrency Wallet by Using the Requests Library
In this section, I determined the current value of a member’s cryptocurrency wallet. I collected the current prices for the Bitcoin and Ethereum cryptocurrencies by using the Python Requests library. For the prototype, I assumed that the member holds the 1.2 Bitcoins (BTC) and 5.3 Ethereum coins (ETH) which can be completed using the following steps:
* Create two variables called my_btc and my_eth. Set them equal to 1.2 and 5.3, respectively.
* Use the Requests library to get the current price (in Canadian dollars) of Bitcoin (BTC) and Ethereum (ETH) by using the API endpoints that the starter code supplied.
* Navigate the JSON response object to access the current price of each coin, and store each in a variable.
* Calculate the value, in Canadian dollars, of the current amount of each cryptocurrency and of the entire cryptocurrency wallet.

### Evaluate the Stock and Bond Holdings by Using the Alpaca SDK
In this section, I determined the current value of a member’s stock and bond holdings. I made an API call to Alpaca via the Alpaca SDK to get the current closing prices of the SPDR S&P 500 ETF Trust (ticker: SPY) and of the iShares Core US Aggregate Bond ETF (ticker: AGG). For the prototype, I  assumed that the member holds 110 shares of SPY, which represents the stock portion of their portfolio and 200 shares of AGG, which represents the bond portion. The process for the above discussed is as follows : 
* Create two variables named my_agg and my_spy and set them equal to 200 and 50, respectively.
* Set the variables for the Alpaca API and secret keys. Using the Alpaca SDK, create the Alpaca tradeapi.REST object. In this object, include the parameters for the Alpaca API key, the secret key, and the version number.
Markup : * Set the following parameters for the Alpaca API call:
** tickers: Use the tickers for the member’s stock and bond holdings.
** timeframe: Use a time frame of one day.
** start_date and end_date: Use the same date for these parameters, and format them with the date of the previous weekday (or 2020-08-07). This is because you want the one closing price for the most-recent trading day.
* Get the current closing prices for SPY and AGG by using the Alpaca get_bars function. Format the response as a Pandas DataFrame by including the df property at the end of the get_bars function.
* Navigating the Alpaca response DataFrame, select the SPY and AGG closing prices, and store them as variables.
* Calculate the value, in dollars, of the current amount of shares in each of the stock and bond portions of the portfolio, and print the results.
### Evaluate the Emergency Fund
In this section, I had to use the valuations for the cryptocurrency wallet and for the stock and bond portions of the portfolio to determine if the credit union member has enough savings to build an emergency fund into their financial plan which can be done using the steps below.
* Create a variable called monthly_income and set its value to 12000.
* To analyze savings health, create a DataFrame called df_savings with two rows. Store the total value in dollars of the crypto assets in the first row and the total value of the shares in the second row.
* Use the df_savings DataFrame to plot a pie chart to visualize the composition of personal savings.
* Use if conditional statements to validate if the current savings are enough for an emergency fund. An ideal emergency fund should be equal to three times your monthly income
- If total savings are greater than the emergency fund, display a message congratulating the person for having enough money in this fund.
- If total savings are equal to the emergency fund, display a message congratulating the person on reaching this financial goal.
- If total savings are less than the emergency fund, display a message showing how many dollars away the person is from reaching the goal.



