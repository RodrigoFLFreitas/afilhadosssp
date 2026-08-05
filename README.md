# 📡 PromoRadar

Site de promoções e achados do **Mercado Livre**. Atualização manual dos links, busca otimizada
(inclusive via Google) e **gerador de posts prontos para Instagram**.

## Arquivos

| Arquivo | Função |
|---------|--------|
| `index.html` | Site. Lê `produtos.json` e monta os cards, filtros e posts automaticamente. |
| `produtos.json` | **Banco de produtos — edite AQUI num lugar só.** |
| `style.css` | Estilos (cores/marca no topo do arquivo). |
| `conteudo-instagram.md` | Templates prontos de post/story/reels/carrossel. |
| `assets/` | Imagens dos produtos (`.webp`). |
| `sitemap.xml` / `robots.txt` | SEO. Troque `seusite.com.br` pelo domínio real. |

## Como adicionar / atualizar um produto

1. Abra `produtos.json`.
2. Copie um bloco `{ ... }` inteiro dentro de `"produtos"` e cole na lista.
3. Edite os campos:
   - `id` — único, sem espaço (ex: `mouse-gamer-rgb`)
   - `nome`, `descricao` — texto otimizado para SEO
   - `categoria` — `audio`, `eletronicos`, `acessorios` ou `casa` (o filtro é criado sozinho)
   - `preco` — só número, ex `33.00`
   - `precoAntigo` — número do preço cheio **OU** `null`. Quando preenchido, aparece o **badge de % desconto** no card e no post.
   - `imagem` — coloque o arquivo em `assets/` e aponte aqui (ex `assets/mouse.webp`)
   - `alt` — descrição da imagem (acessibilidade + SEO)
   - `link` — seu **link de afiliado** do Mercado Livre
4. Salve. O site atualiza sozinho (cards, busca, filtros, JSON-LD do Google e posts).

## Busca

- **Busca no site:** filtra os cards em tempo real por nome/descrição.
- **Busca via Google:** botão `🔎 Google` abre `site:seusite.com.br <termo>` no Google — troque o domínio em `index.html` (`SITE.dominio`).

## Gerar post para Instagram

No card, clique **📸 Gerar post Instagram** → escolha o formato → **Baixar imagem** (1080×1080) + **Copiar legenda**. Veja mais roteiros em `conteudo-instagram.md`.

## Rodar localmente

O site usa `fetch` para ler o JSON, então **precisa de um servidor HTTP** (abrir por `file://` não funciona). Opções:

```bash
npx http-server -p 8080 -c-1
```

Depois abra `http://localhost:8080`. Publicado no **GitHub Pages** funciona direto.

## Antes de publicar (checklist SEO)

- [ ] Trocar `https://seusite.com.br/` pelo domínio real em `index.html`, `sitemap.xml`, `robots.txt`.
- [ ] Ajustar `SITE.dominio` e `SITE.handle` no `<script>` do `index.html`.
- [ ] Adicionar imagem de capa (`capa.jpg`) para compartilhamento (Open Graph).
- [ ] Preencher o `link` do smartwatch em `produtos.json` (está como placeholder).
