Kontner opiera się na gotowym oficjalnym obrazie. Schematy w bazie danych są tworzone przez, że tak powiem zainteresowanych czyli Zabbix sam sobie tworzy schematy, planuję również rozszerzyć bazę danych o backup logów z ELKa.

Analiza Docker Scout wykryła podatności w liczbie:
- Critical: 1
- High: 9
- Medium: 12
- Low: 40

Podatności:

CVE-2026-68121 Critical
- Podatność dotyczy zachowań, których postgres w domyślnej konfiguracji nie przejawia.

Pozostałe podatności dotyczą głównie konfiguracji TLS oraz mechanizmów związanych z URL, URI czy parsowaniu adresów, których PostgreSQL nie używa domyślnie lub nawet wcale. Ponadto postgre jest izolowany od pozostałych kontenerów spoza sieci zabbix oraz nieudostepniony publicznie.

Prawie wszystkie podatności były oznaczone w Docker Scout jako fixable poprzez aktualizację wersji elementów składowych obrazu.