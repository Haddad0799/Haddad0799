<div align="center">

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:161b22,100:1f2937&height=200&section=header&text=Lucas%20Haddad&fontSize=60&fontColor=58a6ff&animation=fadeIn&fontAlignY=38&desc=Backend%20Developer%20%7C%20Java%20%26%20Spring%20Boot&descAlignY=60&descColor=8b949e" />

</div>

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/lucas-haddad-backend-developer/)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:lucas.haddad0799@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Haddad0799)

</div>

---

## 👋 Sobre mim

Desenvolvedor Backend com foco em **Java** e **Spring Boot**, construindo sistemas que resolvem problemas reais de negócio.

Atualmente desenvolvendo o **QueenFitStyle**, uma plataforma de ERP integrada a e-commerce de moda fitness com arquitetura modular, fluxo de publicação orientado a eventos e separação clara entre operação interna e vitrine pública.

Meu objetivo é construir software que seja **consistente, rastreável e escalável** — onde cada decisão arquitetural tem motivo.

---

## 🛠️ Stack

<div align="center">

![Java](https://img.shields.io/badge/Java_21-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot_3-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)
![MinIO](https://img.shields.io/badge/MinIO-C72E49?style=for-the-badge&logo=minio&logoColor=white)
![Flyway](https://img.shields.io/badge/Flyway-CC0200?style=for-the-badge&logo=flyway&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)

</div>

<div align="center">

`Arquitetura Modular` • `Event-Driven` • `Clean Architecture` • `DDD` • `SOLID` • `REST APIs` • `JDBI` • `JUnit 5`

</div>

---

## 🚀 Projetos em Destaque

### 🛍️ QueenFitStyle — ERP + E-commerce Backend

> Monolito modular que resolve um problema real de e-commerce: manter ERP e vitrine sincronizados sem misturar responsabilidades.

O backend opera em dois contextos bem separados:

- **ERP (backoffice)** — cadastro de produtos, SKUs, imagens, preço, estoque e publicação
- **Storefront (loja)** — catálogo desnormalizado otimizado para leitura rápida, filtros e navegação

**Decisões arquiteturais relevantes:**

| Decisão | Motivação |
|---|---|
| Monolito modular (8 módulos) | Fronteiras de domínio claras sem a complexidade operacional de microsserviços |
| Write model separado do read model | ERP não é consultado diretamente pela loja — catálogo é um snapshot publicado |
| JDBI com SQL explícito | Controle total sobre queries críticas, sem ORM escondendo comportamento |
| Upload via pre-signed URL | Arquivo nunca trafega pelo backend; escala sem custo de I/O |
| Eventos de aplicação para sincronização | Desacoplamento entre publicação de produto e atualização do catálogo |
| Revalidação por tags no Next.js | Frontend invalida cache seletivamente após publicação ou despublicação |

**Fluxo de publicação:**

```
Produto criado → SKUs + Imagens + Preço + Estoque
      ↓
Avaliação de completude (EvaluateSkuCompletenessUseCase)
      ↓
Publicação manual → SnapshotAssembler monta retrato completo
      ↓
Evento → CatalogSyncService atualiza read model
      ↓
Webhook → Next.js revalida cache por tags
```

**Lógica de vitrine baseada na imagem principal:**

A `mainImageUrl` define a `mainColor` → o SKU vendável mais barato dessa cor vira a `showcaseSelection` → esse preço é exibido na listagem. Com filtros ativos (cor, tamanho, faixa de preço), a API calcula uma `effectiveSelection` em tempo real — se não há SKU compatível, o produto não aparece no resultado.

**Módulos:**

```
queenfitstyle-project/
├── app/          # Bootstrap Spring Boot, config global e exception handler
├── attribute/    # Categorias (árvore), cores e tamanhos
├── product/      # Núcleo ERP: produtos, SKUs, imagens, importação, IA
├── inventory/    # Estoque, reservas e movimentações
├── pricing/      # Precificação de SKUs
├── catalog/      # Read model da loja (snapshot desnormalizado)
├── storage/      # Integração MinIO/S3 com pre-signed URLs
└── shared/       # Código comum + migrações Flyway (33 versões)
```

**Stack:** Java 21 · Spring Boot 3.3 · PostgreSQL · JDBI · Flyway · MinIO · OpenAI API · Docker Compose · JUnit 5 · Testcontainers

🔗 [Backend](https://github.com/Haddad0799/QUEENFITSTYLE-ERP-STORE-BACKEND) · [ERP UI](https://github.com/Haddad0799/QUEENFITSTYLE-ERP-UI) · [Store UI](https://github.com/Haddad0799/QUEENFITSTYLE-STORE-UI)

---

### 💸 PayFlow — Sistema Distribuído com Mensageria

> Plataforma de pagamentos baseada em microsserviços com comunicação assíncrona via RabbitMQ.

**Conceitos aplicados:**
- Microsserviços com responsabilidades isoladas
- RabbitMQ com Dead Letter Queue (DLQ), Dead Letter Exchange (DLX) e retry automático
- Event-Driven Architecture para desacoplamento entre serviços
- Containerização completa com Docker

🔗 [Ver projeto](https://github.com/Haddad0799/Payflow)

---

### 🏥 Voll Med API — Clínica Médica REST

> API REST para gerenciamento de consultas médicas com autenticação stateless.

**Conceitos aplicados:**
- Autenticação JWT com Spring Security
- Regras de negócio com validações de agendamento
- Testes unitários com JUnit 5
- Versionamento de banco com Flyway

🔗 [Ver projeto](https://github.com/Haddad0799/VollMedApi)

---

## 📊 Estatísticas

<div align="center">

<img height="180em" src="https://github-profile-summary-cards.vercel.app/api/cards/stats?username=Haddad0799&theme=github_dark"/>
<img height="180em" src="https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username=Haddad0799&theme=github_dark"/>

</div>

<div align="center">

[![GitHub Streak](https://streak-stats.demolab.com?user=Haddad0799&theme=github-dark-blue&hide_border=true&background=0d1117&ring=58a6ff&fire=58a6ff&currStreakLabel=58a6ff)](https://git.io/streak-stats)

</div>

<div align="center">

![](https://komarev.com/ghpvc/?username=Haddad0799&color=58a6ff&style=for-the-badge&label=VISUALIZAÇÕES+DO+PERFIL)

</div>

---

## 🎓 Formação

🎓 **Bacharelado em Engenharia de Software** — UniCesumar · 2023–2027 (em andamento)

---

<div align="center">

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:1f2937,50:161b22,100:0d1117&height=120&section=footer"/>

</div>
