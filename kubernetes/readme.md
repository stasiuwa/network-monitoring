PRZESTRZEŃ NAZW: monitoring, wszystkie komponenty systemu odizolowane do przestrzeni nazw odpowiedzialnej za monitorowanie sieci.

RODZAJE OBIEKTÓW: 

STATEFULSET: PostgreSQL i Elasticsearch - aplikacje stanowe, wymagają trwałego powiązania z pamięcią.

DEPLOYMENT: Zabbix Server, Web, Kibana, Logstash, Host-sim - nie przechowują danych lokalnie tylko przetwarzają zapisane z bazy, aplikacje bezstanowe.

SERVICES: postgres i elsatic - dostępne wyłącznie wewnątrz klastra, nie są udostępnianie publiczne = brak zewnętrznego adresu IP. zabbix-web i kibana są wystawione wewnętrznie, ruch zarządzany przez Ingress.

INGRESS: zastosowany dla graficznych interfejsów zabbix i kibana. 
LOADBALANCER: zastosowany dla Logstash i Zabbix server ze względu na użycie TCP. W połączeniu z minikube tunnel przydziela im zewnętrzne IP na hoście.

PRZECHOWYWANIE DANYCH: trwałość danych dla DB i Elasitc została zrealizowana za pomocą volumeClaimTemplates wbudowanych w obiekty typu StatefulSet. 

CONFIGMAP/SECRETS: zmienne środowiskowe i pliki konfiguracyjne poszczególnych usług zostały zapisane w obiektach typu ConfigMap. Konfiguracje są wstrzykiwane do podów poprzez envFrom, pliki przez volumeMounts.

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
- do pliku hosts dodac 127.0.0.1 zabbix.minikube i kibana.minikube. Na Win trzeba odblokowac porty webowe = wywalic usługe IIS WINDOWS

06-network-policy
- wprowadzenie zasady zero trust w klastrze
- postgres dopuszcza ruch tylko od zabbix-server na porcie 5432 protokołem TCP
- logstash <-> host-sim TCP port 5044
- elasticsearch <-> logstash, kibana TCP port 9200
- Kibana, Zabbix Web <-> Ingress Controller, zewnętrzny kontroller do przekazywania ruchu z przegląarek. Pody nie mają powodu wysyłać żądań do graficznych interfejsów.


