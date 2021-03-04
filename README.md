![github](https://user-images.githubusercontent.com/50157566/110019409-0ac9f380-7cee-11eb-9ef7-fa36e18d1a40.jpg)
# Invoicing Process Improvement With Airtable



**Problem:** Invoicing Process was slow and riddled with errors. 
*    Manually entering orders allowed average 20 orders per workday [average volume per month is 1,200].
*    Errors were mainly cause by manual data entry [Human Error]

**Solution:** Extract Report and utilize formulas and scripts to automate invoice process. 



## **Inv_Proc_V.1.0** ~ March 2020 
#### High-Level Process - V.1.0

1. Report extracted
2. Then updated and edited manually by 6 - 12 individuals.
3. Report then transformed and loaded into airtable.
4. Airtable (at this time) then renamed and rearranged column names. 
5. Exported and Uploaded to invoicing software.

## **Inv_Proc_V.1.8** ~ June 2020 
#### High-Level Process - V.1.8

1. Report extracted
2. Shared file manually updated and edited by 6 - 12 individuals.
3. If vba script not viable for contract type skip to step 4.
4. Report then transformed and loaded into airtable.
5. Airtable (at this time) then renamed and rearranged column names. 
6. Exported and Uploaded to invoicing software.

###### **VBA Script to Create Template**
``` Sub CostPay()
    Dim count As Integer
    Dim cost As Doublegit
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


## **Inv_Proc_V.2.0** ~ August 2020
#### High-Level Process - V.2.0

1. Report extracted
2. Shared file manually updated and edited by 6 - 12 individuals.
3. Report then transformed and loaded into airtable.
4. Airtable performs basic CRUD operations.
5. Exported and Uploaded to invoicing software.

    **Updates**
    * Airtable able to perform basic CRUD operations on 3 contract types.
    * Airtable allows consistent invoicing process
    * Airtable saves formulas to perform CRUD operations without having to be updated for individual uses.
    * Airtable's views allows for different template types to be created without having to update formulas or scripts. 
	* excel would error out before running, where as, airtable errors before uploaded template creation.
	* No code needed for contracts fed into Airtable
    **Issues**
    * Adding 5 more additional contract types (using only low code methods)
    * Updating reports manually are still prone to major errors

## **Inv_Proc_V.2.2** ~ September 2020
#### High-Level Process - V.2.2

1. Report extracted
2. Shared file manually updated and edited by 6 - 12 individuals.
3. Report then transformed and loaded into airtable.
4. Airtable performs basic CRUD operations.
5. Exported and Uploaded to invoicing software.

    **Updates**
    *   Formulas are only maintained with advanced formula creation expreience. 
    *   5 our of 8 contracts taken in by Airtable

    **Issues**
    *   Low code method is becoming complicated and difficult to update with changing invoiving requests.
    *   Updating reports manually are still prone to major errors
    *   Stepwise addition resulted in root cause detection difficulties by multi-table CRUD operators.



## **Inv_Proc_V.3.0** ~ November 2020
#### High-Level Process - V.3.0

1. Report extracted
2. Report transformed and loaded to Airtable
3. Airtable Automations links and updates needed information.
4. Editable share link sent out for report edits.
5. Airtable performs basic CRUD operations and template creation.
6. Exported and Uploaded to invoicing software.

    **Updates**
    *   Tracking edits made to records
    *   Tracking on voided records
    *   Improved invoice tracking for teams 
    *   All contracts have same invoicing process.
    *   Human errors are almost eradicated

    **Issues**
    *   Stepwise addition resulted in root cause detection difficulties by multi-table CRUD operators.
    *   Low-code formulas evolved into complex logical equations.


## **Inv_Proc_V.4.0** ~ February 2021
#### High-Level Process - V.4.0

1. Report extracted
2. Report loaded to Airtable
3. Airtable Automations links and updates needed information.
4. Editable share link sent out for report edits.
5. Airtable performs basic CRUD operations and template creation.
6. Exported and Uploaded to invoicing software.

    **Updates**
    *   Useing a map table update needed information.
    *   Formulas used only to perform CRUD functions.
    *   Linear process up data intake and output.
    *   Straight forward process for all contract types.
    