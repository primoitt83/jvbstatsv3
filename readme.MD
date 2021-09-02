# Stack de monitoração Jitsi com grafana, influxDB e telegraf

# Introdução

Este repositório contém arquivos necessários para estabelecimento de uma pilha docker para coleta, armazenamento e exibição de dados estatísticos do Jitsi Videobridge

## Instalação

1. Ajuste a instação conforme seu ambiente editando o arquivo de
 configuração jitsi-stats.conf

Amostra do arquivo de configuração:

```
CONFIG_PASTA=./config
RESTART_POLICY=unless-stopped
INFLUXDB_PORTA=8086
INFLUXDB=jitsi
GRAFANA_PORTA=3000
JITSI_HOST=servidor_jitsi
ENDERECO_SRV_JITSIBRIDGE=localhost
PORTA_API_REST=8081

```

2. Execute o script de instalação

```sh
./instalar
```

## Configuração

Após instalada a pilha de monitoração, configurar o grafana com o seguinte passo a passo:

1. Acessar a interface web do grafana no endereço e porta configurados (ex: localhost:3000)
2. Logar com as credenciais padrão onde usuário/senha é admin/admin
3. Configurar nova senha
1. Adicionar nova fonte de dados em Configuration > Data Sources
  1. Clicar no botão 'Add data source'
  1. Digitar 'influxdb' e escolher a opção 'InfluxDB'
1. Configurar fonte de dados:
  1. Name: Jitsi (ou qualquer outro)
  1. URL: conforme definido no arq. de configuração. Ex: http://influxdb:8086
  1. Database: jitsi
  1. Pressionar o botão 'Save & Test' (confirmar sucesso)
8. Configurar Dashboard em + > Create > Import
  1. Digitar a ID do Dashboard jitsi, 11969, e clicar em 'Load'
  1. Em 'InfluxDB' selecione a fonte de dados configurada no passo anterior
  1. Pressionar o botão Import

![](https://grafana.com/api/dashboards/11969/images/7787/image)

## Referências

* [Jitsi Metricsby mephisto](https://grafana.com/grafana/dashboards/11969)
* [How-to to setup Grafana dashboards to monitor Jitsi, my comprehensive tutorial for the beginner](https://community.jitsi.org/t/how-to-to-setup-grafana-dashboards-to-monitor-jitsi-my-comprehensive-tutorial-for-the-beginner/38696)

## Limitações

Testado no Ubuntu 18.04

## Autor

Antonio Alisio de Meneses Cordeiro (alisio.cordeiro@serpro.gov.br)
