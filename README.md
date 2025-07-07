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
 - buka file  Order_Records di samping column Total_Amount baris 2 pakai rumus :  =VLOOKUP(A2;[Product_Catalog.xlsx]Sheet1!$A$2:$E$501;5;FALSE)
 - lalu di kolom total amount F2 baris 2 =E2*G2 (E2 : Quantity_Purchased , G2 : Stock_Unit) lalu enter dan drak kebawah
 - =VLOOKUP(A2; [Order_Records.xlsx]Sheet1!$A$2:$F$501;2;FALSE)
 - =VLOOKUP(A2; [Order_Records.xlsx]Sheet1!$A$2:$F$501;3;FALSE)
 - =VLOOKUP(A2; [Order_Records.xlsx]Sheet1!$A$2:$F$501;4;FALSE)
 - =VLOOKUP(A2; [Order_Records.xlsx]Sheet1!$A$2:$F$501;5;FALSE)


4	Pull data from the Review_Data file, but first clean the Review_Text column based on the Rating, and add an 'Anomaly' column based on whether the review reason is positive or negative but does not match the given rating. The Anomaly column (with content based on your idea) should highlight any semantic mismatch that implies a specific task or issue.

 - buat sheet2 lalu buat tabel :
1	Bad
2	Poor
3	Average
4	Excellent
5	Good
lalu gunakan rumus ini di sheet 1 =VLOOKUP(B2;Table1;2;FALSE)
   
 - buat sheet2 lalu buat tabel :
5	Pengiriman sangat cepat
5	Sangat puas dengan pembelian ini
4	Produk sesuai ekspektasi
4	Akan beli lagi di toko ini
3	Pelayanan memuaskan
3	Harga terlalu mahal
2	Ukuran tidak sesuai deskripsi
2	Warna berbeda dari gambar
1	Kualitas kurang baik
1	Barang cacat saat diterima
lalu gunakan rumus ini di sheet 1 =INDEX(FILTER(Table2[Column2]; Table2[Column1]=B2); RANDBETWEEN(1; COUNTIF(Table2[Column1]; B2)))

 - mendeteksi anomali
=IF(AND(A2>=4; OR(
   ISNUMBER(SEARCH("Barang cacat saat diterima"; E2));
   ISNUMBER(SEARCH("Kualitas kurang baik"; E2));
   ISNUMBER(SEARCH("Warna berbeda dari gambar"; E2));
   ISNUMBER(SEARCH("Ukuran tidak sesuai deskripsi"; E2))
)); "Anomali – review negatif di rating tinggi";

IF(AND(A2<=2; OR(
   ISNUMBER(SEARCH("Pengiriman sangat cepat"; E2));
   ISNUMBER(SEARCH("Sangat puas dengan pembelian ini"; E2));
   ISNUMBER(SEARCH("Produk sesuai ekspektasi"; E2));
   ISNUMBER(SEARCH("Akan beli lagi di toko ini"; E2))
)); "Anomali – review positif di rating rendah"; "")











