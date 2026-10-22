# Painel SDR MestreMaro (online)

Painel da prospecção (funil, meta, leads, conversas, agendamentos), feito para o **GitHub Pages**.
Ele lê os dados em tempo real do **Firestore**, e o acesso é por login (Firebase Auth).

## Arquivos
- `index.html`: o painel inteiro (HTML + CSS + JS, sem build).
- `firebase-config.js`: configuração pública do app web do Firebase.
- `.nojekyll`: avisa o GitHub Pages para servir os arquivos como estão.

## Como os dados chegam aqui
O agente roda no PC do Calebe e grava tudo na pasta `dados/`. O script `scripts/sincronizar_firebase.py` (no PC) envia essas mudanças para o Firestore a cada 10 segundos, e o painel atualiza na hora.
"Marcar como feito" no painel volta para o PC pelo mesmo script.
Se o PC desligar, o painel mostra os últimos dados e "PC do agente offline".

## Subir no GitHub Pages (pelo site)
1. Crie um repositório no GitHub (ex.: `painel-sdr`).
2. "Add file" > "Upload files": arraste **o conteúdo desta pasta** (`index.html`, `firebase-config.js`, `README.md`, `.nojekyll`) e confirme.
3. Settings > Pages > Source: "Deploy from a branch", branch `main`, pasta `/ (root)` > Save.
4. Em uns minutos o painel abre em `https://SEU-USUARIO.github.io/painel-sdr/`.
5. No Firebase: Authentication > Settings > Domínios autorizados > adicione `SEU-USUARIO.github.io`.

Nunca suba a pasta `dados/` nem a chave `firebase-chave.json`.

## Versão local (sem internet)
A pasta `painel-local/` tem a versão antiga, que lê os arquivos direto: `python painel-local/server.py` e abra http://127.0.0.1:8787.
