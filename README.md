# Threat Grill

Threat Grill conduz uma análise de ameaças por entrevista adaptativa: faz uma pergunta de cada vez, oferece alternativas e aprofunda as respostas com cenários de ataque e evidências.

## Como usar

Invoque a skill com uma arquitetura, aplicação, API, infraestrutura ou fluxo para analisar. Por exemplo:

> Use $threat-grill para analisar a segurança desta API de consulta a benefícios. Faça perguntas de múltipla escolha e, ao final, emita o relatório com STRIDE.

Durante a entrevista:

- Responda com a letra da alternativa ou acrescente contexto em texto livre.
- Escolha **“Não sei / preciso verificar”** quando faltar informação. A análise registra isso como desconhecido, não como falha confirmada.
- A skill faz uma pergunta principal por turno e adapta a próxima pergunta à resposta.
- Você pode pedir um resumo, mudar o foco ou encerrar a análise quando quiser.

## Formato do relatório

O relatório final registra escopo, premissas e limites da revisão. Apresenta ameaças priorizadas numa tabela com estas colunas:

| Prioridade | Ameaça | STRIDE | Justificativa |
|---|---|---|---|

Cada ameaça recebe apenas as categorias STRIDE que se aplicam ao cenário, com justificativa. A classificação descreve a natureza da ameaça; não confirma exploração nem mede gravidade.

- **S — Spoofing:** falsificação de identidade
- **T — Tampering:** adulteração
- **R — Repudiation:** repúdio
- **I — Information Disclosure:** divulgação de informação
- **D — Denial of Service:** negação de serviço
- **E — Elevation of Privilege:** elevação de privilégio

O relatório também inclui ações prioritárias com critérios de validação, evidências pendentes e riscos residuais. Prioridades são qualitativas e justificadas; não são pontuações CVSS.

## Evidências e segurança

As respostas e os artefatos disponíveis fundamentam a análise. Uma declaração do usuário não conta automaticamente como prova técnica. A skill separa fatos observados, declarações, hipóteses e itens não verificados. Use exemplos sanitizados; não compartilhe senhas, tokens ou dados pessoais reais.

A entrevista é uma revisão defensiva e não certifica a segurança do sistema nem executa testes de intrusão por conta própria.

## Instalação

Para instalar como skill do Codex, copie os arquivos deste repositório para:

- Linux/macOS: `~/.codex/skills/threat-grill/`
- Instalação personalizada: `$CODEX_HOME/skills/threat-grill/`

A pasta deve conter `SKILL.md`, `agents/openai.yaml` e `assets/icon.svg`.
