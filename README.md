# 👋 Olá, eu sou o Lucas Haddad

## 🎯 Desenvolvedor Back-end | Java & Spring | Arquitetura de Software  
Desenvolvedor Back-end com foco em Java e Spring, voltado à criação de soluções **escaláveis, robustas e alinhadas às melhores práticas do mercado**.  
Em busca da **primeira oportunidade profissional**, trago experiência prática em projetos autorais e um histórico de disciplina, resiliência e trabalho em equipe, adquirido ao longo de cinco anos no Exército Brasileiro.

---

### 🛠 Habilidades Técnicas  
**Linguagens:** Java · SQL · TypeScript  
**Frameworks:** Spring Boot · Spring Security · Spring Data · Spring Cloud · HATEOAS · Angular  
**Arquiteturas & Padrões:** Microsserviços · APIs REST · Mensageria Assíncrona (RabbitMQ) · Clean Architecture · DDD · SOLID  
**Infraestrutura:** Docker · Docker Compose · Eureka · API Gateway · CI/CD  
**Banco de Dados:** MySQL · PostgreSQL  
**Cloud:** AWS (CDK, CloudFormation) · Google Cloud Platform (badges e projetos práticos)  
**Ferramentas:** Git · GitHub · Jira  
**Testes:** JUnit · Mockito

---

### 🌟 Diferenciais Profissionais  
- **Disciplina & Liderança:** Atuação como instrutor no Exército, com foco em treinamento técnico, logística e desenvolvimento de equipes.  
- **Execução & Autonomia:** Desenvolvimento completo de projetos, desde a arquitetura até a entrega, com documentação detalhada e aplicação de boas práticas.  
- **Comunicação Objetiva:** Facilidade em traduzir demandas complexas em soluções técnicas claras para diferentes públicos.  
- **Aprendizado Contínuo:** Estudo sistemático de novas tecnologias e tendências, com aplicação direta em projetos e laboratórios pessoais.

---

### 🎓 Formação Acadêmica  
**UniCesumar – Bacharelado em Engenharia de Software**  
Fev/2023 – Fev/2027 (em andamento)  
Instituição com nota máxima no MEC, referência em tecnologia. Durante a formação, desenvolvi competências sólidas em planejamento, construção e gestão de sistemas computacionais completos, seguros e de alta qualidade, utilizando Java, inteligência artificial e metodologias atuais de engenharia de software.

---

### 📂 Projetos Principais 

QueenFitStyle ERP (out/2025 – atual)
ERP Modular Monolith para gestão completa de catálogo e estoque de um e-commerce de roupas de academia feminina.

🔹 **Stack**: Java 21 · Spring Boot 3 · Spring Data JPA · MySQL · Maven · AWS S3 (ou MinIO local)
🔹 **Arquitetura**: Hexagonal (Ports & Adapters) + Clean Architecture + DDD
🔹 **Princípio**: Monolith First — modularização interna antes da divisão em microsserviços.

🧱 **Destaques Técnicos:**
- Estrutura modular isolando contextos de catálogo, estoque, importação e armazenamento.  
- **Arquitetura Hexagonal (Ports & Adapters)** com domínio independente de frameworks.  
- **Processamento em lote (batch)** e queries otimizadas para importação de produtos e SKUs.  
- **Upload de imagens via Pre-signed URLs (minIO(Pronto para migrar para buckets aws, gcp ou azure))**, reduzindo carga no backend.  
- Aplicação prática de **DDD** com entidades, agregados e value objects ricos.  
- Separação rigorosa entre **domínio, aplicação e infraestrutura**, com baixo acoplamento.  

📂 **Módulos Principais:**
1. **App Module** – inicialização e orquestração dos módulos internos.  
2. **Catalog Module** – gerenciamento de produtos, SKUs, categorias, cores e imagens.  
3. **Import Module** – importação em massa de produtos e SKUs via Excel, com validação e processamento em lote.  
4. **Storage Module** – upload de imagens com pre-signed URLs e abstração de storage (S3/MinIO).  

⚙️ **Otimizações:**
- Inserções em lote com hibernate
- Evita N+1 problems via fetch joins e consultas customizadas.  
- Upload direto no bucket, armazenando apenas metadados no banco.  

GitHub → [Haddad0799/queenfitstyle-erp](https://github.com/Haddad0799/queenfitstyle-erp)



**PayFlow** (mai/2025 – jun/2025)  
Sistema back-end baseado em microsserviços com Java 17 e Spring Boot 3. Comunica serviços via RabbitMQ (pedidos e pagamentos) para garantir desacoplamento, resiliência e escalabilidade.  
Infraestrutura automatizada via Docker & Docker Compose, registro de serviços com Eureka, roteamento com Spring Cloud Gateway. Projeto para aprofundar arquitetura distribuída, mensageria, design de APIs e infraestrutura como código.  
[GitHub → Haddad0799/PayFlow](https://github.com/Haddad0799/Payflow)

**Voll Med API**  
API completa para agendamento de consultas médicas, construída com Java e Spring Boot. Autenticação e autorização via JWT e Spring Security, controle granular de permissions por roles. Validações de regras de negócio usando Strategy Pattern (princípio Open/Closed), testes unitários com JUnit & Mockito, versionamento de banco via Flyway (MySQL). Projeto voltado ao reforço de boas práticas de design, alta coesão e baixo acoplamento.  
[GitHub → Haddad0799/VollMedApi](https://github.com/Haddad0799/VollMedApi)

---

### 📫 Como me encontrar  
- ✉️ Email: lucas.haddad0799@gmail.com  
- 💼 GitHub: [github.com/Haddad0799](https://github.com/Haddad0799)  
- 🔗 LinkedIn: https://www.linkedin.com/in/lucas-haddad-aa7a0b28a

---


