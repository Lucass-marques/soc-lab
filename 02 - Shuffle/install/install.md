# Instalação do Shuffle

Este documento descreve o processo de instalação do **Shuffle SOAR** utilizando **Docker Compose**, conforme utilizado neste laboratório de SOC.

---

## 1️⃣ Clonando o Repositório

Navegue até o diretório onde o Shuffle será instalado (recomendado: `/opt`) e clone o repositório oficial:

```
cd /opt
git clone https://github.com/Shuffle/Shuffle
```

Após a clonagem, entre no diretório do Shuffle:
```
cd Shuffle
```
---

## 2️⃣ Ajustando Permissões dos Diretórios

O Shuffle utiliza um banco de dados baseado em OpenSearch (Elasticsearch) e requer permissões adequadas para escrita em disco.

Crie o diretório de dados e ajuste as permissões:
```
mkdir shuffle-database && sudo chown -R 1000:1000 shuffle-database
```
O valor 1000:1000 refere-se ao UID e GID padrão utilizados pelo Docker.
Caso seu ambiente utilize IDs diferentes, ajuste conforme necessário.

Essa etapa é essencial para evitar erros de permissão durante a inicialização dos containers.

---

## 3️⃣ Iniciando o Docker Compose

Com as permissões ajustadas, inicie os serviços definidos no arquivo docker-compose.yml:
```
docker compose up -d
```
O parâmetro -d executa os containers em modo daemon, permitindo que o Shuffle rode em segundo plano enquanto o sistema continua disponível para outras tarefas.

---

## 4️⃣ Verificando o Status dos Containers

Após a inicialização, verifique se todos os serviços estão rodando corretamente:
```
docker compose ps
```
---

Esse comando lista os containers ativos e seus respectivos status, permitindo confirmar que o Shuffle e seus componentes foram iniciados com sucesso.

## 5️⃣  Acessando o Shuffle

Com os containers em execução, acesse a interface web do Shuffle pelo navegador.

O endereço e a porta são definidos no docker-compose.yml.
Na maioria dos casos, o acesso será feito via:
```
https://<IP_DA_MÁQUINA>:3443
```
Caso a porta tenha sido alterada, utilize a porta configurada no seu ambiente.

---

## 6️⃣ Configuração Adicional

Dependendo do ambiente e dos objetivos do laboratório, podem ser necessários ajustes adicionais, como:

- Alteração de portas

- Configuração de variáveis de ambiente

- Ajustes de volumes persistentes

- Integração com Elastic Stack

- Configuração de autenticação e segurança

### Observações Importantes

- O Shuffle não deve ser exposto diretamente à internet em ambientes produtivos

- Utilize redes internas ou VPNs para acesso

- Proteja credenciais e variáveis sensíveis

- Monitore logs para troubleshooting

Este Shuffle faz parte de um laboratório educacional e técnico, com foco em automação de resposta, SOC e Blue Team.