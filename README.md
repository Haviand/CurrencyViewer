Currency Viewer
===============
This is a short python3 framework that dynamically displays and converts the cryptocurrencies in your Kraken wallet into equivalents fiat money. Variables and functions may help developpers to easily extract data from Kraken and process value conversions.
It's also possible to store data in a csv file.
Next feature will add high-level orders functions.

Any contribution in any way is welcome. Feel free to contribute to this project!

Author : smechaab

Contact : s.mechaab@protonmail.com
If this script helped you or if you have any feedback, please don't hesitate to contact me.

Credits 
------- 
This code is based on Krakenex Python3 API by veox: https://github.com/veox/python3-krakenex 

* v0.2.1

This is a tiny program I personally use it daily. 
It allows me to check my currencies without logging every 10 minutes on Kraken website. 
This is also very useful for developers on the Krakenex API thanks to dynamically extracted data. 

Please note that you need to fill your kraken.key file with your API keys. You can easily generate a pair of keys on the Kraken website, see the API documentation : https://www.kraken.com/help/api  

v0.2.1 Changes 
---------------- 
Adding CSV log writing feature. Your data are now stored in data.csv by default which is located in the same directory. 
Providing more object-oriented code, thus more library-oriented.

Program features 
---------------- 

1.    Displaying the different amount of crypto currencies you own on your Kraken wallet. 

2.    Displaying the total crypto money you own in equivalent fiat money. 

3.    Adapted to the crypto and fiat currencies you already own. 

4.    If you don't own any fiat money on your Kraken wallet, it will be displayed the equivalent in USD. 
	   
5.    Working with multi-fiat currencies wallets.

6. Writes data in a csv file located in the project folder (default : data.csv).

NOTE: Some bugs need to be fixed with fiat currencies other than EUR or USD,
it will be patched in the next one.

Installation
------------
This package requires Python 3.3 or later, and needs [krakenex](https://github.com/veox/python3-krakenex) library.

You can find a [PyPI package](https://pypi.org/project/currency-viewer/) available.

**Using pip:**

	pip install currency-viewer

Example
-------

See `basic_example.py`
```
from currency_viewer import currency_viewer as cv

a = cv.CurrencyViewer()
a.processCViewer(log=True, currency="USD", time="rfc1123")
```

This is aimed to be very easy to use.

It is also possible to call some intermediate functions :

* ```processCViewer(self, log=True, currency="USD", time="rfc1123")```:
Main function to call, implies to call : collectData(), getMarketPrice(), processingConversion(), displayResults() and writeLog().
Returns nothing


* ```collectData(self)```:
Uses krakenex library get data from Kraken API in Json.
Returns raw data, list of crypto in user's wallet, list of fiat in user's wallet


* ```getXBTtoFiatPrice(self, fiat)```:
Return XBT price for "fiat" input currency


* ```getMarketPrice(self, crypto_index)```:
Returns crypto price in XBT


* ```updateFiatInTotal(self, fiat)```:
Updates "total" dict table to add { Fiat_currency : Total_Wallet_Value }.
Returns nothing


* ```displayResults(self)```:
	* ``values`` (dict), total value of all crypto in XBT
	* ``total`` (dict), total value in fiat currencies


Interesting variables 
--------------------- 

* ``currencies`` : List of differents currencies owned by user 
* ``balance`` : List of the differents amount of crypto currencies owned by client 
* ``market`` :  List of markets concerned by currencies in user's wallet (same order as price) 
* ``values`` : Dictionnary of current values in fiat money user's crypto currencies balance is equivalent to (according to real-time markets) 
		Keys are dynamically generated by markets concerned by user 
		
TESTS: 
----- 
CurrencyViewer uses [pytest](https://pypi.org/project/pytest/) module for its core tests, be sure to have the package beforehand.

Otherwise you can download and install it with pip:
```
pip install pytest
```

You also need to paste a copy of your [kraken.key](https://www.kraken.com/help/api) file into your tests/ directory.

In order to execute tests, go into your CurrencyViewer working directory and launch:
```
pytest tests/test_processing.py
```
or to add python path in pytest command try :
```
python -m pytest tests/test_processing.py
```
	 
TODO: 
----- 
1. Add orders actions
2. Add other exchanges 
3. Add a GUI 
