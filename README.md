# Banking-management-system
#include <iostream>
using namespace std;

class Bank {
    int accNo;
    string name;
    float balance;

public:
    Bank() { accNo = 0; balance = 0; } 

    void createAccount() {
        cout << "Enter Account Number: ";
        cin >> accNo;
        cout << "Enter Name: ";
        cin >> name;
        cout << "Enter Initial Deposit: ";
        cin >> balance;
        cout << "Account Created Successfully!\n";
    }

    void deposit() {
        float amt;
        cout << "Enter Amount to Deposit: ";
        cin >> amt;
        balance += amt;
        cout << "New Balance: " << balance << endl;
    }

    void withdraw() {
        float amt;
        cout << "Enter Amount to Withdraw: ";
        cin >> amt;
        if (amt > balance)
            cout << "Insufficient Balance!\n";
        else {
            balance -= amt;
            cout << "Withdrawal Successful! Balance: " << balance << endl;
        }
    }

    void display() {
        cout << "\n--- Account Details ---\n";
        cout << "Account Number: " << accNo << endl;
        cout << "Name: " << name << endl;
        cout << "Balance: " << balance << endl;
    }

    int getAccNo() { return accNo; }
};

int main() {
    Bank b[5];   
    int choice, num, i;
    bool found;

    do {
        cout << "\n=== BANK MENU ===";
        cout << "\n1. Create Account";
        cout << "\n2. Deposit Money";
        cout << "\n3. Withdraw Money";
        cout << "\n4. Show Account Details";
        cout << "\n5. Exit";
        cout << "\nEnter Choice: ";
        cin >> choice;

        switch (choice) {
            case 1: {
                bool created = false;
                for (i = 0; i < 5; i++) {
                    if (b[i].getAccNo() == 0) {
                        b[i].createAccount();
                        created = true;
                        break;
                    }
                }
                if (!created) cout << "Account limit reached!\n";
                break;
            }

            case 2: {
                cout << "Enter Account Number: ";
                cin >> num;
                found = false;
                for (i = 0; i < 5; i++) {
                    if (b[i].getAccNo() == num) {
                        b[i].deposit();
                        found = true;
                        break;
                    }
                }
                if (!found) cout << "Account not found!\n";
                break;
            }

            case 3: {
                cout << "Enter Account Number: ";
                cin >> num;
                found = false;
                for (i = 0; i < 5; i++) {
                    if (b[i].getAccNo() == num) {
                        b[i].withdraw();
                        found = true;
                        break;
                    }
                }
                if (!found) cout << "Account not found!\n";
                break;
            }

            case 4: {
                cout << "Enter Account Number: ";
                cin >> num;
                found = false;
                for (i = 0; i < 5; i++) {
                    if (b[i].getAccNo() == num) {
                        b[i].display();
                        found = true;
                        break;
                    }
                }
                if (!found) cout << "Account not found!\n";
                break;
            }

            case 5:
                cout << " Thank you for using the bank system!\n";
                break;

            default:
                cout << "Invalid Choice!\n";
        }
    } while (choice != 5);

    return 0;
}
