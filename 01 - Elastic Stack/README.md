# Elastic Stack (SIEM)

## 📌 Visão Geral
O **Elastic Stack** atua como o **SIEM central** deste laboratório SOC, sendo responsável por:

- Coleta e indexação de logs
- Normalização de eventos de segurança
- Criação de regras de detecção
- Geração de alertas acionáveis
- Integração com o SOAR (Shuffle)

Neste lab, o Elastic simula o papel de um SIEM corporativo operando em um ambiente realista, porém controlado.

---

## 🎯 Papel do Elastic no SOC
No contexto de um SOC, o Elastic Stack é responsável por:

- Centralizar logs de sistemas Linux
- Identificar padrões suspeitos (ex: brute force, falhas de autenticação)
- Correlacionar eventos de segurança
- Disparar alertas para automação de resposta

Arquiteturalmente, ele é o **ponto de origem de alertas** que alimentam o SOAR.

---

## 🧱 Componentes Utilizados
Este lab utiliza os seguintes componentes do Elastic Stack:

- **Elasticsearch**
  - Armazenamento e indexação dos logs
  - Execução das regras de detecção
- **Kibana**
  - Visualização dos dados
  - Interface SIEM
  - Criação e gerenciamento de alertas

A stack roda em **uma VM dedicada**, utilizando Docker.

---

## 🔐 Segurança e Autenticação
- Autenticação habilitada (`xpack.security.enabled`)
- Usuários utilizados:
  - `elastic` → administração
  - `kibana_system` → comunicação Kibana ↔ Elasticsearch
- SSL desabilitado **apenas para fins de laboratório**
  - Em produção, SSL seria obrigatório

Essas decisões estão documentadas para deixar claro o **trade-off entre segurança e simplicidade em ambiente de estudo**.

---

## ⚙️ Configurações Versionadas
As configurações principais estão versionadas na pasta:

```
configs/
├── docker-compose.yml.md
```

---

## 🚨 Detecção de Incidentes
As **regras de detecção** não ficam nesta pasta.

Elas estão centralizadas em:
```
06-detections-and-response/
```

---

## 🔁 Integração com SOAR
O Elastic Stack envia alertas para o **Shuffle (SOAR)**, que é responsável por:

- Enriquecimento do alerta
- Abertura de incidente
- Orquestração de resposta
- Integração com DFIR-IRIS

A documentação dessa integração está disponível em:
```
05-integrations/
```

---

## 🧪 Objetivo no Lab
Dentro deste laboratório, o Elastic Stack é usado para:

- Validar ataques simulados
- Detectar comportamentos anômalos
- Servir como base para automações de resposta
- Demonstrar operação real de um SIEM

Este não é um ambiente de aprendizado teórico, mas sim um **SIEM funcional**, operado como em um SOC real.

---

## 📌 Observações Importantes
- Ambiente single-node
- Não recomendado para produção
- Foco total em prática defensiva
- Estrutura preparada para expansão futura (beats, agents, novos índices)

---