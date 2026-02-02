# Instalação do Elastic Stack (Docker)

Este documento descreve o processo de instalação do **Elastic Stack (Elasticsearch + Kibana)** utilizando **Docker e Docker Compose**, conforme implementado neste laboratório SOC.

O objetivo é disponibilizar um **SIEM funcional**, com autenticação habilitada, pronto para ingestão de logs e criação de regras de detecção.

---

## 📌 Pré-requisitos

- Sistema operacional Linux
- Docker instalado
- Docker Compose instalado
- Acesso root ou usuário com permissão sudo
- Porta **9200** (Elasticsearch) e **5601** (Kibana) livres

---

## 📁 Estrutura utilizada

O Elastic Stack foi instalado no seguinte diretório:

```
/opt/elk-stack
```

### 1️⃣ Criação do diretório de instalação
```
mkdir -p /opt/elk-stack
cd /opt/elk-stack
```

### 2️⃣ Criação do arquivo docker-compose.yml

Foi criado um arquivo chamado docker-compose.yml contendo os serviços:

- setup: inicialização e configuração de senhas

- elasticsearch: motor de busca e SIEM

- kibana: interface gráfica e gestão de alertas

- O Elastic Stack está configurado em single-node, adequado para ambiente de laboratório.

**Observação:**
O uso do container setup garante que as senhas do Elasticsearch e do Kibana sejam configuradas automaticamente durante o primeiro start.


### 3️⃣ Criação do arquivo de variáveis (.env)

Para evitar hardcode de credenciais no docker-compose.yml, foi criado um arquivo .env com as senhas:
```
ELASTIC_PASSWORD=senha_do_elastic
KIBANA_PASSWORD=senha_do_kibana
```

Essas variáveis são utilizadas tanto pelo Elasticsearch quanto pelo Kibana.


### 4️⃣ Subida dos containers

Com os arquivos criados, os containers foram iniciados com o comando:

```docker compose up -d```


Após alguns minutos, os serviços ficam disponíveis nas portas configuradas.



### 5️⃣ Ajuste de criptografia do Kibana

O Kibana exige chaves de criptografia para funcionamento correto de recursos como:

- Saved Objects

- Alertas

- Actions

**5.1** Identificar o container do Kibana
```docker ps```

Anotar o ID do container com nome kibana.


**5.2** Gerar as chaves de criptografia
```docker exec -it <ID_KIBANA> /bin/kibana-encryption-keys generate```


Esse comando gera automaticamente as chaves necessárias.


**5.3** Aplicar as chaves no Kibana

As chaves geradas foram adicionadas ao arquivo de configuração do Kibana via execução direta no container:
```
docker exec -it <ID_KIBANA> /bin/bash -c "echo '
xpack.encryptedSavedObjects.encryptionKey: <CHAVE_GERADA>
xpack.reporting.encryptionKey: <CHAVE_GERADA>
xpack.security.encryptionKey: <CHAVE_GERADA>
' >> /usr/share/kibana/config/kibana.yml"
```

Após isso, o container do Kibana deve ser reiniciado:

docker restart <ID_KIBANA>



### 6️⃣ Validação do ambiente

- Elasticsearch:
```
http://IP_DA_VM:9200
```

- Kibana:
```
http://IP_DA_VM:5601
```

Login realizado com o usuário elastic e a senha definida no arquivo .env.
