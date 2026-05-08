# 📘 Správa filmov

## Aplikácia umožňuje:
- pridávať filmy ručne
- načítavať filmy z OMDb API
- vyhľadávať filmy podľa názvu
- zobrazovať všetky uložené filmy

## 🚀 Funkcionalita
- Validácia vstupov (názov, žáner, rok, hodnotenie)
- Integrácia s OMDb API
- Trieda Movie reprezentujúca film
- Jednoduché textové menu

## 📂 Štruktúra projektu
```
sprava-filmov/
  ├── movie.py
  ├── api.py
  ├── manager.py
  ├── main.py
  └── README.md
```

## 🔧 Inštalácia
```
git clone https://github.com/uzivatel/sprava-filmov.git
cd sprava-filmov
pip install -r requirements.txt
```

## ▶️ Spustenie
```
python main.py
```

## 🌐 OMDb API
Aplikácia používa OMDb API: https://www.omdbapi.com/

Pre funkčnosť je potrebné vytvoriť .env súbor:
```
OMDB_API_KEY=vas_kluc
```

## 🧪 Budúce rozšírenia
- Ukladanie filmov do JSON/CSV
- Triedenie filmov podľa roku alebo hodnotenia
- GUI verzia (Tkinter / PyQt)
- Webová verzia (FastAPI)
