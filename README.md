# Site do WO (GitHub Pages)

Páginas públicas que a Play Store e o AdMob exigem. Tudo estático: é só publicar a pasta.

| Arquivo | Para quê | Onde cadastrar o link |
|---|---|---|
| `index.html` | Página do app ("site do desenvolvedor") | Play Console > Presença na loja > Detalhes de contato > Site; AdMob (app-ads.txt) |
| `privacidade.html` | Política de privacidade | Play Console > Conteúdo do app > Política de privacidade; tela de consentimento OAuth (Google Cloud) |
| `excluir-dados.html` | Como excluir os dados (exigência de exclusão de conta/dados) | Play Console > Conteúdo do app > Segurança dos dados > link de exclusão |
| `app-ads.txt` | Autoriza o AdMob a vender anúncios do app | precisa ficar na **raiz** do domínio do site cadastrado na Play |

## Antes de publicar

1. **`app-ads.txt`:** já tem o ID de editor do AdMob (`pub-1790492091178460`). Se um dia
   trocar de conta AdMob, troque o ID lá.
2. **E-mail de contato:** as páginas usam `utlapps.feedback@gmail.com`. Para trocar, procure e
   substitua esse endereço nos três arquivos `.html`.
3. **Link da Play Store** (`index.html`): já aponta para
   `https://play.google.com/store/apps/details?id=com.leonardorabello.wo`; funciona depois da
   publicação.

## Publicar no GitHub Pages

O `app-ads.txt` precisa estar na raiz do domínio (ex.: `https://usuario.github.io/app-ads.txt`).
Por isso, o jeito mais simples é um repositório **só para o site**, com o nome especial
`<seu-usuario>.github.io`:

1. No GitHub, crie o repositório público `<seu-usuario>.github.io`.
2. Envie o **conteúdo** desta pasta (não a pasta em si) para a raiz desse repositório:
   ```bash
   cd site
   git init -b main
   git add .
   git commit -m "Site do WO"
   git remote add origin https://github.com/<seu-usuario>/<seu-usuario>.github.io.git
   git push -u origin main
   ```
3. No repositório: Settings > Pages > Source: **Deploy from a branch**, branch `main`, pasta
   `/ (root)`. Em alguns minutos o site fica em `https://<seu-usuario>.github.io/`.
4. Confira: `https://<seu-usuario>.github.io/privacidade.html`, `.../excluir-dados.html` e
   `.../app-ads.txt`.
5. Cadastre os links nos lugares da tabela acima. No Play Console, o site do desenvolvedor deve
   ser `https://<seu-usuario>.github.io` (sem caminho), para o AdMob achar o `app-ads.txt`.

Se preferir um domínio próprio, aponte-o para o GitHub Pages e crie o arquivo `CNAME` com o
domínio; o `app-ads.txt` continua na raiz.

## Manter atualizado

Ao mudar algo que envolva dados no app (nova permissão, novo SDK, nova coleta), atualize
`privacidade.html` (com a data no topo) e as respostas de Segurança dos dados
(`store/DATA_SAFETY.md`) no Play Console.
