# 🐧 Linux – tahák na jednu obrazovku

## 📁 Navigace
- `pwd` — aktuální cesta
- `ls` — výpis adresáře (`-l` detailně, `-a` skryté)
- `cd /cesta` — změna adresáře
- `cd ..` — o úroveň výš
- `cd ~` — domovský adresář

## 📄 Soubory a adresáře
- `cp zdroj cíl` — kopírování
- `mv zdroj cíl` — přesun/rename
- `rm soubor` — smazání
- `rm -r adresar` — mazání adresáře
- `touch soubor` — nový soubor
- `mkdir adresar` — nový adresář

## 📦 Instalace aplikací
- `sudo apt update` — aktualizace seznamu balíčků
- `sudo apt upgrade` — aktualizace systému
- `sudo apt install <balíček>` — instalace
- `sudo apt remove <balíček>` — odinstalace

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
