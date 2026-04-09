# 📌 Como publicar uma receita nova no portfólio

## Passo a passo

1. **Criar o arquivo HTML da receita**
   - Usar `template-base-receita.html` como base
   - Preencher todos os metadados `<meta>` no `<head>`
   - Preencher ingredientes, passos, notas técnicas
   - Trocar os tokens `--accent-*` no `:root` conforme a paleta da categoria
   - Salvar como `/categoria/nome-da-receita.html`
   - Commit no GitHub

2. **Adicionar a receita no catálogo**
   - Abrir `receitas.json` na raiz do GitHub → lápis (Edit)
   - Adicionar uma linha nova dentro do array `receitas`:
```json
     { "categoria": "bitters", "slug": "bitter-de-laranja", "destaque": false }
```
   - Commit

3. **Pronto.** A receita aparece automaticamente:
   - Na página da categoria (`/bitters/`)
   - No contador da página inicial
   - No card da categoria na página inicial

---

## Regras importantes

- **`categoria`** → deve bater exatamente com o nome da pasta (ex: `bitters`, não `Bitters`)
- **`slug`** → nome do arquivo HTML **sem** o `.html` no final
- **`destaque`** → `true` só pra **UMA** receita por categoria (regra do PRD). Vira card grande na página da categoria. Nas demais, usar `false`.

---

## As 11 categorias e suas pastas

| # | Categoria | Pasta | Paleta Dark Mode |
|---|---|---|---|
| 1 | Licores | `/licores/` | `#C9A84C` dourado |
| 2 | Bitters e Amaros | `/bitters/` | `#A0622A` âmbar escuro |
| 3 | Cordiais | `/cordiais/` | `#C4632A` terracota |
| 4 | Xaropes | `/xaropes/` | `#6A9E52` verde-salva |
| 5 | Coulis | `/coulis/` | `#B04A3A` vermelho tijolo |
| 6 | Shrubs e Ácidos | `/shrubs/` | `#9A6E30` âmbar-mel |
| 7 | Vermutes e Aromatizados | `/vermutes/` | `#8B3A5A` vinho rosado |
| 8 | Fermentados | `/fermentados/` | `#7A8C5A` ocre verde |
| 9 | Extratos | `/extratos/` | `#6B5A8A` roxo profundo |
| 10 | Espumas | `/espumas/` | `#7A8E9A` azul-ardósia |
| 11 | Sodas | `/sodas/` | `#4A9A7A` verde-água |

Paletas completas (Dark + Light Mode) no `ds-portfolio-artesanal.md`.

---

## Arquivos do sistema (não mexer à toa)

- `index.html` (raiz) → página inicial automatizada
- `/{categoria}/index.html` → páginas de categoria, mesmo arquivo genérico em todas
- `receitas.json` → catálogo único do portfólio
- `template-base-receita.html` → template base pra criar receitas novas

---

## Em caso de dúvida

- **Paletas de cor:** consultar `ds-portfolio-artesanal.md` (GitHub) ou `design-system.md` (Projeto Claude)
- **Regras de módulos e componentes:** consultar seção 13 do `ds-portfolio-artesanal.md`
- **Checklist de qualidade por receita:** seção 11 do `ds-portfolio-artesanal.md`
