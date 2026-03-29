# Studio de Beleza Brasil — Landing + Serviços Redesign

**Date:** 2026-03-29
**Project:** SBB (Studio de Beleza Brasil)
**Scope:** Redesign homepage com landing page imersiva + página de serviços otimizada

---

## 1. Arquitetura Geral

**Estrutura:** Uma página única com scroll suave entre seções (SPA-style)

### Seções:
1. **Landing/Hero** — Vídeo intro + copy sofisticada + CTA
2. **Serviços** — Header overlay + categorias de serviços + buttons sticky
3. **Testimoniais** — Depoimentos com espaçamento generoso
4. **Contato** — Call-to-action final

---

## 2. Seção 1: Landing Hero

### Visual
- **Fundo:** Vídeo `intro.mp4` (autoplay, loop, sem som)
- **Overlay:** Gradiente (rgba(10,10,10,0.35) topo → rgba(10,10,10,0.7) base)
- **Altura:** 100vh (full screen)

### Conteúdo
- **Delay:** 2-3 segundos antes do texto começar
- **Animação:** Parágrafo por parágrafo, fade-in suave
- **Copy:**
  ```
  Studio de Beleza Brasil by Madson Soares
  Pioneirismo e Referência em Beleza em Belém

  A Referência Absoluta em Beleza e Estética em Belém
  Uma década não se conta em anos… se prova em resultados, autoridade e transformação real.
  [Continua com os parágrafos conforme envio do usuário]
  ```
- **Botão CTA:** "Conhecer nossos Serviços" (aparece com último parágrafo)
  - Cor: Gold (#c8a96e)
  - Ação: Scroll suave para Seção 2

### Tipografia
- **Eyebrow:** Jost, 0.68rem, uppercase, letter-spacing 0.3em
- **Main Title:** Cormorant Garamond, 3-4rem, bold
- **Body:** Jost, 1rem, line-height 1.7, color: cream

---

## 3. Seção 2: Serviços

### Header Overlay
- **Fundo:** Foto do espaço (background-image, object-fit: cover)
- **Overlay:** Linear gradient (dark topo para transparente)
- **Conteúdo:** Copy revisado sobre estúdio, posicionamento, decade 2014-2024
  ```
  Belém, Pará — Desde 2014
  A Referência Absoluta em Beleza e Estética
  Uma década transformando imagem em presença.
  [Copy completo conforme envio]
  ```
- **Altura:** 50-60vh (menos que hero, mas impactante)

### Buttons Sticky (Topo)
- **Posição:** Fixed, topo da página, z-index alto
- **Layout:** Flex, gap, padding respeitando spacing
- **Buttons:**
  - **Primary:** "Iniciar minha transformação" (background: gold, color: black, padding: 12px 28px, border-radius: 2px)
  - **Secondary:** "Explorar procedimentos" (border: 1px solid gold, color: gold, background: transparent)
- **Comportamento:** Seguem o scroll, sempre visíveis
- **Transição:** Quando chega em serviços, buttons tornam-se mais opacos/destacados

### Serviços por Categoria
Estrutura: Três categorias principais

#### A. Estética Avançada
- Harmonização Facial
- Preenchimento Labial
- Rinomodelação
- Microagulhamento
- Skinbooster
- Micropigmentação

#### B. Salão
- Corte, Coloração e Tratamentos Capilares
- Design de Sobrancelhas
- Alongamento de Cílios

#### C. Bronzeamento
- Bronzeamento Masculino Premium (foto: `bronze-pioneiro`)
- Bronzeamento Feminino (foto: `bronze-masc`)

### Cards de Serviço
- **Layout:** Foto + Descrição
- **Foto:** Posição topo ou full-width
- **Descrição:** Text abaixo, tipografia Jost, color: text-dark
- **Grid:** Responsivo (2-3 colunas desktop)
- **Spacing:** Compacto (menos breathing room entre cards)

### Seçãs de Categoria
Cada categoria tem um header simples (titulo em Cormorant Garamond) + cards abaixo

---

## 4. Seção 3: Testimoniais
- **Layout:** Mantém estrutura existente (slide/carousel ou grid)
- **Spacing:** Generoso (large gaps entre depoimentos, padding maior)
- **Tipografia:** Mantém elegância

---

## 5. Seção 4: Contato
- **Layout:** Form + info de contato
- **Spacing:** Generoso
- **Buttons:** CTA integrados com buttons sticky (mantêm consistência)

---

## 6. Paleta Visual & Tipografia

### Cores (Variáveis CSS existentes)
- **Primary:** Gold (#c8a96e) — Destaque, CTAs
- **Dark:** Charcoal (#141414), Black (#0a0a0a) — Backgrounds
- **Light:** Cream (#faf7f2), Offwhite (#f5f0e8) — Texto, backgrounds
- **Mocha:** #7a5c4a — Accents

### Tipografia
- **Serif:** Cormorant Garamond (headers elegantes, eyebrows)
- **Sans:** Jost (corpo, navegação, descrições)
- **Font Weights:** 300-600 conforme necessidade

### Easing
- **Padrão:** cubic-bezier(0.25, 0.46, 0.45, 0.94) (smooth, sofisticado)

---

## 7. Animações

### Landing Hero
- **Video Load:** opacity 0 → 0.55 (transition: 2.5s ease)
- **Text Fade-in:** Cada parágrafo (animation: fadeIn 0.8s ease-out 2s+delay)
- **Button Fade-in:** Com último parágrafo

### Buttons Sticky
- **Entrance:** Fade-in quando seção 2 começa
- **Scroll Behavior:** Mantêm posição, transição opacity suave

### Serviços Cards
- **Entrance:** Fade-in ao scrollar pra vista (IntersectionObserver)

---

## 8. Responsividade

### Mobile (< 768px)
- **Landing:** Hero mantém 100vh, texto ajusta font-size
- **Buttons Sticky:** Stack vertical ou horizontal compacto, margin respeitado
- **Cards:** 1 coluna
- **Header Overlay:** Texto centralizado, menos padding

### Tablet (768px - 1024px)
- **Cards:** 2 colunas
- **Buttons:** Layout flex, spacing ajustado

### Desktop (> 1024px)
- **Cards:** 2-3 colunas conforme espaço
- **Buttons:** Layout original

---

## 9. Tecnologia

- **HTML:** index.html único (SPA-style, múltiplas seções)
- **CSS:** Novo arquivo ou seções adicionadas a styles.css existente
- **JS:** Scroll suave (Intersection Observer para animações), sticky buttons, video autoplay
- **Assets:** `intro.mp4`, `bronze-pioneiro.jpg/png`, `bronze-masc.jpg/png`, foto do espaço

---

## 10. Critérios de Sucesso

✅ Landing imersiva com vídeo + texto surgindo gradualmente
✅ Scroll suave para serviços (SPA, sem reload de página)
✅ Buttons sticky sempre visíveis, CTA claros
✅ Serviços organizados por categoria, com fotos
✅ Visual sofisticado, mantendo paleta/tipografia existente
✅ Responsivo (mobile, tablet, desktop)
✅ Performance: vídeo otimizado, lazy-loading de images

---

## 11. Removidas

- ❌ Seção "Sobre o Estudio" (consolidada no header de serviços)
- ❌ Cards antigos de apresentação
- ❌ Seções redundantes (mantém: Header + Serviços + Testimonials + Contato)

