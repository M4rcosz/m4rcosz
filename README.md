<p align="center">
  <img src="./assets/header.svg" alt="Marcos, Backend Engineer" width="100%">
</p>

<p align="center">
  <a href="https://linkedin.com/in/m4rcosz"><img src="https://img.shields.io/badge/LINKEDIN-0D0D10?style=for-the-badge&logo=linkedin&logoColor=F2ECEC&labelColor=8B0000"></a>
  <img src="https://img.shields.io/badge/OPEN_TO_REMOTE-8B0000?style=for-the-badge&labelColor=8B0000">
  <img src="https://img.shields.io/badge/UTC−3-0D0D10?style=for-the-badge&labelColor=0D0D10">
</p>

I build backends meant for production, not for `localhost`: well-defined API contracts, data that stays consistent under concurrency, automated tests, and continuous delivery. At cVortex I turned manual support workflows into Python automations and worked on LLM integrations (Gemini API, RAG pipeline) that put me in direct contact with what an unreliable system actually costs the people using it.

> [!NOTE]
> Currently focused on backend services that treat LLMs as a dependency like any other: retries, cost awareness, and failure modes that don't take the request down with them.

<p align="center"><sub>†&nbsp;&nbsp;&nbsp;&nbsp;†&nbsp;&nbsp;&nbsp;&nbsp;†</sub></p>

<h2>&#8224; &nbsp;<i>I.</i> &nbsp;N E X I O<br><sub><sup>full-stack commerce platform</sup></sub></h2>

An e-commerce monorepo built from scratch, focused on the problems that only show up once money and concurrency are involved.

```mermaid
%%{init: {'theme':'base','themeVariables':{
  'primaryColor':'#0D0D10','primaryTextColor':'#EDE7E7','primaryBorderColor':'#B01030',
  'lineColor':'#8B0000','secondaryColor':'#000000','tertiaryColor':'#000000',
  'fontFamily':'Georgia, serif','clusterBkg':'#000000','clusterBorder':'#8B0000',
  'edgeLabelBackground':'#000000'
}}}%%
flowchart LR
    U([Client]) --> W["Next.js storefront<br/>i18n PT/EN"]
    W --> A

    subgraph API["nexio-core · NestJS"]
        direction TB
        A["Auth layer<br/>JWT + Argon2id + RBAC"] --> UC["Use cases<br/>application layer"]
        UC --> D["Domain<br/>entities · invariants"]
        UC --> R["Repositories<br/>Prisma"]
    end

    R --> DB[("PostgreSQL<br/>optimistic locking")]
    P{{"Payment provider"}} -.->|"at-least-once<br/>webhook"| IDK["Idempotency guard"]
    IDK --> UC

    style U fill:#000000,stroke:#B01030,color:#EDE7E7
    style DB fill:#000000,stroke:#B01030,color:#EDE7E7
    style P fill:#000000,stroke:#B01030,color:#EDE7E7
    style IDK fill:#8B0000,stroke:#B01030,color:#FFFFFF
```

<details>
<summary><b>&#8224; &nbsp;Engineering decisions worth defending</b></summary>
<br>

| | |
|---|---|
| **Idempotent webhooks** | Provider redelivery never double-charges |
| **Decimal-safe money** | No floating-point arithmetic anywhere on monetary values |
| **Optimistic locking** | Race conditions on stock and orders fail loudly, not silently |
| **Argon2id + JWT** | OWASP 2025 guidance, refresh tokens, role-based access |
| **Clean Architecture · DDD** | Domain isolated from framework and infrastructure |
| **Vitest + GitHub Actions** | Tests and CI gate every push |

</details>

> [!TIP]
> **The decision that taught me the most:** treating the payment webhook as *at-least-once* delivery instead of *exactly-once*. The idempotency key fixed the symptom. Understanding the provider's actual guarantee changed how I model every external integration since.

<p>
  <a href="https://github.com/M4rcosz/raizes-do-nordeste"><img src="https://img.shields.io/badge/BACKEND-0D0D10?style=flat-square&logo=nestjs&logoColor=F2ECEC&labelColor=8B0000"></a>
  <a href="https://github.com/M4rcosz/nexio-frontend"><img src="https://img.shields.io/badge/STOREFRONT-0D0D10?style=flat-square&logo=nextdotjs&logoColor=F2ECEC&labelColor=8B0000"></a>
  <a href="https://nexio-frontend-wheat.vercel.app"><img src="https://img.shields.io/badge/▶_LIVE_DEMO-B01030?style=flat-square&labelColor=B01030"></a>
</p>

<p align="center"><sub>†&nbsp;&nbsp;&nbsp;&nbsp;†&nbsp;&nbsp;&nbsp;&nbsp;†</sub></p>

<h2>&#8224; &nbsp;<i>II.</i> &nbsp;S U P P O R T &nbsp; A U T O M A T I O N &nbsp; &amp; &nbsp; L L M<br><sub><sup>cVortex</sup></sub></h2>

Python automations that removed recurring manual work from the support team (data extraction, reporting, ticket triage), saving hours per month. I also worked on Gemini API integrations and a RAG pipeline over our internal knowledge base: chunking and retrieval strategy, prompt structure, and handling the cases where the model returns nothing useful.

<sub>`Proprietary code`. Happy to walk through the architecture and trade-offs in a conversation.</sub>

<p align="center"><sub>†&nbsp;&nbsp;&nbsp;&nbsp;†&nbsp;&nbsp;&nbsp;&nbsp;†</sub></p>

<h2>&#8224; &nbsp;<i>III.</i> &nbsp;T O - D O &nbsp; A P P<br><sub><sup>FastAPI + React</sup></sub></h2>

First complete full-stack project. FastAPI backend with SQLAlchemy and a layered architecture, React frontend with React Query and optimistic updates, Vitest tests, fully containerized with Docker Compose.

<p>
  <a href="https://github.com/M4rcosz/YOUR-REPO"><img src="https://img.shields.io/badge/REPOSITORY-0D0D10?style=flat-square&logo=github&logoColor=F2ECEC&labelColor=8B0000"></a>
</p>

<p align="center"><sub>†&nbsp;&nbsp;&nbsp;&nbsp;†&nbsp;&nbsp;&nbsp;&nbsp;†</sub></p>

<h2>&#8224; &nbsp;<i>IV.</i> &nbsp;A R S E N A L</h2>

| | |
|:--|:--|
| **Backend** | Node.js · NestJS · TypeScript · Python · FastAPI · REST |
| **Data** | PostgreSQL · Prisma · MongoDB · relational modeling · migrations |
| **AI** | Gemini API · RAG pipelines · prompt design for production use |
| **Infra** | Docker · Compose · GitHub Actions · Linux (WSL2) · Git · Postman |
| **Frontend** | React · Next.js · Tailwind |

<details>
<summary><b>&#8224; &nbsp;Building next</b></summary>
<br>

- Semantic search over the Nexio catalog using embeddings in PostgreSQL
- Observability for Node services: structured logging, health checks, metrics
- Deeper CI/CD: automated build, tests, migrations, and deploy in one pipeline

</details>

<p align="center">
  <a href="https://linkedin.com/in/m4rcosz">linkedin.com/in/m4rcosz</a>
  &nbsp;&#8224;&nbsp;
  <a href="https://m4rcosz.com">m4rcosz.com</a>
  &nbsp;&#8224;&nbsp;
  <a href="mailto:zmarcos0103@gmail.com">zmarcos0103@gmail.com</a>
</p>

<p align="center">
  <sub><i>build &#183; ship &#183; automate &#183; repeat</i></sub>
</p>
