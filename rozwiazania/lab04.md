**Zadanie 1**
* 1
```sql
CREATE TABLE postac (
id_postaci INT PRIMARY KEY AUTO_INCREMENT,
nazwa VARCHAR(40),
rodzaj ENUM('wiking','ptak','kobieta'),
data_ur DATE,
wiek INT UNSIGNED);
```
* 2
```sql
INSERT INTO postac (nazwa,rodzaj,data_ur,wiek) VALUES 
('Bjorn','wiking','1000-11-11','27'),
('Drozd','ptak','1025-06-27','2'),
('Tesciowa','kobieta','950-01-01','77');
```
* 3
```sql
UPDATE postac SET wiek='88' WHERE nazwa='tesciowa';
```
**Zadanie 2**
* 1
```sql
CREATE TABLE walizka (
id_walizki INT PRIMARY KEY AUTO_INCREMENT,
pojemnosc INT UNSIGNED,
kolor ENUM('rozowy','czerwony','teczowy','zolty'),
id_wlasciciela INT,
FOREIGN KEY(id_wlasciciela) REFERENCES postac(id_postaci) ON DELETE CASCADE);
```
* 2
```sql
ALTER TABLE walizka ALTER COLUMN kolor SET DEFAULT 'rozowy';
```
* 3
```sql
INSERT INTO walizka (pojemnosc,kolor,id_wlasciciela) VALUES 
('20','czerwony','1'),('50','rozowy','3');
```

**Zadanie 3**
* 1
```sql
CREATE TABLE izba (
adres_budynku VARCHAR(50),
nazwa_izby VARCHAR(50),
metraz INT UNSIGNED,
wlasciciel INT,
PRIMARY KEY(adres_budynku,nazwa_izby),
FOREIGN KEY(wlasciciel) REFERENCES postac(id_postaci) ON DELETE SET NULL);
```
* 2
```sql
ALTER TABLE izba ADD kolor_izby VARCHAR(15) DEFAULT 'czarny' AFTER metraz;
```
* 3
```sql
INSERT INTO izba (adres_budynku,nazwa_izby,metraz,kolor_izby,wlasciciel) VALUES ('Krzywa 5','Spizarnia','10','bialy',1);
```

**Zadanie 4**
* 1
```sql
CREATE TABLE przetwory (
id_przetworu INT PRIMARY KEY AUTO_INCREMENT,
rok_produkcji INT(4) DEFAULT '1654',
id_wykonawcy INT,
zawartosc VARCHAR(40),
dodatek VARCHAR(50) DEFAULT 'papryczka chilli',
id_konsumenta INT,
FOREIGN KEY(id_wykonawcy) REFERENCES postac(id_postaci),
FOREIGN KEY(id_konsumenta) REFERENCES postac(id_postaci));
```
* 2
```sql
INSERT INTO przetwory (rok_produkcji,id_wykonawcy,zawartosc,dodatek,id_konsumenta) VALUES (default,3,'bigos',default,1);
```

**Zadanie 5**
* 1
```sql
INSERT INTO postac (nazwa,rodzaj,data_ur,wiek) VALUES ('Floki','wiking','1001-01-01',26),('Ragnar','wiking','1002-02-02',25),('Harald','wiking','1003-03-03',24),('Torvi','wiking','1004-04-04',23),('Jorund','wiking','1005-05-05',22);
```
* 2
```sql
CREATE TABLE statek (
nazwa_statku VARCHAR(40) PRIMARY KEY,
rodzaj_statku ENUM('knarr','drakkar','skeid'),
data_wodowania DATE,
max_ladownosc INT UNSIGNED);
```
* 3
```sql

```
* 4
```sql

```
* 5
```sql

```
* 6
```sql

```
* 7
```sql

```
* 8
```sql

```
* 9
```sql

```
