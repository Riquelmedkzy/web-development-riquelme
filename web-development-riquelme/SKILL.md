
---
name: web-development-riquelme
description: Metodologia pessoal de Matheus Riquelme para planejar, criar, alterar, revisar, testar, proteger, otimizar e publicar sites e aplicações web. Usar em tarefas de frontend, backend, UI/UX, API, banco de dados, segurança, desempenho, hospedagem, infraestrutura, SEO, indexação e Google Search Console. Inclui auditoria de visibilidade de sites públicos.
---

# Web Development — Riquelme

Aplicar esta metodologia em projetos web novos e existentes. Dar prioridade ao objetivo e às instruções explícitas do usuário. Adaptar regras à tecnologia, ao risco e ao estágio (local, homologação ou produção). Não transformar pequenos sites em arquiteturas complexas sem benefício mensurável.

## 1. Processo de engenharia

Seguir o ciclo inspirado em práticas de engenharia da ECC: **entender → planejar → testar → implementar → revisar → verificar → aprender/melhorar**. Não copiar automaticamente scripts, agentes ou hooks da ECC.

1. Inspecionar o código, as rotas, as dependências, os testes e a infraestrutura existentes antes de modificar. Buscar primeiro recursos já disponíveis no projeto e na documentação oficial. Não acrescentar pacotes sem necessidade.
2. Identificar objetivo, público, funcionalidades, stack, domínio, hospedagem e estágio quando relevantes; não repetir perguntas respondidas. Para decisões materialmente abertas, propor alternativas e pedir aprovação.
3. Por padrão, dividir projetos grandes em etapas com checkpoints de design e arquitetura. Executar diretamente mudanças específicas já autorizadas sem burocracia.
4. Especificar critérios de aceitação observáveis para os fluxos importantes. Para bugs, reproduzir o defeito e, quando possível, criar um teste que falhe antes da correção; implementar a menor correção e testar regressões. Para funcionalidades substanciais, preferir TDD quando adequado ao projeto.
5. Revisar arquivos alterados e efeitos colaterais. Preservar dados, estrutura e funcionalidades fora do escopo. Após cada etapa significativa, executar as verificações aplicáveis de [references/quality-and-workflow.md](references/quality-and-workflow.md).
6. Distinguir explicitamente **implementado**, **verificado localmente**, **verificado no ambiente final** e **pendente de credenciais, domínio, serviço ou autorização**. Nunca declarar concluído o que não foi testado.

## 2. Arquitetura, UX e código

- Escolher a arquitetura mais simples, segura e sustentável que atenda aos requisitos; nenhuma stack é obrigatória. Manter responsabilidades claras, evitar duplicações, garantir tratamento de erros e configuração por ambiente.
- Usar **design premium adaptável** por padrão, com identidade própria de cada projeto; não reutilizar automaticamente Bordeaux & Champagne, que pertence ao portfólio RIQUELME.
- Garantir responsividade, HTML semântico, navegação por teclado, foco visível, contraste, legibilidade, formulários acessíveis, estados de carregamento/vazio/erro e preferência por movimento reduzido.
- Utilizar animações e microinterações expressivas quando úteis, com degradação elegante em aparelhos mais modestos. Não trocar função por espetáculo.
- Em React e interfaces componentizadas, preferir composição, componentes com responsabilidade clara, estado mínimo, carregamento sob demanda e prevenção de renderizações ou chamadas de rede desnecessárias. Em outras stacks, usar equivalentes.
- Quando disponível e pertinente, empregar a Skill Impeccable para criticar qualidade visual, hierarquia, espaçamento, responsividade e acessibilidade.

## 3. Segurança como requisito

Sempre ler [references/security-and-infrastructure.md](references/security-and-infrastructure.md) ao trabalhar em código, APIs, dados, autenticação, banco, hospedagem ou deploy. Seguir as exigências abaixo, adaptando à stack:

- **Segredos:** manter chaves secretas, tokens e credenciais fora do cliente, do código-fonte público e dos logs. Não prometer ocultação de endpoints nem chaves que são necessariamente públicas.
- **Banco:** aplicar consultas parametrizadas/prepared statements em toda consulta que use entrada externa, com lista permitida para identificadores dinâmicos.
- **Validação:** usar Zod para dados externos em projetos JS/TS (especialmente no servidor), ou validação de esquema equivalente em PHP, Python, Java e outras stacks.
- **Senhas:** armazenar somente com hash adaptativo seguro, preferencialmente Argon2id ou bcrypt adequado, nunca texto puro ou hash rápido simples.
- **Defesa:** implementar autenticação/autorização corretas, CSRF, XSS, validação de upload, rate limit, headers seguros e HTTPS/TLS conforme o cenário.
- **Auditoria:** registrar eventos críticos de forma estruturada, com minimização de dados e integridade verificável; nenhum armazenamento é absolutamente imune a adulterações.
- **Criptografia:** proteger dados sensíveis em trânsito e repouso, inclusive backups, com gestão de chaves e permissões.
- **Infraestrutura pública:** avaliar proxy reverso, proteção da origem, CDN/WAF/mitigação DDoS, observabilidade, backups e alta disponibilidade; só usar balanceador quando houver múltiplas instâncias ou necessidade demonstrada. Não prometer proteção total contra DDoS.
- Nunca modificar DNS, conta de hospedagem, cobrança, produção ou dados reais sem escopo e autorização adequados.

## 4. Performance

- Avaliar mobile e desktop, também com dispositivo/modo de CPU e rede modestos. Otimizar imagens, dimensões reservadas, fontes, JS, CSS, animações, cache, queries e requisições.
- Medir Core Web Vitals e Lighthouse quando possível e registrar contexto. Usar alvos de boa experiência (LCP até 2,5 s, INP até 200 ms, CLS até 0,1 em dados de campo) como orientação, não garantia.
- Preferir melhorias demonstráveis antes de introduzir complexidade, serviços pagos, cache distribuído ou balanceamento.

## 5. SEO e site fantasma

Sempre ler [references/seo-and-visibility.md](references/seo-and-visibility.md) para páginas públicas, auditorias de busca e preparação de publicação.

- Preparar conteúdo de valor, pesquisa de intenção, títulos, descrições, links internos, HTML rastreável, URLs claras, canonical, robots.txt, sitemap.xml e dados estruturados relevantes.
- Ao final de cada site **público com domínio**, executar uma auditoria anti-site-fantasma: acesso, indexabilidade, consultas de marca e site:dominio, e Search Console se houver acesso. Distinguir não indexado de mal posicionado.
- Quando domínio/propriedade e conta autorizados estiverem disponíveis, adicionar/verificar a propriedade no Google Search Console, submeter sitemap.xml, inspecionar URLs importantes e solicitar indexação onde apropriado. Sem acesso, preparar os arquivos e orientar a etapa pendente, sem afirmar que realizou cadastro.
- Não prometer indexação, posição no Google ou tráfego. Não aplicar indexação a localhost, staging ou áreas privadas; llms.txt não é requisito do Google.

## 6. Entrega

Executar o checklist de qualidade apropriado ao escopo. Relatar alterações, resultados de build/testes/segurança/desempenho/SEO, limitações, riscos restantes e próximos passos. Se o trabalho for exclusivamente local, marcar verificações de produção e indexação como **não aplicáveis ou pendentes**, nunca como aprovadas.

## Origem de práticas complementares

Metodologia própria do usuário, com ideias seletivamente adaptadas de [ECC de affaan-m](https://github.com/affaan-m/ECC) (MIT): ciclo de planejamento, teste, revisão e verificação, padrões de frontend, segurança e SEO. Usar documentação oficial atual de tecnologias e Google como fonte de verdade para comportamento de produtos.
