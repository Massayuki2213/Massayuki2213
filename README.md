# Guilherme Massayuki

**Desenvolvedor Backend** — Java · Spring Boot · Node.js · NestJS · PostgreSQL · Docker

Construo backend que roda em operação real. Hoje sou Líder de TI numa distribuidora de hortifrúti, onde desenvolvi uma plataforma B2B de pedidos integrada ao ERP legado da empresa. Em paralelo, minha pesquisa de TCC compara performance de arquiteturas monolíticas e de microsserviços sob carga, com validação estatística.

9º semestre de Engenharia de Computação — Centro Universitário FACENS.

<p align="left">
  <a href="https://linkedin.com/in/guilherme-massayuki">
    <img src="https://img.shields.io/badge/LinkedIn-guilherme--massayuki-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" />
  </a>
  <a href="mailto:gmoraes806@gmail.com">
    <img src="https://img.shields.io/badge/Email-gmoraes806@gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white" />
  </a>
</p>

---

## Projetos em destaque

### Central de Pedidos — plataforma B2B para distribuidora de hortifrúti

> `Java` `Spring Boot 3.4` `JPA` `Flyway` `PostgreSQL` `React` `Vite` `TypeScript` `PWA` `Docker` `Keycloak` `MinIO` `Caddy` `Prometheus` `Sentry` `Testcontainers`

Mercados, feirantes e restaurantes montam pedidos pelo celular a partir de um catálogo com preço personalizado; a operação administra tudo num painel único. Monorepo com backend Spring Boot (19 services, 11 entidades, migrações Flyway V1→V7) e frontend React/Vite offline-first.

**Decisões técnicas que valem olhar:**

- **Integração com ERP legado sem acoplamento fatal** — datasource secundário read-only via `JdbcTemplate`, deliberadamente excluído do health check. O ERP fora do ar não derruba a aplicação.
- **Sincronização idempotente** — catálogo e preços reconciliados a cada 30 min por snapshot completo com upsert por código de produto. Nunca deleta, nunca sobrescreve preço especial por cliente, nunca apaga valor com `null`.
- **Padrão outbox para faturamento** — pedido confirmado entra numa outbox e é entregue por worker com retry, através de um sink desacoplado por interface. Trocar o destino não toca no fluxo.
- **PWA offline-first** — o carrinho sobrevive a refresh e à falta de internet.
- **Domínio modelado com cuidado** — máquina de estados do pedido com histórico, preço em cascata (cliente → loja → geral), quantidades fracionadas (1,5 kg).
- **Operação** — Actuator/Prometheus, logs JSON em produção, Sentry, CI no GitHub Actions e testes de integração com Testcontainers.

➡️ **[Ver repositório](LINK_DO_REPO)**

---

### Benchmarking de Persistência Poliglota: Monolito vs. Microsserviços

> `Node.js` `NestJS` `TypeScript` `PostgreSQL` `TypeORM` `MongoDB` `Mongoose` `Docker` `k6` `Prometheus` `Grafana`

Pesquisa aplicada (TCC, aprovada em banca em jun/2026): o mesmo Prontuário Eletrônico do Paciente implementado em duas arquiteturas para comparação controlada de performance.

- **Persistência poliglota** — PostgreSQL/TypeORM para dados relacionais, MongoDB/Mongoose para histórico clínico e laudos.
- **Observabilidade dupla** — Prometheus e Grafana medindo latência e throughput das duas arquiteturas em paralelo, com CPU e memória limitadas via Docker Compose para comparação justa.
- **Testes de carga em k6** — scripts simétricos com distribuição round-robin de usuários virtuais. Identifiquei o ponto de colapso de SLA do monolito em ~200 VUs.
- **Validação estatística** — ANOVA e teste Tukey HSD para comprovar a significância das diferenças, em vez de comparar médias no olho.
- **LGPD desde o schema** — AES-256, hash SHA-256 de CPF, metadados de consentimento e logs de auditoria append-only.

➡️ **[Ver repositório](LINK_DO_REPO)**

---

## Tecnologias

**Backend**

![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=for-the-badge&logo=nestjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)

**Dados**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![Hibernate](https://img.shields.io/badge/JPA%20%2F%20Hibernate-59666C?style=for-the-badge&logo=hibernate&logoColor=white)
![Flyway](https://img.shields.io/badge/Flyway-CC0200?style=for-the-badge&logo=flyway&logoColor=white)

**Infra e Observabilidade**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)
![Sentry](https://img.shields.io/badge/Sentry-362D59?style=for-the-badge&logo=sentry&logoColor=white)

**Segurança e Mensageria**

![Keycloak](https://img.shields.io/badge/Keycloak-4D4D4D?style=for-the-badge&logo=keycloak&logoColor=white)
![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?style=for-the-badge&logo=rabbitmq&logoColor=white)

**Frontend**

![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)

---

## Sobre mim

- Foco em **backend, APIs REST e sistemas distribuídos**
- Interesse particular em **performance, observabilidade e integração com sistemas legados** — o tipo de problema em que a resposta certa raramente é reescrever tudo
- Trabalho com **SOLID, Clean Code, Conventional Commits e code review**
- Inglês: **leitura técnica fluente**, conversação em evolução
- Aberto a oportunidades como Desenvolvedor Backend

---

⭐ Se algum projeto te foi útil, deixe uma estrela.
