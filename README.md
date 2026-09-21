# Raissa Beltrame — Personal Trainer

Site de página única (one page) para captação de alunas via WhatsApp.
CREF 193897-G/SP · Professora de spinning · Bragança Paulista/SP

## Como publicar no GitHub Pages

1. Crie um repositório público, ex.: `raissa-beltrame`.
2. Envie os arquivos `index.html`, `logo.png` e este `README.md` para a raiz do repositório.
3. No repositório: **Settings → Pages → Source: Deploy from a branch → Branch: `main` / `/ (root)` → Save**.
4. Em 1 a 2 minutos o site fica em `https://SEU-USUARIO.github.io/raissa-beltrame/`.

## O que trocar antes de divulgar

Abra o `index.html` e procure por:

| Procure por | O que é | Obrigatório? |
|---|---|---|
| `SEU-USUARIO.github.io/raissa-beltrame` | aparece 4x (canonical, og:url, og:image, JSON-LD). Troque pela URL real após publicar. | Sim — sem isso o preview no WhatsApp não mostra imagem |
| `const CFG = {` | painel de edição no fim do arquivo (telefone, Facebook, fita, depoimentos, crédito) | conforme o caso |
| `<!-- TROCAR PELA FOTO DA RAISSA` | bloco na seção "Quem vai treinar você" | recomendado |

### Painel de edição (`CFG`, no fim do `index.html`)

```js
whatsapp: "5511940424585"   // só números, com 55 na frente. Muda os 8 botões de uma vez.
facebook: ""                 // cole a URL; vazio = o ícone do Facebook nem aparece
vagasLimitadas: true         // false = esconde a fita "Mais procurado"
depoimentos: false           // true + preencher listaDepoimentos = liga a seção
credito: null                // { texto:"Site por Mariano", url:"https://wa.me/55..." }
```

### Colocar a foto dela

Basta subir o arquivo com o nome **`raissa.jpg`** na mesma pasta do `index.html`.
Não precisa editar nada no código: se o arquivo existir, ele aparece; se não existir,
o logo assume o lugar automaticamente (`onerror`).

Requisitos da foto:
- vertical, proporção 4:5 (ex.: 800x1000 px), mínimo 800 px de largura
- **sem texto por cima** (nada de card de Instagram com "QUEM SOU EU?" escrito)
- ela centralizada ou à direita do quadro, corpo até a cintura
- salvar como JPG com até ~250 KB

Para ajustar o enquadramento, mude `object-position:50% 20%` na regra `.retrato .foto`
(primeiro número = horizontal, segundo = vertical).

## Detalhes técnicos

- 1 arquivo, ~100 KB. O logo está embutido em base64 (WebP) — o site não quebra se o `logo.png` faltar.
- `logo.png` é usado só para o preview em WhatsApp/Facebook/Instagram (`og:image`).
- Única dependência externa: Google Fonts. Se cair, as fontes do sistema assumem sem quebrar o layout.
- Sem formulário, sem cookies, sem analytics, sem localStorage → nada de LGPD a tratar.
- Contraste testado (WCAG AA), navegação por teclado, `prefers-reduced-motion` respeitado.
- SEO: title, description, Open Graph e JSON-LD (Person + LocalBusiness com os dois planos).

## Domínio próprio (opcional)

Comprando `raissabeltrame.com.br` (~R$ 40/ano no Registro.br), aponte para o GitHub Pages
criando um arquivo `CNAME` na raiz com o domínio dentro e configurando o DNS conforme o
guia do GitHub. Mantenha o HTTPS ligado em Settings → Pages.
