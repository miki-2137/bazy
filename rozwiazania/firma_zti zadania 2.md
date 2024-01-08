## Zadanie 1
```sql
SELECT d.nazwa,MIN(p.pensja),MAX(p.pensja),AVG(p.pensja) FROM dzial d JOIN pracownik p ON p.dzial=d.id_dzialu GROUP BY d.nazwa;
```
## Zadanie 2
```sql
SELECT k.pelna_nazwa,SUM(pz.ilosc*pz.cena) FROM klient k JOIN zamowienie z ON z.klient=k.id_klienta JOIN pozycja_zamowienia pz ON pz.zamowienie=z.id_zamowienia GROUP BY z.id_zamowienia ORDER BY SUM(pz.cena*pz.ilosc) DESC LIMIT 10;
```
## Zadanie 3
```sql
SELECT SUM(pz.ilosc*pz.cena) AS przychod,YEAR(z.data_zamowienia) AS rok FROM pozycja_zamowienia pz JOIN towar t ON t.id_towaru=pz.towar JOIN zamowienie z ON z.id_zamowienia=pz.zamowienie GROUP BY rok ORDER BY przychod DESC
```
## Zadanie 7
```sql
SELECT (SUM(pz.ilosc*pz.cena)-SUM(t.cena_zakupu*pz.ilosc)) AS dochod,YEAR(z.data_zamowienia) AS rok FROM pozycja_zamowienia pz JOIN towar t ON t.id_towaru=pz.towar JOIN zamowienie z ON z.id_zamowienia=pz.zamowienie GROUP BY rok;
```
