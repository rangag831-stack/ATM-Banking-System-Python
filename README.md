# ATM-Banking-System-Python
ATM project
# Project Name: ATM Banking System

"I developed a console-based ATM Banking System using Python. The application allows users to credit money, debit money, check their account balance, and view transaction history. I used functions to divide the application into modules, lists to store transaction details, conditional statements for validations, and a while loop to maintain the ATM menu."


# BLOCK 1: Variable Initialization
balance = 0                 # Stores the initial account balance
mini_statement = []         # Creates an empty list to store transactions


# BLOCK 2: Credit Function
def credit():               # Defines a function to deposit money
    global balance          # Allows us to modify the global balance variable

    amount = float(input("Enter amount to credit: "))  # Gets deposit amount from user and converts it into float

    if amount <= 0:         # Checks whether the entered amount is zero or negative
        print("Please enter a positive amount.")  # Displays error message for invalid amount

    else:                   # Executes when the entered amount is positive
        balance += amount   # Adds deposit amount to the existing balance
        mini_statement.append(f"Credited: ${amount}")  # Stores deposit transaction in the list
        print(f"${amount} credited to your account.")  # Displays successful deposit message


# BLOCK 3: Debit Function
def debit():                # Defines a function to withdraw money
    global balance          # Allows us to modify the global balance variable

    amount = float(input("Enter amount to debit: "))  # Gets withdrawal amount from user

    if amount <= 0:         # Checks whether withdrawal amount is zero or negative
        print("Please enter a positive amount.")  # Displays error message

    elif amount > balance:  # Checks whether withdrawal amount exceeds available balance
        print("Insufficient balance.")  # Displays insufficient balance message

    else:                   # Executes when withdrawal amount is valid
        balance -= amount   # Subtracts withdrawal amount from account balance
        mini_statement.append(f"Debited: ${amount}")  # Stores withdrawal transaction in the list
        print(f"${amount} debited from your account.")  # Displays successful withdrawal message


# BLOCK 4: Check Balance Function
def check_balance():        # Defines a function to check account balance
    print(f"Your current balance is: ${balance}")  # Displays the current account balance


# BLOCK 5: Mini Statement Function
def show_mini_statement():  # Defines a function to display transaction history
    print("\n------ MINI STATEMENT ------")  # Displays mini statement heading

    if len(mini_statement) == 0:  # Checks whether the transaction list is empty
        print("No transactions found.")  # Displays message when there are no transactions

    else:                   # Executes when transactions are available
        for i in mini_statement:  # Loops through each transaction in the list
            print(i)        # Displays each transaction

    print(f"Available Balance: ${balance}")  # Displays the remaining account balance


# BLOCK 6: Menu Function
def menu():                 # Defines the main ATM menu function
    while True:             # Repeats the menu until the user chooses Exit

        print("\nATM Menu:")  # Displays ATM menu heading
        print("1. Credit")  # Displays deposit option
        print("2. Debit")   # Displays withdrawal option
        print("3. Balance")  # Displays balance inquiry option
        print("4. Mini Statement")  # Displays transaction history option
        print("5. Exit")    # Displays exit option

        choice = input("Enter your choice (1-5): ")  # Gets menu selection from user

        if choice == '1':   # Checks whether user selected Credit
            credit()        # Calls credit function

        elif choice == '2':  # Checks whether user selected Debit
            debit()         # Calls debit function

        elif choice == '3':  # Checks whether user selected Balance
            check_balance() # Calls check balance function

        elif choice == '4':  # Checks whether user selected Mini Statement
            show_mini_statement()  # Calls mini statement function

        elif choice == '5':  # Checks whether user selected Exit
            print("Thank you for using the ATM. Goodbye!")  # Displays exit message
            break           # Stops the while loop and exits the menu

        else:               # Executes when user enters an invalid option
            print("Invalid choice. Please try again.")  # Displays invalid choice message


# BLOCK 7: Main Function Calling
menu()                      # Calls the menu function and starts the ATM application



