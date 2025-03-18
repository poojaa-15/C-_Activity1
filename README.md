# C-_Activity1


#include <iostream>
#include <string>

using namespace std;

const int MAX_EXPENSES = 100; 

struct Expense {
    string category;
    double amount;
};

void addExpense(Expense expenses[], int& expenseCount) {
    if (expenseCount >= MAX_EXPENSES) {
        cout << "Expense list is full!" << endl;
        return;
    }
    
    cout << "Enter expense category: ";
    cin >> expenses[expenseCount].category;
    cout << "Enter expense amount: ";
    cin >> expenses[expenseCount].amount;
    
    expenseCount++;
    cout << "Expense added successfully!" << endl;
}

void displayExpenses(const Expense expenses[], int expenseCount) {
    if (expenseCount == 0) {
        cout << "No expenses to display!" << endl;
        return;
    }

    cout << "\nYour Expenses: \n";
    for (int i = 0; i < expenseCount; i++) {
        cout << "Category: " << expenses[i].category << ", Amount: " << expenses[i].amount << endl;
    }
}

double calculateTotal(const Expense expenses[], int expenseCount) {
    double total = 0;
    for (int i = 0; i < expenseCount; i++) {
        total += expenses[i].amount;
    }
    return total;
}

int main() {
    Expense expenses[MAX_EXPENSES];
    int expenseCount = 0;
    int choice;

    while (true) {
        cout << "\nExpense Tracker Menu: \n";
        cout << "1. Add Expense\n";
        cout << "2. View Expenses\n";
        cout << "3. Calculate Total\n";
        cout << "4. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                addExpense(expenses, expenseCount);
                break;
            case 2:
                displayExpenses(expenses, expenseCount);
                break;
            case 3:
                cout << "Total Expenses: " << calculateTotal(expenses, expenseCount) << endl;
                break;
            case 4:
                cout << "Exiting program..." << endl;
                return 0;
            default:
                cout << "Invalid choice. Please try again." << endl;
        }
    }

    return 0;
}
