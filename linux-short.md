# 🐧 Linux – rychlý tahák

## 📁 Navigace
- `pwd` — aktuální cesta
- `ls` — výpis adresáře  
  - `ls -l` — detailní výpis  
  - `ls -a` — zobrazí i skryté soubory
- `cd /cesta` — změna adresáře  
- `cd ..` — o úroveň výš  
- `cd ~` — domovský adresář

## 📄 Soubory a adresáře
- `cp zdroj cíl` — kopírování souboru/adresáře
- `mv zdroj cíl` — přesun nebo přejmenování
- `rm soubor` — smazání souboru
- `rm -r adresar` — rekurzivní mazání adresáře
- `touch soubor` — vytvoření prázdného souboru
- `mkdir adresar` — vytvoření adresáře

## 📦 Instalace aplikací

### APT (Ubuntu/Debian)
- `sudo apt update` — aktualizuje seznam balíčků
- `sudo apt upgrade` — nainstaluje dostupné aktualizace
- `sudo apt install <balíček>` — nainstaluje aplikaci
- `sudo apt remove <balíček>` — odinstaluje aplikaci (ponechá konfiguraci)

### DNF (Fedora)
- `sudo dnf install <balíček>` — nainstaluje aplikaci
- `sudo dnf remove <balíček>` — odinstaluje aplikaci
- `sudo dnf update` — aktualizuje systém

### Pacman (Arch)
- `sudo pacman -S <balíček>` — nainstaluje aplikaci
- `sudo pacman -R <balíček>` — odinstaluje aplikaci
- `sudo pacman -Syu` — kompletní update systému (sync + refresh + upgrade)

## 🔧 Systém
- `uname -a` — informace o kernelu
- `top` / `htop` — běžící procesy
- `df -h` — využití disků
- `free -h` — využití RAM
- `whoami` — aktuální uživatel
- `id` — UID/GID a skupiny

## 📚 Čtení souborů
- `cat soubor` — zobrazí celý obsah
- `less soubor` — stránkování
- `head -n 20 soubor` — prvních 20 řádků
- `tail -f log.txt` — živé sledování logu

## 🔍 Hledání
- `grep "text" soubor` — hledání v souboru
- `grep -r "text" /cesta` — rekurzivní hledání
- `find /cesta -name "*.log"` — hledání souborů podle jména

## 🔑 Práva
- `chmod 755 soubor` — změna práv
- `chown user:group soubor` — změna vlastníka
- `ls -l` — zobrazí práva a vlastníky

## 🌐 Síť
- `ping seznam.cz` — test připojení
- `ip a` — síťová rozhraní
- `curl URL` — stáhne obsah stránky
- `wget URL` — stáhne soubor

## 🧰 Ostatní
- `man příkaz` — manuálová stránka
- `history` — historie příkazů
- `sudo příkaz` — spustí příkaz jako root
- `nano soubor` — jednoduchý textový editor
