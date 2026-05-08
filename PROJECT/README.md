# Regulace tepelného čerpadla podle přebytků FVE

Tento projekt slouží k automatickému zapínání a vypínání tepelného čerpadla
na základě přebytků výroby z domácí fotovoltaické elektrárny.

## Funkce projektu
- Čtení výkonu FVE z Growatt API nebo Home Assistantu
- Čtení teplot a stavu čerpadla přes Modbus TCP
- Regulace podle nastavitelných prahů (zapnutí/vypnutí)
- Webové rozhraní (Flask) s grafem výkonu a teplot
- Logování dat do CSV
- Možnost rozšíření o GUI (Tkinter)

## Struktura projektu
```
project/
├── app/
│   ├── heatpump.py        # komunikace s TČ přes Modbus
│   ├── growatt.py         # Growatt API klient
│   ├── homeassistant.py   # HA API klient
│   ├── regulator.py       # logika regulace
│   ├── web.py             # Flask webserver
│   └── config.py          # IP adresy, tokeny, prahy
├── templates/
│   └── index.html
├── static/
├── README.md
├── requirements.txt
└── run.py
```

## Instalace
```
git clone https://github.com/fricosk/Regulacia-TC-prebytkami-FV.git
cd Regulacia-TC-prebytkami-FV
python /m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```


## Spuštění
```
python run.py
```


## Konfigurace
V souboru `config.py` nastavte:
- IP adresu tepelného čerpadla
- Growatt token
- Home Assistant token
- prahy zapnutí/vypnutí

## Bezpečnost
- Tokeny doporučujeme ukládat do `.env`
- Modbus komunikace není šifrovaná – používejte pouze v lokální síti

## Budoucí rozšíření
- MQTT integrace
- Docker image
- Watchdog pro Modbus
- Automatické ukládání grafů

