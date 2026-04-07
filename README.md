# Grocery-Billing-system_DIYA-AGRAWAL_202501100700072_ECE-B 
from abc import ABC, abstractmethod

# [cite: 5, 6] Abstract base class Payment
class Payment(ABC):
    def __init__(self, user_name):
        self.user_name = user_name
        self.original_amount = 0
        self.final_amount = 0

    @abstractmethod
    def pay(self, amount):
        pass

    def generate_receipt(self):
        print(f"--- Receipt for {self.user_name} ---")
        print(f"Original Amount: {self.original_amount}")
        print(f"Final Amount Paid: {self.final_amount:.2f}")
        print("-" * 30)

# [cite: 8, 9] Credit Card Payment Implementation
class CreditCardPayment(Payment):
    def pay(self, amount):
        self.original_amount = amount
        gateway_fee = amount * 0.02
        gst = gateway_fee * 0.18
        self.final_amount = amount + gateway_fee + gst
        self.generate_receipt()

# [cite: 10, 11] UPI Payment Implementation
class UPIPayment(Payment):
    def pay(self, amount):
        self.original_amount = amount
        cashback = 50 if amount > 1000 else 0
        self.final_amount = amount - cashback
        self.generate_receipt()

# [cite: 12] PayPal Payment Implementation
class PayPalPayment(Payment):
    def pay(self, amount):
        self.original_amount = amount
        intl_fee = amount * 0.03
        conv_fee = 20
        self.final_amount = amount + intl_fee + conv_fee
        self.generate_receipt()

# [cite: 13, 14] Wallet Payment Implementation
class WalletPayment(Payment):
    def __init__(self, user_name, balance):
        super().__init__(user_name)
        self.balance = balance

    def pay(self, amount):
        self.original_amount = amount
        if amount > self.balance:
            print(f"Transaction Failed for {self.user_name}: Insufficient wallet balance.")
        else:
            self.balance -= amount
            self.final_amount = amount
            print(f"Wallet updated. Remaining balance: {self.balance}")
            self.generate_receipt()

# [cite: 15, 16] Function to demonstrate Runtime Polymorphism
def process_payment(payment_obj, amount):
    payment_obj.pay(amount)

# [cite: 17] Main execution
if __name__ == "__main__":
    # Create objects
    cc = CreditCardPayment("Alice")
    upi = UPIPayment("Bob")
    pp = PayPalPayment("Charlie")
    wallet = WalletPayment("Diana", 500)

    # Process transactions
    process_payment(cc, 1000)
    process_payment(upi, 1500)
    process_payment(pp, 2000)
    process_payment(wallet, 300)

