# Threat Grill

Threat Grill conduz análises de ameaças por entrevista adaptativa: faz uma pergunta de cada vez, oferece alternativas e aprofunda os caminhos de ataque mais relevantes. Ao final, organiza as ameaças por prioridade e classifica cada uma com STRIDE.

## Usar no ChatGPT pela web

Há dois caminhos, conforme os recursos habilitados na sua conta ou workspace.

### Carregar a skill diretamente

Se a página **Skills** estiver disponível no ChatGPT web:

1. Abra **Plugins** na barra lateral e selecione a aba **Skills**.
2. Selecione **Criar** e depois **Carregar do computador**.
3. Envie o ZIP da skill, com `SKILL.md` na raiz e os arquivos de apoio junto dele.
4. Aguarde a verificação. Se aparecer **Requer análise**, revise as informações solicitadas e conclua a instalação.
5. Em um chat, digite `@` e escolha **Threat Grill** no seletor.

A disponibilidade e o fluxo de instalação podem variar entre contas, planos e workspaces. Consulte [Skills no ChatGPT](https://help.openai.com/en/articles/20001066-skills-in-chatgpt).

### Usar a skill dentro de um plugin

Se o upload de uma skill independente não estiver disponível, use o fluxo de plugins, que funciona no ChatGPT web quando habilitado no workspace:

1. Inicie uma conversa em **Chat** ou **Work** e digite `@`.
2. Procure e selecione **Plugin Creator**.
3. Peça para criar um plugin chamado **Threat Grill** e anexe o `SKILL.md` deste repositório como referência.
4. Instrua o Plugin Creator a preservar o fluxo de entrevista adaptativa: uma pergunta de múltipla escolha por vez, respostas livres permitidas, registro de evidências e relatório final com prioridades e classificação STRIDE.
5. Revise as instruções e teste com uma arquitetura conhecida antes de instalar ou compartilhar o plugin.

Esse caminho requer que o Plugin Creator esteja habilitado e que sua conta tenha permissão para criar plugins. Veja [Build plugins](https://learn.chatgpt.com/docs/build-plugins). A documentação também descreve a disponibilidade de skills independentes por superfície em [Build skills](https://learn.chatgpt.com/docs/build-skills).

## Instalação como Skill no Codex

Para instalar como skill do Codex, copie os arquivos deste repositório para:

- Linux/macOS: `~/.codex/skills/threat-grill/`
- Instalação personalizada: `$CODEX_HOME/skills/threat-grill/`

A pasta deve conter `SKILL.md`, `agents/openai.yaml` e `assets/icon.svg`.

## Instalar no Claude Code

O `SKILL.md` da Threat Grill pode ser usado pelo Claude Code, mas deve ficar na pasta de skills dele. O arquivo `agents/openai.yaml` é metadado opcional para ChatGPT/Codex e não é necessário para o Claude Code.

### Instalação pessoal

Clone o repositório na pasta de skills do usuário:

```bash
git clone https://github.com/niltonj/threat-grill.git ~/.claude/skills/threat-grill

### Instalação em um projeto
Para disponibilizar a skill a quem trabalha no projeto, coloque seus arquivos em:

<raiz-do-projeto>/.claude/skills/threat-grill/SKILL.md

Inclua também os arquivos de apoio da skill, se houver, e versione a pasta .claude/skills/threat-grill/ no Git.

### Usar

No Claude Code, digite:
/threat-grill

## Como usar

Comece com uma arquitetura, aplicação, API, infraestrutura ou fluxo. Por exemplo:

> Use Threat Grill para analisar a segurança desta API de consulta a benefícios. Faça perguntas de múltipla escolha e, ao final, emita o relatório com STRIDE.

Durante a entrevista:

- Responda com a letra da alternativa ou acrescente contexto em texto livre.
- Use **“Não sei / preciso verificar”** quando faltar informação. A skill registra isso como desconhecido, não como falha confirmada.
- A pergunta seguinte se adapta à resposta; a entrevista não é um questionário fixo.
- Você pode pedir um resumo, mudar o foco ou encerrar a análise quando quiser.

## Formato do relatório

O relatório final registra escopo, premissas e limites da revisão. Apresenta os cenários priorizados em uma tabela:

| Prioridade | Ameaça | STRIDE | Justificativa |
|---|---|---|---|

Cada ameaça recebe apenas as categorias STRIDE sustentadas pelo cenário, com justificativa. STRIDE descreve a natureza da ameaça; não comprova exploração nem mede gravidade.

- **S — Spoofing:** falsificação de identidade
- **T — Tampering:** adulteração
- **R — Repudiation:** repúdio
- **I — Information Disclosure:** divulgação de informação
- **D — Denial of Service:** negação de serviço
- **E — Elevation of Privilege:** elevação de privilégio

O relatório também inclui ações prioritárias com critérios de validação, evidências pendentes e riscos residuais. As prioridades são qualitativas e justificadas; não são pontuações CVSS.

## Evidências e segurança

As respostas e os artefatos disponíveis fundamentam a análise. Uma declaração do usuário não conta automaticamente como prova técnica. A skill separa fatos observados, declarações, hipóteses e itens não verificados. Use exemplos sanitizados; não compartilhe senhas, tokens ou dados pessoais reais.

A entrevista é uma revisão defensiva. Ela não certifica a segurança do sistema nem executa testes de intrusão automaticamente.
