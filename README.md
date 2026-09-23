# Skills para PPTX

Catálogo de skills para transformar dados e fontes de negócio em apresentações PowerPoint executivas, editáveis e rastreáveis.

> Este repositório documenta as skills e aponta para suas fontes. Ele não redistribui os arquivos `SKILL.md` nem substitui as licenças dos repositórios originais.

## Skills incluídas

### 1. `data-storytelling`

Transforma dados brutos em uma narrativa orientada à decisão. Ajuda a organizar contexto, problema, evidências, insights, recomendações e próximos passos, evitando “data dump” e separando fato de interpretação.

- [Página no skills.sh](https://skills.sh/wshobson/agents/data-storytelling)
- [Repositório no GitHub](https://github.com/wshobson/agents)

### 2. `pptx-deck-context`

Prepara o contrato do deck antes da diagramação: audiência, decisão, framework narrativo, fontes, rastreabilidade, paleta, tipografia, espaçamento e especificação slide a slide.

- [Página no skills.sh](https://skills.sh/wshobson/agents/pptx-deck-context)
- [Repositório no GitHub](https://github.com/wshobson/agents)

### 3. `pptx-reference-deck-analysis`

Analisa um PowerPoint de referência como evidência visual, extraindo proporção, tema, fontes, cores, layouts, ritmo e padrões de composição sem alterar ou copiar o deck original.

- [Página no skills.sh](https://skills.sh/wshobson/agents/pptx-reference-deck-analysis)
- [Repositório no GitHub](https://github.com/wshobson/agents)

### 4. `pptx`

Cria, lê, edita, renderiza e valida arquivos `.pptx` e `.potx`. Inclui orientações para `python-pptx`, edição OOXML, gráficos nativos, notas, validação estrutural e QA visual.

- [Página no skills.sh](https://skills.sh/anthropics/skills/pptx)
- [Repositório no GitHub](https://github.com/anthropics/skills)

### 5. `prepare-analysis-input`

Prepara fontes brutas — Excel, CSV, PDF, Word, imagens, e-mails, transcrições e textos — em um pacote isolado, normalizado e rastreável para a etapa de análise. Não cria o deck nem define a storyline.

- Skills.sh: não localizado no catálogo no momento da publicação
- [Repositório no GitHub](https://github.com/armel-felipe/prepare-analysis-input)

### 6. `frontend-slides`

Cria apresentações HTML ricas em animação, sem dependências, com stage fixo 16:9 e estética anti-"AI slop". Converte PowerPoint para web (preservando imagens e conteúdo) e exporta HTML para PDF. Não gera `.pptx` diretamente — para isso, combine com a skill `pptx`.

- [Página no skills.sh](https://skills.sh/zarazhangrui/frontend-slides)
- [Repositório no GitHub](https://github.com/zarazhangrui/frontend-slides)

### 7. `powerpoint`

Cria, lê, edita, renderiza e valida arquivos `.pptx` e `.potx` via `pptxgenjs` e edição OOXML. Inclui gráficos nativos, notas, validação estrutural e QA visual. Complementar à skill `pptx` (mesma família, com ênfase em `pptxgenjs`).

- [Página no skills.sh](https://skills.sh/anthropics/skills/powerpoint)
- [Repositório no GitHub](https://github.com/anthropics/skills)

## Fluxo recomendado

```text
prepare-analysis-input (opcional)
        ↓
data-storytelling
        ↓
pptx-deck-context
        ↓
pptx-reference-deck-analysis (se houver deck de referência)
        ↓
pptx  (ou powerpoint, para geração via pptxgenjs)
        ↓
QA de conteúdo, estrutura e renderização
```

### Caminho alternativo: HTML → PPTX

Para converter uma apresentação HTML existente em `.pptx`, o fluxo é de reconstrução (não conversão automática):

```text
frontend-slides (cria/edita a apresentação HTML; exporta para PDF)
        ↓
pptx (reconstrói cada slide como .pptx a partir do conteúdo e do design do HTML)
        ↓
QA de conteúdo, estrutura e renderização
```

## Instalação pelo skills.sh

O comando padrão é:

```bash
npx skills add <owner>/<repo>@<skill>
```

### Claude Code

```bash
npx skills add wshobson/agents@data-storytelling -a claude-code
npx skills add wshobson/agents@pptx-deck-context -a claude-code
npx skills add wshobson/agents@pptx-reference-deck-analysis -a claude-code
npx skills add anthropics/skills@pptx -a claude-code
npx skills add github.com/armel-felipe/prepare-analysis-input -a claude-code
npx skills add zarazhangrui/frontend-slides -a claude-code
npx skills add anthropics/skills@powerpoint -a claude-code
```

Ou instale o repositório completo e selecione as skills desejadas quando o CLI solicitar:

```bash
npx skills add wshobson/agents -a claude-code
npx skills add anthropics/skills -a claude-code
npx skills add https://github.com/armel-felipe/prepare-analysis-input.git -a claude-code
npx skills add zarazhangrui/frontend-slides -a claude-code
```

### ChatGPT / Codex

O ChatGPT na web não possui um instalador `npx skills` nativo. Para uso com o ecossistema OpenAI, a instalação compatível é no **Codex CLI**:

```bash
npx skills add wshobson/agents@data-storytelling -a codex
npx skills add wshobson/agents@pptx-deck-context -a codex
npx skills add wshobson/agents@pptx-reference-deck-analysis -a codex
npx skills add anthropics/skills@pptx -a codex
npx skills add https://github.com/armel-felipe/prepare-analysis-input.git -a codex
npx skills add zarazhangrui/frontend-slides -a codex
npx skills add anthropics/skills@powerpoint -a codex
```

No ChatGPT web, a alternativa manual é abrir o link do GitHub, copiar o `SKILL.md` da skill desejada e adicioná-lo às instruções/arquivos de um GPT personalizado ou de um projeto, respeitando a licença do repositório original.

## Instalação manual

Para agentes que não usam o CLI, copie o `SKILL.md` da skill para o diretório de skills do agente. Os diretórios mais comuns são:

```text
Claude Code: ~/.claude/skills/<nome-da-skill>/SKILL.md
Codex:       ~/.codex/skills/<nome-da-skill>/SKILL.md
OpenCode:    ~/.config/opencode/skills/<nome-da-skill>/SKILL.md
Projeto:     .opencode/skills/<nome-da-skill>/SKILL.md
```

## Licenças e atribuição

Consulte a licença de cada repositório antes de redistribuir ou modificar uma skill. As skills `pptx` e `powerpoint` do repositório `anthropics/skills` contêm termos próprios; a skill `frontend-slides` do repositório `zarazhangrui/frontend-slides` é distribuída sob licença MIT. Este catálogo não altera esses termos.
