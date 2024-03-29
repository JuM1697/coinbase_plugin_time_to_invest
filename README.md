# Coinbase Plugin Time To Invest
Nagios Plugin to monitor prices of specific Crypto Currencies on Coinbase.

## Purpose
The goal of this script is to monitor current buy rates for various Crypto Currencies on Coinbase, including the fees.
### When should I use this plugin?
If you have in your head something like: "If I can get 1 BTC for 2.000$ I want to receive a notification." - This is the plugin you were looking for.
### Why should I use this plugin?
Due to the fact that Coinbase has really high fees it's interesting to monitor the buy prices including the fees without checking the app or web interface all the time.
Connecting this script with Icinga or Nagios makes it even easier to automatically start processes if your desired price is currently live.

## Functionality
This script works using the official Coinbase API (key and secret).  
The plugin has been written in Python which gives it the additional feature to use the official Coinbase Python Library.  
The plugin also returns the current price for the defined amount as performance data.

## Requirements
* argparse
* coinbase
### Requirements installation
`pip install argparse`  
`pip install coinbase` 

## Usage
Just call the script using the following parameters and input values:  
`./check_cbTimeToInvest.py -k <API Key> -s <API Secret> -c <Which Crypto do you want to buy> -a <Crypto Wallet> -b <Amount of Crypto you want to buy> -p <Your desired payment method> -i <How much of your payment Method do you want to invest>`

Example:  
`./check_cbTimeToInvest.py -k 'xxxxxxxxxxxxxxxx' -s 'xxxxxxxxxxxxxxxxxxxxxx' -c 'BTC' -a 'BTC Wallet' -b '1' -p 'USD Wallet' -i '1000.00'`

## Exit Codes
|Code|Nagios State|Description|Output|
|---|---|---|---|
|0|OK - Green|The desired price for the specified currency is not reached|Your desired target price is not reached. Keep waiting! \| price=\<value\>|
|2|Critical - Red|The desired price for the specified currency is not reached.|Your desired target price is reached! \| price=\<value\> |
