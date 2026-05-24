01-base.yaml
- Tworzy dedykowany namespace oraz zmienne środowiskowe i plik konfiguracyjny logstasha.

02-statefulsets.yaml
- Użycie Statefulset gwarantuje stałość podów bazodanowych wraz z trwałym wiązaniem wolumenu danych z konkretnym podem. 

03-deployments.yaml
- Zabbix serwer oraz web, logstash, kibana nie przechowują własnego stanu lokalnie tylko w bazie danych, stąd zastosowanie obiektu Deployment z 1 repliką.

04-host-sim.yaml
- Narzędzia monitorujące zostały spakowane w jeden pod, odwzorowany jako deployment, który przesyła logi wewnętrznie do logstasha oraz utrzymuje komunikację aggenta zabbix z serwerem.

05-ingress.yaml
- zastosowany do zarządzania ruchem http. mapowanie portów podów w klastrze na domeny.