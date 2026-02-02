# Shuffle

## Visão Geral

O **Shuffle** é uma plataforma **SOAR (Security Orchestration, Automation and Response)** open source, utilizada para automatizar respostas a incidentes de segurança, integrar ferramentas do SOC e padronizar fluxos operacionais.

Neste laboratório, o Shuffle atua como o **orquestrador central de resposta**, consumindo alertas (principalmente do Elastic Stack) e executando playbooks automatizados para investigação, enriquecimento e contenção de ameaças.

---

## Objetivo no Laboratório

O Shuffle é utilizado para:

- Automatizar respostas a alertas de segurança
- Orquestrar ações entre múltiplas ferramentas (Elastic, APIs externas, bloqueios, enriquecimento)
- Reduzir tempo de resposta a incidentes (MTTR)
- Simular um ambiente real de **SOC moderno com automação**
- Servir como base para testes de playbooks ofensivos e defensivos

---

## Integração com o Elastic Stack

No contexto deste lab:

- O **Elastic** é responsável por:
  - Coleta de logs
  - Detecção de eventos suspeitos
  - Geração de alertas

- O **Shuffle** é responsável por:
  - Receber alertas (Webhook / API)
  - Executar playbooks automatizados
  - Tomar decisões baseadas em lógica e contexto
  - Acionar respostas (ex: bloqueio, enriquecimento, notificação)

Essa separação reflete a arquitetura real de SOCs corporativos.