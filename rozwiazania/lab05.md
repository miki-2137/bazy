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
INSERT INTO postac (pesel,id_postaci,nazwa,rodzaj,data_ur,wiek) VALUES ('10572642851',9,'Gertruda Nieszczera','syrena','977-06-06',50);
```

## Zadanie 3
* a
```sql

```
* b
```sql

```
* c
```sql

```

## Zadanie 4
* a
```sql

```
* b
```sql

```
* c
```sql

```

## Zadanie 5
* a
```sql

```
* b
```sql

```
* c
```sql

```
* d
```sql

```
* e
```sql

```
* f
```sql

```
