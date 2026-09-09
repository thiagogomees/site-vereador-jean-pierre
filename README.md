# Site Modelo — Vereador Jean Pierre (Avante • Campina Grande/PB)

Site institucional demonstrativo em HTML puro. Sem build, sem banco de dados. Funciona abrindo `index.html` ou publicando em qualquer hospedagem estática.

## Estrutura

```
site-vereador-jean-pierre/
├── index.html          # Página inicial (hero, sobre, atuação, trajetória, galeria, vídeos, contato)
├── proposituras.html   # Proposituras com busca/filtro + formulário de sugestão via WhatsApp
├── noticias.html       # Notícias editáveis (painel do gabinete, senha modelo jean70777)
└── assets/
    ├── config.js       # ★ CONFIG CENTRAL: WhatsApp, e-mail, senha — troque aqui
    ├── logo-avante.svg # Logo modelo (recriação — substituir pelo oficial antes de publicar)
    ├── posse-1.jpg, posse-2.jpg, posse-3.jpg  # Fotos oficiais CMCG (Josenildo Costa)
    └── tech.jpg, sao-joao.jpg, campina-centro.jpg  # Ilustrativas locais
```

## 1) Configuração em 2 minutos (obrigatório antes de publicar)

Abra `assets/config.js` e troque:

```js
whatsapp: "5583999999999",  // <- número real, só dígitos com 55+DDD (placeholder atual)
email: "gab.jeanpierre@campinagrande.pb.leg.br", // <- oficial, já atualizado
senhaPainel: "jean70777",   // <- senha definitiva do painel de notícias
```

O `index.html` e `proposituras.html` leem esse arquivo automaticamente:
- Formulário de contato → monta mensagem e abre `wa.me/SEU_NUMERO?text=...`
- Botão flutuante de WhatsApp → aponta para o número configurado
- Sugestão de propositura → também vai para o WhatsApp

> Você escolheu **placeholder de WhatsApp por enquanto** e **informar outro e-mail depois**. O site já funciona com os placeholders acima — basta trocar o `config.js` quando tiver os dados.

## 2) Como usar cada página

### index.html — Contato
- Campos: nome, telefone, bairro, assunto, mensagem.
- Ao enviar: valida, abre o WhatsApp com texto pronto + mostra confirmação.
- Fallback: se `config.js` não carregar (arquivo local `file://`), usa o número placeholder embutido.

### proposituras.html — Sugestão
- 9 matérias-modelo com filtro por tipo/status + busca.
- “Sugira uma proposta” → abre WhatsApp com a sugestão formatada.

### noticias.html — Painel do gabinete
- Clique **Área do gabinete** → senha `jean70777` (ou a que você definir em `config.js` — troque também no código: procure `jean70777` no arquivo e substitua; há comentário `// TROCAR SENHA AQUI`).
- Publicar: título + editoria + imagem (`assets/...` ou URL) + link + texto.
- Salvo em `localStorage` do navegador (`jp_noticias`). Para site real multiusuário, migre para CMS/planilha (ver §4).

## 3) Publicação gratuita (3 opções)

**A) Netlify Drop (mais fácil, 1 min):**
1. Acesse app.netlify.com/drop, arraste a pasta `site-vereador-jean-pierre`.
2. Ganha URL `https://jean-pierre-cg.netlify.app`. Troque o nome em Site settings.

**B) Vercel:**
```
npx vercel ./site-vereador-jean-pierre --prod
```

**C) GitHub Pages:**
Suba a pasta como repositório → Settings → Pages → Deploy from branch → `/root`.

Nenhuma exige backend. Todo o JS é estático.

## 4) Evoluções recomendadas (quando sair do modelo)

- [ ] Substituir `logo-avante.svg` pelo oficial do Avante + foto oficial do vereador (com autorização).
- [ ] Trocar senha do painel por login real (Netlify Identity, Firebase Auth ou área WP).
- [ ] Migrar notícias de `localStorage` para Google Sheets / Notion API / CMS (Decap CMS).
- [ ] Conectar formulário a e-mail via Formspree/Basin além do WhatsApp (para registro formal).
- [ ] Registrar domínio `vereadoreanpierre.com.br` e apontar para a hospedagem.
- [ ] Incluir acessibilidade VLibras + contraste (a CMCG usa OneTap/VLibras).

## 5) Fontes e créditos (manter no rodapé)

- Posse 20/08/2026: Paraíba 24 Horas + DIVICOM/CMCG — https://www.paraiba24horas.com.br/noticia/suplente-jean-pierre-toma-posse-como-vereador-na-cmcg
- Fotos: Josenildo Costa / CMCG (crédito obrigatório).
- Candidatura 70.777 Avante: TSE via Estadão Eleições 2024.
- Eleitos 2024 CG: G1 PB 06/10/2024.
- Legislativo: camaracg.pb.gov.br • SAPL sapl.campinagrande.pb.leg.br • YouTube @CamaraCGOficial.

## 6) Aviso legal

Site **modelo para demonstração**, sem vínculo oficial com a Câmara Municipal de Campina Grande ou com o partido Avante. Textos de proposituras e notícias são exemplos editáveis. Valide todo conteúdo com o gabinete antes de publicar como oficial. Período eleitoral: observar Lei 9.504/97 e orientações da Presidência da CMCG.
