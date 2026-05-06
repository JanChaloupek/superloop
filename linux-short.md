# 🐧 Linux – rychlý tahák

## 📁 Navigace
- `pwd` — aktuální cesta
- `ls` — výpis adresáře  
  - `ls -l` (detailně), `ls -a` (skryté)
- `cd /cesta` — změna adresáře  
- `cd ..` — o úroveň výš  
- `cd ~` — domovský adresář

## 📄 Soubory a adresáře
- `cp zdroj cíl` — kopírování
- `mv zdroj cíl` — přesun/rename
- `rm soubor` — smazání
- `rm -r adresar` — rekurzivní mazání
- `touch soubor` — nový soubor
- `mkdir adresar` — nový adresář

## 📦 Instalace aplikací
### APT (Ubuntu/Debian)
- `sudo apt update`
- `sudo apt upgrade`
- `sudo apt install <balíček>`
- `sudo apt remove <balíček>`

### DNF (Fedora)
- `sudo dnf install <balíček>`
- `sudo dnf remove <balíček>`
- `sudo dnf update`

### Pacman (Arch)
- `sudo pacman -S <balíček>`
- `sudo pacman -R <balíček>`
- `sudo pacman -Syu` — update systému

## 🔧 Systém
- `uname -a` — info o kernelu
- `top` / `htop` — procesy
- `df -h` — disky
- `free -h` — RAM
- `whoami` — uživatel
- `id` — UID/GID

## 📚 Čtení souborů
- `cat soubor` — celý obsah
- `less soubor` — stránkování
- `head -n 20 soubor` — začátek
- `tail -f log.txt` — živé logy

## 🔍 Hledání
- `grep "text" soubor` — hledání
- `grep -r "text" /cesta` — rekurzivně
- `find /cesta -name "*.log"` — hledání souborů

## 🔑 Práva
- `chmod 755 soubor` — práva
- `chown user:group soubor` — vlastník
- `ls -l` — zobrazí práva

## 🌐 Síť
- `ping seznam.cz` — test
- `ip a` — síťová rozhraní
- `curl URL` — stáhne obsah
- `wget URL` — stáhne soubor

## 🧰 Ostatní
- `man příkaz` — manuál
- `history` — historie
- `sudo příkaz` — root
- `nano soubor` — editor
