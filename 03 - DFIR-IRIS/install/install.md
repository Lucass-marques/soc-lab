# 🚀 Instalação do DFIR-IRIS


## 1️⃣ Clonando o Repositório

Navegue até o diretório /opt e clone o repositório oficial do DFIR-IRIS:
```
cd /opt
git clone https://github.com/dfir-iris/iris-web.git
cd iris-web
```

--- 

## 2️⃣ Configurando a Versão

Para garantir estabilidade, recomenda-se utilizar uma versão específica do DFIR-IRIS.

No exemplo abaixo, utilizei a versão v2.4.11:
```
git checkout v2.4.11
```

⚠️ Você pode consultar as versões disponíveis no GitHub do projeto e ajustar conforme necessário.

---

## 3️⃣ Configurando o Ambiente

Crie o arquivo de variáveis de ambiente a partir do modelo:
```
cp .env.model .env
```

Edite o arquivo .env conforme o seu ambiente, ajustando principalmente:

- Portas expostas

- Credenciais padrão

- Configurações de banco de dados

- URLs de acesso

- Exemplo de edição:

- nano .env

## 4️⃣ Construindo e Inicializando os Contêineres

Com o ambiente configurado, execute os comandos abaixo:
```
docker compose build
docker compose up -d
```

Esse processo irá:

- Construir as imagens necessárias

- Inicializar os contêineres do DFIR-IRIS

- Subir a aplicação em segundo plano (modo daemon)

## 5️⃣ Verificando o Status

Para verificar se os contêineres estão em execução:
```
docker compose ps
```

Todos os serviços devem estar com status Up.

## 6️⃣ Acessando o DFIR-IRIS

Após a inicialização, acesse a interface web pelo navegador:
```
https://<IP_DA_VM>:2443
```

🔎 A porta padrão é **2443**, mas pode variar conforme o arquivo .env.

Caso utilize HTTPS com certificado próprio ou proxy reverso, ajuste conforme sua infraestrutura.

## 🔔 Integrações e Notificações

O DFIR-IRIS pode ser integrado com outras ferramentas do seu SOAR, incluindo:

- Elastic Stack

- Shuffle

- APIs de IA para análise de incidentes

- Webhooks (ex: Discord, Slack, etc.)

Essas integrações são normalmente configuradas após a instalação, via interface web ou automações externas.