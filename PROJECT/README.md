# Weather Analytics 2024 – Bratislava vs Victoria

Aplikace porovnává meteorologické údaje mezi městy **Bratislava (SK)** a **Victoria (CA)** v období **2.–15. března 2024**.  
Data jsou získávána z API **Open‑Meteo**, zpracována pomocí **Pandas** a vizualizována pomocí **Plotly**.

---

## 🚀 Funkce aplikace
- Stažení historických meteorologických dat z Open‑Meteo
- Výpočet meteorologických metrik:
  - **Srel** – relativní sluneční svit (%)
  - **GDD** – růstový potenciál nad 5 °C
  - **RDI** – intenzita deště (mm/h)
  - **DI** – index větrné expozice
- Export zpracovaných dat do CSV
- Webový dashboard s tabulkami a interaktivními grafy
- Oddělená 3‑vrstvá architektura (Repository → Service → Routes)

---

## 🛠 Použité technologie
- **FastAPI** – backend a API
- **httpx (async)** – volání externího API
- **Pandas, NumPy** – datové výpočty
- **Jinja2** – šablony
- **Plotly.js** – interaktivní grafy
- **Uvicorn** – server

---

## 📁 Struktura projektu
```
src/
 ├── app/
 │    ├── models.py
 │    ├── repository.py
 │    ├── services.py
 │    ├── routes.py
 │    └── templates/
 ├── main.py
 └── run.py
```

---

## ▶️ Spuštění projektu

### 1) Instalace závislostí
```bash
pip install -r requirements.txt
```

### 2) Spuštění aplikace
```bash
python run.py
```

### 3) Otevření dashboardu
- Dashboard: **http://localhost:8000/**
- API endpoint: **http://localhost:8000/api/weather**

---

## 📊 Popis metrik

| Metrika | Význam |
|--------|--------|
| **Srel (%)** | Relativní sluneční svit – poměr slunečního svitu k délce dne |
| **GDD (°C)** | Growing Degree Days – růstový potenciál nad 5 °C |
| **RDI (mm/h)** | Intenzita deště v daný den |
| **DI** | Index větrné expozice (kombinace větru a slunečního svitu) |

---

## 📦 Export dat
Aplikace automaticky ukládá zpracovaná data do složky:

```
output/bratislava.csv
output/victoria.csv
```

---

## 📝 Poznámky k projektu
- Datumové rozmezí a města jsou aktuálně pevně nastavené v kódu.
- Pro produkční použití by bylo vhodné přidat validaci dat a konfigurační soubor.
- Šablona využívá Plotly 3.4.0 z CDN.

---

## 📚 Licence
Projekt vytvořen jako závěrečný projekt kurzu Python (Robot Dreams).

