Kontner opiera się na gotowym oficjalnym obrazie. Używam swojego pliku konfiguracyjnego oraz określam własny pipeline config pod suricate odbierający logi z filebeata w określonym formacie

Analiza Docker Scout wykryła podatności w liczbie:
- Critical: 1
- High: 15
- Medium: 23
- Low: 3

Wykryte podatności w głównej mierze dotyczą bibliotek Ruby/Java używanych przez Logstash. Sporo jest podatności związanych z operacjami kryptograficznymi. Główne zagrożenia to DoS, błędy pamięci i manipulacja sesją. Aczkolwiek podatności nie dotyczą mojego środowiska ze względu na brak ekspozycji publicznej oraz brak bezpośredniego wpływu użytkownika na większość komponentów systemowych. Logstash przetwarza tylko określone dane o określonym formacie (logi suricata) przekazywane określonym kanałem - Filebeeat
