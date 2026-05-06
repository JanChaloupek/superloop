# 📌 Základní Linux příkazy (tahák)

## 📁 Práce s adresáři a soubory

### Navigace
- `pwd` — zobrazí aktuální cestu
- `ls` — výpis obsahu adresáře  
  - `ls -l` — detailní výpis  
  - `ls -a` — včetně skrytých souborů
- `cd /cesta` — změna adresáře  
- `cd ..` — o úroveň výš  
- `cd ~` — domovský adresář

### Práce se soubory
- `cp zdroj cíl` — kopírování
- `mv zdroj cíl` — přesun/rename
- `rm soubor` — smazání souboru  
- `rm -r adresar` — rekurzivní mazání
- `touch soubor` — vytvoření prázdného souboru
- `mkdir adresar` — vytvoření adresáře

---

## 📦 Instalace aplikací

### Debian/Ubuntu (APT)
- `sudo apt update`
- `sudo apt upgrade`
- `sudo apt install <balíček>`
- `sudo apt remove <balíček>`
- `apt search <term>`

### Fedora/RHEL (DNF)
- `sudo dnf install <balíček>`
- `sudo dnf remove <balíček>`
- `sudo dnf update`

### Arch Linux (pacman)
- `sudo pacman -S <balíček>`
- `sudo pacman -R <balíček>`
- `sudo pacman -Syu` — update systému

---

## 🔧 Systémové informace
- `uname -a` — info o kernelu
- `top` / `htop` — procesy
- `df -h` — využití disků
- `free -h` — RAM
- `whoami` — aktuální uživatel
- `id` — UID/GID

---

## 📄 Zobrazení obsahu souborů
- `cat soubor.txt` — zobrazí celý obsah
- `less soubor.txt` — stránkování
- `head -n 20 soubor.txt` — prvních 20 řádků
- `tail -f log.txt` — živé sledování logu

---

## 🔍 Hledání
- `grep "text" soubor.txt` — hledání v souboru
- `grep -r "text" /cesta` — rekurzivně
- `find /cesta -name "*.log"` — hledání souborů podle jména

---

## 🔑 Práva a vlastníci
- `chmod 755 soubor` — změna práv
- `chown uživatel:skupina soubor` — změna vlastníka
- `ls -l` — zobrazí práva

---

## 🌐 Síť
- `ping seznam.cz` — test připojení
- `ip a` — síťová rozhraní
- `curl URL` — stáhne obsah
- `wget URL` — stáhne soubor

---

## 🧰 Další užitečné
- `man <příkaz>` — manuál
- `history` — historie příkazů
- `sudo <příkaz>` — spustí jako root
- `echo "text"` — vypíše text
- `nano soubor.txt` — jednoduchý editor
