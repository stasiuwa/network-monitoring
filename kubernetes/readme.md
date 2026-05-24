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

06-network-policy
- wprowadzenie zasady zero trust w klastrze
- postgres dopuszcza ruch tylko od zabbix-server na porcie 5432 protokołem TCP
- logstash <-> host-sim TCP port 5044
- elasticsearch <-> logstash, kibana TCP port 9200
- Kibana, Zabbix Web <-> Ingress Controller, zewnętrzny kontroller do przekazywania ruchu z przegląarek. Pody nie mają powodu wysyłać żądań do graficznych interfejsów.