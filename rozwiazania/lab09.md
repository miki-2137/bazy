```sql
DELIMITER //
CREATE TRIGGER kreatura_before
BEFORE INSERT ON kreatura
FOR EACH ROW 
BEGIN
	IF NEW.waga<=0
    THEN
		SET NEW.waga=1;
	END IF;
END
//;
```

```sql
DELIMITER $$
CREATE TRIGGER wyprawa_after_delete AFTER DELETE ON wyprawa
BEGIN
INSERT INTO archiwum_wypraw SELECT w.id_wyprawy,w.nazwa,w.data_rozpoczecia,w.data_zakonczenia,k.nazwa FROM wyprawa w INNER JOIN kreatura k ON k.idKreatury=w.kierownik WHERE id_wyprawy=old.id_wyprawy;
END
$$
```
