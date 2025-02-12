# Banking-system-python-mini-project

class BankingSystem:

    def __init__(self, account_holder,  pin , balance=0):
        self.account_holder = account_holder
        self.pin = pin
        self.balance = balance

    def login(self, entered_pin):
        return entered_pin == self.pin

    def deposit(self, amount):
        self.balance += amount
        return f"Deposited Rs{amount}. Current balance: Rs{self.balance}"

    def withdraw(self, amount):
        if amount <= self.balance:
            self.balance -= amount
            return f"Withdrawn Rs{amount}. Current balance: Rs{self.balance}"
        else:
            return "Insufficient funds."


def main():
    account_holder = "Diya Ummer"
    pin = "2503"
    current_balance = 75000

    user_account = BankingSystem(account_holder, pin, current_balance)

    # Login
    entered_pin = input("Enter your PIN: ")
    if user_account.login(entered_pin):
        print("Successfully logged in! Welcome to Kotak Mahindra Bank!")
    else:
        print("Incorrect PIN. Please try again.")
        return

    # Account selection
    while True:
        print("\nSelect your Account:")
        print("1. Savings Account")
        print("2. Current Account")

        choice = input("Select your Account (1/2): ")

        if choice == "1":
            print("Successfully Logged In to Savings Account.")
            break
        elif choice == "2":
            print("Sorry, This account holder does not hold a Current Account. Thank you.")
        else:
            print("Invalid option. Please enter 1 or 2.")

    # Banking options
    while True:
        print("\nSelect your transaction:")
        print("1. Withdraw")
        print("2. Deposit")
        print("3. Check Balance")
        print("4. Exit")

        choice = input("Enter your transaction (1/2/3/4): ")

        if choice == "1":
            withdraw_amount = float(input("Enter the withdrawal amount: "))
            print(user_account.withdraw(withdraw_amount))
        elif choice == "2":
            deposit_amount = float(input("Enter the deposit amount: "))
            print(user_account.deposit(deposit_amount))
        elif choice == "3":
            print(f"Your current balance is: Rs{user_account.balance}")
        elif choice == "4":
            print("Thank you for using our ATM - Kotak Mahindra Bank. Goodbye!")
            break
        else:
            print("Invalid option. Please enter 1, 2, 3, or 4.")


if __name__ == "__main__":
    main()

