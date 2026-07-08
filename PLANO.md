# Plano — LP de Planos da Clint (V1 e V2)

## Objetivo
Landing page de planos da Clint em duas versões (V1 e V2), com a **copy exata do PDF** (`LANDING PAGE - planos.pdf`) e a **identidade visual de** `https://www.useclint.com/clint_vs_time_interno.html` (cores, formato, tipografia). A única diferença entre V1 e V2 é a **disposição da seção de planos**, conforme o próprio PDF define ("V2 - muda só a disposição dos planos").

## Identidade extraída da página de referência

### Cores (CSS variables idênticas)
| Variável | Valor | Uso |
|---|---|---|
| `--purple` | `#4E3AFF` | Destaques, itálicos em títulos, labels |
| `--purple-2` | `#8E7CFF` | Itálicos sobre fundo escuro |
| `--purple-soft` | `#F5F3FF` / `--purple-deep` `#2A1A99` | Fundos suaves / gradiente |
| `--pink` | `#FF2D6F` | Labels em fundo escuro, acentos |
| `--ink` | `#0E0B2E` | Texto principal e fundos escuros (hero, CTA final, footer) |
| `--ink-2` | `#3A3554` / `--muted` `#7A7596` | Texto secundário |
| `--line` | `#E7E3FB` / `--line-2` `#D6D0F5` | Bordas |
| `--paper` | `#FAFAFE` | Fundo de seções alternadas |
| WhatsApp | `#25D366` / hover `#1FB855` | Botões de WhatsApp |

### Tipografia
- **Poppins** (300–800) — títulos e corpo. H1/H2 com `letter-spacing` negativo, `clamp()` fluido, palavras-chave em `<em>` itálico roxo.
- **JetBrains Mono** (400–500) — kickers/labels de seção (`.label`, uppercase, tracking `.2em`, traço antes), tags, valores.

### Formato / componentes reutilizados
- Header fixo com blur, logo Clint (SVG), nav, botão verde WhatsApp; menu drawer no mobile (mesmo JS da referência).
- Kicker `.label` (— TEXTO) antes de cada H2 de seção.
- Hero escuro (`--ink`) com gradientes radiais roxo/rosa.
- Cards com `border-radius` 20–24px, borda `--line`; card destacado escuro com os mesmos gradientes.
- Toggle de cadência (Semanal/Quinzenal) — reproduzido na seção "Configure a sua operação", como o PDF pede ("fazer como nessa página").
- CTA final escuro centralizado + footer escuro completos da referência.

## Estrutura da página (as duas versões)
1. **Header** — idêntico à referência.
2. **Hero** (escuro) — H1 "Como funcionam os planos da Clint", sub, CTA "Ver planos" (âncora `#planos`) e linha "2.000+ operações ativas · Setup em 30 dias · Parceiro oficial Meta".
3. **Os planos** (`#planos`) — *única seção que muda entre V1 e V2* (abaixo).
4. **Setup completo → "Configure a sua operação"** — texto do PDF + toggle Semanal/Quinzenal (identidade da página de referência).
5. **A escolha certa** — "Qual é o melhor plano para mim" com **tabela comparativa** PLATAFORMA × SETUP COMPLETO (6 critérios do PDF).
6. **Em quanto tempo funciona** — "30 dias..." + 3 cards de timeline (Dias 1–10, 11–20, 21–30).
7. **Próximo passo** (CTA final escuro) — "Fale com a Clint e escolha seu plano" + botão verde "Falar com a IA no WhatsApp".
8. **FAQ** — "Ainda com dúvidas?" com 6 perguntas em accordion (`<details>`, sem JS).
9. **Footer** — idêntico à referência.

## V1 × V2 (seção de planos)
- **V1** (`planos_v1.html`): dois cards **lado a lado**. Card 1 branco — tag "CRM completo", nome "Plataforma", preço "R$ 149/usuário/mês". Card 2 **escuro em destaque** — tag "Plataforma + IA + Squad humana", nome "Setup completo", preço "Sob medida", squad detalhada (Gestor externo · Especialista em IA · Analista de dados) e nota "*Veja qual é o melhor pra você na seção abaixo."
- **V2** (`planos_v2.html`): planos em **linhas horizontais empilhadas** (full-width), com tags "Plano 1" / "Plano 2" como no PDF. Plano 2 se chama "Plataforma + IA + Squad humana" (sem o título "Setup completo") e lista enxuta de 4 itens, como na página 4 do PDF. O bloco "Configure a sua operação" vira um **banner gradiente** logo abaixo dos planos (fluxo da V2 no PDF).

## Responsive (mobile-first nos pontos críticos)
- Breakpoint principal `980px` (o mesmo da referência).
- **Tabela comparativa**: no desktop, grid de 3 colunas (critério | Plataforma | Setup completo) com cabeçalho escuro. **No mobile cada linha vira um card empilhado**: critério no topo e os dois valores abaixo, cada um identificado pelo nome do plano via `::before` (mono, uppercase) — nada de scroll horizontal.
- Cards de planos, timeline e footer colapsam para 1 coluna; toggle de cadência ocupa 100% da largura; menu vira drawer lateral.
- Tipografia fluida com `clamp()` — títulos nunca estouram no mobile.

## Copy
- 100% extraída do PDF, sem alterações. CTAs usados: "Ver planos" e "Falar com a IA no WhatsApp" (ambos do PDF).
- Único ajuste: o PDF traz um "da" duplicado em "O time **da da** Clint te acompanha..." (FAQ) — tratado como erro de digitação e escrito "O time da Clint". Reverter se for intencional.
- Links de WhatsApp, nav e footer: os mesmos da página de referência.

## Arquivos
- `PLANO.md` — este plano
- `planos_v1.html` — versão 1 (cards lado a lado)
- `planos_v2.html` — versão 2 (planos empilhados, tags Plano 1/Plano 2)

Ambos são HTML únicos e autossuficientes (CSS inline, Google Fonts, JS mínimo: drawer mobile, sombra do header e toggle de cadência), prontos pra publicar ao lado das demais páginas do site.
