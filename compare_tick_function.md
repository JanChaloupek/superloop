# Porovnání tří časovacích funkcí v CircuitPythonu

Toto srovnání shrnuje rozdíly mezi **adafruit_ticks**, **time.monotonic()** a **time.monotonic_ns()** z hlediska přesnosti, vhodnosti pro superloop, práce s přetečením a praktického použití.

---

## 🧭 Přehled

| Funkce | Typ hodnoty | Přesnost | Přetečení | Bezpečné porovnání | Vhodné pro |
|-------|--------------|----------|-----------|---------------------|-------------|
| **adafruit_ticks** (`ticks_ms`) | integer (ms) | stabilní | ~6,2 dne | ano (`ticks_diff`) | superloop, periodické úlohy, debounce, robotika |
| **time.monotonic()** | float32 (s) | klesá v čase | ne | ne | lidsky čitelné časy, logování |
| **time.monotonic_ns()** | integer (ns) | velmi vysoká | prakticky ne | ne (nutné řešit ručně) | profilování, měření krátkých intervalů |

---

## 🧩 Detailní charakteristika

### **1. adafruit_ticks (ticks_ms, ticks_diff, …)**

- Vrací **celé číslo v milisekundách**.
- Přesnost se **nezhoršuje** s dobou běhu.
- Přetečení je **bezpečné** díky `ticks_diff()`.
- Navrženo přímo pro **superloop**, stavové automaty a periodické úlohy.
- Standard v Adafruit knihovnách.

**Výhody:**
- stabilní přesnost  
- bezpečné porovnání  
- ideální pro robotiku a testovací prostředí  

---

### **2. time.monotonic()**

- Vrací **float v sekundách**.
- V CircuitPythonu je float **32bit (single precision)** → cca 7 desetinných číslic.
- Jak čas roste, float **ztrácí rozlišení** → rozdíly mohou být nepřesné.
- Nepřetéká, ale není vhodný pro přesné plánování.

**Výhody:**
- lidsky čitelný čas  
- dobré pro logování nebo měření delších intervalů  

**Nevýhody:**
- ztráta přesnosti po hodinách/dnech  
- nevhodné pro přesné řízení  
- nevhodné pro superloop  

---

### **3. time.monotonic_ns()**

- Vrací **64bit integer v nanosekundách**.
- Nepoužívá float → přesnost se nezhoršuje.
- Přetečení je teoreticky možné, ale v praxi nereálné.
- Není navrženo pro plánování, chybí wrap‑safe API jako u `ticks_ms`.

**Výhody:**
- vysoké rozlišení  
- vhodné pro profilování nebo měření velmi krátkých úseků  

**Nevýhody:**
- žádné pomocné funkce pro plánování  
- různé platformy mohou mít různé skutečné rozlišení  

---

## 🧠 Doporučení pro praxi

- **Pro superloop, robotiku, periodické úlohy → `adafruit_ticks`**  
  Nejbezpečnější a nejstabilnější volba.

- **Pro lidsky čitelné časy → `time.monotonic()`**

- **Pro profilování a měření krátkých intervalů → `time.monotonic_ns()`**

---

## 🟦 Porovnání floatů podle platformy

| Platforma | Implementace | Velikost | Přesnost | Vhodné pro časování |
|-----------|--------------|----------|----------|----------------------|
| **CPython (PC, Raspberry Pi)** | double | 64 bit | ~15–17 číslic | ✔ ano |
| **MicroPython (Microbit, ESP32, STM32)** | float | 32 bit | ~7 číslic | ❌ ne |
| **CircuitPython** | float | 32 bit | ~7 číslic | ❌ ne |

### 🧩 Proč je to tak velký rozdíl?

**CPython double (Raspberry Pi)**  
- mantisa: 53 bitů  
- rozlišení: ~1e‑15  
- i po 1 000 000 sekundách (~11 dní) máš rozlišení ~1 mikrosekunda  

**MicroPython/CircuitPython float**  
- mantisa: 24 bitů  
- rozlišení: ~1e‑7  
- po 10 000 sekundách (~2.7 h) máš rozlišení ~1 ms  
- po 100 000 sekundách (~27 h) máš rozlišení ~10 ms  

Proto:

- **Na Raspberry Pi je `time.monotonic()` naprosto v pohodě.**  
- **Na MicroPythonu/CircuitPythonu je `time.monotonic()` nepoužitelný pro přesné časování.**

---

## 📊 Přesnost 32bit floatu podle velikosti času

Float32 má 24bit mantisu, což znamená, že dokáže přesně reprezentovat jen asi **7 desetinných číslic**.  
Jakmile číslo roste, float musí „vyhazovat“ nejmenší bity → ztrácí rozlišení.

| Hodnota času (sekundy) | Binární velikost | Nejmenší rozlišitelný krok | Přesnost v milisekundách | Co to znamená |
|------------------------|------------------|-----------------------------|---------------------------|----------------|
| **1 s** | 2⁰ | 2⁻²³ ≈ 0.00000012 | 0.00012 ms | Perfektní přesnost |
| **10 s** | 2³ | 2⁻²⁰ ≈ 0.000001 | 0.001 ms | Stále velmi dobré |
| **100 s** | 2⁶ | 2⁻¹⁷ ≈ 0.000008 | 0.008 ms | Stále OK |
| **1 000 s (~17 min)** | 2¹⁰ | 2⁻¹³ ≈ 0.00012 | 0.12 ms | Začíná se zhoršovat |
| **10 000 s (~2.7 h)** | 2¹³ | 2⁻¹⁰ ≈ 0.00098 | 0.98 ms | Už neumí rozlišit 1 ms |
| **100 000 s (~27 h)** | 2¹⁷ | 2⁻⁶ ≈ 0.0156 | 15.6 ms | Ztráta přesnosti v desítkách ms |
| **1 000 000 s (~11.5 dní)** | 2²⁰ | 2⁻³ ≈ 0.125 | 125 ms | Ztráta přesnosti v řádu stovek ms |

---

## 🧠 Co z toho plyne?

✔ Po několika hodinách běhu:  
`time.monotonic()` už nedokáže rozlišit 1 ms.

✔ Po jednom dni:  
float už neumí rozlišit ani 10 ms.

✔ Po týdnu:  
float neumí rozlišit ani 100 ms.

---

## 🧪 Mini‑příklady

### Periodická úloha (správně)

```python
import adafruit_ticks as ticks

next_time = ticks.ticks_add(ticks.ticks_ms(), 100)

while True:
    if ticks.ticks_diff(next_time, ticks.ticks_ms()) <= 0:
        print("tick")
        next_time = ticks.ticks_add(next_time, 100)
```

### Měření krátkého úseku

```python
import time

start = time.monotonic_ns()
# ... kód ...
elapsed_ns = time.monotonic_ns() - start
```

### Lidsky čitelné logování

```python
import time

print("Start:", time.monotonic())
```
