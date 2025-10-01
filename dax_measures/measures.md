# DAX Measures for UPI Transaction Dashboard

This document contains the key DAX measures used in the UPI Transaction Dashboard. These measures help calculate metrics related to transactions, customers, and banks for analytical insights.

---

## 1. Transaction Metrics

### 1.1 Total Transactions

Total Transactions = COUNT('UPI_Transactions'[TransactionID])
Counts the total number of UPI transactions.

### 1.2 Total Amount Transferred
Total Amount = SUM('UPI_Transactions'[Amount])
Calculates the total amount transferred through UPI.

### 1.3 Average Transaction Value
Average Transaction = AVERAGE('UPI_Transactions'[Amount])
Gives the average value of all transactions.

### 1.4 Maximum Transaction Amount
Max Transaction = MAX('UPI_Transactions'[Amount])
Returns the highest transaction amount.

### 1.5 Minimum Transaction Amount
Min Transaction = MIN('UPI_Transactions'[Amount])
Returns the lowest transaction amount.

---

## 2. Transaction Status Metrics

### 2.1 Successful Transactions
Successful Transactions = 
CALCULATE(
    COUNT('UPI_Transactions'[TransactionID]),
    'UPI_Transactions'[Status] = "Success"
)
Counts only successful transactions.

### 2.2 Failed Transactions
Failed Transactions = 
CALCULATE(
    COUNT('UPI_Transactions'[TransactionID]),
    'UPI_Transactions'[Status] = "Failed"
)
Counts only failed transactions.

### 2.3 Success Rate (%)
Success Rate (%) = 
DIVIDE(
    [Successful Transactions],
    [Total Transactions],
    0
) * 100
Calculates the percentage of successful transactions.

---

## 3.Customer Metrics

### 3.1 Total Customers
Total Customers = DISTINCTCOUNT('UPI_Transactions'[CustomerAccountNumber])
Counts unique customers.

### 3.2 Average Transaction per Customer
Avg Transaction per Customer = 
DIVIDE([Total Transactions], [Total Customers], 0)
Average number of transactions per customer.

### 3.3 Total Amount per Customer
Avg Amount per Customer = 
DIVIDE([Total Amount], [Total Customers], 0)
Average total amount transferred per customer.

---

## 4.Bank Metrics

### 4.1 Total Sending Banks
Total Sending Banks = DISTINCTCOUNT('UPI_Transactions'[BankNameSent])
Counts unique sending banks.

### 4.2 Total Receiving Banks
Total Receiving Banks = DISTINCTCOUNT('UPI_Transactions'[BankNameReceived])
Counts unique receiving banks.

### 4.3 Top Bank by Transaction Volume
Top Sending Bank = 
TOPN(
    1,
    SUMMARIZE(
        'UPI_Transactions',
        'UPI_Transactions'[BankNameSent],
        "TotalAmount", SUM('UPI_Transactions'[Amount])
    ),
    [TotalAmount],
    DESC
)
dentifies the bank with the highest transaction amount.

---

## 5.Payment Mode & Device Metrics

### 5.1 Transactions by Payment Mode
Transactions by Payment Mode = COUNTROWS('UPI_Transactions')
Can be used in a visual grouped by PaymentMode.

### 5.2 Transactions by Device Type
Transactions by Device Type = COUNTROWS('UPI_Transactions')
Can be used in a visual grouped by DeviceType.

---

## 6.Time-Based Metrics

### 6.1 Time-Based Metrics
Transactions Today = 
CALCULATE(
    [Total Transactions],
    'UPI_Transactions'[TransactionDate] = TODAY()
)
Counts transactions for the current day.

### 6.2 Transactions This Month
Transactions This Month = 
CALCULATE(
    [Total Transactions],
    FILTER(
        'UPI_Transactions',
        MONTH('UPI_Transactions'[TransactionDate]) = MONTH(TODAY()) &&
        YEAR('UPI_Transactions'[TransactionDate]) = YEAR(TODAY())
    )
)
Counts transactions for the current month.

### 6.3 Monthly Transaction Trend
Monthly Amount = 
CALCULATE(
    [Total Amount],
    DATESMTD('UPI_Transactions'[TransactionDate])
)
Shows total transaction amount month-to-date.

---

## 7. City & Gender Metrics

### 7.1 Total Transactions by City
Transactions by City = COUNTROWS('UPI_Transactions')
Use this measure with a City column in visuals.

### 7.2 Total Amount by Gender
Amount by Gender = SUM('UPI_Transactions'[Amount])
se with the Gender column for comparison.




