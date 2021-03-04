# Invoicing Process Improvement With Airtable

Problem: Invoicing Process was slow and riddled with errors. 
    *    Manually entering orders allowed average 20 orders per workday [average volume per month is 1,200].
    *    Errors were mainly cause by manual data entry [Human Error]

Solution: Extract Report and utilize formulas and scripts to automate invocie process. 



**Inv_Proc_V.1.0** ~ March 2020 
#### High-Level Process - V.1.0

1. Report extracted
2. Then updated and edited manually by 6 - 12 individuals.
3. Report then transformed and loaded into airtable.
4. Airtable (at this time) then renamed and rearranged column names. 
5. Exported and Uploaded to invoicing software.

**Inv_Proc_V.1.8** ~ June 2020 
#### High-Level Process - V.1.8

1. Report extracted
2. Shared file manually updated and edited by 6 - 12 individuals.
3. Run vba script contract type could use script then step 5 if no script step 4. 
3. Report then transformed and loaded into airtable.
4. Airtable (at this time) then renamed and rearranged column names. 
5. Exported and Uploaded to invoicing software.

###### **VBA Script to Create Template**
``` Sub CostPay()
    Dim count As Integer
    Dim cost As Double
    Dim new_row As Integer
    Dim last_row As Variant
    Dim Order_IdentifierAs Integers

   ' setting starting loop values
    count = 0       	
    cost = 0
    new_row = 2
    last_row = Cells(Rows.Count, 1).End(xlUp).Row

    For i = 2 To last_row
        If Cells(i + 1, 1).Value <> Cells(i, 1).Value Then

        ' if criteria matches from the row before then do:
            last_row2 = Worksheets("MASTER").Range("A" & Rows.Count).End(xlUp).Row + 1
        
            'sets the customer name
            customer_name = Cells(i, 2).Value
        
            ' keep running total
            cost = cost + Cells(i, 23).Value
	
            ' Creates a Unique Identifier	
            count = count + 1    
            order_identifier = Cells(i,8).Value + count
                 
            ' Creating "MASTER" template
            Worksheets("MASTER").Cells(last_row2, 1).Value = OrderIdentifier
            Worksheets("MASTER").Cells(last_row2, 3).Value = Cells(i, 11).Value
            Worksheets("MASTER").Cells(last_row2, 4).Value = Cells(i, 10).Value
            Worksheets("MASTER").Cells(last_row2, 5).Value = Cells(i, 10).Value
            Worksheets("MASTER").Cells(last_row2, 6).Value = "#"
            Worksheets("MASTER").Cells(last_row2, 7).Value = Today Funtion
            Worksheets("MASTER").Cells(last_row2, 8).Value = Cells(i, 11).Value
            Worksheets("MASTER").Cells(last_row2, 9).Value = Item ID
            Worksheets("MASTER").Cells(last_row2, 10).Value = cost
            Worksheets("MASTER").Cells(last_row2, 11).Value = 0.01
            Worksheets("MASTER").Cells(last_row2, 12).Value = Cells(i, 1).Value
            Worksheets("MASTER").Cells(last_row2, 13).Value = "Today"
            Worksheets("MASTER").Cells(last_row2, 14).Value = "INVOICE ONLY"
            Worksheets("MASTER").Cells(last_row2, 15).Value = "DO NOT SEND PO TO VENDOR...FOR INVOICING PURPOSES ONLY...NOTHING SHIPS...DO NOT CANCEL PO"
            Worksheets("MASTER").Cells(last_row2, 16).Value = "Sarah Brown"
            Worksheets("MASTER").Cells(last_row2, 17).Value = "888-888-88888"
            Worksheets("MASTER").Cells(last_row2, 18).Value = "Email@domain.com"
            
            new_row = new_row + 1
            
            ' Resets total for next customername
            cost = 0
            OrderIdentifier = 0
            
        ' If the rows are the same keep running total
        Else
        'adding keeping the running total
        cost = cost + Cells(i, 23).Value

        End If
    Next i
End Sub
```


**Inv_Proc_V.2.0** ~ August 2020
#### High-Level Process - V.1.8

1. Report extracted
2. Shared file manually updated and edited by 6 - 12 individuals.
3. Run vba script contract type could use script then step 5 if no script step 4. 
3. Report then transformed and loaded into airtable.
4. Airtable (at this time) then renamed and rearranged column names. 
5. Exported and Uploaded to invoicing software.


*	Created 2 contract types templates with basic formulas
*	Why would I change from something that works to Airtable?
    **PROS**
    * Airtable saves formulas to perform CRUD operations without having to be updated for individual uses.
    * Airtable's views allowed for different template types to be created without having to update formulas or scripts. 
	* excel would error out before running where as airtable errors before uploaded template creation (script errors during)
	* No code needed for invoicing 1200+ orders a month
    **CONS**
    * Lack of knowledge with Airtable can't invoice
    * how to incorportate 8 more additional contract types (using formula only based logic)
    * Updating Sales Orders _Manual_

**Inv_Proc_V.2.2** ~ November 2020
* 7/8 contract types being invoiced.

    **PROS**
    *   All contracts created equal
    *   All Invoicing can be done with minimal interference

    **CONS**
    *   Formulas are only maintained with advanced formula creation expreience. (Not feasible)
    *   LookUps were difficult to track 
    *   Only one administrator


**Inv_Proc_V.3.0**
