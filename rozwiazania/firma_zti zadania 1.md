## Zadanie 1
```sql
SELECT imie,nazwisko,data_urodzenia FROM pracownik;
```
## Zadanie 2
```sql
SELECT imie,nazwisko,YEAR(curdate())-YEAR(data_urodzenia) FROM pracownik;
```
## Zadanie 3
```sql
SELECT nazwa,COUNT(p.id_pracownika) FROM dzial JOIN pracownik p ON p.dzial=dzial.id_dzialu GROUP BY nazwa;
```
## Zadanie 4
```sql
SELECT k.nazwa_kategori,COUNT(kategoria) FROM kategoria k JOIN towar t ON t.kategoria=id_kategori GROUP BY nazwa_kategori;
```
## Zadanie 5
```sql
SELECT k.nazwa_kategori,GROUP_CONCAT(t.nazwa_towaru) FROM kategoria k JOIN towar t ON t.kategoria=k.id_kategori GROUP BY k.nazwa_kategori;
```
## Zadanie 6
```sql
SELECT ROUND(AVG(pensja),2) FROM pracownik;
```
## Zadanie 7
```sql
SELECT AVG(pensja) FROM pracownik WHERE YEAR(curdate())-YEAR(data_zatrudnienia)>=5;
```
## Zadanie 8
```sql
SELECT t.nazwa_towaru,SUM(p.ilosc) FROM towar t JOIN pozycja_zamowienia p ON p.towar=t.id_towaru GROUP BY t.nazwa_towaru ORDER BY SUM(p.ilosc) DESC LIMIT 10;
```
## Zadanie 9
```sql
SELECT z.numer_zamowienia,SUM(p.cena*p.ilosc) FROM zamowienie z JOIN pozycja_zamowienia p ON p.zamowienie=z.id_zamowienia WHERE YEAR(z.data_zamowienia)=2017 AND QUARTER(z.data_zamowienia)=1 GROUP BY z.numer_zamowienia;
```
## Zadanie 10
```sql
SELECT p.imie,p.nazwisko,SUM(pz.cena*pz.ilosc) FROM pracownik p JOIN zamowienie z ON z.pracownik_id_pracownika=p.id_pracownika JOIN pozycja_zamowienia pz ON pz.zamowienie=z.id_zamowienia GROUP BY p.id_pracownika ORDER BY SUM(pz.cena*pz.ilosc) DESC;
```
