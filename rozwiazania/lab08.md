## Zadanie 1
* 1
```sql

```
* 2
```sql
SELECT nazwa FROM kreatura k LEFT JOIN uczestnicy u ON u.id_uczestnika=k.idKreatury WHERE u.id_uczestnika IS NULL;
```
* 3
```sql
SELECT w.nazwa,SUM(e.ilosc) FROM wyprawa w JOIN uczestnicy u ON u.id_wyprawy=w.id_wyprawy JOIN ekwipunek e ON e.idKreatury=u.id_uczestnika GROUP BY w.nazwa;
```
## Zadanie 2
* 1
```sql

```
* 2
```sql

```
## Zadanie 3
* 1
```sql

```
* 2
```sql

```
## Zadanie 4
* 1
```sql

```
* 2
```sql

```
## Zadanie 5
* 1
```sql

```
