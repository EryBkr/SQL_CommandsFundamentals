# SQL Commands Fundamentals


# SELECT SORGUSU


```sql
select * from Product  
```Tabloya ait bütün sütunları getirir```
```

```sql
select Id from Product 
``` Tabloya ait spesifik sütunları getirebiliriz```
```
```sql
select Name,Price from Product 
 ``` Çoklu sütun çağırımı```
 ```
 ```sql
select Name as ProductName,Price as Fiyat  from Product 
``` Sütun ismini as ile belirleyebiliyoruz```
```


# WHERE SORGUSU
```sql
 select * from Product where Id=1 
 ``` Id değerinin 1 olduğu kaydı alırız```
 ```
 
 ```sql
 select * from Product where Price=2000 
 ```Fiyatı 2000 e eşit olan kaydı aldık```
 ```
 ```sql
 select * from Product where Price>2000 
 ```Fiyatı 2000 den büyük olan kayıtları aldık```
 ```
 
 ```sql
 select Name from Product where Price >=2000 
 ```Fiyatı 2000 den büyük ya da eşit olan kayıtların isimlerini aldık```
 ```
 
 ```sql
 select Name from Product where Price >2000 And Price<4000 
 ```And operatörünü kullandık```
 ```
 ```sql
 select Name from Product where Price >2000 or Price<4000 
 ```or operatörünü de kullandık```
 ```
 
 ```sql
 select Name from Product where Name='Samsung S5' 
 ``` String ifadeye eşit kayıtları alırız```
 ```
 
 ```sql
 select Name from Product where Name!='Samsung S5' 
 ```Not operatörünü kullandık```
 ```
 
 ```sql
 select * from Product where Name='Samsung S5' and Price=2000 
 ``` Ekstra sorgu ile uygun kaydı bulduk```
 ```
 
 ```sql
 select * from Product where Name='Samsung S5' and (Price=2000 or Price=3000) 
 ``` Bu şekilde sorgularımızı bölebiliriz```
 ```
 
 ```sql
 select * from Product where Price Between 2000 and 4000 
 ``` Between ile de aralık belirleyebiliyoruz```
 ```
 
 ```sql
 select * from Product where Price Not Between 3000 and 4000 
 ```Not Between arasında olmayan anlamı katar```
 ```
 
 ```sql
 select * from Product where Name IN ('Samsung S6','Samsung S5')
 ``` IN Operatörü de string ve int eşitliklerde kullanılabilir```
 ```
 
 ```sql
 select * from Product where Name NOT IN ('Samsung S6','Samsung S5') 
 ``` NOT IN ile verilen string hariç kayıtlar gelir```
 ```
 
 ```sql
 select * from Product where Name LIKE '%Sam%' 
 ```LIKE ile verilen string in dahil olduğu ifadeler bulunur.% sembolü ile string in nerede aranması gerektiğine karar verilir```
 ```
 
 ```sql
 select * from Product where Name NOT LIKE '%S5%'  
 ``` NOT LIKE ile verilen stringin hariç olduğu kayıtlar getirilir```
 ```
 
 ```sql
 select * from Product where Name NOT LIKE '%S5%' and Price<4000 
 ``` S5 stringi dahil olmayan ve fiyatı 4000 den aşağı olan kayıtları aldık```
 ```

# ORDER SORGUSU
```sql
 select * from Product  order by Price 
 ``` Fiyata göre artan sıralama yaptık```
```

```sql
 select * from Product order by  Price desc 
 ``` Fiyata göre azalan sıralama yaptık```
 ```
 
```sql
select * from Product order by Name,Price DESC 
``` İsme göre sıraladık ardına Fiyata göre azalan sıralama yaptık```
```


# SQL FONKSİYONLARI
```sql
 select min(Price) from Product 
 ``` Minimum fiyat bilgisini getirdik```
 ```
 ```sql
 select min(Price) as MinFiyat from Product 
 ``` Kolon ismi belirledik```
 ```
 
 ```sql
 select min(Price) as [Minimum Fiyat] from Product 
 ``` Kolon isminde boşluk vs... kullanmak istiyorsak köşeli parantez kullanmamız gerekiyor```
 ```
 ```sql
 select max(Price) as [Max Fiyat] from Product 
 ``` Max kullanımı```
 ```
 ```sql
 select top 1 Name,Price from Product order by Price DESC 
 ``` Top 1 en üstteki 1 kaydı almamızı sağlar,sıralayarak gereken kaydı alabiliriz```
 ```
 ```sql
 select count(*) from Product 
 ``` count ile kolonları gönderdik ve tabloda kaç kayıt olduğunu bulduk```
 ```
 ```sql
 select AVG(Price) from Product 
 ``` Fiyatların ortalamasını aldık```
 ```
 ```sql
 select SUM(Price) from Product 
 ``` Fiyatların toplamını elde ettik```
 ```
 ```sql
 select SUM(Price * Stock) from Product 
 ``` Bu şekilde matematiksel işlemler yapabiliriz```
 ```
 ```sql
 select LEN('Eray') 
 ``` Karakter sayısını bulur```
 ```
 ```sql
 select LEN(Name),Name as Lengh from Product 
 ``` Database de bulunan isimleri ve karakter sayısını gösterdik```
 ```
 ```sql
 select Name as Name,LEFT(Name,3) from Product 
 ``` Veritabanında ki isimlerin ilk 3 karakterini aldık.Right olarak kullanımı da mevcuttur```
 ```
 ```sql
 select LOWER(Name) from Product 
 ``` İsimler küçük harflerle yazılmış olur```
 ```
 ```sql
 select UPPER(Name) from Product  
 ``` İsimler büyük harflerle yazılmış olur```
 ```


# GROUP BY KULLANIMI
```sql
 select distinct Name from Product 
 ``` Tekrarlayan alanları almadık.Normalde 2 adet S5 vardı```
 ```
 ```sql
 select Name from Product group by Name 
 ``` Şu hali ile distinct ile aynı işlemi yaptı```
 ```
 ```sql
 select Name,Count(*) as Adet from Product group by Name 
 ``` isme göre grupladık ve S5 ten iki adet olduğu için 2 sonucunu diğerlerinde ise 1 sonucu aldık```
 ```
 ```sql
 select Name,Sum(Price) as Adet from Product where Price<4000 group by Name 
 ``` where sorgusu ile de kullanabiliriz```
 ```
 ```sql
 select Name,Count(*) as Adet from Product group by Name having Count(*)>1 
 ``` gruplanmış sütun için filtre yazdık.Aynı isme sahip 2 ve daha fazla ürün gelecek```
 ```


# INSERT 
```sql
 Insert into Product (Name,Price,Image,Stock) Values ('Iphone 12',12000,'15.jpg',5) 
 ``` Bu şekilde ekleme işlemi  yapıyoruz```
 ```


# UPDATE
```sql
 Update Product Set Name='Iphone 12 Pro',Price=13000 where Id=5
 ```
 ```sql
 Update Product Set Image='No Pic' where Image is Null 
 ``` Bu şekilde de null kontrolü yapıp ekleyebiliriz.NOT olarak kullanılabilir```
 ```

# DELETE
```sql
delete from Product where Id=5
```


# JOIN SORGULARI
```sql
 select * from Orders inner join Customers on Orders.CustomerID = Customers.CustomerID 
 ``` CustomersID ile aralarında ilişki bulunan iki tabloyu birleştirdik```
 ```
 ```sql
 select o.OrderID,o.CustomerID,c.CompanyName from Orders o inner join Customers c on o.CustomerID = c.CustomerID 
 ``` Bu şekilde kısatmalı olarakta kullanabiliriz```
 ```
 ```sql
 select o.OrderID,o.CustomerID,c.CompanyName,c.City from Orders o inner join Customers c on o.CustomerID = c.CustomerID where c.City='London' 
 ``` Bu şekilde where sorgusu da ekleyebiliriz```
 ```
 ```sql
select o.OrderDate,c.CompanyName,od.UnitPrice,od.ProductID,p.ProductName from Orders o inner join Customers c on o.CustomerID=c.CustomerID inner join [Order Details] od on od.OrderID=o.OrderID inner join Products p on p.ProductID=od.ProductID 
``` 4 tabloyu ortak ilişkilerle bir araya getirdik.Orders tablosundan müşterilere ve ürün isimlerine kadar ulaştık```
```
```sql
 select o.OrderDate,c.CompanyName,od.UnitPrice,od.ProductID,p.ProductName,(od.UnitPrice*od.Quantity) [Toplam Fiyat] from Orders o inner join Customers c on o.CustomerID=c.CustomerID inner join [Order Details] od on od.OrderID=o.OrderID inner join Products p on p.ProductID=od.ProductID 
 ``` Bu şekilde toplam fiyat vs... gibi bilgiler eklenebilir```
 ```
 ```sql
 select o.OrderID,sum(od.UnitPrice*od.Quantity) as Total  from  Orders o inner join Customers c on o.CustomerID=c.CustomerID inner join [Order Details] od on od.OrderID=o.OrderID inner join Products p on p.ProductID=od.ProductID group by o.OrderID  order by Total 
 ``` Group by ile bu şekilde sıralayıp kullanabiliriz```
 ```


# LEFT JOIN
```sql
 select c.CompanyName,o.OrderID from Customers c left join Orders o on o.CustomerID=c.CustomerID 
 ``` left join anahtar sözcüğünün solunda ki tablo tamamiyle getirilir sağ taraftaki tabloda ki karşılığı null olsa bile görebiliriz```
 ```
 ```sql
 select c.CompanyName,o.OrderID from Customers c left join Orders o on o.CustomerID=c.CustomerID  where o.OrderID is null  
 ``` Bu şekilde sorgu da atabiliriz```
 ```

# RIGHT JOIN
```sql
 select o.OrderID,e.EmployeeID from Orders o right join Employees e on e.EmployeeID=o.EmployeeID 
 ``` Bu sorguda da sağ tarafta bulunan tabloyu tamamiyle getiriyoruz```
 ```



# UNION Kullanımı
```sql
 select e.Country  from Employees e union all select o.ShipCountry from Orders o 
 ``` union distinct mantığıyla belirlediğimiz tablolardaki kolonu alt alta ekler.union all kullanırsak ise tekrarlı bir şekilde ekleyebilir```
 ```


# SubQuery Kullanımı
```sql
 select * from Orders o where o.EmployeeID=(select e.EmployeeID from Employees e where e.FirstName='Nancy') 
 ``` Gerekli tabloda ki belli bir bilgi ile işlem yapmak istiyorsak alt sorgu yazabilirz```
 ```
 ```sql
 select c.CompanyName,(select count(o.OrderID) from Orders o where o.CustomerID=c.CustomerID) as Count from Customers c 
 select * from Products p where p.ProductID in (1,2,3) 
 ``` Alt satırda bu örneğin içerisinde ki id leri subQuery ile dinamik alalım```
 ```
 ```sql
 select * from Products p where p.ProductID in (select od.ProductID from [Order Details] od where od.Quantity>100) 
 ``` Order Details tablosundan Sayısı 100 den büyük olan siparişlerin Product Id lerini alıp işlem yaptık```
 ```



# EXISTS OPERATÖRÜ
```sql
 where EXISTS (True or False --> SubQuery) şeklinde kullanılır
 ```
 ```sql
select * from Customers c where EXISTS (select count(*) from Orders o where c.CustomerID=o.CustomerID group by o.CustomerID having count(*)>2) 
``` Sipariş sayısı ikiden büyük olan müşteriler```
```



# ANY & ALL Kullanımı
```sql
 select p.ProductName from Products p where p.ProductID = any (select p.ProductID from [Order Details] od where od.Quantity>10) 
 ```any (id=2) or (id=3) or (id=4) gibi çalışır```
 ```
 ```sql
 select p.ProductName from Products p where p.ProductID > all (select p.ProductID from [Order Details] od where od.Quantity>1) 
 ```all (id=2) and (id=3) and (id=4) gibi çalışır```
 ```
