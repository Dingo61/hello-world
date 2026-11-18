# 🌍 Hello, World!
### A Brief History of Computers Doing Exactly What We Told Them To Do

> *"There are only two hard things in Computer Science: cache invalidation, naming things, and off-by-one errors."*

Welcome to the **Hello World Museum of Questionable Programming Decisions**.

This repository contains groundbreaking examples of software engineering spanning several decades.

Every program has one objective:

**Convince an expensive collection of silicon that the world exists.**

Some languages accomplish this elegantly.

Others require a compiler, three manuals, a system administrator, and a small sacrifice to the computing gods.

---

## 🐍 Python — The Optimist

**Year:** 1991  
**Philosophy:** Life is short. Indentation is compulsory.

```python
print("Hello, World!")

# Advanced enterprise edition
try:
    print("Everything is working perfectly.")
except Exception:
    print("Have you tried turning it off and on again?")
```

**Developer notes:**

Python is an excellent language for turning a five-line script into a 400 MB virtual environment.

```python
import numpy
import pandas
import polars
import duckdb

print("Hello, World!")

# Congratulations.
# Your Hello World now requires dependency management.
```

---

## 🗄️ Microsoft T-SQL — The Bureaucrat

**Year:** 1989 (SQL Server)  
**Philosophy:** Why print something when you can SELECT it?

```sql
SELECT 'Hello, World!' AS Message;
```

### Enterprise Edition

```sql
BEGIN TRY
    BEGIN TRANSACTION;

    DECLARE @Message NVARCHAR(100) = 'Hello, World!';

    SELECT
        @Message AS Message,
        GETDATE() AS ExecutionTime,
        @@SERVERNAME AS ResponsibleParty;

    COMMIT TRANSACTION;
END TRY
BEGIN CATCH
    IF @@TRANCOUNT > 0
        ROLLBACK TRANSACTION;

    SELECT ERROR_MESSAGE() AS Excuse;
END CATCH;
```

**DBA wisdom:**

> A SQL query without a WHERE clause is just a very enthusiastic UPDATE waiting to happen.

```sql
-- Famous last words
UPDATE dbo.Employees
SET Salary = Salary * 2;

-- WHERE EmployeeID = 42;
-- Oops.
```

---

## 🟨 JavaScript — The Unpredictable Genius

**Year:** 1995  
**Philosophy:** Everything is an object. Except when it isn't.

```javascript
console.log("Hello, World!");
```

### Understanding JavaScript

```javascript
console.log(1 + 1);       // 2
console.log("1" + 1);     // "11"
console.log("1" - 1);     // 0
console.log([] + []);     // ""
console.log([] + {});     // "[object Object]"
console.log(typeof null); // "object"

// Everything is fine.
// Please do not ask questions.
```

**JavaScript developer motto:**

> If it works, don't touch it. If it doesn't work, install another package.

---

## 🏛️ FORTRAN 77 — The Ancient Engineer

**Year:** 1977  
**Philosophy:** Computers are for calculating things, not looking pretty.

```fortran
      PROGRAM HELLO
      PRINT *, 'HELLO, WORLD!'
      END
```

### Mining Engineer Edition

```fortran
      PROGRAM ORE
      REAL TONNES, GRADE, METAL
      TONNES = 1000000.0
      GRADE = 0.625
      METAL = TONNES * GRADE
      PRINT *, 'HELLO FROM THE PIT!'
      PRINT *, 'CONTAINED METAL:', METAL
      END
```

**Historical notes:**

- Variable names were short.
- Memory was expensive.
- Programmers were expected to understand mathematics.
- Nobody had heard of a Python virtual environment.
- The code probably still runs somewhere in a government department.

> FORTRAN programmers don't die. They just GOTO 100.

---

## 🏦 COBOL — The Immortal Accountant

**Year:** 1959  
**Philosophy:** If English is good enough for Shakespeare, it's good enough for banking software.

```cobol
       IDENTIFICATION DIVISION.
       PROGRAM-ID. HELLO.
       PROCEDURE DIVISION.
           DISPLAY "HELLO, WORLD!".
           STOP RUN.
```

### Corporate Edition

```cobol
       IDENTIFICATION DIVISION.
       PROGRAM-ID. PROFIT.
       DATA DIVISION.
       WORKING-STORAGE SECTION.
       01 REVENUE PIC 9(7) VALUE 1000000.
       01 EXPENSE PIC 9(7) VALUE 999999.
       01 PROFIT  PIC 9(7).

       PROCEDURE DIVISION.
           SUBTRACT EXPENSE FROM REVENUE
               GIVING PROFIT.
           DISPLAY "ANNUAL PROFIT: " PROFIT.
           DISPLAY "MANAGEMENT BONUS APPROVED".
           STOP RUN.
```

**Fun fact:**

COBOL has outlived countless predictions of its demise.

Somewhere, a bank is running software older than its CEO.

And it works.

**Nobody touch it.**

---

## ⚙️ C — The Chainsaw

**Year:** 1972  
**Philosophy:** We trust the programmer. This may have been a mistake.

```c
#include <stdio.h>

int main(void) {
    printf("Hello, World!\n");
    return 0;
}
```

### Memory Management Edition

```c
#include <stdlib.h>

int main(void) {
    char *hello = malloc(100);

    // TODO: Actually say hello.
    // TODO: Check malloc.
    // TODO: Free memory.
    // TODO: Investigate mysterious crash.

    free(hello);
    return 0;
}
```

> C gives you enough rope to hang yourself, your operating system, and occasionally the printer.

---

## ☕ Java — The Corporate Committee

**Year:** 1995  
**Philosophy:** Why use one line when twelve will do?

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

### Enterprise Architecture

```text
HelloWorld/
│
├── AbstractHelloFactory.java
├── HelloFactoryInterface.java
├── HelloFactoryImplementation.java
├── HelloService.java
├── HelloServiceImpl.java
├── WorldRepository.java
├── WorldRepositoryImpl.java
├── application.properties
└── HelloWorld.java
```

**Estimated development time:** 3 sprints.

**Estimated meetings:** 47.

**Actual functionality:** Prints "Hello, World!"

---

## 🐚 Bash — The System Administrator

**Year:** 1989  
**Philosophy:** Everything is a file. Everything else is a permissions problem.

```bash
#!/bin/bash

echo "Hello, World!"

if [ "$EUID" -ne 0 ]; then
    echo "Please run as root."
else
    echo "Excellent. Now we can really break things."
fi
```

**System administrator's prayer:**

> May your backups be recent and your `rm -rf` commands be precise.

---

## 🔵 PowerShell — The Windows Whisperer

**Year:** 2006  
**Philosophy:** Everything is an object, including your problems.

```powershell
Write-Host "Hello, World!"

Get-Process |
    Sort-Object CPU -Descending |
    Select-Object -First 5

# Hello World has escalated into system diagnostics.
```

**Windows administration rule:**

If it can be clicked, it can probably be scripted.

If it can't be scripted, Microsoft will eventually add a 37-character cmdlet.

---

## 🦀 Rust — The Overprotective Parent

**Year:** 2015  
**Philosophy:** Memory safety is not optional.

```rust
fn main() {
    println!("Hello, World!");
}
```

**Compiler conversation:**

```text
Programmer: I would like to use this variable.

Rust: Is it yours?

Programmer: Yes.

Rust: Are you sure?

Programmer: Yes.

Rust: Has anyone else borrowed it?

Programmer: No.

Rust: Can you prove that?

Programmer: I just wanted to print Hello World.

Rust: ERROR E0382.
```

---

## 📊 SQL vs Python — The Eternal Argument

**SQL developer:**

```sql
SELECT AVG(grade)
FROM dbo.BlockModel
WHERE pit_flag = 1;
```

**Python developer:**

```python
import pandas as pd

df = pd.read_csv("block_model.csv")

result = df.loc[df["pit_flag"] == 1, "grade"].mean()

print(result)
```

**Management:**

"Can you put that in Excel?"

---

# 🏆 Programming Language Awards

| Award | Winner | Reason |
|---|---|---|
| Most likely to still be running in 2075 | COBOL | Nobody knows how to replace it |
| Best at scientific number crunching | FORTRAN | Has been doing it since before most programmers were born |
| Most likely to install 400 dependencies | JavaScript | One package to left-pad them all |
| Best at making simple things readable | Python | Until someone imports 17 libraries |
| Most likely to ruin your Friday | T-SQL | `UPDATE` without `WHERE` |
| Most dangerous in the wrong hands | C | Direct access to the foot-shooting mechanism |
| Most concerned about your safety | Rust | Won't let you borrow your own toothbrush |
| Most likely to require a committee | Java | FactoryFactoryFactory |
| Most likely to delete the wrong folder | Bash | `rm -rf` |
| Most likely to produce a 3 AM incident | PowerShell | The scheduled task worked perfectly |

---

# ⛏️ A Special Message for Mining Engineers

Mining engineers have been programming since computers occupied entire rooms.

The development process hasn't changed much.

```text
1959: Write FORTRAN code.
1969: Run FORTRAN code.
1979: Modify FORTRAN code.
1989: Convert FORTRAN code.
1999: Fix converted FORTRAN code.
2009: Rewrite everything in Python.
2019: Discover the original FORTRAN was faster.
2026: Ask AI to explain the FORTRAN.
2027: Ask AI why the Python doesn't work.
```

### The Ultimate Block Model Algorithm

```python
def calculate_profit(tonnes, grade, price):
    revenue = tonnes * grade * price

    costs = revenue * 1.05

    return revenue - costs


print(calculate_profit(1_000_000, 0.62, 100))

# Congratulations.
# You have developed a realistic mining feasibility study.
```

---

# 🤖 The AI Era

**2020:** Programmer writes code.

**2023:** AI helps programmer write code.

**2025:** AI writes code while programmer drinks coffee.

**2026:** AI writes code, AI reviews code, AI tests code.

**2027:** Two AI agents argue about whether the code is necessary.

Meanwhile, the original FORTRAN program continues running perfectly.

---

## 🧠 Final Words of Wisdom

> **Programming is the art of telling a computer what to do, then spending the rest of the day figuring out why it did exactly that.**

And remember:

```python
while True:
    print("Hello, World!")
    break

# The first successful software project:
# Delivered on time.
# Under budget.
# No feature requests.
```

---

### ⭐ If you enjoyed this repository...

Give it a star.

If you found a bug, congratulations.

You are now the maintainer.

---

**Built with:** Coffee ☕, questionable assumptions, and decades of accumulated technical debt.

**License:** MIT — May Include Trouble
