## Wouldn't the row context from calculated column filter the table for sumx's row context?

No, the row context from the calculated column does not filter the table for `SUMX`'s row context. Instead, they operate independently. The row context created by the calculated column is specific to the current row being processed in the table, while the row context created by `SUMX` iterates over the entire table or the table passed to it.

Also extremely, extremely useful:
https://www.sqlbi.com/articles/row-context-in-dax/

In particular:

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/9f3498ae-2473-403a-84d1-4884c9c17a68)



### Detailed Explanation

Let's clarify this with a step-by-step breakdown:

1. **Row Context from Calculated Column**:
   - When you create a calculated column, DAX evaluates the expression for each row in the table. This evaluation creates a row context specific to the current row.

2. **Row Context from SUMX**:
   - When you use `SUMX` inside the calculated column, it introduces a new row context for each row it iterates over in the table specified (usually the same table).

### Example

Given the `Sales` table:

| SaleID | ProductID | Quantity |
|--------|-----------|----------|
| 1      | 1         | 2        |
| 2      | 1         | 3        |
| 3      | 2         | 1        |
| 4      | 2         | 4        |
| 5      | 3         | 5        |

#### Calculated Column Example

Let's add a calculated column that sums the `Quantity` for all sales:

```dax
TotalQuantity = SUMX(Sales, Sales[Quantity])
```

### Step-by-Step Evaluation

#### For SaleID = 1:

1. **Row Context from Calculated Column**:
   - Current row: { SaleID = 1, ProductID = 1, Quantity = 2 }
   - This row context is for evaluating the `TotalQuantity` column for SaleID = 1.

2. **Row Context from SUMX**:
   - `SUMX` iterates over the entire `Sales` table:
     - Iteration 1: { SaleID = 1, ProductID = 1, Quantity = 2 }
     - Iteration 2: { SaleID = 2, ProductID = 1, Quantity = 3 }
     - Iteration 3: { SaleID = 3, ProductID = 2, Quantity = 1 }
     - Iteration 4: { SaleID = 4, ProductID = 2, Quantity = 4 }
     - Iteration 5: { SaleID = 5, ProductID = 3, Quantity = 5 }

3. **SUMX Calculation**:
   - For each iteration, `SUMX` evaluates `Sales[Quantity]`:
     - 2 + 3 + 1 + 4 + 5 = 15
   - Result for SaleID = 1: 15

#### For SaleID = 2:

1. **Row Context from Calculated Column**:
   - Current row: { SaleID = 2, ProductID = 1, Quantity = 3 }
   - This row context is for evaluating the `TotalQuantity` column for SaleID = 2.

2. **Row Context from SUMX**:
   - `SUMX` iterates over the entire `Sales` table again:
     - Iteration 1: { SaleID = 1, ProductID = 1, Quantity = 2 }
     - Iteration 2: { SaleID = 2, ProductID = 1, Quantity = 3 }
     - Iteration 3: { SaleID = 3, ProductID = 2, Quantity = 1 }
     - Iteration 4: { SaleID = 4, ProductID = 2, Quantity = 4 }
     - Iteration 5: { SaleID = 5, ProductID = 3, Quantity = 5 }

3. **SUMX Calculation**:
   - For each iteration, `SUMX` evaluates `Sales[Quantity]`:
     - 2 + 3 + 1 + 4 + 5 = 15
   - Result for SaleID = 2: 15

This pattern continues for each row in the `Sales` table.

### Key Point

The row context of the calculated column does **not** filter the table for the `SUMX` function. Instead, `SUMX` independently iterates over the entire table (or the table passed to it) and creates its own row context for each row it processes. This is why `SUMX` can sum the `Quantity` for all rows in the table, even though it is used within a calculated column. 

### Conclusion

In DAX, each row context is independent. The row context created by the calculated column allows DAX to evaluate the expression for each specific row in the table. The row context created by `SUMX` (or any other iterator function) allows it to iterate over the entire table and evaluate an expression for each row it processes. They do not filter each other; instead, they coexist and serve different purposes.
