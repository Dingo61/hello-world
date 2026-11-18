---

# 🪨 The Rosetta Stone of Programming Disasters

### One Mining Block. Six Languages. Forty-Seven Ways to Get It Wrong.

> *"The mathematics hasn't changed in 60 years. Unfortunately, neither have some of the bugs."*

## ⛏️ Our Mission

A mining engineer discovers a block of iron ore.

The block has the following properties:

| Property | Value |
|---|---:|
| X dimension | 25 m |
| Y dimension | 25 m |
| Z dimension | 5 m |
| Density | 2.50 t/m³ |
| Iron grade | 62% |
| Gold content | Sadly, zero |

**The challenge:**

Calculate the block volume, tonnes and contained iron.

### The Mathematics

```text
VOLUME = X × Y × Z

TONNES = VOLUME × DENSITY

IRON = TONNES × GRADE
```

Expected results:

```text
Volume:          3,125.00 m³
Tonnes:          7,812.50 t
Contained Iron:  4,843.75 t
```

Simple enough?

Let's see how six generations of programmers handle it.

---

## 🏛️ 1. FORTRAN 77 — The Original Mining Engineer

**1977: When computers were expensive and programmers were expected to know mathematics.**

```fortran
      PROGRAM BLOCK
      REAL X, Y, Z, DENSITY, GRADE
      REAL VOLUME, TONNES, IRON

      X = 25.0
      Y = 25.0
      Z = 5.0
      DENSITY = 2.5
      GRADE = 0.62

      VOLUME = X * Y * Z
      TONNES = VOLUME * DENSITY
      IRON = TONNES * GRADE

      PRINT *, 'VOLUME:', VOLUME
      PRINT *, 'TONNES:', TONNES
      PRINT *, 'IRON:', IRON

      END
```

**Engineering assessment:**

✅ Fast  
✅ Simple  
✅ Mathematically correct  
✅ Probably running on a mainframe somewhere

⚠️ Programmer retired in 1994.

⚠️ Nobody knows what happens if you change line 7.

**Historical observation:**

FORTRAN 77 used fixed-form source code. Statements generally began in column 7.

Six spaces weren't a stylistic choice.

They were the law.

---

## 🏦 2. COBOL — The Accountant Gets Involved

**1959: Because somebody has to explain the numbers to management.**

```cobol
       IDENTIFICATION DIVISION.
       PROGRAM-ID. OREBLOCK.

       DATA DIVISION.
       WORKING-STORAGE SECTION.

       01 BLOCK-X       PIC 9(3) VALUE 25.
       01 BLOCK-Y       PIC 9(3) VALUE 25.
       01 BLOCK-Z       PIC 9(3) VALUE 5.
       01 DENSITY       PIC 9V99 VALUE 2.50.
       01 GRADE         PIC 9V99 VALUE 0.62.

       01 BLOCK-VOLUME  PIC 9(9)V99.
       01 BLOCK-TONNES  PIC 9(9)V99.
       01 BLOCK-IRON    PIC 9(9)V99.

       01 DISPLAY-IRON  PIC Z(9)9.99.

       PROCEDURE DIVISION.

           COMPUTE BLOCK-VOLUME =
               BLOCK-X * BLOCK-Y * BLOCK-Z

           COMPUTE BLOCK-TONNES =
               BLOCK-VOLUME * DENSITY

           COMPUTE BLOCK-IRON =
               BLOCK-TONNES * GRADE

           MOVE BLOCK-IRON TO DISPLAY-IRON

           DISPLAY "CONTAINED IRON: "
               DISPLAY-IRON

           STOP RUN.
```

**Engineering assessment:**

✅ Accurate  
✅ Auditable  
✅ Excellent for financial reporting

⚠️ Requires a paragraph to introduce a variable.

⚠️ The original developer is now a company director.

**Management observation:**

The accountant immediately asks:

*"Can we depreciate the iron before we mine it?"*

---

## 🐍 3. Python — The Data Scientist Arrives

**1991: Finally, a language where the code resembles the mathematics.**

```python
x, y, z = 25, 25, 5
density = 2.5
grade = 0.62

volume = x * y * z
tonnes = volume * density
iron = tonnes * grade

print(f"Contained iron: {iron:,.2f} tonnes")
```

Output:

```text
Contained iron: 4,843.75 tonnes
```

**Engineering assessment:**

✅ Readable  
✅ Easy to maintain  
✅ Runs almost anywhere

⚠️ A data scientist has spotted the code.

### The Data Scientist's Improvement

```python
import numpy as np
import pandas as pd

block = pd.DataFrame({
    "x": [25],
    "y": [25],
    "z": [5],
    "density": [2.5],
    "grade": [0.62]
})

block["volume"] = (
    block["x"] * block["y"] * block["z"]
)

block["tonnes"] = block["volume"] * block["density"]

block["iron"] = block["tonnes"] * block["grade"]

print(block)
```

**Result:**

Exactly the same answer.

**Additional requirements:**

- Python virtual environment
- NumPy
- Pandas
- Package dependency management
- Three meetings about using Polars instead

**Senior engineer's observation:**

*"We used to calculate this with a slide rule."*

---

## 🗄️ 4. T-SQL — The Database Administrator Takes Control

**1989: Because the answer clearly belongs in a relational database.**

```sql
DECLARE @X DECIMAL(10,2) = 25;
DECLARE @Y DECIMAL(10,2) = 25;
DECLARE @Z DECIMAL(10,2) = 5;

DECLARE @Density DECIMAL(10,2) = 2.50;
DECLARE @Grade DECIMAL(10,2) = 0.62;

SELECT
    Volume = @X * @Y * @Z,
    Tonnes = @X * @Y * @Z * @Density,
    ContainedIron =
        @X * @Y * @Z * @Density * @Grade;
```

**Engineering assessment:**

✅ Accurate  
✅ Easy to query  
✅ Integrates with the block model database

⚠️ DBA wants an index.

⚠️ Management wants a stored procedure.

⚠️ Someone suggests a persisted computed column.

### The Enterprise Upgrade

```sql
SELECT
    'Hello, World!' AS Message,
    'Mining block calculated successfully' AS Status,
    'Please do not UPDATE without WHERE' AS Warning;
```

**DBA's observation:**

*"The calculation takes 0.0001 seconds. The change approval takes three weeks."*

---

## 🟨 5. JavaScript — The Web Developer Wants a Dashboard

**1995: Because every mining calculation needs an interactive browser interface.**

```javascript
const block = {
    x: 25,
    y: 25,
    z: 5,
    density: 2.5,
    grade: 0.62
};

const volume = block.x * block.y * block.z;
const tonnes = volume * block.density;
const iron = tonnes * block.grade;

console.log(`Contained iron: ${iron.toFixed(2)} tonnes`);
```

**Engineering assessment:**

✅ Works  
✅ Can run in a browser  
✅ Excellent for dashboards

⚠️ Developer wants to introduce React.

⚠️ Another developer recommends TypeScript.

⚠️ Someone has created a blockchain token representing the ore.

### JavaScript's Special Contribution

```javascript
const tonnes = "7812.5";

console.log(tonnes + 100);

// Output: "7812.5100"
```

**Mining engineer:**

*"Why has the ore reserve increased?"*

**JavaScript developer:**

*"It's a feature of dynamic typing."*

---

## ⚙️ 6. C — The Performance Engineer Arrives

**1972: Because apparently the previous five solutions weren't fast enough.**

```c
#include <stdio.h>

int main(void)
{
    double x = 25.0;
    double y = 25.0;
    double z = 5.0;

    double density = 2.5;
    double grade = 0.62;

    double volume = x * y * z;
    double tonnes = volume * density;
    double iron = tonnes * grade;

    printf("Contained iron: %.2f tonnes\n", iron);

    return 0;
}
```

**Engineering assessment:**

✅ Fast  
✅ Efficient  
✅ Minimal overhead

⚠️ Programmer now wants to rewrite the entire block model engine.

⚠️ Somebody mentions CUDA.

⚠️ GPU procurement request submitted.

**Performance engineer:**

*"We can calculate ten billion blocks per second!"*

**Mining engineer:**

*"That's impressive. But we only have one block."*

---

# 🏆 The Rosetta Stone Scorecard

| Language | Correct Answer | Code Complexity | Likely Problem |
|---|---|---|---|
| FORTRAN 77 | ✅ | Low | Nobody understands the legacy code |
| COBOL | ✅ | Medium | Excessive paperwork |
| Python | ✅ | Very low | Dependency explosion |
| T-SQL | ✅ | Low | DBA permissions |
| JavaScript | ✅ | Low | Strings pretending to be numbers |
| C | ✅ | Low | Programmer discovers pointers |

### Final Result

All six programming languages calculated:

**4,843.75 tonnes of contained iron.**

The mathematics took approximately three seconds to understand.

The software development consumed six programmers, two project managers, an infrastructure team and a considerable quantity of coffee.

---

# 🤖 BONUS: The AI Mining Engineer — 2026

**The newest member of the engineering team.**

**Mining Engineer:**

*"Calculate the contained iron in this block."*

**AI Assistant:**

*"Certainly! First, let's develop a comprehensive, scalable, cloud-native, containerised mineral resource estimation architecture."*

**Mining Engineer:**

*"I just need the tonnes."*

**AI Assistant:**

*"I've created a 47-page project specification, a Docker configuration, a CI/CD pipeline and an AGENTS.md file."*

**Mining Engineer:**

*"What about the iron?"*

**AI Assistant:**

*"Good question. Would you like me to explain the concept of iron?"*

---

## 🧓 The Retired Mining Engineer Has the Final Word

```fortran
      PROGRAM EXPERIENCE

      PRINT *, 'AFTER 50 YEARS OF COMPUTING'
      PRINT *, 'I HAVE LEARNED THREE THINGS:'
      PRINT *, '1. GARBAGE IN = GARBAGE OUT'
      PRINT *, '2. BACKUP BEFORE CHANGING ANYTHING'
      PRINT *, '3. NEVER TRUST THE FIRST RESULT'

      END
```

### The Universal Law of Mining Software

> **If the result looks wrong, check the data.**
>
> **If the data looks correct, check the algorithm.**
>
> **If both look correct, check the units.**
>
> **If everything looks correct, somebody has probably divided by 100 twice.**

---

### 🪨 Repository Status

**Code:** Operational  
**Mathematics:** Verified  
**Documentation:** Mostly fictional  
**Ore Reserve:** Subject to further drilling  
**Management Confidence:** Unreasonably high  

**Final Engineering Sign-off:**

*Works on my machine. Your orebody may vary.*

---
