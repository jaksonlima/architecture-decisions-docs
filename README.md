# Documentação de Decisões Técnicas e Arquitetura

Este repositório contém:

- 📄 **RFC** (Request for Comments) – *Discussões abertas sobre propostas de melhorias, mudanças técnicas ou novas funcionalidades. Aqui ocorre a colaboração antes de qualquer decisão.*
- 🏛️ **ADR** (Architecture Decision Record) – *Registra decisões arquiteturais tomadas. É o que ficou decidido após as discussões das RFCs.*
- 🏗️ **System Design** – *Documenta o projeto técnico de sistemas, descrevendo arquitetura, componentes, integrações, segurança e escalabilidade.*

---

<details>
<summary><strong>📄 RFC-001 - Adoção de Kafka para Comunicação entre Microserviços</strong></summary>

### Autor
Jakson Lima

### Data
02/06/2025

### Status
Em Discussão

### 1. Contexto
Atualmente, nossos microserviços se comunicam via REST síncrono. Temos enfrentado problemas de escalabilidade, alta latência e falhas em cascata.

### 2. Problema
- Alto acoplamento entre serviços.
- Dependência da disponibilidade do serviço remoto.
- Crescimento da latência em horários de pico.

### 3. Proposta
Adotar o Apache Kafka como solução de mensageria assíncrona para:
- Desacoplar serviços.
- Melhorar a resiliência e escalabilidade.
- Permitir comunicação assíncrona baseada em eventos.

### 4. Alternativas Consideradas
- **RabbitMQ:** Mais simples, porém menos escalável.
- **Google Pub/Sub:** Solução gerenciada, porém aumenta dependência externa.
- **Manter REST:** Não resolve os problemas atuais.

### 5. Impacto
- Curto prazo: aumento na complexidade.
- Longo prazo: maior resiliência e escalabilidade.

### 6. Plano de Ação
- Criar POC.
- Capacitar o time.
- Migrar gradualmente.

### 7. Feedback e Discussões
Aberto até 10/06/2025.

</details>

---

<details>
<summary><strong>🏛️ ADR-005 - Adoção de Kafka como Broker de Mensageria</strong></summary>

### Data
12/06/2025

### Status
Aceito

### 1. Contexto
Durante a RFC-001, discutimos a necessidade de melhorar a comunicação entre microserviços.

### 2. Decisão
Adotamos o **Apache Kafka** como broker de mensageria para comunicação assíncrona.

### 3. Motivação
- Resolver problemas de acoplamento e resiliência.
- Suportar picos de carga.
- Evoluir para Event-Driven.

### 4. Alternativas Consideradas
- Manter REST.
- Usar RabbitMQ.
- Usar Google Pub/Sub.

### 5. Consequências

**Positivas**
- Maior escalabilidade e resiliência.
- Desacoplamento dos serviços.

**Negativas**
- Aumento da complexidade operacional.
- Curva de aprendizado.
- Necessidade de observabilidade mais robusta.

</details>

---

<details>
<summary><strong>🏗️ System Design - Serviço de Processamento de Pagamentos</strong></summary>

### Autor
Jakson Lima

### Data
02/06/2025

### Status
Em desenvolvimento

---

### 1. Contexto
Precisamos de um serviço escalável, seguro e resiliente para processar pagamentos de nossos clientes, garantindo alta disponibilidade e integridade das transações.

---

### 2. Objetivos
- Processar pagamentos com baixa latência.
- Garantir consistência e integridade financeira.
- Suportar picos de até 500 transações por segundo.
- Oferecer observabilidade e capacidade de auditoria.

---

### 3. Escopo
- Processamento de pagamentos via cartão, boleto e PIX.
- Integração com gateways externos (ex.: Stripe, Adyen, bancos locais).
- Geração de relatórios financeiros.
- APIs para os times de backoffice e produtos.

---

### 4. Arquitetura de Alto Nível

