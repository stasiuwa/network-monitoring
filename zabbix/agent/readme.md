Kontner opiera się na gotowym oficjalnym obrazie. Plik konfiguracyjny określa port nasłuchiwania oraz adres, z racji ze agent działa w tej samej sieci co zabbix serwer to adres wskazuje na localhosta.

Analiza Docker Scout wykryła podatności w liczbie apline/agent
- Critical: 0/0
- High: 2/2
- Medium: 2/5
- Low: 1/0

Podatności odnośnie obrazu alpine śa identyczne jak w przypadku zabbix-web. Podatności związane stricte z zabbix-agent odnoszą się do SSH, z którego agent nie korzysta oraz certyfikatów TLS które nie są udostępnione publicznie.