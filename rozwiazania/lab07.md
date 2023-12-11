## Zadanie 1
* 1
```sql
SELECT AVG(waga) FROM kreatura WHERE rodzaj='wiking';
```
* 2
```sql
SELECT AVG(waga),COUNT(rodzaj),rodzaj FROM kreatura GROUP BY rodzaj;
```
* 3
```sql
SELECT AVG(1700-YEAR(dataUR)),rodzaj FROM kreatura GROUP BY rodzaj;
SELECT AVG(YEAR(CURDATE())-YEAR(dataUr)) FROM kreatura GROUP BY rodzaj;
```

## Zadanie 2
* 1
```sql
SELECT SUM(ilosc*waga),rodzaj FROM zasob GROUP BY rodzaj;
```
* 2
```sql
SELECT nazwa, AVG(waga),SUM(ilosc),SUM(waga) FROM zasob GROUP BY nazwa HAVING SUM(ilosc)>=4 AND SUM(waga)>10;
SELECT nazwa, AVG(waga),SUM(ilosc),SUM(waga) FROM zasob WHERE ilosc>=4 GROUP BY nazwa HAVING SUM(waga)>10;
```
* 3
```sql
SELECT rodzaj,SUM(ilosc),COUNT(DISTINCT nazwa) FROM zasob GROUP BY rodzaj HAVING MIN(ilosc)>1;
```

## Zadanie 3
* 1
```sql
SELECT kreatura.nazwa,SUM(ekwipunek.ilosc) FROM kreatura INNER JOIN ekwipunek ON ekwipunek.idKreatury=kreatura.idKreatury GROUP BY kreatura.nazwa;
```
* 2
```sql
SELECT kreatura.nazwa, zasob.nazwa FROM kreatura INNER JOIN ekwipunek ON ekwipunek.idKreatury=kreatura.idKreatury INNER JOIN zasob ON zasob.idZasobu=ekwipunek.idZasobu ORDER BY kreatura.nazwa;
```
* 3
```sql
SELECT kreatura.nazwa,ekwipunek.idZasobu FROM kreatura LEFT JOIN ekwipunek ON kreatura.idKreatury=ekwipunek.idKreatury HAVING ekwipunek.idZasobu IS NULL;
```

## Zadanie 4
* 1
```sql
SELECT kreatura.nazwa,kreatura.dataUr,zasob.nazwa FROM kreatura NATURAL JOIN ekwipunek,zasob WHERE kreatura.rodzaj='wiking' AND YEAR(kreatura.dataUr) LIKE '167_';
SELECT kreatura.nazwa,kreatura.dataUr,zasob.nazwa FROM kreatura NATURAL JOIN ekwipunek LEFT JOIN zasob ON zasob.idZasobu=ekwipunek.idZasobu WHERE kreatura.rodzaj='wiking' AND YEAR(kreatura.dataUr) LIKE '167_';
```
* 2
```sql
SELECT k.nazwa,dataUr,z.nazwa FROM kreatura k JOIN ekwipunek e ON e.idKreatury=k.idKreatury JOIN zasob z ON e.idZasobu=z.idZasobu WHERE z.rodzaj='jedzenie' ORDER BY dataUr ASC LIMIT 5;
```
* 3
```sql
SELECT CONCAT(k1.nazwa,' - ',k2.nazwa) FROM kreatura k1,kreatura k2 WHERE k2.idKreatury-k1.idKreatury=5;
```

## Zadanie 5
* 1
```sql
SELECT k.rodzaj,AVG(e.ilosc*z.waga) FROM kreatura k JOIN ekwipunek e ON e.idKreatury=k.idKreatury JOIN zasob z ON z.idZasobu=e.idZasobu WHERE k.rodzaj NOT IN('malpa','waz') GROUP BY k.rodzaj HAVING SUM(e.ilosc)<30;
```
* 2
```sql
SELECT k.nazwa,k.rodzaj,k.dataUr FROM kreatura k, (SELECT min(dataUr) min, max(dataUr) max FROM kreatura GROUP BY rodzaj) b WHERE b.min=k.dataUr OR b.max=k.dataUr;

SELECT 'nalmlodsza',a.maxData,b.nazwa,a.rodzaj FROM (SELECT max(dataUr) maxData, rodzaj FROM kreatura GROUP BY rodzaj) a, (SELECT nazwa,dataUr FROM kreatura) b WHERE a.maxData=b.dataUr UNION SELECT 'najstarsza',a.minData,b.nazwa,a.rodzaj FROM (SELECT min(dataUr) minData, rodzaj FROM kreatura GROUP BY rodzaj) a, (SELECT nazwa,dataUr FROM kreatura) b WHERE a.minData=b.dataUr;
```
