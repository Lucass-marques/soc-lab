# Visão Geral da Arquitetura do SOC

Este documento descreve a arquitetura do **Laboratório SOC Open Source com SIEM, SOAR e DFIR**, desenvolvido para simular o funcionamento de um **Security Operations Center (SOC) real**, utilizando apenas ferramentas open source.

O foco do projeto é demonstrar **conhecimento prático**, fluxo operacional e integração entre tecnologias defensivas.

---

## Arquitetura em Alto Nível

O laboratório é composto por **quatro máquinas virtuais independentes**, cada uma com uma responsabilidade clara dentro do SOC.  
Essa abordagem reflete ambientes corporativos reais, onde ferramentas críticas não compartilham o mesmo host.

---

## Componentes da Arquitetura

### VM 1 – Elastic Stack (SIEM)
**Responsabilidade:** Detecção e Correlação de Eventos de Segurança

- Coleta centralizada de logs
- Correlação de eventos
- Criação de alertas de segurança
- Visualização e análise de dados

O Elastic Stack atua como o **coração do SOC**, sendo responsável por identificar comportamentos suspeitos e gerar alertas acionáveis.

---

### VM 2 – Shuffle (SOAR)
**Responsabilidade:** Orquestração e Automação de Resposta

- Recebimento de alertas do SIEM
- Execução de playbooks automatizados
- Enriquecimento de eventos
- Integração com ferramentas externas

O Shuffle simula o papel de um **SOAR corporativo**, reduzindo tarefas manuais e acelerando o tempo de resposta.

---

### VM 3 – Ollama (IA Local)
**Responsabilidade:** Análise Assistida por Inteligência Artificial

- Análise contextual de alertas
- Apoio à triagem inicial
- Classificação de severidade
- Explicação de eventos suspeitos

A utilização de IA local elimina dependência de serviços em nuvem e simula ambientes SOC com **enriquecimento inteligente interno**.

---

### VM 4 – DFIR-IRIS (Resposta a Incidentes)
**Responsabilidade:** Gerenciamento e Investigação de Incidentes

- Criação e gestão de incidentes
- Linha do tempo (timeline)
- Organização de evidências
- Suporte à resposta a incidentes

O DFIR-IRIS representa o sistema de **Incident Response**, onde os alertas se tornam incidentes reais para investigação.

---

## Fluxo Operacional do SOC

1. Eventos e logs são gerados pelos sistemas monitorados
2. O Elastic Stack ingere e correlaciona os dados
3. Alertas de segurança são criados
4. O Shuffle recebe os alertas
5. Playbooks automatizados são executados:
   - Enriquecimento com IA (Ollama)
   - Criação de incidente no DFIR-IRIS
6. O analista SOC investiga e responde ao incidente
7. Notificações são enviadas para canais externos (ex: Discord)

---

## Princípios Utilizados

- Separação de responsabilidades
- Arquitetura modular
- Automação de processos
- Boas práticas de SOC
- Foco defensivo (Blue Team)

---

Esta arquitetura foi projetada para **simular um SOC real**, servindo como ambiente de estudo, prática e demonstração de competências técnicas para vagas de **Analista SOC Júnior**.

