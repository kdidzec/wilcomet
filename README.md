# Wilcom Tutorial App (pronto para build)

Arquivos incluídos:
- Projeto Vite + React (esqueleto)
- App com versão PT-BR e imagens reais do Wilcom em `public/imagens/`
- Autenticação por Firebase (placeholder) e compra via WhatsApp (QR + link)

## Como usar (rápido)
1. Instale Node.js (v18+)
2. Abra um terminal na pasta do projeto
3. Rode:
   npm install
4. Substitua `src/firebaseConfig.js` com as configurações do seu projeto Firebase.
   - Console: https://console.firebase.google.com/
   - Ative Authentication > Email/Password
5. Para testar em dev:
   npm run dev
   -> abra http://localhost:5173
6. Para build:
   npm run build
7. Para gerar APK (usando Capacitor):
   - npm install @capacitor/core @capacitor/cli --save
   - npx cap init
   - npm run build
   - npx cap add android
   - npx cap copy
   - npx cap open android
   - No Android Studio: Build > Build APK(s)

## Observações
- Imagens já foram copiadas para public/imagens/
- O arquivo src/firebaseConfig.js contém placeholders. Substitua com as suas credenciais.
- Se quiser que eu gere o APK para você, escolha a opção C (eu te guio) e posso fornecer um workflow para CI.


## Variável de ambiente para mensagem do WhatsApp

O texto do botão/QR do WhatsApp é lido da variável de ambiente `VITE_WHATSAPP_MESSAGE` no momento do build.
No GitHub Actions você deve criar o *secret* `VITE_WHATSAPP_MESSAGE` com a mensagem desejada.

Exemplo de mensagem:
```
Olá! Quero comprar acesso PRO — Plano Mensal
```

Se essa variável não for fornecida, será usada uma mensagem padrão:
`Olá! Quero comprar acesso ao Wilcom Tutorial PRO — quero informações sobre pagamento e liberação.`

