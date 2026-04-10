Kontner opiera się na obrazie alpine, w którym zainstalowałem filebeata oraz suricate korzystając z multi-stage build. Następnie skopiowałem pliki konfiguracyjne

filebeata - komunikacja z ELK oraz ścieżka do logów eve.json

suricata - adresy sieci lokalnej, ustawienia monitorowania interfejsu, wyjście logów oraz aktywowane reguły. foldery na logi oraz reguły są podpięte w compose.

Ponadto, w obrazie jest uruchomiony supervisor, który odpowiada za działanie suricaty i filebeata, skonfigurowany w pliku supervisord.conf. Określa prametry startujące usługi oraz automatyczne uruchamianie i restartowanie obu zn ich.

Analiza Docker Scout wykryła podatności w liczbie debian/host-sim:
- Critical: 0/0
- High: 0/9
- Medium: 2/2
- Low: 21/26

CVE-2026-34040 - nie uzywam Docker AuthZ pluginu, kontener działa w zamkniętym środowisku, bez ekspozycji na zewnątrz
CVE-2026-31931 - inna wersja suricaty
CVE-2026-31932 - brak określonego w podatności ruchu w moim środowisku, poza tym podatność zażegnana w wersjach, których debian nie ma w swoim repo.
CVE-2026-31933 - moj obraz jest podatny ze wzgledu na wersje (debian repo 7.0.10, najnowsza dostepna 7.0.15). Moze powodowac problemy wydajnosci suricaty.
CVE-2026-31934, CVE-2026-31935, CVE-2026-32280 - nie analizuje ruchu, którego dotyczy podatność
CVE-2026-39883 - wymaga dsotępu lokalnego, gdyby nie to, mogłoby być krytyczną podatnością