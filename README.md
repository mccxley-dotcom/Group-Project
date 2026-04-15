# Personal Budget Tracker

---

## a. Student Information

| Field          | Details                        |
|----------------|-------------------------------|
| Full Name      | [              |
| Student ID     | [              |
| Course Code    | CNS1001 - Introduction to Programming |



---

## b. Problem Statement

Many people have difficulty managing their money because they do not consistently track
their income and expenses. Without a simple tracking tool, it is easy to overspend without
realising where money is going.

**Why this project was chosen:** Budgeting is a real, everyday problem faced by students,
working adults, and families. A simple program that records income, tracks spending by
category, and shows the remaining balance can make a meaningful difference.

**Intended user:** Students managing allowances or part-time income, and anyone who wants
a straightforward way to monitor monthly spending.

---

## c. Program Description

The Personal Budget Tracker is a menu-driven Python program that allows a user to:

1. Set their monthly income
2. Add expenses by category and amount
3. View a full list of recorded expenses
4. View a budget summary showing income, total expenses, remaining balance, and
   a warning if they have overspent or are close to the budget limit
5. Clear all data and start over
6. Exit the program

**Overall flow:**
- The program starts by welcoming the user and displaying a menu.
- The user selects an option by entering a number (1–6).
- The program performs the requested action and returns to the menu.
- This loop continues until the user chooses to exit (Option 6).

---

## d. Programming Concepts Used

| Concept              | How It Is Used                                                                 |
|----------------------|--------------------------------------------------------------------------------|
| Variables            | Store income (`income = 0`) and running totals                                 |
| Input / Output       | `input()` collects user choices and values; `print()` displays results         |
| Conditionals (`if`)  | Check menu choices, detect overspending, validate empty input                  |
| Loops (`while`)      | Main menu loop runs until user exits; `get_valid_amount` loops on bad input    |
| Functions            | `main()`, `add_expense()`, `view_expenses()`, `show_summary()`, and more       |
| Lists                | `expenses` is a list that stores each expense record                           |
| Dictionaries         | Each expense is stored as `{"category": str, "amount": float}`                 |
| Input Validation     | `get_valid_amount()` catches `ValueError` and rejects negative/zero amounts    |
| `try / except`       | Handles non-numeric input without crashing the program                         |
| `enumerate()`        | Numbers each expense row when displaying the expense list                      |

---

## e. How to Run the Program

**Requirements:** Python 3.x (no external libraries needed)

**Steps:**

1. Make sure Python is installed on your computer.
   - Check by opening a terminal and typing: `python --version`
2. Navigate to the project folder in your terminal:
   ```
   cd path/to/
   ```
3. Run the program:
   ```
   python project.py
   ```
4. Follow the on-screen menu to use the tracker.

---

## f. Required Libraries

No external libraries are required. This project uses only Python built-in features.

---

## g. Sample Inputs and Outputs

**Starting the program:**
```
============================================
   Welcome to the Personal Budget Tracker   
============================================
Track your income and expenses with ease.

========== Personal Budget Tracker ==========
1. Set Monthly Income
2. Add Expense
3. View All Expenses
4. View Budget Summary
5. Clear All Data
6. Exit
=============================================
Enter your choice (1-6):
```

**Setting income (Option 1):**
```
Enter your choice (1-6): 1

--- Set Monthly Income ---
Enter your monthly income: $50000
Income set to $50000.00
```

**Adding an expense (Option 2):**
```
Enter your choice (1-6): 2

--- Add Expense ---
Enter expense category (e.g., Food, Transport, Rent): Food
Enter amount for 'Food': $8000
Expense recorded: Food - $8000.00
```

**Viewing all expenses (Option 3):**
```
--- All Expenses ---
#     Category             Amount
--------------------------------------
1     Food                 $ 8000.00
2     Transport            $ 3500.00
3     Utilities            $ 5000.00
--------------------------------------
      TOTAL                $16500.00
```

**Viewing budget summary (Option 4):**
```
--- Budget Summary ---
  Monthly Income:    $ 50000.00
  Total Expenses:    $ 16500.00
  Remaining Balance: $ 33500.00

  You have used 33.0% of your monthly budget.
  You are within your budget. Keep it up!
```

**Overspending warning:**
```
  *** WARNING: You have OVERSPENT by $5000.00! ***
```

---

## h. Manual Testing / Validation

| 1 | Set valid income               | Option 1 → `50000` | "Income set to $50000.00"  | "Income set to $50000.00"                | Pass   |
| 2 | Set invalid income (negative)  | Option 1 → `-200`  | "Amount must be greater than zero" | "Amount must be greater than               zero" | Pass   |
| 3 | Set invalid income (text)      | Option 1 → `abc`   | "Please enter a valid number"   | "Please enter a valid number"       | Pass   |
| 4 | Add valid expense              | Option 2 → `Food` → `8000`   | "Expense recorded: Food - $8000.00"| "Expense recorded: Food - $8000.00"   | Pass   |
| 5 | Add expense with empty category| Option 2 →  (blank) → Enter | "Category cannot be empty. Expense was not added."   | "Category cannot be empty. Expense was not added."   | Pass   |
| 6 | View expenses when list empty  | Option 3 (no expenses added)  | "No expenses recorded yet."                          | "No expenses recorded yet."                          | Pass   |
| 7 | Overspending warning           | Income `$5000`, Expenses `$6000` | "WARNING: You have OVERSPENT by $1000.00!"       | "WARNING: You have OVERSPENT by $1000.00!"           | Pass   |
| 8 | Add expense before income set  | Option 2 (income = 0)         | "Please set your monthly income first"               | "Please set your monthly income first"               | Pass   |

---

## i. Challenges and Lessons Learned

**Challenge 1 — Input Validation**
One challenge was making sure the program did not crash when the user entered text instead
of a number. This was solved by using `try / except ValueError` inside a `while True` loop
in the `get_valid_amount()` function, which keeps asking until a valid number is entered.

**Challenge 2 — Organising Data**
Deciding how to store multiple expense records was another challenge. A plain list could
only store amounts, not categories. Using a list of dictionaries (e.g., `{"category": "Food",
"amount": 8000}`) solved this cleanly and made it easy to display and total the records.

**Lessons Learned:**
- Breaking a program into small functions makes it much easier to test and fix.
- Input validation is essential — users will always type something unexpected.
- Dictionaries are very useful for storing related pieces of information together.
- Testing edge cases (like negative numbers, empty strings, no income set) is just as important as testing the normal flow.