Web Development — Riquelme

A universal AI Agent Skill for professional web development.

A reusable, framework-independent development methodology designed to help AI coding assistants build secure, accessible, maintainable, high-performance, and search-friendly websites.

This skill is self-contained and requires no previous conversation history, personal context, or knowledge of past projects.

Features

- Web Design & UI/UX — Responsive layouts, accessibility, consistent design systems, and meaningful animations.
- Software Engineering — Clean architecture, reusable components, maintainable code, and structured development workflows.
- Security — API secret protection, parameterized SQL queries, Zod validation, secure password hashing, access control, and rate limiting.
- Infrastructure — HTTPS/TLS, reverse proxies, DDoS mitigation, audit logging, encryption, and conditional load balancing.
- Database Connections (Serverless) — Connection pooling (PgBouncer, Prisma Accelerate, provider poolers), pool sizing, idle connection cleanup, and limits to prevent "too many connections" errors.
- Performance — Core Web Vitals, image optimization, caching, efficient rendering, and mobile performance.
- SEO & Indexing — Technical SEO, XML sitemaps, Google Search Console workflows, and search visibility diagnostics.
- Quality Assurance — Testing, code review, security checks, regression prevention, and verification reports.

How It Works

The skill follows a structured engineering workflow:

Understand → Plan → Test → Implement → Review → Verify → Improve

It adapts its recommendations to each project's requirements, technology stack, hosting environment, and complexity.

The skill avoids unnecessary infrastructure and does not require a specific programming language or framework.

Installation

AI agents supporting Agent Skills

1. Download or clone this repository.
2. Locate the "web-development-riquelme" directory containing "SKILL.md".
3. Add that directory to your AI agent's Skills location or import it using the agent's supported installation method.
4. Activate the skill when working on a website or web application.

Installation steps vary by AI platform.

AI assistants without native Skills support

You can still use this methodology:

1. Open the "SKILL.md" file.
2. Copy its entire contents.
3. Paste the instructions into your AI assistant's conversation or custom instructions.
4. Provide your project requirements or source files.

The assistant can then follow the methodology without previous memory.

Example Usage

Create a website:

"Use the web-development-riquelme skill to design and build a responsive, secure, and optimized website."

Review an existing project:

"Apply the web-development-riquelme skill to audit this application for security, performance, accessibility, and code quality."

Review database connections in a serverless environment:

"Analise a forma como este projeto se conecta ao banco de dados em um ambiente serverless. Verifique se as conexões estão sendo abertas de forma direta, sem reuso, ou se estamos utilizando um connection pooler (como PgBouncer ou Prisma Accelerate). Refatore a configuração do banco para usar pooling de conexões, garanta que conexões ociosas sejam encerradas corretamente e configure limites para evitar que o banco de dados trave por excesso de conexões simultâneas."

Improve search visibility:

"Use the web-development-riquelme skill to analyze my website's technical SEO, indexing readiness, and search visibility."

Security Principles

The methodology emphasizes secure-by-design development, including:

- Never exposing private API keys or credentials in client-side code.
- Using parameterized database queries.
- Validating untrusted inputs.
- Protecting user credentials with modern password hashing.
- Enforcing server-side authentication and authorization.
- Protecting sensitive information in transit and at rest.
- Maintaining appropriate security logs and monitoring.
- Applying infrastructure safeguards based on actual deployment requirements.

Security controls must be implemented and verified within the capabilities of the selected technology and hosting environment.

Important Limitations

This skill provides instructions and engineering standards. It does not independently provide infrastructure, credentials, deployment access, or external integrations.

Actual implementation and verification depend on the capabilities and permissions available to the AI agent.

Search engine indexing, ranking, DDoS protection, and service availability cannot be guaranteed.

Compatibility

Designed around the open Agent Skills format.

The skill can be used by compatible AI coding agents or manually supplied to conversational AI assistants.

Native installation and automatic activation depend on the individual platform.

Acknowledgements

The methodology incorporates established software engineering practices and selected workflow concepts inspired by "ECC — Everything Claude Code" (https://github.com/affaan-m/ECC).

License

MIT License. See the repository's "LICENSE" file.

---

Developed by Riquelme.

Build better. Secure by design. Verify everything.