## Zadanie 1
* a
```sql
DELETE FROM postac WHERE NOT nazwa='Bjorn' AND rodzaj='wiking' ORDER BY wiek DESC LIMIT 2;
```
* b
```sql
ALTER TABLE przetwory DROP FOREIGN KEY przetwory_ibfk_1;
ALTER TABLE przetwory DROP FOREIGN KEY przetwory_ibfk_2;
ALTER TABLE walizka DROP FOREIGN KEY walizka_ibfk_1;
ALTER TABLE postac MODIFY id_postaci INT, DROP PRIMARY KEY;
```

## Zadanie 2
* a
```sql
ALTER TABLE postac ADD pesel CHAR(11) FIRST;
UPDATE postac SET pesel='10572642894'+id_postaci;
ALTER TABLE postac ADD PRIMARY KEY (pesel);
```
* b
```sql
ALTER TABLE postac MODIFY rodzaj ENUM('wiking','ptak','kobieta','syrena');
```
* c
```sql
INSERT INTO postac (pesel,id_postaci,nazwa,rodzaj,data_ur,wiek) VALUES ('10572642894'+id_postaci,9,'Gertruda Nieszczera','syrena','977-06-06',50);
```

## Zadanie 3
* a
```sql
UPDATE postac SET nazwa_statku='Odyn' WHERE nazwa LIKE '%a%';
```
* b
```sql
UPDATE statek SET max_ladownosc=0.7*max_ladownosc WHERE data_wodowania BETWEEN '1901-01-01' AND '2000-12-31';
```
* c
```sql
ALTER TABLE postac ADD CHECK (wiek<1000);
```

## Zadanie 4
* a
```sql
ALTER TABLE postac MODIFY rodzaj ENUM('wiking','ptak','kobieta','syrena','wąż');
INSERT INTO postac (pesel,id_postaci,nazwa,rodzaj,data_ur,wiek) VALUES ('10572642864'+id_postaci,10,'Loko','wąż','1022-02-02',5);
```
* b
```sql
CREATE TABLE marynarz LIKE postac;
INSERT INTO marynarz SELECT * FROM postac WHERE nazwa_statku IS NOT NULL;
```
* c
```sql
ALTER TABLE marynarz ADD FOREIGN KEY(nazwa_statku) REFERENCES statek(nazwa_statku)
```

## Zadanie 5
* a
```sql
UPDATE postac SET nazwa_statku=NULL;
```
* b
```sql
DELETE FROM postac WHERE nazwa='Jorund';
```
* c
```sql
DELETE FROM statek;
```
* d
```sql
DROP TABLE statek;
```
* e
```sql
CREATE TABLE zwierz (id INT AUTO_INCREMENT PRIMARY KEY,nazwa VARCHAR(40),wiek INT UNSIGNED);
```
* f
```sql
INSERT INTO zwierz(nazwa,wiek) SELECT nazwa,wiek FROM postac WHERE rodzaj='ptak' OR rodzaj='wąż';
```
