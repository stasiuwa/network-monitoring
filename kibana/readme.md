Zakładka Analytics -> Create Data View -> Name: np. Suricata, Index-patternL:filebeat -> save data view -> wtedy mozna przegladac jakie logi z suricaty przychodzą do elasticsearcha. Nie ma predefiniowanych dashboardów itp. narazie

Kontner opiera się w pełni na gotowym oficjalnym obrazie, zmienne środowiskowe są zawarte w pliku .env. 

Analiza Docker Scout wykryła podatności w liczbie:
- Critical: 3
- High: 39
- Medium: 44
- Low: 10

Wykryte podatności o poziomie Crictical

CVE-2026-33937

- Potencjalnie krytyczna, ale w moim setupie nie mam endpointów spełniających podatność

CVE-2025-62718

- Umiarkowane ryzyko, nie posiadam zewnętrznego wejścia sterującego URL requestów

CVE-2025-55130 

- Niskie ryzyko, nie korzystam z podatnego modelu uprawnień 

Odnośnie podatności oznaczonych jako High i ich niepojętej ilość. Przeglądając je po kolei wnioskuję, że wszystkie odnoszą się do podatności występujących w przypadku ekpsozycji usługi publicznie, co nie występuje w moim setupie więc daruję sobie rozpisywanie wszystkich po kolei.