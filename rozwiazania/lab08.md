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
SELECT w.nazwa,COUNT(u.id_uczestnika),GROUP_CONCAT(k.nazwa) FROM wyprawa w JOIN uczestnicy u ON u.id_wyprawy=w.id_wyprawy  JOIN kreatura k ON k.idKreatury=u.id_uczestnika GROUP BY w.nazwa;
```
* 2
```sql
SELECT e.kolejnosc,e.dziennik,s.nazwa,k.nazwa FROM etapy_wyprawy e JOIN sektor s ON s.id_sektora=e.sektor JOIN wyprawa w ON w.id_wyprawy=e.idWyprawy JOIN kreatura k ON k.idKreatury=w.kierownik ORDER BY w.data_rozpoczecia ASC, e.idEtapu ASC;
```
## Zadanie 3
* 1
```sql
SELECT COUNT(e.sektor),s.nazwa FROM sektor s LEFT JOIN etapy_wyprawy e ON s.id_sektora=e.sektor GROUP BY s.nazwa;
SELECT IFNULL(COUNT(e.sektor),'0'),s.nazwa FROM sektor s LEFT JOIN etapy_wyprawy e ON s.id_sektora=e.sektor GROUP BY s.nazwa;
```
* 2
```sql
SELECT nazwa,IF(COUNT(u.id_uczestnika)>0,'bral udzial w wyprawie','nie bral udzialu w wyprawie') FROM kreatura k LEFT JOIN uczestnicy u ON k.idKreatury=u.id_uczestnika GROUP BY k.nazwa;
```
## Zadanie 4
* 1
```sql
SELECT nazwa,SUM(LENGTH(e.dziennik)) FROM wyprawa w JOIN etapy_wyprawy e ON e.idWyprawy=w.id_wyprawy GROUP BY w.nazwa HAVING SUM(LENGTH(e.dziennik))<400;
```
* 2
```sql
SELECT w.nazwa,(SUM(e.ilosc*z.waga)/COUNT(DISTINCT u.id_uczestnika)) FROM wyprawa w JOIN uczestnicy u ON u.id_wyprawy=w.id_wyprawy JOIN ekwipunek e ON e.idKreatury=u.id_uczestnika JOIN zasob z ON z.idZasobu=e.idZasobu GROUP BY w.nazwa;
```
## Zadanie 5
* 1
```sql
SELECT k.nazwa,DATEDIFF(day,k.dataUr,w.data_rozpoczecia) FROM kreatura k JOIN uczestnicy u ON u.id_uczestnika=k.idKreatury JOIN wyprawa w ON w.id_wyprawy=u.id_wyprawy;
```
