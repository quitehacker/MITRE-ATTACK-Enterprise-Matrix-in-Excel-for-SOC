# Formula Used in Coverage Sheet
```
=IF(A2<>"",IF(INDEX(Techniques[Coverage],MATCH(A2,Techniques[Name],0))>0,INDEX(Techniques[Coverage],MATCH(A2,Techniques[Name],0)),""),"")
```

### Check if A2 is non-empty
`=IF(A2<>"", ...)`

This checks if cell A2 contains any text. If A2 is empty, the formula will return an empty string "". If A2 contains some text, the formula will continue to the next part.

### Lookup the corresponding 'Coverage' value:
`INDEX(Techniques[Coverage],MATCH(A2,Techniques[Name],0))`

Here, MATCH finds the position of the value in A2 within the Name column of the Techniques table. INDEX then retrieves the corresponding value from the Coverage column at the position specified by the MATCH function.

###  Check if the 'Coverage' value is greater than 0
`IF(INDEX(...) > 0, INDEX(...), "")`

The IF function checks if the Coverage value obtained from the INDEX function is greater than 0. If it is, the INDEX value is returned as the result of the formula. If it is not (meaning the value is 0 or negative), the formula returns an empty string "".

### Return the result or an empty string if A2 is empty:
`=IF(A2<>"", IF(...), "")`

The outer IF ensures that the entire formula results in an empty string if A2 was empty to start with, effectively making the formula return a result only if there is a value in A2 to match.


# Formulas Used in Techniques Sheet
## Data Source No.
```
=LEN(E2)-LEN(SUBSTITUTE(E2,",",""))+1
```
This Excel formula is used to count the number of items in a cell separated by commas. Let's break down each part of the formula for our sample data string.
> Command: Command Execution, File: File Access, File: File Creation, Windows Registry: Windows Registry Key Access

1. **`LEN(E2)`**:
    - This function returns the length of the string in cell E2, including all characters (letters, numbers, spaces, punctuation, etc.).
    - Result: 123 characters (including spaces and commas).

2. **`SUBSTITUTE(E2,",","")`**:
    - This function replaces all commas in the text in cell E2 with nothing (effectively removing them). 
    - Modified String: "Command: Command Execution File: File Access File: File Creation Windows Registry: Windows Registry Key Access"
    - This version has no commas, just spaces separating the terms.

3. **`LEN(SUBSTITUTE(E2,",",""))`**:
    - After removing the commas from E2, this function calculates the length of the new string without the commas.
    - Result: 120 characters.

4. **`LEN(E2) - LEN(SUBSTITUTE(E2,",",""))`**:
    - This expression calculates the number of commas in E2 by subtracting the length of the string without commas from the length of the original string.
    - Result: 123 - 120 = 3. This number represents the total commas that were originally in the string.

5. **`+1`**:
   - This part adds one to the result. It's necessary because the number of items in a list separated by commas is always one more than the number of commas. For example, in "apple, banana, cherry", there are two commas but three items.
   - Result: 3 (commas) + 1 = 4 items.

Thus, the entire formula `=LEN(E2)-LEN(SUBSTITUTE(E2,",",""))+1` calculates the number of comma-separated items in the string located in cell E2. If E2 contains "apple, banana, cherry", the formula returns 3.

## Data Sources Available
```
=SUM(IF(ISERROR(FIND(Sources[Data Source],[@[Data Sources]])),0,1)*IF(Sources[Available]="yes",1,0))
```

The formula calculates how many data sources listed in the "Sources" table are both mentioned in the "Techniques" table's current row and marked as "available" in the "Sources" table. It effectively counts the number of available sources that are actively used or referenced in each technique.

### Let's assume you have two tables structured as follows:
1. **Sources Table**:
     ```
     Data Source                 | Available
     ----------------------------|----------
     Command                     | yes
     Command: Command Execution  | yes
     ```

2. **Techniques Table**:
     ```
     Data Sources
     ---------------------------------------
     Command: Command Execution, File: File Access, File: File Creation, Windows Registry: Windows Registry Key Access
     ```

### Applying the Formula
This formula is intended to be used within the Techniques table. It will perform the following operations for each row in the Techniques table:

1. **`FIND(Sources[Data Source],[@[Data Sources]])`**:
   - For each row in the Techniques table, it searches for each `[Data Source]` from the Sources table within the `[Data Sources]` column of the Techniques table. It returns the position of the first character of the first match. If there is no match, it results in an error.

2. **`ISERROR(...)`**:
    - This checks whether the FIND(...) function resulted in an error. If FIND(...) results in an error (meaning no match), ISERROR(...) returns TRUE, otherwise FALSE.

3. **`IF(ISERROR(...),0,1)`**:
   - This converts the result of ISERROR(...) into 0 or 1. If there is an error (no match), it returns 0. If there's no error (a match is found), it returns 1.

4. **`IF(Sources[Available]="yes",1,0)`**:
   - Checks if the corresponding row in the Sources table where the match was found has "yes" in the `[Available]` column. If it is, the result is 1; otherwise, it's 0.

5. **`... * ...`**:
   - Multiplication acts as an AND operator. A row contributes `1` to the sum if there's a match in `[Data Sources]` that is also marked as "available" in the Sources table.
   - Sums up the results across all rows.
  
6. **`SUM(...)`**:
   - This sums up all the results. Only rows where both conditions are satisfied (i.e., data source matches and is available) contribute a 1 to the sum.

## No. of Subtechnique
`=IF([@Technique]=[@ID],SUM(IF([@ID]=[Technique],1,0))-1,"")`

## Detection Rule for Technique
`=IF(SUM(IF($C2=Detections,IF(Detections[Is Active]="yes",1,0),0))>0,SUM(IF($C2=Detections,IF(Detections[Is Active]="yes",1,0),0)),"")`

## Detection Rule for SubTechnique
`=IF(IF(ISNUMBER([@[No. of Sub Techniques]]),[@[No. of Sub Techniques]]>0,FALSE),SUM(IF([@Technique]=[Technique],[Detection Rules for Technique],0))-IF(ISNUMBER([@[Detection Rules for Technique]]),[@[Detection Rules for Technique]],0),"")`

## Min. Detection Rule
`=@IF(AND(ISNUMBER([@[No. of Sub Techniques]]),[@[No. of Sub Techniques]]>1),[No. of Sub Techniques],1)`

## Expected Detection Rule
`=[@[Min. Detection Rules]]+IF(IF(ISNUMBER([@[No. of Sub Techniques]]),[@[No. of Sub Techniques]]>0,FALSE),SUM(IF([@Technique]=[Technique],[Detection Rules Modifier],0)),[@[Detection Rules Modifier]])`

## Detection Rules
`=IF(ISNUMBER([@[Detection Rules for Technique]]),[@[Detection Rules for Technique]],0)+IF(ISNUMBER([@[Detection Rules for SubTech]]),[@[Detection Rules for SubTech]],0)`

## Coverage
`=IF([@[Detection Rules]]>=[@[Expected Detection Rules]],1,[@[Detection Rules]]/[@[Expected Detection Rules]])`

## Technique Status
`=IF([@[Expected Detection Rules]]<=0,"disabled",IF([@[Data Sources Available]]>0, IF([@[Detection Rules]]>0,"detect","no detect"),IF([@[Detection Rules]]>0,"inconsistent","no sources")))`

## Error Checks
`=IF([@[Expected Detection Rules]]<0,"expected detection rules negative!",IF([@[Detection Rules]]>[@[Expected Detection Rules]],"more detection rules than expected!",IF(AND(IF(ISNUMBER([@[Detection Rules for Technique]]),[@[Detection Rules for Technique]]>0,FALSE),IF(ISNUMBER([@[No. of Sub Techniques]]),[@[No. of Sub Techniques]]>0,FALSE)),IF([@[Detection Rules for Technique]] > IF(ISNUMBER([@[Detection Rules Modifier]]),[@[Detection Rules Modifier]],0), "modifier should be increased for the technique", ""),"")))`
