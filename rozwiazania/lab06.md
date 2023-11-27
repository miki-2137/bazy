## Zadanie 1
* 1
```sql
CREATE TABLE kreatura SELECT * FROM wikingowie.kreatura;
CREATE TABLE zasob SELECT * FROM wikingowie.zasob;
CREATE TABLE ekwipunek SELECT * FROM wikingowie.ekwipunek;
```
* 2
```sql
SELECT * FROM zasob;
```
* 3
```sql
SELECT * FROM zasob WHERE rodzaj='jedzenie';
```
* 4
```sql
SELECT idZasobu,ilosc FROM ekwipunek WHERE ekwipunek.idKreatury IN (1,3,5);
```

## Zadanie 2
* 1
```sql
SELECT * FROM kreatura WHERE rodzaj!='wiedzma' AND udzwig>=50;
```
* 2
```sql
SELECT * FROM zasob WHERE waga BETWEEN 2 AND 5;
```
* 3
```sql
SELECT * FROM kreatura WHERE nazwa LIKE '%or%' AND udzwig BETWEEN 30 AND 70;
```
## Zadanie 3
* 1
```sql
SELECT * FROM zasob WHERE MONTH(dataPozyskania)=07 OR MONTH(dataPozyskania)=08;
```
* 2
```sql
SELECT * FROM zasob WHERE rodzaj IS NOT NULL ORDER BY waga;
```
* 3
```sql
SELECT * FROM kreatura WHERE dataUr IS NOT NULL ORDER BY dataUr LIMIT 5;
```
## Zadanie 4
* 1
```sql
SELECT DISTINCT rodzaj FROM zasob;
```
* 2
```sql
SELECT CONCAT(nazwa," - ",rodzaj)AS 'nazwa - rodzaj' FROM kreatura WHERE rodzaj LIKE 'wi%';
```
* 3
```sql
SELECT *, CONCAT(ilosc*waga) AS calkowita_waga FROM zasob WHERE YEAR(dataPozyskania) BETWEEN 2000 AND 2007;
```
## Zadanie 5
* 1
```sql
SELECT 0.7*waga AS netto,0.3*waga AS waga_odpadkow FROM zasob;
```
* 2
```sql
SELECT * FROM zasob WHERE rodzaj IS NULL;
```
* 3
```sql
SELECT DISTINCT rodzaj FROM zasob WHERE nazwa LIKE'Ba%' OR nazwa LIKE '%os' ORDER BY rodzaj;
```
