Kontner opiera się w pełni na gotowym oficjalnym obrazie, zmienne środowiskowe są zawarte w pliku .env. 

Analiza Docker Scout wykryła podatności w liczbie:
 - Critical: 0
 - High: 10
 - Medium: 14 
 - Low: 2

Wykryte podatności o poziomie High

CVE-2026-33871, CVE-2026-22184, CVE-2026-24881, CVE-2026-33870, CVE-2026-27135

- Potencjalnie niebezpieczne ale moje środowisko nie udostępnia żadnego kontenera publicznie. Ponadto w przypadku 27135 Elastic domyślnie korzysta z innej wersji HTTP niż w podatności.

CVE-2026-24882, CVE-2026-0861

- Ryzyko niskie, wymaga specyficznego użycia funkcjonalności/spełnienia specyficznych warunków które nie są wykorzystywane w moim setupie.

CVE-2026-68973

- Ryzyko niskie, Obraz używa GnuPG tylko podczas instalacji Elasticsearcha, więc podatnośc dotyczy funkcji niewykorzystywanej podczas działania obrazu.

CVE-2026-4046

- Brak ryzyka, Elastic przetwarza JSON w kodowaniu UTF-8 (Podatność dotyczy IBM1390/1399)

CVE-2026-4424

- Brak ryzyka, Elasticsearch nie przetwarza archiwów RAR objętych podatnością
