HW16: Bank Accounts: Modified to Include Sorting and Searching Methods
You have been hired as a programmer by a major bank. Your first project is a small banking transaction system. The user of the
program (the teller) can create a new account, as well as perform deposits, withdrawals, balance inquiries, close accounts, etc.
For this assignment, you must have at least the following classes:
1. A Bank class which consists of an unsorted ArrayList of Accounts currently active or closed.
In addition, the Bank class has several static member variables and methods:
totalAmountInSavingsAccts - sum total of balances in all Savings accounts
totalAmountInCheckingAccts - sum total of balances in all Checking accounts
totalAmountInCDAccts - total - sum total of balances in all CD accounts
totalAmountInAllAccts - total - sum total of balances in all accounts
Make sure to provide appropriate methods so as to allow for the addition to, subtraction from, and reading of, the
current values of each of these static variables.
Be sure to print the values of all of these static variables when you print the database of accounts.
The Bank Class also has an ArrayList of Integers (e.g., ArrayList<Integers> acctNumSortKey) to act as a sorting key
to sort the database of Accounts by account numbers.
The Bank Class also has an ArrayList of Integers (e.g., ArrayList<Integers> ssnSortKey) to act as a sorting key to
sort the database of Accounts by SSNs.
The Bank Class also has an ArrayList of Integers (e.g., ArrayList<Integers> nameSortKey) to act as a sorting key to
sort the database of Accounts alphabetically by Name objects.
The Bank class does not override either the toString() or the equals() method.
*2. An Account class which consists of a Depositor, an account number, an account type, account status (open or closed),
account balance, an ArrayList of TransactionReceipts performed on the account (Note: creating an account is
considered a transaction.).
The Account class must have a copy constructor and override both the toString() and the equals() methods.
The Account class has several subclasses:
2a.The SavingsAccount class is a subclass of the Account class.
For Saving Accounts, deposits and withdrawals are allowed at any time.
The SavingsAccount class must have a copy constructor and override both the toString() and the equals() methods.
2b.The CheckingAccount class is a subclass of the Account class.
For Checking Accounts, deposits, withdrawals, and check clearing are allowed at any time. Remember, you may only
clear a check if the date on the check is no more than six months ago. No post-dated checks (checks with a future date)
may be cleared. Use the Calendar class to implement this. In addition, a check will clear only if there is sufficient funds
in the account. If the account lacks sufficient funds, the check will not clear and the account will be charged a $2.50
Service Fee for “bouncing” a check. In addition to the previous rules, if the current balance of the account is below
$2500, each withdrawal or cleared check is charged a fee of $1.50.
The CheckingAccount class must have a copy constructor and override both the toString() and the equals() methods.
2c.The CDAccount class is a subclass of the Account class.
The class has a data member: a maturityDate which is a Calendar class object.
As before, deposits and withdrawals will be allowed only on or after the maturity date. When a deposit or withdrawal is
made, have the user select a new maturity date for the CD. The choices are either 6, 12, 18, or 24 months from the date of
the deposit or withdrawal. Again, use the Calendar class to implement this.
The CDAccount class must have a copy constructor and override both the toString() and the equals() methods.
3. A Depositor class which has a Name and a social security number.
The Depositor class must have a copy constructor and override both the toString() and the equals() methods.
4. A Name class which consists of first and last names.
The Name class must have a copy constructor and override the toString(), the equals(), and the compareTo() methods.
5. A Check class with data fields consisting of an account number, the check amount, and a dateOfCheck
The Check class must have a copy constructor and override the toString() method.
6. A TransactionTicket class with data fields consisting of a dateOfTransaction, typeOfTransaction (deposit, withdrawal,
balance inquiry, new account, delete account, etc.), account number, amountOfTransaction (for deposits and
withdrawals), termOfCD (6, 12, 18, or 24 months - see below).
The TransactionTicket class must have a copy constructor and override the toString() method.
7. A TransactionReceipt class with data fields consisting of a TransactionTicket, successIndicatorFlag, reasonForFailure
String, preTransactionBalance, postTransactionBalance, postTransactionMaturityDate (for CDs).
The TransactionReceipt class must have a copy constructor and override the toString() method.
You must implement appropriate methods in each class so as to implement the functionality required.
The data members of each class must be private (or protected when providing subclass access).
Provide accessor and mutator methods as necessary.
An Account object should access subclass methods using polymorphism.
Remember, all I/O should be done only in the methods of the class that contains the main() method.
Initially, the account information of existing customers is to be read into the database.use method readAccts() described below.
(Note: the ArrayList of Accounts will grow dynamically as each account is created.) The program keeps track of the actual
number of currently active accounts.
After initialization, a neatly formatted table of the initial unsorted database of active accounts should be printed. Use
method printAccts() described below
Now sort The ArrayList of Accounts into ascending numerical order by account number using the Account Number sort
key (e.g., acctNumSortKey) and the QuickSort Algorithm. After sorting, print a neatly formatted table of the sorted
database of active accounts. Use method printAcctsByAcctNumSortKey() to do this.
Now sort The ArrayList of Accounts into ascending order by SSN using the SSN sort key (e.g., ssnSortKey) and the
Bubble Sort Algorithm. After sorting, print a neatly formatted table of the sorted database of active accounts by SSN.
Create and use method printAcctsBySSNSortKey() to do this.
Now sort The ArrayList of Accounts into alphabetical order by Name using the Name sort key (e.g., nameSortKey) and
the Insertion Sort Algorithm. After sorting, print a neatly formatted table of the sorted database of active accounts by in
alphabetical order. Create and use method printAcctsByNameSortKey() to do this.
The program then allows the user to select from the following menu of transactions:
Select one of the following:
W - Withdrawal
D - Deposit
C - Clear Check
N - New account (NOTE: the ArrayList of Accounts will grow when you create a new Account)
B - Balance
I - Account Info (without transaction history) (NOTE: include at least one depositor who has multiple accounts)
H - Account Info plus Account Transaction History
S - Close Account (close (shut), but do not delete the account) (Note: no transactions are allowed on a closed account)
R - Reopen a closed account
X - Delete Account (close and delete the account from the database)) (NOTE: must have zero balance to delete)
Q - Quit
Note 1: The Clear Check transaction is only valid for checking accounts. It is like a withdrawal; except, you must also check the
date of the check. You may only clear a check if the date on the check is no more than six months ago. No post-dated
checks (checks with a future date) may be cleared. Use the Calendar class to implement this. In addition, a check will
clear only if there is sufficient funds in the account. If the account lacks sufficient funds, the check will not clear and the
account will be charged a $2.50 Service Fee for “bouncing” a check.
Note 2: CD accounts will now contain a maturityDate. Deposits and Withdrawals will be allowed only on or after the maturity
date. When a deposit or withdrawal is made, have the user select a new maturity date fro the CD. the choices are either 6,
12, 18, or 24 months from the date of the deposit or withdrawal. Again, use the Calendar class to implement this.
The main method then prompts the user for a selection. You should verify that the user has typed in a valid selection (otherwise
print out an error message and repeat the prompt). Once the user has entered a valid selection, using a switch statement,
appropriate methods (in the class that contains the main() method) should be called to perform the specific transaction. These
methods will call the class implemented methods as necessary.
At the end, before the user quits, the program prints the contents of the final database four ways:
a) unsorted
b) sorted by account number (using the QuickSort Algorithm)
c) sorted by SSN (using the Bubble Sort Algorithm)
d) sorted alphabetically (using the Insertion Sort Algorithm)
Invalid operations are to be handled by exceptions. You should minimally implement the following exceptions:
InvalidAccountException
InvalidAmountException
AccountClosedException
InsufficientFundsException
InvalidMenuSelectionException
PostDatedCheckException
CheckTooOldException
AccountNotCheckingAccountException
CDMaturityDateException
All exceptions are to be handled within the Bank Class except for the InvalidMenuSelectionException which is to be
handled within main().
Note: Make sure that when a method in an aggregate class returns a reference to a field object, it returns a reference to a
copy of the field object.
Make sure to use enough test cases so as to completely test program functionality.
Make sure that there is at least one depositor that has multiple accounts at the bank.
Make sure that there is at least two depositors with the same last name and different first names.
Notes:
1. All output must be file directed (i.e., sent to an output file)
2. Only output must go to the file - not interactive prompts and menus.
3. No global variables are allowed
4. The program and all methods must be properly commented.
5. All data members of classes are to be private (or protected when providing subclass access)
6. All I/O should be done within the methods of the class that contains the main() method.
Extra Credit #1:
The initial database of Accounts should be printed as follows:
a) unsorted
b.1) sorted by account number (using the QuickSort Algorithm - using sort key acctNumQuickSortKey)
b.2) sorted by account number (using the Bubble Sort Algorithm - using sort key acctNumBubbleSortKey)
b.3) sorted by account number (using the Insertion Sort Algorithm - using sort key acctNumInsertionSortKey)
c.1) sorted by SSN (using the QuickSort Algorithm - using sort key ssnQuickSortKey)
c.2) sorted by SSN (using the Bubble Sort Algorithm - using sort key ssnBubbleSortKey)
c.3) sorted by SSN (using the Insertion Sort Algorithm - using sort key ssnInsertionSortKey)
d.1) sorted by Name (using the QuickSort Algorithm - using sort key nameQuickSortKey)
d.2) sorted by Name (using the Bubble Sort Algorithm - using sort key nameBubbleSortKey)
d.3) sorted by Name (using the Insertion Sort Algorithm - using sort key nameInsertionSortKey)
At the end, before the user quits, the program prints the contents of the final database as follows:
a) unsorted
b.1) sorted by account number (using the QuickSort Algorithm - using sort key acctNumQuickSortKey)
b.2) sorted by account number (using the Bubble Sort Algorithm - using sort key acctNumBubbleSortKey)
b.3) sorted by account number (using the Insertion Sort Algorithm - using sort key acctNumInsertionSortKey)
c.1) sorted by SSN (using the QuickSort Algorithm - using sort key ssnQuickSortKey)
c.2) sorted by SSN (using the Bubble Sort Algorithm - using sort key ssnBubbleSortKey)
c.3) sorted by SSN (using the Insertion Sort Algorithm - using sort key ssnInsertionSortKey)
d.1) sorted by Name (using the QuickSort Algorithm - using sort key nameQuickSortKey)
d.2) sorted by Name (using the Bubble Sort Algorithm - using sort key nameBubbleSortKey)
d.3) sorted by Name (using the Insertion Sort Algorithm - using sort key nameInsertionSortKey)
