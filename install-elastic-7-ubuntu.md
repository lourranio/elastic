# Instalando Elasticsearch 7

## BAIXAR 

Depois de logar no Ubuntu Server, execute os seguintes comandos:

    wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
     
    sudo apt-get install apt-transport-https
     
    echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" |

    sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
     
    sudo apt-get update && sudo apt-get install elasticsearch

## CONFIGURACAO 

Agora, altere as configurações usando o vi:

    sudo vi /etc/elasticsearch/elasticsearch.yml

Remova o comentário (#) da linha node.nome, para isso coloque o vi em modo de inserção teclando i

Altere network.host para 0.0.0.0

Altere discovery.seed.hosts para [“127.0.0.1”]

E cluster.initial_master_nodes para [“node-1”]

Quando terminar, tecle ESC para sair do modo de inserção, então digite :wq para salvar e sair do vi.

Execute os comandos abaixo para iniciar o Elasticsearch e para configurar a inicialização automática.

    sudo /bin/systemctl daemon-reload
    sudo /bin/systemctl enable elasticsearch.service
    sudo /bin/systemctl start elasticsearch.service


O elastic search demora um pouco a levantar. Analise os logs. 
Pode ser que demore uns 5 min pra subir dependendo do seu hardware.


## TESTES

Em linha de comando:

    curl -XGET 127.0.0.1:9200
