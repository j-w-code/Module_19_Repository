# *Fintech Finder Transactions*
---
## Fintech Finder Transactions 
This project covers the usage of Python, Streamlit, Blockchain, and Ganache testing evnironments to create a signed Ethereum transaction. The results of using a Streamlit web UI frontend are written to a test ethereum blockchain. 

>"When I came up with Ethereum, my first first thought was, 'Okay, this thing is too good to be true.' Vitalik Buterin"

## Technologies 
This project uses Python, Streamlit, web3, and Ganache libraries to generate web UI front ends, and write transactions to a test block chain. 

[Python](https://github.com/python)
[Streamlit](https://github.com/streamlit)
[web3](https://github.com/ethereum/web3.py)
[Ganache](https://github.com/trufflesuite/ganache)

### Installation Guide

In order to use this program please import and utilize the following libraries and dependencies: 

```python
import streamlit as st
from dataclasses import dataclass
from typing import Any, List
from web3 import Web3
w3
```

## Usage
The following blocks of code are fundamental in executing the program. 

```python
from crypto_wallet import generate_account, get_balance, send_transaction
```
These helper functions are imported from a crypto wallet backend. They allow the fintech finder application to generate the account data, check balance, and send the transaction.

```python
candidate_database = {
    "Lane": ["Lane", "0xaC8eB8B2ed5C4a0fC41a84Ee4950F417f67029F0", "4.3", .20, "Images/lane.jpeg"],
    "Ash": ["Ash", "0x2422858F9C4480c2724A309D58Ffd7Ac8bF65396", "5.0", .33, "Images/ash.jpeg"],
    "Jo": ["Jo", "0x8fD00f170FDf3772C5ebdCD90bF257316c69BA45", "4.7", .19, "Images/jo.jpeg"],
    "Kendall": ["Kendall", "0x8fD00f170FDf3772C5ebdCD90bF257316c69BA45", "4.1", .16, "Images/kendall.jpeg"]
}
```
This simple database stores a dictionary with the values for our fintech candidates, their ratings, hourly wage in ETH, and profile photos. 

```python
def get_people(w3):
    db_list = list(candidate_database.values())

    for number in range(len(people)):
        st.image(db_list[number][4], width=200)
        st.write("Name: ", db_list[number][0])
        st.write("Ethereum Account Address: ", db_list[number][1])
        st.write("FinTech Finder Rating: ", db_list[number][2])
        st.write("Hourly Rate per Ether: ", db_list[number][3], "eth")
        st.text(" \n")
```
This function writes the resutls of the database to the streamlit web interface for selection by the user. 

```python
account = generate_account()
st.sidebar.write(account.address)
```
This code calls the generate_account function and saves it as a variable called "account". this variable is then written to a sidebar in the streamlit interface.

```python
wage = candidate_database[person][3] * hours
st.sidebar.write(wage)
```
This code calculates the amount of ETH to pay each candidate based on the information contained in the database multiplied by the number of hours. The calculation is then saved as a variable "wage" and written into a streamlit sidebar. 

```python
if st.sidebar.button("Send Transaction"):
    transaction_hash = send_transaction(w3,account,candidate_address, wage)
    st.sidebar.markdown("#### Validated Transaction Hash")
    st.sidebar.write(transaction_hash)
    st.balloons()
get_people(w3)
```
This function creates a sidebar in streamlit to send the transaction. The "transaction_hash" variable stores the send_transaction function with it's attendant values. The remaining streamlit code writes this function into the web UI. 

## Results
The following media shows the results of our Fintech Finder program. 

![<alt text>](https://i.postimg.cc/QtwvQ51T/Screen-Shot-2022-08-28-at-1-06-59-PM.png)

This image shows our Streamlit web interface with a validated transaction hash. 

![<alt text>](https://i.postimg.cc/Vv90qqpG/Screen-Shot-2022-08-28-at-11-58-27-AM.png)

This shows our primary account (index 0) with the corresponding amount of ETH withdrawn. 

![<alt text>](https://i.postimg.cc/6Q6cy32x/Screen-Shot-2022-08-28-at-12-04-58-PM.png)

This shows the transactions panel with our transaction history. 
