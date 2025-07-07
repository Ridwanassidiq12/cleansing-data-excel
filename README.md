# cleansing-data-excel

1	Pull all data from the Customer_Info file into the Main_Ecommerce file on the Order_Data sheet.
 - =VLOOKUP(A2;[Customer_Info.xlsx]Sheet1!$A$2:$E$501;2;FALSE)
 - =VLOOKUP(A2;[Customer_Info.xlsx]Sheet1!$A$2:$E$501;3;FALSE)
 - =VLOOKUP(A2;[Customer_Info.xlsx]Sheet1!$A$2:$E$501;4;FALSE)
 - =VLOOKUP(A2;[Customer_Info.xlsx]Sheet1!$A$2:$E$501;5;FALSE)

2 Pull data from the Product_Catalog file, but first clean the Stock_Unit column, then transfer all the data along with the key to the Main_Ecommerce file on the Order_Data sheet.	
 - clean data di  Stock_Unit, pertama klik column Stock_Unit -> tab data -> Text to Columns -> Pilih Delimited > klik Next -> Centang Space > klik Next -> finish dan hapus value column 6 dan 7
 - =VLOOKUP(A2;[Product_Catalog.xlsx]Sheet1!$A$2:$E$501;2;FALSE)
 - =VLOOKUP(A2;[Product_Catalog.xlsx]Sheet1!$A$2:$E$501;3;FALSE)
 - =VLOOKUP(A2;[Product_Catalog.xlsx]Sheet1!$A$2:$E$501;4;FALSE)
 - =VLOOKUP(A2;[Product_Catalog.xlsx]Sheet1!$A$2:$E$501;5;FALSE)

3	Pull data from the Order_Records file, but you must fill in the Total_Amount column using information from the Product_Catalog file. Then transfer all the data along with the  key into the Main_Ecommerce file on the Order_Data sheet.
