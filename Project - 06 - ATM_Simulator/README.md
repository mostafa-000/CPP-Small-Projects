
<table align="center" width="100%" border="1">
  <tr>
    <td align="center">
      <h2>ATM_Simulator</h2>
    </td>
  </tr>
  <tr>
    <td align="center">
<img width="1536" height="1024" alt="564576" src="https://github.com/user-attachments/assets/c377a35e-2b45-43ff-8841-06f8558f847e" />
    </td>
  </tr>
</table>










> 💡 This project is built on the same client data model used in [Project - 03 - BankClientManagementSystem](https://github.com/mostafa-000/CPP-Small-Projects/tree/main/Project%20-%2003%20-%20BankClientManagementSystem), reusing the `stClient` structure and the `Clients.txt` file, but simulates a completely different scenario: an **ATM machine** used directly by the client instead of a bank employee managing accounts.

---

## 📌 Description

A console-based ATM simulator where a client logs in using their Account Number and PIN Code, then performs common ATM operations: quick withdraw with preset amounts, normal withdraw with a custom amount, deposit, and balance check — all backed by the same client data file used across the bank project series.

---

## ✨ Features

- Client login using Account Number and PIN Code, with repeated attempts until valid credentials are entered
- Quick Withdraw with preset amounts (100$, 200$, 500$, 1,000$, 5,000$) or a custom "Other" option
- Normal Withdraw with a custom amount entered by the client
- Withdrawal validation: amount must be a multiple of 5 and cannot exceed the current balance
- Deposit with validation to reject zero or negative amounts
- Instant balance check
- All balance changes are saved back to `Clients.txt`

---

## 🗂️ Project Structure

| Function | Responsibility |
|---|---|
| `Logen_ATM()` | Handles the ATM login loop until valid credentials are provided |
| `LoadClientInfo_ATM()` / `FindClientByUserNameAndPassword_ATM()` | Validates login credentials against `Clients.txt` |
| `ShowMainMenue_ATM()` / `PrefroMainMenueOption_ATM()` | Displays and routes the ATM main menu |
| `QuickWithdraw_ATM()` | Handles the preset-amount withdraw menu |
| `NormalWithdraw_ATM()` / `NormalWithdrawMoney()` | Handles a custom-amount withdraw |
| `IsWithdrawAmountValid_ATM()` | Validates a withdraw amount (multiple of 5, within balance) |
| `WithdrawMoney()` | Applies a withdraw to the current client's balance |
| `Deposit()` | Handles depositing money into the current client's balance |
| `CheckBalanc_ATM()` | Displays the current client's balance |
| `UpdateClientByAccountNumber_ATM()` | Saves the updated client balance back to the file |

---

## 🔁 Program Flow

1. Program starts and shows the **ATM Login Screen**.
2. Client enters Account Number and PIN Code; the program keeps retrying until a match is found in `Clients.txt`.
3. On success, the **ATM Main Menu** is shown with the client's name.
4. Client picks an operation: Quick Withdraw, Normal Withdraw, Deposit, or Check Balance.
5. For withdraws, the amount is validated (multiple of 5, not exceeding the balance) before being confirmed and applied.
6. Every successful transaction updates `CurrentClient.AccountBalance` and saves it back to `Clients.txt`.
7. Logout returns back to the Login Screen.

---

## 🕹️ Gameplay

Not applicable — this is a menu-driven console application, not a game.

---

## 💻 Sample Input

```
 >| Enter Username?
1001
 >| Enter password?
2580

  >>>>> Choose Any [1 to 5] ? 1

  >> ENTER NUMBER ? 3
  >> Are you sure about the operation? (Y/N): y
```

---

## 🖥️ Sample Output

```
   |--->  [ Welcom Mostafa ]  <---| 
 <=*====================================*=>
   |   >>>  ATM main menu screen  <<<   |
 <=*====================================*=>
   | [1] Quick Withdraw                 |
   | [2] Normal Withdraw.               |
   | [3] Deposit.                       |
   | [4] Check Balance.                 |
   | [5] Logout.                        |
 <=*====================================*=>

  | Your Mony Balance: 4500.00
```

---

## 🧠 Concepts Practiced

- Structs (`stClient`)
- File handling with `fstream` (read/write)
- Input validation loops
- Function reuse across related projects (shared data model)
- Menu-driven program design with switch statements
- Pass-by-reference vs pass-by-value

---

## ▶️ How to Run

1. Open the project in Visual Studio (or any C++ IDE).
2. Build and run the project.
3. Make sure a `Clients.txt` file exists in the same directory with at least one valid client record, otherwise login will always fail.
4. Log in using an existing Account Number and PIN Code, then use the ATM menu.

---

## 📚 What I Learned

- How to simulate a real-world ATM flow (login → operation → confirmation → balance update)
- How to validate numeric input against multiple business rules (multiple of 5, sufficient balance, positive amount)
- How reusing an existing data structure and file (`stClient`, `Clients.txt`) can let two different applications share the same data source
- The importance of returning from validation functions cleanly to avoid re-running the same menu unexpectedly

---

## ⚠️ Known Issues

- `UpdateCurrentClientNOM_ATM()` is defined but never actually updates anything useful — it assigns to a local variable that is discarded when the function ends, and it's also unused in the program (dead code).
- In `IsWithdrawAmountValid_ATM()`, the condition `amount > CurrentClient.AccountBalance` is always true on first entry since the function is only called after that exact check fails in `WithdrawMoney()`, making part of the condition redundant in that path.
- `QuickWithdraw_ATM()` declares a local `char Ask` variable that is never used.
- Some output messages still contain casual/inconsistent English (e.g. "Mony", "Entrr", "Balanc") that could be cleaned up for a more professional feel.

---

## 🚀 Future Improvements

- Remove dead code such as `UpdateCurrentClientNOM_ATM()`
- Clean up minor spelling issues in console messages ("Mony" → "Money", "Entrr" → "Enter", "Balanc" → "Balance")
- Add a receipt-style summary after each transaction (previous balance, amount, new balance)
- Add a maximum daily withdrawal limit, similar to real ATMs
- Add input validation to reject non-numeric input instead of relying on default int/double behavior

---

## 🛠️ Built With

- C++
- Standard Library: `iostream`, `fstream`, `string`, `vector`, `iomanip`

---

⭐ If you found this project useful, consider giving the repo a star!
