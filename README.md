class ATM:
    def __init__(self):
        self.pin = ""
        self.balance = 0

     
        self.accounts = {
            "ravi": "101",
            "priya": "102",
            "amit": "103"
        }

        self.menu()

    def menu(self):
        while True:
            print("""
            press
            1 for create pin
            2 for change pin
            3 for check balance
            4 for withdraw
            5 for deposit
            6 for transfer
            7 for exit
            """)

            user_input = input("Enter your choice: ")

            if user_input == "1":
                self.create_pin()

            elif user_input == "2":
                self.change_pin()

            elif user_input == "3":
                self.check_balance()

            elif user_input == "4":
                self.withdraw()

            elif user_input == "5":
                self.deposit()

            elif user_input == "6":
                self.transfer()

            elif user_input == "7":
                print("Thank you for using ATM")
                break

            else:
                print("Invalid Choice")

    def create_pin(self):
        print("Create Pin")
        self.pin = input("Enter new pin: ")
        self.balance = int(input("Enter initial balance: "))
        print("Pin created successfully")

    def change_pin(self):
        old_pin = input("Enter old pin: ")
        if old_pin == self.pin:
            self.pin = input("Enter new pin: ")
            print("Pin changed successfully")
        else:
            print("Wrong Pin")

    def check_balance(self):
        user_pin = input("Enter pin: ")
        if user_pin == self.pin:
            print("Your Balance is:", self.balance)
        else:
            print("Wrong Pin")

    def withdraw(self):
        user_pin = input("Enter pin: ")
        if user_pin == self.pin:
            amount = int(input("Enter amount: "))
            if amount <= self.balance:
                self.balance -= amount
                print("Withdraw successful")
                print("Remaining Balance:", self.balance)
            else:
                print("Insufficient Balance")
        else:
            print("Wrong Pin")

    def deposit(self):
        user_pin = input("Enter pin: ")
        if user_pin == self.pin:
            amount = int(input("Enter amount: "))
            self.balance += amount
            print("Deposit successful")
            print("Updated Balance:", self.balance)
        else:
            print("Wrong Pin")

    def transfer(self):
        user_pin = input("Enter pin: ")

        if user_pin == self.pin:

            name = input("Enter receiver name: ").strip().lower()

            if name in self.accounts:
                print("Name Matched ✔")

                acc_no = input("Enter receiver account number: ")

                if acc_no == self.accounts[name]:

                    amount = int(input("Enter transfer amount: "))

                    if amount <= self.balance:
                        self.balance -= amount
                        print("Transfer Successful")
                        print("Remaining Balance:", self.balance)
                    else:
                        print("Insufficient Balance")

                else:
                    print("Account Number Mismatch")

            else:
                print("Account Name Not Found")

        else:
            print("Wrong Pin")


sbi = ATM(
