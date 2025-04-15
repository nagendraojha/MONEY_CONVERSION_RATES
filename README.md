# MONEY_CONVERSION_RATES
1. Importing Libraries:
BeautifulSoup from bs4: Used for parsing HTML data and extracting information.

requests: Used to send HTTP requests to the website and get HTML content.

2. Initial Setup:
currencies: An empty list to store all the currencies' names and their short codes (symbols).

page: Retrieves the raw HTML of the x-rates.com home page, which contains a list of currency options.

3. Scraping the Currency List:
soup: A BeautifulSoup object is created to parse the raw HTML content.

options: All <option> tags in the HTML are extracted, and the last 11 options (which don't represent valid currencies) are excluded using [:-11].

Looping through options:

Extracts the currency short code and the full name.

Creates a dictionary for each currency with keys name and short, and appends them to the currencies list.

Prints out the list of currencies with their position in the list (e.g., "1. Euro (EUR)").

4. User Input for Currency:
currency_index: Prompts the user to enter the position number of the currency they want to convert from. The input is adjusted (subtracting 1) to match the correct index in the list of currencies.

currency: The currency object (from the currencies list) based on the user's input.

amount: The user is prompted to enter an amount in the selected currency (with validation that the input is a floating point number).

5. Scraping Exchange Rates:
currencies_table_url: Constructs the URL for the currency exchange rate table based on the selected currency (currency['short']) and the amount entered by the user.

currencies_table_page: Fetches the exchange rate table from the URL.

soup: Creates a BeautifulSoup object to parse the HTML content of the exchange rate page.

6. Extracting Exchange Rates:
table_rows: Extracts all rows of the exchange rate table (skipping the first header row).

Looping through table_rows:

Extracts the currency and the corresponding exchange rate from each row.

Prints the amount of the selected currency in various other currencies using the format {:.3f} to display the exchange rate with three decimal places.

7. Final Output:
The script outputs the exchange rate for the user-specified amount of the selected currency, converted into other currencies.

Example Output:
The output might look like this:

vbnet
Copy
Edit
1. Euro (EUR)
2. British Pound (GBP)
3. Canadian Dollar (CAD)
Enter your currency's position number: 1
Enter amount of euros (if amount isn't integer, then write it with a dot, not comma): 100

For 100 euros you'll get:

1.179 GBP
1.420 CAD
1.750 USD
...
Key Points:
The script dynamically scrapes currency names and exchange rates from x-rates.com.

It allows the user to select a currency and input an amount to convert.

The script then fetches live exchange rates and displays the conversion for the entered amount in other currencies.
