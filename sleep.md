# 🧵 Problémy s nepoužitím `sleep()` v MicroPythonu a CircuitPythonu  
*(RP2040 – Raspberry Pi Pico / Pico W)*

Tento dokument vysvětluje, proč je důležité používat `sleep()` v nekonečných smyčkách a vláknech, a proč se MicroPython a CircuitPython chovají odlišně.

---

## 🟦 1. Proč je `sleep()` důležitý obecně

V nekonečné smyčce:

```python
while True:
    pass
```

procesor:

- běží na 100 %
- nikdy neuvolní řízení
- nikdy nedá prostor jiným částem runtime
- nikdy neumožní garbage collectoru proběhnout

To může způsobit různé problémy podle toho, jaký interpreter používáte.

---

# 🟥 2. MicroPython: proč smyčka bez `sleep()` může způsobit problémy

MicroPython na RP2040:

- běží jako **jeden interpreter**
- sdílí **jeden heap**
- sdílí **jeden garbage collector**
- sdílí **jeden interpreter lock** mezi jádry

### Pokud běží smyčka bez `sleep()`:

### ❌ 1. Garbage collector se nemusí spustit  
Interpreter nedostane šanci provést GC → paměť se plní → `MemoryError`.

### ❌ 2. Další vlákna se nedostanou ke slovu  
Druhé jádro sdílí interpreter → může čekat na lock → program se „zasekne“.

### ❌ 3. uasyncio se zastaví  
Event loop nedostane čas → žádné tasky se neprovedou.

### ❌ 4. Časovače MicroPythonu nefungují správně  
Interní tick hook se neprovede → čas se „zastaví“.

### ❌ 5. Program může působit jako zamrzlý  
I když hardware běží, MicroPython runtime stojí.

---

## 🟩 Jak to řešit v MicroPythonu

Použít:

```python
time.sleep(0)
```

nebo

```python
time.sleep_ms(1)
```

To:

- uvolní interpreter lock  
- umožní GC proběhnout  
- umožní přepnutí vláken  
- sníží spotřebu CPU  

---

# 🟦 3. CircuitPython: proč smyčka bez `sleep()` nevadí tolik

CircuitPython:

- používá **jen jedno jádro** (druhé je vypnuté)
- má **jiný plánovač**
- má **jiný garbage collector**
- má **automatické yieldování**

To znamená:

### ✔ CircuitPython si sám vkládá „yield“  
I když napíšeš:

```python
while True:
    pass
```

CircuitPython:

- občas uvolní řízení  
- spustí GC  
- obslouží USB  
- obslouží časovače  
- obslouží event loop  

### ✔ Proto se CircuitPython nezasekne  
Je navržený tak, aby byl „blbuvzdorný“ pro začátečníky.

---

# 🟥 4. Rozdíly mezi MicroPythonem a CircuitPythonem

| Vlastnost | MicroPython | CircuitPython |
|----------|-------------|----------------|
| Počet jader | 2 (obě dostupná) | 1 (druhé vypnuté) |
| Threading | Ano | Ne |
| GC | Musí dostat prostor | Běží automaticky |
| Nekonečná smyčka bez sleep | Může blokovat runtime | Nevadí |
| Výkon | Vyšší | Nižší |
| Stabilita pro začátečníky | Nižší | Vyšší |

---

# 🟦 5. Doporučení pro výuku

### Pokud učíte **paralelní programování** → MicroPython  
Ale vždy používat:

```python
time.sleep(0)
```

### Pokud učíte **základy programování** → CircuitPython  
Protože:

- méně chyb  
- méně problémů s GC  
- méně problémů s vlákny  
- jednodušší chování  

---

# 🟩 6. Shrnutí

- `sleep()` je důležitý, protože uvolňuje interpreter.  
- MicroPython sdílí interpreter mezi dvěma jádry → smyčka bez `sleep()` může blokovat GC, vlákna i časovače.  
- CircuitPython běží jen na jednom jádře a má automatické yieldování → smyčka bez `sleep()` nevadí.  
- Pro paralelní programování je MicroPython výkonnější, ale vyžaduje disciplínu.  
- Pro začátečníky je CircuitPython stabilnější.

