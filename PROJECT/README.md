# Evidence pojištěných
Jednoduchá konzolová aplikace pro správu evidence pojištěných osob.
Umožňuje přidávat nové pojištěné, zobrazovat seznam všech osob a vyhledávat podle jména a příjmení.

## 🚀 Funkce aplikace
- Přidání nového pojištěného (jméno, příjmení, věk, telefon)
- Vypsání všech uložených pojištěných
- Vyhledávání podle jména a/nebo příjmení
- Automatické ukládání dat do souboru pojisteni.json
- Načítání dat při startu aplikace

📂 Struktura projektu
```
projekt/
 ├── main.py          # Uživatelské rozhraní (menu)
 ├── evidence.py      # Evidence pojištěných + práce se souborem
 ├── pojisteny.py     # Třída Pojisteny
 ├── pojisteni.json   # Uložená data (vytvoří se automaticky)
 └── README.md
```

## ▶️ Spuštění aplikace
Aplikaci spustíte příkazem:
```
python main.py
```
Vyžaduje Python 3.10+.

🧪 Ukázka výstupu
```
------------------------------
Evidence pojištěných
------------------------------
1 - Přidat pojištěného
2 - Vypsat všechny
3 - Vyhledat
4 - Konec
```

## 🗂 Ukázka uložených dat (JSON)
```json
[
    {
        "jmeno": "Jan",
        "prijmeni": "Novák",
        "vek": 30,
        "telefon": "777123456"
    }
]
```

## 🔧 Budoucí rozšíření
- Validace telefonního čísla
- Mazání pojištěného
- Úprava existujícího záznamu
- Export do CSV
- Unit testy
- GUI (Tkinter / PyQt)
