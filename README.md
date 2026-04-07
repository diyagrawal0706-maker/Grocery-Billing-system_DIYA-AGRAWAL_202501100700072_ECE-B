# Grocery-Billing-system_DIYA-AGRAWAL_202501100700072_ECE-B 

Smart Payment Processing System (OOP in Python)
 Overview

This project is a Smart Payment Processing System built using Object-Oriented Programming (OOP) concepts in Python. It simulates multiple payment methods like Credit Card, UPI, PayPal, and Wallet, each with its own processing logic.

The system demonstrates key OOP principles:

Abstraction
Inheritance
Polymorphism

 Features
Common interface for all payment types using an abstract base class
Different payment methods with unique transaction rules
Real-time transaction processing
Receipt generation for each transaction
Wallet balance management
Demonstrates runtime polymorphism

Class Structure
 Base Class: Payment
Stores user name
Abstract method: pay(amount)
Concrete method: generate_receipt()
 Derived Classes
 CreditCardPayment
Charges 2% gateway fee
Adds 18% GST
Final amount = amount + fee + GST
 UPIPayment
₹50 cashback if amount > ₹1000
Final amount = amount - cashback
PayPalPayment
6% international fee
2% fixed currency conversion fee
Final amount = amount + fees
 WalletPayment
Maintains a wallet balance
Transaction fails if balance is insufficient
Deducts amount if successful
Polymorphism

Each payment type overrides the pay() method differently.
You can call the same method (pay()) on different objects, and it behaves accordingly.

 Project Structure
 SmartPaymentSystem/

 payment.py          # Base class
 credit_card.py      # CreditCardPayment class
 upi.py              # UPIPayment class
 paypal.py           # PayPalPayment class
 wallet.py           # WalletPayment class
 main.py             # Driver code to test transactions
 README.md
 How to Run
Clone the repository:
git clone https://github.com/your-username/smart-payment-system.git
Navigate to the project folder:
cd smart-payment-system
Run the program:
python main.py
 Example Usage
payments = [
    CreditCardPayment("Diya"),
    UPIPayment("Diya"),
    PayPalPayment("Diya"),
    WalletPayment("Diya", balance=5000)
]

for payment in payments:
    payment.pay(1500)
 Concepts Demonstrated
Concept	Implementation
Abstraction	Abstract base class Payment
Inheritance	All payment types inherit from Payment
Polymorphism	Different implementations of pay()
Encapsulation	Data stored within objects
Learning Outcome

By completing this project, you will understand:

How to design class hierarchies
How to use abstract classes in Python
Real-world use of OOP concepts
Writing modular and reusable code
 Contribution

Feel free to fork this repository and improve the project by:

Adding new payment methods
Enhancing UI (CLI/GUI)
Adding error handling



sample test case

--- Receipt for Alice ---
Original Amount: 1000
Final Amount Paid: 1023.60
------------------------------
--- Receipt for Bob ---
Original Amount: 1500
Final Amount Paid: 1450.00
------------------------------
--- Receipt for Charlie ---
Original Amount: 2000
Final Amount Paid: 2080.00
------------------------------
Wallet updated. Remaining balance: 200
--- Receipt for Diana ---
Original Amount: 300
Final Amount Paid: 300.00
------------------------------
