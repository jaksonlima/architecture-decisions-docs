# RFC-001 - Adoção de Kafka para Comunicação entre Microserviços

- **Autor:** Jakson Lima
- **Data:** 02/06/2025
- **Status:** Em Discussão <!-- (ou Aprovado / Rejeitado) -->

## 1. Contexto
Atualmente, nossos microserviços se comunicam via REST síncrono. Temos enfrentado problemas de escalabilidade, alta latência e falhas em cascata.

## 2. Problema
- Alto acoplamento entre serviços.
- Dependência da disponibilidade do serviço remoto.
- Crescimento da latência em horários de pico.

## 3. Proposta
Adotar o Apache Kafka como solução de mensageria assíncrona para:
- Desacoplar serviços.
- Melhorar a resiliência e escalabilidade.
- Permitir comunicação assíncrona baseada em eventos.

## 4. Alternativas Consideradas
- **RabbitMQ:** Mais simples, porém menos escalável para nosso caso.
- **Google Pub/Sub:** Solução gerenciada, porém aumenta dependência externa.
- **Manter REST:** Não resolve os problemas atuais.

## 5. Impacto
- **Curto prazo:** Aumento na complexidade de desenvolvimento e operações.
- **Médio/longo prazo:** Maior resiliência, escalabilidade e capacidade de evoluir a arquitetura para Event-Driven.

## 6. Plano de Ação
- Criar uma POC utilizando Kafka.
- Capacitar o time na utilização e operação do Kafka.
- Migrar gradualmente as integrações críticas.

## 7. Feedback e Discussões
Aberto para sugestões até **10/06/2025**.

---
