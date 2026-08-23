# Publicar o portfólio em gabrielnaves.com (GitHub Pages)

Esta pasta já está pronta para subir. Conteúdo:

- `index.html` — o site (versão colorida). É o que abre em gabrielnaves.com.
- `pb.html` — versão preto & branco (opcional). Fica acessível em gabrielnaves.com/pb.html.
- `CNAME` — arquivo que diz ao GitHub qual é o domínio (`gabrielnaves.com`). Não apagar.
- `.nojekyll` — evita que o GitHub tente “processar” o site. Não apagar.

---

## 1. Criar o repositório e subir os arquivos

1. Crie uma conta/entre no GitHub e clique em **New repository**.
2. Nome sugerido: `gabrielnaves-site` (público). Não marque “Add README”.
3. Envie **todos os arquivos desta pasta** para a raiz do repositório (arraste no botão *Add file → Upload files*, ou via git):

```
git init
git add .
git commit -m "Portfólio Gabriel Naves"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/gabrielnaves-site.git
git push -u origin main
```

## 2. Ligar o GitHub Pages

1. No repositório: **Settings → Pages**.
2. Em **Source**, escolha **Deploy from a branch**.
3. Branch: **main** / pasta **/ (root)** → **Save**.
4. Em **Custom domain** já deve aparecer `gabrielnaves.com` (vem do arquivo `CNAME`). Se não, digite e salve.
5. Depois que o DNS propagar, marque **Enforce HTTPS**.

## 3. Configurar o DNS (na GoDaddy)

No painel do domínio `gabrielnaves.com` → **DNS / Gerenciar zonas**, adicione:

**Domínio raiz (@) — 4 registros tipo A, apontando para o GitHub Pages:**

| Tipo | Nome | Valor            |
|------|------|------------------|
| A    | @    | 185.199.108.153  |
| A    | @    | 185.199.109.153  |
| A    | @    | 185.199.110.153  |
| A    | @    | 185.199.111.153  |

(Opcional, IPv6 — 4 registros tipo AAAA em @: `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`.)

**Subdomínio www — 1 registro CNAME:**

| Tipo  | Nome | Valor                 |
|-------|------|-----------------------|
| CNAME | www  | SEU_USUARIO.github.io |

> Troque `SEU_USUARIO` pelo seu usuário do GitHub.

**O registro que você já tem** — `CNAME  _domainconnect → _domainconnect.gd.domaincontrol.com` — é da própria GoDaddy (Domain Connect). **Pode deixar como está**, ele não interfere no site.

## 4. Conferir

- A propagação de DNS costuma levar de alguns minutos a algumas horas.
- Teste `https://gabrielnaves.com` e `https://www.gabrielnaves.com`.
- Se aparecer aviso de certificado logo após configurar, aguarde — o HTTPS do GitHub é emitido automaticamente depois que o DNS resolve.

---

### Observações
- Para atualizar o site no futuro, basta substituir o `index.html` no repositório (novo commit). Eu gero o arquivo novo quando você quiser.
- Não consigo alterar o DNS por você (isso é feito na sua conta da GoDaddy) — mas o arquivo `CNAME` e os passos acima deixam tudo pronto.
