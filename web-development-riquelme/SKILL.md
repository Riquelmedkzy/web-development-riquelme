
---
name: web-development-riquelme
description: Skill universal e autossuficiente para planejar, criar, corrigir, revisar, proteger, otimizar e lançar sites ou aplicações web. Usar em tarefas de design UI/UX, frontend, backend, APIs, banco de dados, autenticação, testes, segurança, infraestrutura, performance, SEO e indexação, mesmo quando a IA não possui memória ou contexto prévio.
---

# Universal Web Development

Aplicar esta metodologia a qualquer projeto web, novo ou existente, independentemente da IA, linguagem, framework, provedor ou pessoa que o utiliza. **Não presumir memória, projetos anteriores, preferências pessoais, credenciais ou infraestrutura existente.** Este arquivo contém todas as regras necessárias; nenhum outro skill, plugin ou arquivo de referência é obrigatório.

## 1. Começar sem memória

1. Ler a solicitação atual e inspecionar os arquivos, estrutura, dependências, testes e configurações do projeto, se disponíveis. Extrair deles o contexto em vez de inventá-lo.
2. Identificar, quando necessário, objetivo, público, funcionalidades, tecnologia, dados manipulados, riscos, plataforma de execução, domínio e fase (local, teste ou produção). Fazer somente perguntas cuja resposta mude materialmente a solução.
3. Se não houver projeto existente, recomendar uma stack adequada ao problema e às restrições informadas. Não impor frameworks, bancos, microserviços, serviços pagos ou complexidade desnecessária.
4. Responder no idioma do usuário. Respeitar escopo e decisões explícitas. Não mencionar experiências passadas, nomes de pessoas ou marcas que não tenham sido fornecidos na tarefa atual.
5. Trabalhar com as ferramentas realmente disponíveis. Sem terminal, navegador, acesso ao código ou contas externas, fornecer uma solução e um roteiro verificável, **sem alegar que executou testes, publicou ou configurou serviços**.

## 2. Fluxo de engenharia

Seguir um processo proporcional ao trabalho: **entender → planejar → testar → implementar → revisar → verificar → melhorar**.

- Para novos sites ou alterações grandes, organizar requisitos, páginas/fluxos, dados, critérios de aceitação e um plano curto. Validar decisões importantes antes de fazer mudanças difíceis de reverter.
- Para bugs, primeiro reproduzir o erro; quando houver ambiente de testes adequado, escrever um teste de regressão que falhe, corrigir a causa e verificar que passou.
- Para funcionalidades críticas, preferir testes unitários, de integração e de ponta a ponta conforme o risco. Aplicar TDD quando agregar segurança e clareza; não transformar correções triviais em cerimônia.
- Inspecionar bibliotecas e padrões já presentes; escolher soluções mantidas e compatíveis. Consultar documentação oficial atual antes de depender de comportamento ou versões que possam mudar.
- Preservar dados e funcionalidades fora do escopo, revisar alterações e evitar efeitos colaterais. Não executar comandos destrutivos, alterar produção, DNS, faturamento ou dados reais sem autorização.

## 3. Arquitetura e qualidade de código

- Escolher estrutura simples, modular e sustentável, com separação adequada entre apresentação, lógica, acesso a dados e infraestrutura. Evitar duplicações, funções excessivamente grandes e dependências desnecessárias.
- Adotar nomes claros, tipos quando disponíveis, tratamento consistente de erros, entradas e saídas explícitas, configuração por ambiente e princípio do menor privilégio.
- Em interfaces componentizadas, preferir composição, estado mínimo, componentes reutilizáveis e carregamento sob demanda. Em outras tecnologias, empregar padrões equivalentes.
- Usar contratos estáveis para APIs, erros compreensíveis, paginação/limites quando necessários e testes para rotas e operações sensíveis.
- Manter documentação mínima de instalação, ambiente, comandos de teste e decisões operacionais indispensáveis.

## 4. Design, UX e acessibilidade

- Criar identidade visual adaptada ao propósito, público e marca de cada site. Priorizar hierarquia visual, tipografia, contraste, espaçamento, consistência, clareza de navegação e uma aparência profissional; não impor paleta ou estilo universal.
- Projetar primeiro para leitura e uso em telas pequenas e adaptar a tablet/desktop. Conferir menus, formulários, tabelas, imagens, estados vazios, carregamento, erros e feedback após ações.
- Usar HTML semântico, rótulos de formulário, foco visível, navegação por teclado, contraste adequado e textos alternativos relevantes. Respeitar preferências de movimento reduzido.
- Empregar animações, microinterações, efeitos 3D ou glassmorphism somente quando adequados à proposta, mantendo legibilidade e funcionamento em aparelhos modestos.
- Revisar visualmente quando houver prévia; se não houver renderização, declarar a limitação e sugerir como verificar.

## 5. Segurança — requisitos obrigatórios

Aplicar defesa em profundidade e adequar cada controle à linguagem, ao risco e à hospedagem. Segurança não depende apenas do frontend.

### Segredos e APIs

- Manter senhas de serviços, chaves secretas, tokens privados e credenciais exclusivamente no servidor ou gerenciador de segredos, nunca em código cliente, commits, URLs públicas, respostas ou logs. Separar configurações por ambiente e revisar exposições.
- Para integrar uma API que requer segredo, fazer a chamada no backend ou em função de servidor autorizada. Não prometer esconder endpoints públicos ou chaves que precisam ser públicas no cliente; restringir escopo, cotas e origem quando o provedor permitir.
- Definir autenticação e autorização no servidor; não tratar CORS, campos ocultos ou validação de frontend como barreiras de segurança.

### Banco, validação e identidade

- **Usar consultas parametrizadas/prepared statements** em SQL que recebe entrada externa. Não concatenar parâmetros; aplicar allowlist para nomes de colunas, tabelas e ordenação dinâmica. ORMs não dispensam revisar SQL bruto.
- **Usar Zod** para validar entradas de fronteira em projetos JavaScript/TypeScript, sobretudo no servidor. Em PHP, Python, Java ou outras linguagens, usar validação robusta equivalente. Validar tipo, tamanho, formato, limites, arquivos e campos permitidos; não confiar somente no navegador.
- Guardar senhas apenas como **hash adaptativo com sal**, preferencialmente Argon2id, ou bcrypt quando adequado. Nunca texto puro, criptografia reversível de senhas ou MD5/SHA rápido isolado.
- Proteger sessões/cookies com atributos apropriados (HttpOnly, Secure, SameSite), expiração, revogação e recuperação de conta segura. Verificar permissões por recurso/ação e prevenir IDOR, CSRF, XSS, injeção e upload perigoso.
- Implementar rate limit por IP/conta/endpoint, mais rigoroso em login, recuperação, cadastro, envio de mensagens e operações caras. Considerar bloqueios progressivos, erros não reveladores e proxies confiáveis.

### Auditoria, criptografia e rede

- Registrar tentativas relevantes de login, alterações de permissão, ações administrativas, falhas graves e eventos sensíveis com horário, identificador de correlação, ator quando conhecido e resultado. Minimizar dados pessoais; **não registrar** senhas, tokens, cookies ou conteúdo confidencial.
- Proteger logs com acessos restritos, centralização e, quando disponível, escrita append-only/WORM, cópias externas, retenção, alertas e verificação de integridade. Projetar logs **resistentes e evidentes a adulterações**, nunca prometer inviolabilidade absoluta.
- Usar HTTPS/TLS em produção, proteger conexões internas quando aplicável, criptografar informações sensíveis e backups em repouso e manter chaves separadas, restritas e rotacionáveis.
- Configurar cabeçalhos de segurança (incluindo CSP apropriada), tratamento de erros sem vazamento de detalhes, atualizações de dependências, backups e recuperação conforme o risco.

## 6. Infraestrutura e proteção DDoS

- Em hospedagem compatível, avaliar proxy reverso para TLS, roteamento, saúde da aplicação e restrição de acesso à origem por rede/firewall. Proxy não garante anonimato do IP de origem nem impede indisponibilidade.
- Para mitigar DDoS, combinar recursos upstream do provedor, CDN/WAF, cache, rate limits, monitoramento e plano de resposta quando justificado. Uma aplicação isolada não consegue neutralizar todos os ataques volumétricos.
- **Usar balanceador de carga somente quando houver múltiplas instâncias, métricas de tráfego ou demanda de disponibilidade** que justifiquem seu custo e complexidade. Prever health checks, sessões/estado compartilhados e falha controlada.
- Não adicionar proxy, CDN, balanceador, criptografia de volume ou serviços de nuvem fictícios a um projeto puramente local. Preparar o desenho para produção e explicitar o que depende de domínio, provedor e permissões.

## 7. Desempenho

- Otimizar imagens modernas e responsivas, fontes, CSS/JS, cache, renderização, consultas, payloads e requisições de rede. Usar lazy loading onde adequado e reservar espaço para evitar deslocamentos.
- Testar mobile e desktop com limitações realistas de CPU/rede. Medir Lighthouse e Core Web Vitals quando houver ambiente: alvos orientativos de LCP ≤ 2,5 s, INP ≤ 200 ms e CLS ≤ 0,1 em dados reais.
- Distinguir testes sintéticos de medições de usuários. Nunca inventar scores nem afirmar que uma otimização melhorou resultados sem evidência.

## 8. SEO e auditoria de “site fantasma”

Para **sites públicos destinados à busca orgânica**, aplicar SEO desde o desenvolvimento:

1. Definir público, temas, intenção de pesquisa e conteúdo útil. Associar páginas a consultas relevantes, sem exagero de palavras-chave nem técnicas manipulativas.
2. Criar títulos e descrições exclusivos, URL estável, headings coerentes, links internos rastreáveis, canonical, idioma e dados estruturados válidos quando pertinentes.
3. Garantir que páginas importantes respondam corretamente, tenham conteúdo acessível ao rastreador e não estejam acidentalmente bloqueadas por robots.txt, noindex, autenticação, canonical ou redirecionamentos.
4. Gerar **sitemap.xml** válido, com URLs absolutas e canônicas que devam ser indexadas, e referenciá-lo no robots.txt quando adequado. Nunca incluir páginas privadas ou de teste.
5. No lançamento ou auditoria de domínio público, buscar site:dominio, marca e consultas-alvo, verificar indexabilidade e, com acesso autorizado, analisar os relatórios do **Google Search Console**. O operador site: é um indício limitado, não prova completa.
6. Se a propriedade do domínio e a conta estiverem acessíveis com autorização, verificar/cadastrar o site no Search Console, enviar sitemap.xml, inspecionar páginas prioritárias e solicitar indexação quando apropriado. Sem acesso, explicar passos e dependências; não declarar cadastro realizado.
7. Distinguir site não indexado, página bloqueada, site novo aguardando descoberta e site indexado com baixa posição. Corrigir causas controláveis e informar que **sitemap e solicitação não garantem indexação, ranking ou tráfego**.
8. Não tentar indexar localhost, staging, áreas privadas ou páginas deliberadamente noindex. Não tratar llms.txt como requisito de indexação do Google.

## 9. Verificação final obrigatória

Após alterações relevantes, executar o que for possível e declarar o status de cada item:

1. **Build e execução:** instalação, compilação, sintaxe, rotas e fluxos principais.
2. **Tipos e lint:** verificações configuradas na stack.
3. **Testes:** unitários, integração e E2E relevantes; priorizar autenticação, permissões, formulários, APIs, operações de banco e regressões. Buscar boa cobertura (por exemplo, 80% em código crítico quando realista), sem alegar porcentagem não medida.
4. **Segurança:** segredos, dependências, entradas, SQL, permissões, sessões, headers e auditoria; não expor os segredos encontrados.
5. **Interface:** responsividade, acessibilidade, estados de erro e desempenho.
6. **SEO:** sitemap, robots, canonical, metadados e diagnóstico de visibilidade apenas quando aplicável.
7. **Revisão das mudanças:** conferir diferenças e efeitos colaterais, respeitando arquivos e dados fora do escopo.
8. **Destino:** se houver publicação autorizada, testar o ambiente real separadamente; sucesso local não comprova produção.

## 10. Formato de entrega

Responder com:

- **Resultado:** o que foi implementado, corrigido ou recomendado.
- **Evidência:** testes e medições executados, com status PASSOU/FALHOU/NÃO EXECUTADO/NÃO APLICÁVEL.
- **Riscos e pendências:** problemas restantes, limitações de ferramenta, credenciais, conta ou hospedagem.
- **Próximo passo:** ação mais útil e objetiva, sem sugerir publicação ou mudanças externas que o usuário não autorizou.

Manter a resposta proporcional ao trabalho. Quando não houver ferramentas para agir, fornecer instruções ou código revisável e deixar claro o que outra pessoa ou IA precisará executar.
