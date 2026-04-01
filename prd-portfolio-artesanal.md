# PRD — Portfólio de Receitas Artesanais
**Alta Coquetelaria Caseira**
Para uso por desenvolvedores, designers e IAs

---

## 1. Visão do produto

### O que é

Um portfólio digital pessoal para documentar receitas de alta coquetelaria artesanal — licores, bitters, xaropes, fermentados e outros insumos desenvolvidos com precisão técnica e identidade autoral.

### Para que serve

Funciona como referência técnica pessoal: registro sistemático de receitas, parâmetros de processo, decisões de formulação e notas de ajuste. Cada receita documentada é uma versão validada e reproduzível, consultável a qualquer momento — no bar, no evento, na cozinha.

### O que não é

Não é um blog público. Não é um canal de venda. Não é voltado para ensino ou audiência externa. O público primário é o próprio autor.

### Compatibilidade futura

Por ser HTML estático puro, cada receita pode ser embeddada via `<iframe>` em sites externos — Framer, Webflow ou qualquer plataforma que suporte embed — sem nenhuma adaptação.

---

## 2. Persona

**Ederson — bartender e autor do portfólio**

- Freelance com atuação em eventos e contexto doméstico
- Produz insumos artesanais com rigor técnico e linguagem científica
- Consulta receitas durante o preparo — precisa de leitura rápida sob pressão
- Documenta versões finais validadas, não rascunhos
- Usa o portfólio como extensão da memória técnica, não como vitrine

**Necessidades principais:**
- Encontrar uma receita específica em menos de 10 segundos
- Ler os parâmetros críticos (temperatura, tempo, ABV) em 2 segundos
- Confiar que o que está documentado é exato e reproduzível
- Adicionar novas receitas sem inconsistência visual ou estrutural
- Visualizar o design completo da receita antes de publicar

---

## 3. Arquitetura de navegação

### 3 níveis de profundidade

```
Nível 1 — Índice (/)
  └── Nível 2 — Página de categoria (/licores/, /xaropes/, ...)
        └── Nível 3 — Receita individual (/licores/flor-de-sabugueiro.html)
```

### URLs

```
/                                         → índice geral
/licores/                                 → todas as receitas de licores
/licores/flor-de-sabugueiro.html          → receita individual
/bitters/                                 → todas as receitas de bitters
/xaropes/gengibre-demerara.html           → receita individual
```

### Princípio de geração

- **Receitas individuais** → arquivos HTML criados manualmente a partir do template
- **Páginas de categoria** → geradas automaticamente por JavaScript lendo os metadados `<meta>` de cada receita
- **Índice** → gerado automaticamente por JavaScript lendo os metadados de todas as receitas

O autor nunca edita o índice nem as páginas de categoria manualmente.

---

## 4. Página — Índice (`/`)

### Descrição

Página de entrada do portfólio. Apresenta o portfólio e exibe as 9 categorias como cards de navegação. Modo light.

### Componentes

**Nav (sticky)**
- Logo/nome do portfólio à esquerda em Gambetta
- Links de navegação à direita em Satoshi
- Background branco, border-bottom sutil

**Hero**
- Título em Gambetta com subtítulo em itálico
- Descrição curta (1–2 linhas)
- Contadores: número de categorias e total de receitas publicadas

**Grid de categorias**
- 9 cards — um por categoria
- Cada card: ícone ou acento colorido da categoria, nome, número de receitas
- Clique navega para a página da categoria

**Footer**
- Nome do portfólio

### Critérios de aceite

- [ ] Grid de categorias reflete automaticamente o número real de receitas em cada categoria
- [ ] Contador total de receitas atualiza sem edição manual
- [ ] Clique em categoria navega para `/categoria/`
- [ ] Nav permanece visível durante scroll
- [ ] Página carrega sem dependência de backend

---

## 5. Página — Categoria (`/licores/`, `/xaropes/`, ...)

### Descrição

Lista todas as receitas de uma categoria em grid de cards. Gerada automaticamente por JavaScript. Modo light.

### Componentes

**Header da categoria**
- Nome da categoria com acento colorido correspondente
- Número de receitas na categoria
- Descrição curta da categoria (1–2 linhas)

**Grid de cards de receita**
- 3 colunas em desktop, 1 em mobile
- Card featured (span 2 colunas) para receita mais recente ou em destaque
- Cada card: barra de acento, nome, descrição curta, tags, métricas rápidas

**Breadcrumb**
- Início → Nome da categoria

### Como é gerada

JavaScript lê os metadados `<meta>` de todos os arquivos HTML na pasta da categoria e monta os cards automaticamente. Nenhuma edição manual necessária.

```html
<!-- metadados obrigatórios em cada receita — usados para gerar os cards -->
<meta name="receita-categoria"        content="licores">
<meta name="receita-slug"             content="flor-de-sabugueiro">
<meta name="receita-nome"             content="Flor de Sabugueiro">
<meta name="receita-subtitulo"        content="Sous Vide">
<meta name="receita-descricao"        content="Licor artesanal estilo St-Germain...">
<meta name="receita-rendimento"       content="750ml">
<meta name="receita-abv"              content="20%">
<meta name="receita-tempo"            content="2h30">
<meta name="receita-nome-cientifico"  content="Sambucus nigra">
<meta name="receita-tags"             content="sous vide, floral, 20% ABV">
<meta name="receita-destaque"         content="true">
```

### Critérios de aceite

- [ ] Nova receita aparece na página da categoria após commit e push — sem edição manual
- [ ] Receita marcada como destaque (`receita-destaque: true`) ocupa card featured
- [ ] Breadcrumb funcional em todos os níveis
- [ ] Grid responsivo em 375px e 768px

---

## 6. Página — Receita Individual

### Descrição

Documento técnico completo de uma receita. Arquivo HTML criado manualmente a partir do `template-base-receita.html`. Modo dark. Estrutura fixa — todas as receitas seguem exatamente o mesmo template.

### Preview visual

O autor abre o arquivo HTML diretamente no browser e vê o documento completo com design final, antes de publicar. O que aparece no browser é idêntico ao que aparece publicado.

### Seções obrigatórias

**Hero**
- Label de categoria (10px uppercase, cor acento)
- Título em Gambetta (nome do insumo)
- Subtítulo em itálico (técnica ou característica)
- Badge de rendimento (canto direito)

**Stats Row — 4 slots livres**
- 4 métricas específicas da receita
- Regra: os 4 números que o bartender precisa antes de começar
- Valores curtos (números, unidades, siglas) — nunca frases
- Labels máximo 2 palavras

**Ingredientes**
- Grid 2 colunas
- Ingrediente principal em card destaque (full width, borda de acento)
- Cada card: dot colorido · quantidade exata · nome · nota técnica

**Passo a Passo**
- Linha do tempo vertical numerada
- Tag de alerta inline quando houver risco ou detalhe crítico

**Tabela de ordem de adição** *(quando aplicável)*
- Presente quando a receita tiver compostos com timing diferente
- Colunas: Ingrediente · Quando adicionar · Motivo

**Notas Técnicas**
- Grid 2 colunas, mínimo 2 cards
- Pelo menos 1 card warn quando houver risco de processo

**Footer**
- `{nome da receita} · {categoria} · {nome científico ou técnico}`

### Seções opcionais

- Harmonizações sugeridas
- Variações da receita
- Changelog da receita (histórico de ajustes)

### Critérios de aceite

- [ ] Stats row legível sem scroll em viewport ≥ 375px
- [ ] Ingrediente principal sempre em full width
- [ ] Todos os steps conectados pela linha vertical sem quebra
- [ ] Tabela de ordem de adição presente quando houver ≥ 2 compostos com timing diferente
- [ ] Mínimo 2 notas técnicas, sendo 1 warn quando houver risco
- [ ] Metadados `<meta>` completos no `<head>`
- [ ] Arquivo abre e renderiza corretamente no browser sem servidor local
- [ ] Embed via `<iframe>` funciona sem erros (Framer, Webflow)

---

## 7. Categorias

9 categorias com paleta de acento própria definida em `ds-portfolio-artesanal.md`.

| # | Categoria | Pasta | Exemplos |
|---|---|---|---|
| 1 | Licores | `/licores/` | Flor de sabugueiro, licor de café |
| 2 | Bitters e Amaros | `/bitters/` | Bitter de laranja, amaro caseiro |
| 3 | Cordiais | `/cordiais/` | Cordial de maracujá, elderflower |
| 4 | Xaropes | `/xaropes/` | Simples, demerara, orgeat, lavanda |
| 5 | Vermutes e Aromatizados | `/vermutes/` | Vermute branco, quinado |
| 6 | Fermentados | `/fermentados/` | Kombucha, ginger beer, kefir |
| 7 | Extratos | `/extratos/` | Tintura de baunilha, oleoresinas |
| 8 | Drinks | `/drinks/` | Receitas autorais, clássicos |
| 9 | Refrigerantes | `/refrigerantes/` | Água tônica, ginger ale, sodas |

---

## 8. Estrutura de arquivos do repositório

```
/
├── index.html                        ← índice (gerado por JS, não editar)
├── ds-portfolio-artesanal.md         ← Design System
├── prd-portfolio-artesanal.md        ← este documento
├── template-base-receita.html             ← template base para novas receitas
├── assets/
│   ├── fonts/
│   │   ├── Gambetta/                 ← arquivos .woff2 locais
│   │   └── Satoshi/                  ← arquivos .woff2 locais
│   ├── css/
│   │   ├── base.css                  ← tokens, reset, tipografia
│   │   ├── dark.css                  ← paleta dark mode (receitas)
│   │   └── light.css                 ← paleta light mode (índice, categorias)
│   └── js/
│       └── gerar-index.js            ← lê metadados e gera cards automaticamente
├── licores/
│   ├── index.html                    ← página da categoria (gerada por JS)
│   └── flor-de-sabugueiro.html       ← receita individual
├── bitters/
├── cordiais/
├── xaropes/
├── vermutes/
├── fermentados/
├── extratos/
├── drinks/
└── refrigerantes/
```

---

## 9. Fluxo de trabalho — adicionar nova receita

```
1. Duplicar template-base-receita.html
2. Renomear para o nome da receita (ex: gengibre-demerara.html)
3. Mover para a pasta da categoria (ex: /xaropes/)
4. Preencher os dados: ingredientes, passos, stats row, notas
5. Preencher os metadados <meta> no <head>
6. Abrir no browser para verificar o design
7. Revisar contra o checklist do Design System (seção 11)
8. GitHub Desktop: Commit → Push
9. Site atualizado em ~1 minuto
```

A página da categoria e o índice atualizam automaticamente no passo 9.

---

## 10. Regras de negócio

### Publicação de receitas

- Receita só publicada com medidas exatas — faixas como "20–25g" indicam receita em desenvolvimento
- Rendimento calculado com base em perdas reais do processo
- ABV final calculado quando a receita contiver ingredientes alcoólicos
- Shelf life documentado com base em parâmetro técnico (ABV, pH ou Brix)

### Stats Row

- 4 slots obrigatórios — nunca deixar vazio
- Valores curtos: números, unidades, siglas — nunca frases
- Labels máximo 2 palavras

### Categorias

- Cada receita pertence a exatamente 1 categoria
- A categoria define a paleta de acento e a pasta do arquivo
- Categoria não muda após publicação

### Notas Técnicas

- Toda receita com risco de processo deve ter pelo menos 1 nota warn
- Shelf life aparece como nota técnica em toda receita que produza insumo armazenável

### Metadados

- Todos os campos `<meta>` são obrigatórios antes de publicar
- `receita-destaque: true` em no máximo 1 receita por categoria

### Fontes

- Desenvolvimento: Fontshare CDN
- Produção: arquivos locais em `/assets/fonts/`
- Fallback obrigatório: `'Georgia', serif` e `'Helvetica Neue', sans-serif`

---

## 11. Padrões de qualidade

### Técnicos
- Medidas exatas em todas as receitas publicadas
- Rendimento, ABV e shelf life calculados e documentados
- Todos os metadados `<meta>` preenchidos

### Visuais
- Paleta de acento correta para a categoria
- Fontes Gambetta + Satoshi com fallback declarado
- Grid de 8px em todos os espaçamentos
- Responsividade testada em 375px e 768px
- Contraste verificado conforme seção 12 do Design System

### De conteúdo
- Stats row com 4 métricas específicas e relevantes
- Nome científico presente quando ingrediente principal for botânico
- Mínimo 2 notas técnicas, sendo 1 warn quando aplicável

---

## 12. Stack técnico

| Componente | Tecnologia | Motivo |
|---|---|---|
| Hospedagem | GitHub Pages | Gratuito, versionado, sem servidor |
| Páginas | HTML + CSS + JS vanilla | Portabilidade máxima, embed via iframe |
| Geração de índice | JavaScript no browser | Sem build, sem ferramentas extras |
| Fontes | Fontshare CDN (dev) + local (prod) | Estabilidade em produção |
| Controle de versão | Git + GitHub Desktop | Interface visual, sem terminal |

---

## 13. Arquivos de contexto para o Claude Projetos

Com estes arquivos carregados no Projeto, qualquer nova receita pode ser gerada com um único prompt.

| Arquivo | Função |
|---|---|
| `ds-portfolio-artesanal.md` | Tokens de cor, tipografia, componentes, regras de design |
| `prd-portfolio-artesanal.md` | Arquitetura, categorias, regras de negócio, fluxo de trabalho |
| `template-base-receita.html` | Template HTML base — a ser criado na próxima etapa |

---

*PRD — Portfólio Alta Coquetelaria Caseira*
