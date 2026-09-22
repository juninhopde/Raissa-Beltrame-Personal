# Raissa Beltrame — Personal Trainer

Site institucional de página única para captação de alunas via WhatsApp.

**Raissa Beltrame** · Personal trainer CREF 193897-G/SP · Professora de spinning
Bragança Paulista e região — SP

---

## Arquivos

| Arquivo | Para que serve | Pode apagar? |
|---|---|---|
| `index.html` | O site inteiro: HTML, CSS, JavaScript, logo e foto embutidos | Não |
| `logo.png` | Usado só no preview de link (WhatsApp, Facebook, Instagram) | Não |
| `raissa.jpg` | Foto opcional de alta qualidade. Se existir, substitui a foto embutida | Sim |
| `404.html` | Página de erro no mesmo visual do site | Sim |
| `robots.txt` | Libera a indexação e aponta o sitemap | Sim |
| `sitemap.xml` | Ajuda o Google a achar a página | Sim |
| `.gitignore` | Evita subir lixo do sistema para o repositório | Sim |

O `index.html` é autossuficiente: mesmo sozinho, sem nenhum outro arquivo, o site abre
completo e com imagem. Os demais arquivos só somam.

---

## Publicar no GitHub Pages

1. Crie um repositório **público**, ex.: `raissa-beltrame`.
2. Suba todos os arquivos na **raiz** do repositório (não dentro de uma pasta).
3. **Settings → Pages → Source: Deploy from a branch → Branch: `main` / `/ (root)` → Save**.
4. Em 1 a 2 minutos o site sobe em `https://SEU-USUARIO.github.io/raissa-beltrame/`.

### Checklist obrigatório antes de divulgar

- [ ] Trocar `SEU-USUARIO.github.io/raissa-beltrame` pela URL real. Aparece em **5 lugares
      no `index.html`** (canonical, `og:url`, `og:image`, JSON-LD), **1 no `robots.txt`** e
      **1 no `sitemap.xml`**. Sem isso o link compartilhado no WhatsApp não mostra imagem.
- [ ] Preencher ou confirmar o Facebook (`CFG.facebook` — vazio esconde o ícone).
- [ ] Raissa ler e aprovar os textos de "Quem sou", "Incluído em todos os planos" e o FAQ.
- [ ] Confirmar se ela quer o valor por aula do plano mensal exposto (R$ 99,83).
- [ ] Testar no celular: os dois botões flutuantes, os 8 links de WhatsApp e o menu.

---

## Manutenção do dia a dia

Tudo que muda com frequência está num único bloco no **fim do `index.html`**:

```js
const CFG = {
  whatsapp: "5511940424585",   // só números, com 55 na frente. Atualiza os 8 botões de uma vez.
  facebook: "",                 // cole a URL; vazio = o ícone do Facebook nem aparece
  vagasLimitadas: true,         // false = esconde a fita "Mais procurado"
  depoimentos: false,           // true + preencher listaDepoimentos = liga a seção
  listaDepoimentos: [
    // { texto: "Depoimento real da aluna.", autora: "Ana, 34 anos" },
  ],
  credito: null                 // { texto:"Site por Mariano", url:"https://wa.me/55..." }
};
```

### Trocar a foto

Suba o arquivo com o nome exato **`raissa.jpg`** na raiz do repositório. Não precisa
editar código: se existir, ele entra no lugar da foto embutida; se não existir, o site usa
a que já está dentro do `index.html`.

Requisitos da foto boa:

- vertical (proporção entre 3:5 e 4:5), mínimo 800 px de largura
- **sem texto por cima** — arte de carrossel do Instagram não serve
- de preferência sem logo de outra marca na roupa
- JPG de até ~250 KB

Para ajustar o enquadramento, altere `object-position:50% 10%` na regra `.retrato .foto-base`
(primeiro valor = horizontal, segundo = vertical).

### Mudar as cores

As cores vivem em variáveis no topo do `<style>`. Para trocar o dourado pelo laranja da
identidade dos posts, basta alterar `--ouro`, `--ouro-claro`, `--ouro-escuro` e `--metal`.

---

## Decisões técnicas

- **Página única, arquivo único.** Sem build, sem framework, sem dependência de CDN além do
  Google Fonts. Se o Google Fonts cair, as fontes do sistema assumem e o layout não quebra.
- **Sem formulário, cookies, analytics ou localStorage.** Não há dado pessoal coletado, então
  não há obrigação de LGPD a cumprir. Contato acontece direto no WhatsApp.
- **Acessibilidade:** contraste verificado em WCAG AA, navegação por teclado, `aria-label` nos
  ícones, skip link e `prefers-reduced-motion` respeitado (desliga todas as animações).
- **Performance:** imagens em WebP/JPEG otimizados e embutidos; o canvas de partículas para de
  desenhar quando sai da tela, para não consumir bateria no celular.
- **SEO:** title, description, Open Graph, Twitter Card e JSON-LD (`Person` + `LocalBusiness`
  com os dois planos e a área atendida).

---

## Domínio próprio (opcional)

`raissabeltrame.com.br` custa cerca de R$ 40/ano no Registro.br. Para usar:

1. Crie um arquivo `CNAME` na raiz do repositório contendo só o domínio.
2. No Registro.br, aponte os registros A para os IPs do GitHub Pages e o CNAME de `www`
   para `SEU-USUARIO.github.io`.
3. Em Settings → Pages, informe o domínio e marque **Enforce HTTPS**.
4. Atualize as URLs do checklist acima para o domínio novo.
