# SQL-fundamental-queries
sql basic queries

***********************************
Create new database and table

/*CREATE DATABASE İkİncİdb;*/

/*CREATE TABLE personellistesi(
PerNo int identity(1,1) primary key,
Adiniz char(20),
Soyadiniz char(25),
DogumTRH date);*/

/Personellistesi tablosuna yeni kayıt ekle/
INSERT INTO Personellistesi(PerNo,Adınız,Soyadınız,DogunTRH,BolumNo,Cinsiyet,IsbasTRH,maas)
VALUES(1116,'Cem','Şahin','08.27.1989','C','Erkek','09.25.2021',400);

/Eklenen yeni kişinin maasından 50 tl çıkart/
UPDATE Personellistesi SET maas=maas-50 WHERE Adınız='Cem';

/Eklenen kişiyi tablodan sil/
DELETE FROM Personellistesi WHERE Adınız='Cem';

/*maas'ı %25 arttır ve YeniMaas olarak PerNo,
Adınız,Soyadınız listelet?*/

SELECT PerNo,Adınız,Soyadınız,maas,(maas*1.25)
AS YeniMaas FROM Personellistesi;



/*BolumNo'su D olanların,Soyadını gösterip maasını +500 ekleyip 
Kıdemli olarak listele?*/

SELECT Soyadınız,(maas+500) AS Kıdemli
FROM Personellistesi WHERE BolumNo='D';

/Tabloda ki bütün cinsiyetleri büyük harfle yazdır/

SELECT UPPER(Cinsiyet) AS 'BUYUK HARFLERLE'
FROM Personellistesi;



/Tablodaki cinsiyetlerin hepsini küçük harfle yazdır?/

SELECT LOWER(Cinsiyet) AS 'kucuk harflerle'
FROM Personellistesi;



/Tablodaki bütün maasları toplat/

SELECT SUM(maas) FROM Personellistesi;


/Tablodaki en büyük maası göster?/

SELECT MAX(maas) AS 'En fazla deger' FROM Personellistesi;



/Tablodaki en düşük değeri göster/

SELECT MIN(maas) AS 'En az deger' FROM Personellistesi;

/*artan sıralama için */ ASC

/*azalan sıralama için */ DESC

/Tablodaki Adınız alanındaki sütünları artan sırala/

SELECT*FROM Personellistesi ORDER BY BolumNo ASC;



/Tablodaki maas alanını azalan sırala/

SELECT*FROM Personellistesi ORDER BY maas DESC;




/Tablodaki Erkek olanların maaslarını artan sırala/

SELECT*FROM Personellistesi WHERE Cinsiyet='Erkek' ORDER BY maas ASC;



/Tablodaki ad ve soyadları göster/

SELECT Adınız,Soyadınız FROM Personellistesi;




/Tablodaki Adı Can ve maası 700 den büyük olanları listelet/

SELECT*FROM Personellistesi WHERE Adınız='Can' AND maas>700;




/Tablodaki Adı Can veya maası 700 den büyük olanları listelet?/

SELECT*FROM Personellistesi WHERE Adınız='Can' OR maas>700;

***************************************************************

UPDATE DELETE SELECT CREATE EXAMPLES

/*UPDATE ogrenci SET Ad='derin'WHERE Ad='ahmet';*/

/*DELETE FROM ogrenci WHERE Soyad='Ziyagil';*/

/*SELECT Ad,Soyad FROM ogrenci;*/
/*SELECT * FROM ogrenci;*/

/*SELECT * from ogrenci WHERE Ad='nur';*/

/*SELECT * FROM ogrenci WHERE Ad='leyla' ORDER BY Soyad ASC;*/
/*SELECT * FROM ogrenci WHERE Ad='leyla' ORDER BY Soyad DESC;*/

/*CREATE TABLE sinif (
OgrenciNo char (8) PRIMARY KEY,
Adi char (15),
Soyadi char (15),
DogTarihi date,
Cinsiyet char (1),
HarcKredisi char (5),
Adres char (50)
);*/

***********************************************************************

SELECT EXAMPLES

/* SELECT * FROM Ogrenci; */

/* SELECT OgrNo,Adi,Soyadi from Ogrenci; */

/* SELECT Adi,Soyadi,DTarihi AS 'Dogum Tarihi' FROM Ogrenci; */

/* SELECT Adi AS Adiniz,Soyadi AS Soyadiniz  FROM Ogrenci; */

/* SELECT DISTINCT DYeri FROM Ogrenci; */

/* SELECT*FROM Ogrenci WHERE Cinsiyet='K'; */

/* SELECT *FROM Ogrenci WHERE Kredi='.T.'; */

/* SELECT * FROM Ogrenci WHERE Kredi='.T.' AND Cinsiyet='E'; */

/* SELECT*FROM Ogrenci WHERE Vize<50; */

/* SELECT*FROM Ogrenci WHERE Final>Vize; */

/* SELECT *FROM Ogrenci WHERE Soyadi='Demir'; */

/*SELECT * FROM Ogrenci WHERE Adi !='Nihal'; */

/* SELECT * FROM Ogrenci WHERE DTarihi<'31.12.1999'; */
*******************************************************************


















/*List the people whose salary is 5600 and whose name is Can in the table.*/
SELECT Ad, Soyad, BrutUcret FROM Personellist WHERE BrutUcret IN (5600) 
(SELECT*FROM Personellist WHERE Soyad='Can')


/*SELECT*FROM Personellist WHERE BolNO=2 AND Adres='Beşiktaş' 
(SELECT*FROM Personellist WHERE Adres='Beşiktaş')
SELECT Adınız,Soyadınız FROM Personellistesi WHERE maas>=
(SELECT AVG(maas)FROM Personellistesi)
List the staff whose BolNO number is 4 and whose address is Beşiktaş in the personnel table.
*/

(SELECT*FROM Personellist WHERE Adres='Beşiktaş')

List the people whose salary is 5600 and whose name is Can in the table.

SELECT Ad, Soyad, BrutUcret FROM Personellist WHERE BrutUcret IN (5600) 
(SELECT*FROM Personellist WHERE Soyad='Can')


/*SELECT*FROM Personellist WHERE BolNO=2 AND Adres='Beşiktaş' 
(SELECT*FROM Personellist WHERE Adres='Beşiktaş')
SELECT Adınız,Soyadınız FROM Personellistesi WHERE maas>=
(SELECT AVG(maas)FROM Personellistesi)
Personeller tablosundaki BolNO su 4 olan Adresi Beşiktaşları listelet
*/

SELECT Adınız+' '+Soyadınız FROM Personellistesi; /Tek satırda ad ve soyadı listeler/
/Tablodaki BolumNosu F ve tablodaki Puanı 60 ile 80 arasındakileri listelet?/
SELECT *FROM Personellistesi WHERE BolumNo='F'
(SELECT *FROM Personellistesi WHERE Puan>60 AND Puan<80)

SELECT *FROM Personellistesi WHERE BolumNo='F'
(SELECT *FROM Personellistesi WHERE Puan BETWEEN 60 AND 80)

BrutUcreti ortalama BrutUcretten fazla olanı listelet?
SELECT*FROM Personellist WHERE BrutUcret>(SELECT AVG(BrutUcret) FROM Personellist);

BolumNo su 2 olup BrutUcreti 5000 den fazla olanları listelet ?
SELECT *FROM Personellistesi WHERE BolumNo='2'
(SELECT *FROM Personellistesi WHERE BrutUcret>5000)

Tablodaki en yüksek BrutUcreti alt sorgu ile listelet?
SELECT *FROM Personellistesi WHERE 
(SELECT *FROM Personellistesi WHERE )





