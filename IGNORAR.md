# MONTAR WIKI CARPACCIO DESTE PROJETO

Você deve utilizar a skill de Wiki Carpaccio criada anteriormente para construir a Wiki persistente deste projeto.

A Wiki NÃO ficará dentro deste repositório.

O destino EXATO da Wiki é:

/home/gaab/Documentos/gitHub/GaabWiki

NÃO crie a Wiki em outro diretório.

---

# 1. OBJETIVO

Seu trabalho é reconstruir, com o máximo de fidelidade possível, o conhecimento relevante deste projeto e transformá-lo em uma Wiki Carpaccio persistente.

Você deve analisar:

- código atual;
- estrutura completa do projeto;
- documentação;
- README;
- arquivos de configuração;
- propostas;
- especificações;
- documentos de planejamento;
- issues, quando disponíveis localmente;
- commits;
- histórico relevante;
- TODAS as branches locais e remotas disponíveis;
- diferenças entre branches;
- decisões arquiteturais;
- decisões abandonadas;
- funcionalidades implementadas;
- funcionalidades planejadas;
- funcionalidades removidas;
- problemas conhecidos;
- testes;
- scripts;
- dependências;
- infraestrutura;
- convenções;
- domínio do sistema;
- qualquer outro artefato relevante encontrado no projeto.

Não assuma que a branch atual representa toda a história do projeto.

---

# 2. REGRA FUNDAMENTAL: NÃO ALTERE O PROJETO

Durante esta tarefa:

NÃO altere:

- código-fonte;
- configurações;
- dependências;
- testes;
- README existente;
- documentação existente;
- branches;
- commits;
- histórico Git.

Sua tarefa é ANALISAR.

A única escrita permitida relacionada ao resultado desta tarefa é no diretório:

/home/gaab/Documentos/gitHub/GaabWiki

Se precisar criar arquivos temporários para análise, coloque-os em /tmp ou outro local temporário e remova-os ao terminar.

---

# 3. PRIMEIRO: LEIA A SKILL

Antes de fazer qualquer coisa:

1. localize a skill de Wiki Carpaccio criada anteriormente;
2. leia a skill integralmente;
3. siga seus workflows;
4. trate a skill como contrato operacional desta tarefa.

Não improvise outra metodologia.

---

# 4. SEGUNDO: DESCUBRA O PROJETO

Antes de criar qualquer Wiki:

analise a estrutura do repositório.

Identifique:

- linguagem;
- frameworks;
- runtime;
- entrypoints;
- arquitetura;
- aplicações;
- bibliotecas;
- serviços;
- banco de dados;
- integrações;
- frontend;
- backend;
- infraestrutura;
- testes;
- scripts;
- CI/CD;
- documentação.

Não escreva a Wiki ainda.

Primeiro construa mentalmente um mapa do projeto.

---

# 5. TERCEIRO: ANALISE TODAS AS BRANCHES

Esta etapa é OBRIGATÓRIA.

Liste:

```bash
git branch -a

e analise todas as branches disponíveis.

Inclua:

branch atual;
branches locais;
branches remotas;
branches de feature;
branches de desenvolvimento;
branches experimentais;
branches aparentemente abandonadas.

NÃO faça checkout destrutivo.

Use comandos Git somente para leitura.

Exemplos:

git branch -a
git log --all --oneline --decorate --graph
git log <branch>
git diff <branch1>...<branch2>
git show <commit>
git log --all -- <arquivo>

Adapte os comandos conforme necessário.

6. CADA BRANCH DEVE SER ANALISADA SEPARADAMENTE

Não trate todas as branches como se fossem uma única implementação.

Para cada branch relevante, determine:

propósito;
estado;
funcionalidades existentes;
arquitetura;
diferenças em relação às outras branches;
funcionalidades exclusivas;
decisões diferentes;
código experimental;
funcionalidades abandonadas;
possíveis decisões históricas.

Crie uma visão histórica do projeto.

Exemplo conceitual:

main
 └── estado atual

develop
 └── mudanças ainda não integradas

feature/auth
 └── tentativa de autenticação
 └── decisão X

feature/auth-v2
 └── substituiu feature/auth
 └── decisão Y

Não presuma qual branch é "melhor".

Documente o que existe.

7. HISTÓRIA DO PROJETO

Analise o Git como fonte histórica.

Procure:

decisões importantes;
grandes refatorações;
mudanças de arquitetura;
features adicionadas;
features removidas;
bugs corrigidos;
tentativas abandonadas;
migrações;
mudanças de tecnologia;
commits que expliquem decisões.

Não transforme cada commit em documentação.

Extraia somente conhecimento persistente.

8. DOCUMENTAÇÃO E PROPOSTAS

Procure agressivamente por documentos como:

README.md
docs/
documentation/
spec/
specs/
proposal/
proposals/
design/
architecture/
notes/
planning/
research/

Além disso, procure arquivos:

*.md
*.txt
*.pdf
*.docx
*.json
*.yaml
*.yml

quando forem relevantes.

Se existir uma proposta original do projeto, analise-a separadamente do código.

Isso é importante porque:

PROPOSTA ≠ IMPLEMENTAÇÃO.

Não transforme uma intenção em fato.

9. DIFERENÇA ENTRE "PLANEJADO" E "IMPLEMENTADO"

Esta distinção é obrigatória.

A Wiki deve diferenciar:

IMPLEMENTADO
PLANEJADO
PARCIAL
ABANDONADO
EXPERIMENTAL
DESCONHECIDO

Exemplo:

Se o README diz:

"O sistema terá autenticação OAuth."

mas nenhuma implementação existe:

NÃO escreva:

"O sistema utiliza OAuth."

Escreva algo como:

"OAuth foi definido como parte da proposta, mas não há evidência de implementação no estado analisado."

10. CONTRADIÇÕES

Procure deliberadamente por contradições entre:

README;
documentação;
proposta;
código;
testes;
branches;
histórico Git;
configuração.

Exemplo:

README:

PostgreSQL

Código:

MySQL

Não esconda a contradição.

Registre:

Status: conflito
Fonte A: README
Fonte B: configuração atual
Estado provável: ...

Se for possível determinar o estado atual pelo código, faça isso claramente.

11. CÓDIGO É A FONTE DE VERDADE DO ESTADO ATUAL

Para saber o que realmente está implementado:

código atual
    >
testes/configuração
    >
documentação atual
    >
histórico
    >
proposta
    >
inferência

Mas isso não significa apagar informações históricas.

A Wiki deve preservar decisões e contexto relevantes.

12. NÃO CONFUNDA HISTÓRIA COM ESTADO ATUAL

Uma funcionalidade pode ter existido e posteriormente ter sido removida.

Documente isso como histórico.

Exemplo:

A autenticação OAuth existiu na branch feature/oauth,
mas foi removida posteriormente e não está presente no estado atual.

Não diga simplesmente:

O projeto possui OAuth.
13. DESTINO DA WIKI

Crie a Wiki EXATAMENTE em:

/home/gaab/Documentos/gitHub/GaabWiki

Antes de escrever:

verifique se o diretório existe;
verifique se contém uma Wiki deste projeto;
se existir conteúdo, NÃO sobrescreva cegamente;
analise o que já existe;
preserve conhecimento válido;
atualize apenas o necessário.

A Wiki deve ser incremental.

14. IDENTIDADE DO PROJETO

A Wiki precisa conseguir identificar claramente qual projeto documenta.

Crie uma página inicial apropriada contendo:

nome do projeto;
propósito;
estado atual;
stack;
arquitetura em alto nível;
repositório de origem;
branch considerada estado atual;
data da última análise;
principais áreas da Wiki.

Não invente informações.

15. ESTRUTURA MÍNIMA

Utilize a estrutura definida pela skill.

No mínimo:

GaabWiki/
└── <identificador-do-projeto>/
    ├── CLAUDE.md
    ├── index.md
    ├── log.md
    ├── raw/
    └── wiki/

O nome do projeto deve ser derivado do próprio repositório.

Não crie dezenas de subdiretórios antecipadamente.

16. FONTES BRUTAS

Se houver documentação ou artefatos que devam ser preservados como fonte:

coloque cópias em:

raw/

quando isso fizer sentido.

IMPORTANTE:

Não copie indiscriminadamente o repositório inteiro.

Não duplique código.

Não transforme o diretório da Wiki em um segundo repositório.

Preserve apenas fontes relevantes para conhecimento persistente.

17. WIKI

Crie páginas somente quando houver conhecimento suficiente para justificá-las.

Possíveis páginas:

architecture.md
current-state.md
decisions.md
domain.md
database.md
api.md
conventions.md
known-issues.md
roadmap.md
history.md
branches.md

Esses nomes são sugestões.

Não crie todos automaticamente.

18. BRANCHES.MD

Como este projeto possui múltiplas branches, considere criar:

wiki/branches.md

Ela deve explicar:

branches encontradas;
propósito conhecido;
estado;
diferenças importantes;
funcionalidades exclusivas;
decisões históricas relevantes.

Não transforme isso em um dump de Git.

Extraia conhecimento.

19. HISTORY.MD

Se o histórico for relevante, crie:

wiki/history.md

Ela deve explicar a evolução do projeto em alto nível.

Exemplo:

Fase 1 — protótipo
Fase 2 — mudança de arquitetura
Fase 3 — implementação atual
Fase 4 — experimentos abandonados

Somente faça isso quando houver evidência suficiente.

20. DECISIONS.MD

Crie ou atualize decisions.md para decisões arquiteturais ou técnicas importantes.

Para cada decisão relevante:

# Decisão: ...

## Contexto

...

## Decisão

...

## Motivo

...

## Alternativas

...

## Evidência

...

## Status

Atual / substituída / abandonada

Quando uma decisão foi substituída, mantenha a história.

21. CURRENT-STATE.MD

Crie uma visão objetiva do estado atual.

Ela deve responder:

"Se eu entrar neste projeto hoje, o que realmente existe?"

Inclua:

funcionalidades;
arquitetura;
componentes;
integrações;
banco;
estado de testes;
limitações;
pendências relevantes.

Não misture isso com roadmap.

22. ROADMAP

Só crie roadmap.md se houver evidências reais de planejamento.

Separe:

Planejado explicitamente
Inferido
Ideias antigas
Abandonado

Nunca apresente uma inferência como roadmap oficial.

23. CONVENÇÕES

Documente somente convenções realmente observadas.

Exemplos:

nomenclatura;
estrutura de pastas;
padrões de API;
padrões de testes;
tratamento de erros;
arquitetura;
estilo de código;
organização de serviços.

Não crie "boas práticas" genéricas.

A Wiki descreve ESTE projeto.

24. PROBLEMAS E DÍVIDAS

Procure por:

TODO;
FIXME;
BUG;
HACK;
comentários importantes;
issues documentadas;
testes quebrados;
dependências problemáticas;
arquitetura inconsistente.

Mas não transforme todo TODO em "problema crítico".

Classifique conforme evidência.

25. INDEX.MD

O index.md deve ser o mapa principal.

Ele precisa permitir que outro agente entre na Wiki e descubra rapidamente:

O que é este projeto?
Qual seu estado atual?
Onde está a arquitetura?
Quais são as decisões?
Quais são os problemas?
Quais são as fontes?
Onde está o histórico?
Quais branches são importantes?

Use Wikilinks.

26. QUALIDADE DA WIKI

Depois de criar a primeira versão:

faça uma segunda passagem completa.

Pergunte:

Existe informação duplicada?
Alguma página contradiz outra?
Alguma afirmação não possui evidência?
Alguma informação planejada foi confundida com implementada?
Alguma decisão histórica foi perdida?
Alguma branch importante foi ignorada?
Algum documento relevante foi ignorado?
O índice aponta para tudo?
Existem links quebrados?
Existem páginas inúteis?
A Wiki está maior do que precisa estar?

Corrija.

27. NÃO MAXIMIZE O TAMANHO

Uma Wiki maior NÃO é necessariamente uma Wiki melhor.

Priorize:

densidade de conhecimento
>
quantidade de texto

Não copie documentação inteira para a Wiki se ela não precisa ser sintetizada.

Não copie código.

Não gere descrições genéricas.

Não escreva texto apenas para preencher páginas.

28. RASTREABILIDADE

Sempre que possível, indique a origem de informações importantes.

Exemplos:

Fonte: README.md
Fonte: src/Auth/TokenService.cs
Fonte: commit abc123
Fonte: branch feature/auth
Fonte: docs/proposal.md

A Wiki deve permitir que outro agente investigue de onde uma informação veio.

29. GIT DA WIKI

A Wiki é independente do projeto.

Se:

/home/gaab/Documentos/gitHub/GaabWiki

já for um repositório Git:

utilize-o normalmente.

Se não for, NÃO inicialize automaticamente outro repositório sem necessidade.

Primeiro verifique o estado existente.

Não faça commits automaticamente a menos que isso seja explicitamente permitido pelas instruções existentes da Wiki.

30. RESULTADO FINAL

Ao terminar, a Wiki deverá representar:

ESTADO ATUAL
+
ARQUITETURA
+
DECISÕES
+
CONHECIMENTO DE DOMÍNIO
+
CONVENÇÕES
+
PROBLEMAS
+
HISTÓRIA
+
BRANCHES
+
PLANEJAMENTO REAL
+
FONTES

sem transformar o projeto em uma massa de documentação redundante.

31. REGRA ABSOLUTA CONTRA ALUCINAÇÃO

Se você não sabe:

não invente.

Se há conflito:

registre o conflito.

Se algo parece provável:

marque como inferência.

Se algo foi planejado mas não implementado:

marque como planejado.

Se algo existiu apenas em uma branch:

diga isso.

Se não há evidência:

não transforme em fato.

32. AO FINAL

Apresente um relatório curto contendo:

projeto analisado;
branch considerada como estado atual;
quantidade de branches analisadas;
principais fontes analisadas;
páginas criadas;
principais decisões identificadas;
principais contradições encontradas;
principais lacunas de conhecimento;
caminho final da Wiki:

/home/gaab/Documentos/gitHub/GaabWiki/<projeto>

qualquer ponto que NÃO pôde ser determinado com segurança.

Não faça alterações no projeto original.

A única entrega desta tarefa é a Wiki Carpaccio persistente.