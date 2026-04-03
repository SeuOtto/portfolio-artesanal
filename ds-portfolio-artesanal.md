# Design System — Portfólio de Receitas Artesanais
**Alta Coquetelaria Caseira**
Para uso por desenvolvedores, designers e IAs

---

## 0. Princípios

Este Design System governa todos os documentos e páginas do portfólio de receitas artesanais. Toda decisão visual parte de quatro premissas:

1. **Identidade antes de estética** — cada cor, fonte e espaço comunica algo. Nada é decorativo sem função.
2. **Fixo + variável** — a identidade é fixa; o acento de categoria é variável. Nunca o contrário.
3. **Legibilidade é inegociável** — contraste mínimo de 4.5:1 em todos os textos principais.
4. **Grid de 8px** — todo espaçamento, padding, gap, margin e dimensão de componente é múltiplo de 8px. Exceções permitidas apenas em border-radius (pode usar 4px) e tamanhos de fonte (escala tipográfica própria).

---

## 1. Sobre o uso de Hex vs rgba

A distinção é funcional e deve ser seguida consistentemente:

**Hex** → cores sólidas e opacas. Usado quando a cor precisa ser exata e não transparente.
- Textos
- Acentos primários
- Fundo principal da página

**rgba** → quando a transparência é parte intencional do efeito visual. O fundo aparece levemente através da superfície, criando profundidade e coesão.
- Superfícies de cards
- Bordas
- Fundos de badges e tags
- Estados hover

```
REGRA: se o elemento precisa "respirar" sobre o fundo → use rgba.
       se o elemento precisa de cor exata e sólida    → use Hex.
```

---

## 2. Paleta Dark Mode (receitas individuais)

Aplicada em todos os documentos de receita.

### Fundos

| Token | Formato | Valor | Uso |
|---|---|---|---|
| `--bg-primary` | Hex | `#1C2B1A` | Fundo principal |
| `--bg-surface` | rgba | `rgba(255,255,255,0.03)` | Cards e superfícies |
| `--bg-surface-hover` | rgba | `rgba(255,255,255,0.056)` | Estado hover de cards |

### Texto

| Token | Formato | Valor | Ratio | Uso |
|---|---|---|---|---|
| `--text-primary` | Hex | `#F5F0E8` | 13.13:1 AAA | Texto corrido, parágrafos |
| `--text-secondary` | rgba | `rgba(245,240,232,0.72)` | 7.45:1 AAA | Descrições, corpo de steps |
| `--text-muted` | rgba | `rgba(245,240,232,0.45)` | 3.82:1 AA Large | Notas, sublegendas |
| `--text-hint` | rgba | `rgba(245,240,232,0.38)` | 3.13:1 AA Large | Rodapés, metadados |

> `--text-muted` e `--text-hint` são usados apenas em elementos decorativos e de contexto, nunca em texto corrido.

### Bordas

| Token | Formato | Valor | Uso |
|---|---|---|---|
| `--border-default` | rgba | `rgba(201,168,76,0.25)` | Bordas padrão |
| `--border-emphasis` | rgba | `rgba(201,168,76,0.50)` | Card de ingrediente destaque |
| `--border-subtle` | rgba | `rgba(245,240,232,0.08)` | Divisores internos leves |

---

## 3. Paleta Light Mode (índice / impressão)

Aplicada na página de índice e como base para impressão. O verde `#1C2B1A` migra de fundo para cor de texto — mantendo a identidade botânica em ambos os modos.

### Fundos

| Token | Formato | Valor | Uso |
|---|---|---|---|
| `--bg` | Hex | `#F2F5F0` | Fundo principal — subtom verde sutil |
| `--bg-surface` | Hex | `#FFFFFF` | Cards e superfícies |
| `--bg-surface-2` | Hex | `#F7FAF6` | Rodapé de cards, áreas secundárias |
| `--bg-hover` | rgba | `rgba(28,43,26,0.04)` | Estado hover |

### Texto

| Token | Formato | Valor | Ratio | Uso |
|---|---|---|---|---|
| `--text-primary` | Hex | `#1C2B1A` | 13.54:1 AAA | Títulos, corpo principal |
| `--text-secondary` | rgba | `rgba(28,43,26,0.65)` | 4.64:1 AA | Descrições, corpo de cards |
| `--text-muted` | rgba | `rgba(28,43,26,0.52)` | 3.21:1 AA Large | Notas, placeholders |
| `--text-hint` | rgba | `rgba(28,43,26,0.50)` | 3.00:1 AA Large | Metadados, rodapés |

### Bordas

| Token | Formato | Valor | Uso |
|---|---|---|---|
| `--border-default` | rgba | `rgba(28,43,26,0.10)` | Bordas padrão de cards |
| `--border-subtle` | rgba | `rgba(28,43,26,0.06)` | Divisores internos |

### Acento — Light Mode

| Token | Formato | Valor | Ratio | Uso |
|---|---|---|---|---|
| `--accent` | Hex | `#A07830` | 3.66:1 | Elementos ≥ 18px — títulos, stats |
| `--accent-small` | Hex | `#7A5A1E` | 5.77:1 AA | Texto < 18px — labels, categorias |
| `--accent-mid` | Hex | `#C9A84C` | — | Barras decorativas, elementos não-texto |
| `--accent-border` | rgba | `rgba(160,120,48,0.22)` | — | Bordas de acento |
| `--accent-bg` | rgba | `rgba(160,120,48,0.07)` | — | Fundo de badges |

> **Regra crítica:** usar `--accent-small` em todo texto de acento abaixo de 18px.

---

## 4. Categorias e Paletas de Acento

O acento é a única cor que muda entre categorias. Ele aparece em: barra lateral do documento, números e valores de destaque, badges e tags, círculo numerado dos steps, título em itálico no hero.

### Tokens de acento (nomenclatura fixa — valores trocam por categoria)

| Token | Formato | Uso |
|---|---|---|
| `--accent-primary` | Hex | Barra lateral, círculo de step, ícones |
| `--accent-light` | Hex | Quantidades, subtítulos, valores numéricos |
| `--accent-border` | rgba | Bordas de cards com acento |
| `--accent-bg` | rgba | Fundo de badges e tags |

---

### Categoria 1 — Licores
*Qualquer licor artesanal: floral, cítrico, herbal, spiced, cremoso*

| Token | Dark Mode | Light Mode |
|---|---|---|
| `--accent-primary` | `#C9A84C` | `#A07830` |
| `--accent-light` | `#E8D5A3` | `#7A5A1E` |
| `--accent-border` | `rgba(201,168,76,0.50)` | `rgba(160,120,48,0.22)` |
| `--accent-bg` | `rgba(201,168,76,0.08)` | `rgba(160,120,48,0.07)` |

> Dourado envelhecido — preciosidade botânica, processo artesanal, raridade.

---

### Categoria 2 — Bitters e Amaros
*Bitters caseiros, amaros, aperitivos amargos*

| Token | Dark Mode | Light Mode |
|---|---|---|
| `--accent-primary` | `#A0622A` | `#7A4020` |
| `--accent-light` | `#D4A574` | `#5C2E0E` |
| `--accent-border` | `rgba(160,98,42,0.50)` | `rgba(122,64,32,0.22)` |
| `--accent-bg` | `rgba(160,98,42,0.08)` | `rgba(122,64,32,0.07)` |

> Âmbar escuro — madeira, casca, raiz, processo lento de extração.

---

### Categoria 3 — Cordiais
*Cordiais de frutas, flores, ervas e especiarias*

| Token | Dark Mode | Light Mode |
|---|---|---|
| `--accent-primary` | `#C4632A` | `#9B4520` |
| `--accent-light` | `#E8A882` | `#6B2E10` |
| `--accent-border` | `rgba(196,99,42,0.50)` | `rgba(155,69,32,0.22)` |
| `--accent-bg` | `rgba(196,99,42,0.08)` | `rgba(155,69,32,0.07)` |

> Terracota — fruta madura, casca, doçura equilibrada com acidez.

---

### Categoria 4 — Xaropes
*Xaropes simples, ricos, flavorizados, gomme, oleo-saccharums*

| Token | Dark Mode | Light Mode |
|---|---|---|
| `--accent-primary` | `#6A9E52` | `#3E7235` |
| `--accent-light` | `#A8CC90` | `#2A5E22` |
| `--accent-border` | `rgba(106,158,82,0.50)` | `rgba(62,114,53,0.22)` |
| `--accent-bg` | `rgba(106,158,82,0.08)` | `rgba(62,114,53,0.07)` |

> Verde-salva — erva fresca, extrato aquoso, botânico leve.

---

### Categoria 5 — Vermutes e Aromatizados
*Vermutes brancos e tintos, quinados, vinhos aromatizados*

| Token | Dark Mode | Light Mode |
|---|---|---|
| `--accent-primary` | `#8B3A5A` | `#6B2848` |
| `--accent-light` | `#C48DAA` | `#4A1432` |
| `--accent-border` | `rgba(139,58,90,0.50)` | `rgba(107,40,72,0.22)` |
| `--accent-bg` | `rgba(139,58,90,0.08)` | `rgba(107,40,72,0.07)` |

> Vinho rosado — uva, maceração longa, processo vínico.

---

### Categoria 6 — Fermentados
*Kombucha, kefir de água, ginger beer, jun, kvass, rejuvelac*

| Token | Dark Mode | Light Mode |
|---|---|---|
| `--accent-primary` | `#7A8C5A` | `#4E6030` |
| `--accent-light` | `#B0C494` | `#2E4418` |
| `--accent-border` | `rgba(122,140,90,0.50)` | `rgba(78,96,48,0.22)` |
| `--accent-bg` | `rgba(122,140,90,0.08)` | `rgba(78,96,48,0.07)` |

> Ocre esverdeado — processo vivo, levedura, fermentação natural.

---

### Categoria 7 — Extratos
*Tinturas alcoólicas, extratos botânicos, oleoresinas, concentrados*

| Token | Dark Mode | Light Mode |
|---|---|---|
| `--accent-primary` | `#6B5A8A` | `#4A3A6A` |
| `--accent-light` | `#A898C8` | `#2E2248` |
| `--accent-border` | `rgba(107,90,138,0.50)` | `rgba(74,58,106,0.22)` |
| `--accent-bg` | `rgba(107,90,138,0.08)` | `rgba(74,58,106,0.07)` |

> Roxo profundo — alquimia, extração concentrada, potência aromática.

---

### Categoria 8 — Drinks
*Receitas autorais, releituras de clássicos, drinks de temporada*

| Token | Dark Mode | Light Mode |
|---|---|---|
| `--accent-primary` | `#3A7A8A` | `#1E5A6A` |
| `--accent-light` | `#80C0CC` | `#0C3E4A` |
| `--accent-border` | `rgba(58,122,138,0.50)` | `rgba(30,90,106,0.22)` |
| `--accent-bg` | `rgba(58,122,138,0.08)` | `rgba(30,90,106,0.07)` |

> Azul-petróleo — gelo, coqueteleira, técnica precisa, serviço.

---

### Categoria 9 — Refrigerantes
*Sodas artesanais, águas tônicas, ginger ale, sodas botânicas, shrubs*

| Token | Dark Mode | Light Mode |
|---|---|---|
| `--accent-primary` | `#4A9A7A` | `#2A7A5A` |
| `--accent-light` | `#88CCB4` | `#0E5A3C` |
| `--accent-border` | `rgba(74,154,122,0.50)` | `rgba(42,122,90,0.22)` |
| `--accent-bg` | `rgba(74,154,122,0.08)` | `rgba(42,122,90,0.07)` |

> Verde-água — frescor, carbonatação, leveza.

---

### Resumo visual das categorias

```
1. Licores          →  Dourado        #C9A84C
2. Bitters e Amaros →  Âmbar escuro   #A0622A
3. Cordiais         →  Terracota      #C4632A
4. Xaropes          →  Verde-salva    #6A9E52
5. Vermutes         →  Vinho rosado   #8B3A5A
6. Fermentados      →  Ocre verde     #7A8C5A
7. Extratos         →  Roxo profundo  #6B5A8A
8. Drinks           →  Azul-petróleo  #3A7A8A
9. Refrigerantes    →  Verde-água     #4A9A7A
```

---

## 5. Tipografia

### Famílias

| Função | Família | Fonte |
|---|---|---|
| Display / títulos | `Gambetta` | Fontshare (ITF) — gratuita comercial |
| Corpo / UI | `Satoshi` | Fontshare (ITF) — gratuita comercial |

```html
<style>
  @import url('https://api.fontshare.com/v2/css?f[]=gambetta@300,400,600,300i,400i,600i&f[]=satoshi@300,400,500&display=swap');
</style>
```

> **Dependência externa:** Gambetta e Satoshi dependem do CDN `api.fontshare.com`. Para garantir disponibilidade em produção, fazer download dos arquivos e hospedar no repositório — permitido pela licença ITF.

**Nunca substituir por:** Inter, Roboto, Arial, system-ui, Space Grotesk.

**Fallback seguro se Fontshare estiver indisponível:**
```css
font-family: 'Gambetta', 'Georgia', serif;
font-family: 'Satoshi', 'Helvetica Neue', sans-serif;
```

---

### Escala tipográfica

| Nível | Família | Tamanho | Peso | Uso |
|---|---|---|---|---|
| H1 Hero | Gambetta | `clamp(36px, 5vw, 58px)` | 300 | Título principal da receita |
| H1 Hero itálico | Gambetta italic | igual | 300 | Destaque do título — cor `--accent-light` |
| H2 Seção | Gambetta | `26px` | 400 | Títulos de seção |
| Step title | Gambetta | `18px` | 600 | Título de cada passo |
| Valor numérico grande | Gambetta | `24–40px` | 300–400 | Stats, rendimento, quantidades |
| Body | Satoshi | `14px` | 300 | Texto corrido de steps e notas |
| Label | Satoshi | `13px` | 500 | Nome de ingrediente, título de card |
| Note | Satoshi | `11px` | 400 | Sublabels, notas de ingrediente |
| Tag / badge | Satoshi | `10px` | 500 | Tags de step, alertas |
| Metadata | Satoshi | `10px` | 400–500 | Labels de stats, footer, cabeçalhos |

### Regras tipográficas

- **Letter-spacing em uppercase/metadata:** `0.15em` a `0.25em` — nunca zero
- **Line-height corpo:** `1.65` a `1.75`
- **Line-height títulos:** `1.05` a `1.1`
- **Números:** sempre Gambetta — nunca Satoshi
- **Peso máximo Satoshi:** 500 — 600 e 700 pesam demais sobre fundo escuro
- **Itálico no hero:** sempre na segunda linha ou no substantivo principal — nunca no título inteiro

---

## 6. Espaçamento — Grid de 8px

**Regra:** todo valor de espaçamento é múltiplo de 8px.
**Exceção permitida:** border-radius pode usar 4px (metade da unidade base).
**Exceção:** tamanhos de fonte seguem escala tipográfica própria.

### Escala de espaçamento

| Token | Valor | Múltiplo | Uso típico |
|---|---|---|---|
| `--space-1` | `8px` | 1× | Gap interno mínimo, dot de ingrediente |
| `--space-2` | `16px` | 2× | Padding de cards, gap entre elementos |
| `--space-3` | `24px` | 3× | Padding horizontal de cards maiores |
| `--space-4` | `32px` | 4× | Margin-bottom de section header |
| `--space-5` | `40px` | 5× | Padding bottom de step |
| `--space-6` | `48px` | 6× | Padding top do hero em mobile |
| `--space-7` | `56px` | 7× | Margin-bottom entre seções |
| `--space-8` | `64px` | 8× | Padding top do hero em desktop |
| `--space-10` | `80px` | 10× | Padding bottom da página |

### Border-radius

| Contexto | Valor |
|---|---|
| Tag / badge | `4px` |
| Cards de ingrediente e nota | `8px` |
| Stats row, tabelas, hero badge | `16px` |
| Círculos (step, section header) | `50%` |

---

## 7. Componentes

### 7.1 Barra lateral de categoria

```css
width: 8px;
height: 100%;
background: var(--accent-primary);  /* Hex */
border-radius: 4px;
flex-shrink: 0;
```

---

### 7.2 Card de ingrediente

```
padding: 16px
border-radius: 8px
gap interno: 16px

Padrão:    background --bg-surface (rgba) · border --border-default (rgba)
Hover:     background rgba(accent-primary, 0.06)
Destaque:  border-color --accent-border · background --accent-bg · grid-column 1/-1

Estrutura:
  dot 8×8px  → --accent-primary (Hex)
  quantidade → Gambetta 20px, --accent-light (Hex)
  nome       → Satoshi 13px weight 500, --text-primary (Hex)
  nota       → Satoshi 11px weight 400, --text-muted (rgba)
```

---

### 7.3 Stats Row — 4 slots livres

Não há campos fixos — cada receita define seus 4 indicadores. Regra de seleção: quais são os 4 números que um bartender precisa saber antes de começar esta receita?

```
Layout: grid 4 colunas · separador 1px --border-default
padding por célula: 16px · border-radius: 16px · overflow: hidden

Valor: Gambetta 24px, --accent-light (Hex)
Label: Satoshi 10px uppercase letter-spacing 0.18em, --text-hint (rgba)
```

**HTML template:**
```html
<div class="stats">
  <div class="stat">
    <div class="stat-value"><!-- VALOR --></div>
    <div class="stat-label"><!-- LABEL --></div>
  </div>
  <!-- repetir ×4 -->
</div>
```

**Exemplos por categoria:**

| Categoria | Slot 1 | Slot 2 | Slot 3 | Slot 4 |
|---|---|---|---|---|
| Licor sous vide | `85°C` Temperatura | `2h30` Sous Vide | `20%` ABV | `34g` Açúcar/100ml |
| Xarope | `1:1` Ratio | `15min` Cozimento | `60°Bx` Concentração | `21 dias` Validade |
| Bitter / amaro | `40%` ABV | `3 sem` Maceração | `15ml` Dose padrão | `18 meses` Shelf life |
| Drink | `90ml` Rendimento | `2 pt` Espumante | `8%` ABV estimado | `1 min` Preparo |
| Fermentado | `7–10d` Fermentação 1 | `3–5d` Fermentação 2 | `3,0` pH alvo | `0,5%` ABV |
| Vermute | `750ml` Base | `30 dias` Maceração | `16%` ABV | `6 meses` Shelf life |
| Extrato | `70%` ABV base | `14 dias` Maceração | `5ml` Dose | `24 meses` Shelf life |
| Refrigerante | `500ml` Rendimento | `72h` Carbonatação | `3,2` pH | `7 dias` Validade |

Regras: valores curtos (números, unidades, siglas), labels máximo 2 palavras, 4 slots sempre preenchidos.

---

### 7.4 Step (linha do tempo)

```
Layout: grid [48px | 1fr]

Círculo:   32×32px · 50% · border 2px --accent-primary (Hex)
           background --bg-primary (Hex) · Gambetta 15px --accent-primary

Linha:     2px · --border-default (rgba) · absolute left 24px

Padding conteúdo: 0 0 40px 16px

Título:    Gambetta 18px weight 600, --text-primary (Hex)
Corpo:     Satoshi 14px weight 300, --text-secondary (rgba), line-height 1.75

Tag:       padding 4px 8px · border-radius 4px
           background --accent-bg (rgba) · border --accent-border (rgba)
           texto --accent-light (Hex) · Satoshi 10px weight 500 uppercase
```

---

### 7.5 Tabela

```
border-radius: 8px · overflow: hidden
border: 1px solid --border-default (rgba)

Cabeçalho:  padding 16px · background --accent-bg ×1.25
            Satoshi 10px uppercase letter-spacing 0.2em · --accent-primary (Hex)

Célula:     padding 16px · border-top --border-default (rgba)
            Satoshi 13px · --text-secondary (rgba)
            1ª coluna: weight 500, --text-primary (Hex)

Hover:      background --accent-bg ×0.5
```

---

### 7.6 Card de nota técnica

```
padding: 16px · border-radius: 8px

Padrão:  background --bg-surface (rgba) · border --border-default (rgba)
Warn:    border --accent-border opacity 0.45 · background --accent-bg opacity 0.05

Ícone:   16px · margin-bottom 8px
Título:  Satoshi 11px weight 500 uppercase letter-spacing 0.12em · --accent-primary (Hex)
Corpo:   Satoshi 12px weight 300 · --text-muted (rgba) · line-height 1.65
```

---

### 7.7 Section header

```
Layout: flex align-center gap 16px · margin-bottom 32px

Marcador:  32×32px · 50% · background --accent-primary (Hex)
           texto --bg-primary (Hex) · Satoshi 11px weight 500

Título:    Gambetta 26px weight 400 · --text-primary (Hex)
Linha:     flex 1 · height 1px · --border-default (rgba)
```

---

### 7.8 Hero badge

```
padding: 24px · border-radius: 16px
background: --accent-bg (rgba) · border: --border-default (rgba)

Número: Gambetta 40px weight 300 · --accent-primary (Hex)
Label:  Satoshi 10px weight 400 uppercase letter-spacing 0.15em · --text-hint (rgba)
```

---

## 8. Animações

`fadeUp` aplicado apenas nos elementos de entrada — melhora performance em GitHub Pages.

```css
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(16px); }
  to   { opacity: 1; transform: translateY(0); }
}
```

| Elemento | Delay | Anima? |
|---|---|---|
| Hero | `0s` | Sim |
| Stats row | `0.1s` | Sim |
| Primeiro section header | `0.15s` | Sim |
| Todos os demais | — | Não |

Duração padrão: `0.8s ease both`

---

## 9. Responsividade

| Breakpoint | Ajuste |
|---|---|
| `max-width: 600px` | Hero: 1 coluna, badge oculto |
| `max-width: 600px` | Stats row: 2 colunas |
| `max-width: 600px` | Grid ingredientes: 1 coluna |
| `max-width: 600px` | Grid notas: 1 coluna |
| `max-width: 600px` | Ingrediente destaque: `grid-column: 1` |

---

## 10. O que nunca fazer

| Proibido | Motivo |
|---|---|
| Espaçamentos fora do grid de 8px | Quebra a consistência rítmica do layout |
| Hex em bordas e superfícies | Precisa de transparência — usar rgba |
| rgba em textos e acentos primários | Precisa de cor exata e sólida — usar Hex |
| Trocar `Gambetta` por outra fonte | Quebra a identidade editorial |
| Trocar `Satoshi` por Inter, Roboto ou system-ui | Torna genérico |
| `font-weight` 600 ou 700 em Satoshi | Pesa demais sobre fundo escuro |
| Alterar `--bg-primary` entre receitas | A identidade do portfólio depende do fundo fixo |
| Mais de 1 acento por documento | Uma categoria, um acento — sempre |
| Gradientes ou sombras decorativas | Contra a legibilidade sobre fundo escuro |
| Texto abaixo de 10px | Ilegível em telas menores |
| Acento `#A07830` em texto < 18px no light mode | Contraste insuficiente — usar `--accent-small` |

---

## 11. Checklist para cada nova receita

- [ ] Categoria definida (1 das 9) → tokens de acento aplicados
- [ ] Barra lateral com `--accent-primary` (Hex)
- [ ] Fontes carregadas via Fontshare (Gambetta + Satoshi)
- [ ] Rendimento calculado e correto no hero badge
- [ ] Stats row com 4 métricas específicas da receita
- [ ] Ingrediente principal em card destaque (full width)
- [ ] Todos os passos numerados e conectados pela linha vertical
- [ ] Tabela de ordem de adição presente (quando aplicável)
- [ ] Mínimo 2 notas técnicas
- [ ] Footer com nome · categoria · nome científico ou técnico
- [ ] Todos os espaçamentos no grid de 8px
- [ ] Light mode: texto de acento < 18px usando `--accent-small`
- [ ] Contraste verificado: text-primary ≥ 4.5:1, text-secondary ≥ 4.5:1
- [ ] Responsividade testada em 375px e 768px

---

## 12. Resumo de contraste — referência rápida

| Token | Modo | Ratio | Nível | Uso seguro |
|---|---|---|---|---|
| `--text-primary` | Dark | 13.13:1 | AAA | Qualquer tamanho |
| `--text-secondary` | Dark | 7.45:1 | AAA | Qualquer tamanho |
| `--text-muted` | Dark | 3.82:1 | AA Large | ≥ 18px ou bold ≥ 14px |
| `--text-hint` | Dark | 3.13:1 | AA Large | Metadados decorativos |
| `--accent-primary` | Dark | 6.52:1 | AA | Qualquer tamanho |
| `--accent-light` | Dark | 10.27:1 | AAA | Qualquer tamanho |
| `--text-primary` | Light | 13.54:1 | AAA | Qualquer tamanho |
| `--text-secondary` | Light | 4.64:1 | AA | Qualquer tamanho |
| `--text-muted` | Light | 3.21:1 | AA Large | ≥ 18px ou bold ≥ 14px |
| `--text-hint` | Light | 3.00:1 | AA Large | Metadados decorativos |
| `--accent` | Light | 3.66:1 | AA Large | Texto ≥ 18px apenas |
| `--accent-small` | Light | 5.77:1 | AA | Texto < 18px |

---

*Design System — Portfólio Alta Coquetelaria Caseira*

---

## 13. Módulos opcionais — lógica de uso

O template base é modular. O núcleo visual é fixo; o conteúdo é variável.
A consistência vem dos tokens e da tipografia — não de todas as receitas
terem as mesmas seções.

### Núcleo fixo — presente em toda receita

Nav · Hero · Stats row · Ingredientes · Método · Notas técnicas · Footer

### Stats row — número de slots

| Slots | Classe CSS | Quando usar |
|---|---|---|
| 2 | `stats-2col` | Receitas simples, poucos parâmetros relevantes |
| 3 | `stats-3col` | Exatamente 3 métricas significativas |
| 4 | _(padrão)_ | Receitas complexas com 4 métricas reais |

Nunca inventar métricas para preencher slots. Nunca deixar slot vazio no HTML.

### Grid de ingredientes — variantes

| Variante | Classe CSS | Quando usar |
|---|---|---|
| 1 coluna | `ingredients-grid-1col` | ≤ 4 ingredientes |
| 2 colunas | _(padrão)_ | ≥ 5 ingredientes |
| Com fases | `.ingredients-phase` como separador | Timing radicalmente diferente entre grupos |

`.ingredients-phase` ocupa `grid-column: 1 / -1` e não é um card de ingrediente.

### Método — simples vs. passo a passo

| Componente | Classe CSS | Quando usar |
|---|---|---|
| Método simples | `.method-block` | Processo direto, 1–2 etapas sem parâmetros distintos |
| Passo a passo | `.steps` | 3+ etapas com ações ou parâmetros diferentes |

Nunca usar os dois ao mesmo tempo.

### Tabela de dados — quando incluir

Incluir apenas em um destes casos:
1. **Ordem de adição** — 2+ ingredientes com timing crítico diferente
2. **Parâmetros técnicos** — Brix, pH, sorbato, temperatura

Omitir nos demais casos. Nunca criar a seção vazia.
Componente CSS: `.data-table` (mesmo estilo para ambos os casos).

### Notas técnicas — quantidade mínima

| Situação | Mínimo |
|---|---|
| Receita simples, sem risco | 1 nota (shelf life) |
| Receita com risco de processo | 2 notas (1 warn + shelf life) |
| Receita complexa | 2–4 conforme conteúdo real |

`.warn` apenas quando há risco real. Não usar para recomendações.

### Bloco de fonte/crédito — `.source-block`

Incluir quando a receita tem origem externa documentada.
Omitir completamente em receitas autorais.

### Hero badge — rendimento fixo vs. variável

| Situação | Ação |
|---|---|
| Rendimento fixo | Exibir `.hero-badge` normalmente |
| Rendimento variável / proporcional | Omitir `.hero-badge`; mencionar em nota |

### O que nunca fazer com os módulos

| Proibido | Motivo |
|---|---|
| Método simples + passo a passo juntos | Redundância |
| Tabela vazia | Quebra a lógica visual |
| Inventar métricas para 4 slots | Perde credibilidade |
| `.warn` em recomendações | Desvaloriza alertas reais |
| Fonte/crédito em receita autoral | Contradiz identidade autoral |
| Omitir shelf life em insumos armazenáveis | Informação técnica obrigatória |
