Aby połączyć agenta do zabbixa nalezy wejśc na strone web
Monitoring -> Hosts
Kliknąć na gotowego hosta nastepnie Configuration -> Host
zmienic nazwe hosta na zabbix-agent jeśli jest inna, ponadto w zakładce Interfaces ustawić opcję DNS podać nazwę zabbix-agent port 10050

Kontner opiera się na gotowym oficjalnym obrazie. Zmienne środowiskowe w pliku .env określają tylko port komunikacji z serwerem oraz strefę czasową dla lepszej czytelności logów.

Analiza Docker Scout wykryła podatności w liczbie alpine/zabbixweb:
- Critical: 0/0
- High: 2/4
- Medium: 2/9
- Low: 1/2

Większośc podatności dotyczy TLS, HTTP2 i narzedzi systemowych. W przypadku mojego obrazu nie korzystam z niestandardowej konfiguracji, brak SMB, XML crpyto, HTTP2 (domyślnie uzywa HTTP1) oraz przede wszystkim brak publicznej ekspozycji więc podatności można zingonorwacć.