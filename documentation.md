Crie uma landing page estática em Vue 3 + Vite para subir no Cloudflare Pages.

Objetivo:
Página intermediária simples e confiável antes de enviar o usuário para o checkout.

URL do botão:
https://checkout.familiadepremios.com.br/?pdv_code=l0041m

Identidade visual baseada no checkout enviado:
- Verde principal: #4f8500
- Verde escuro: #3f7100
- Verde claro: #c7e99b
- Fundo claro: #f5f7f4
- Texto principal: #17233a
- Bordas: #4b5563
- Branco: #ffffff

Conteúdo da página:
Título principal:
"Você está quase lá!"

Subtítulo:
"Para continuar com sua participação, clique no botão abaixo."

Card central:
- Mostrar uma mensagem curta:
"Ambiente seguro para continuar sua compra."
- Botão grande verde:
"Continuar para o checkout"

Abaixo do botão:
"Você será direcionado para o checkout oficial."

Requisitos:
- Usar Vue 3 + Vite.
- Layout responsivo para celular e desktop.
- Página bem leve, sem bibliotecas pesadas.
- Não fazer redirecionamento automático.
- O redirecionamento só deve acontecer quando o usuário clicar no botão.
- Usar visual limpo, parecido com a página do checkout.
- Centralizar o conteúdo na tela.
- Criar um card com bordas arredondadas, sombra suave e botão verde.
- Adicionar pequeno selo visual no topo: "Cota em dobro!"
- Preparar para Cloudflare Pages.

Estrutura:
- package.json
- index.html
- src/main.js
- src/App.vue
- README.md

Configuração Cloudflare Pages:
- Framework preset: Vite
- Build command: npm run build
- Output directory: dist

Crie o código completo de todos os arquivos.