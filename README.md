# Manual: Como Vincular um Projeto Flutter (Dart) ao Firebase (2025)

## ✅ Pré-requisitos

Antes de iniciar, certifique-se de que você tem:
- Flutter instalado (`flutter --version`)
- Dart SDK (incluso no Flutter)
- Conta no Firebase: https://console.firebase.google.com
- Android Studio ou VS Code
- Emulador Android/iOS

---

## 🚀 Passo 1: Criar um Projeto Flutter

Se ainda não tem um projeto, crie um:

```bash
flutter create nome_do_projeto
cd nome_do_projeto
```

---

## 🏗️ Passo 2: Criar um Projeto no Firebase

- Vá para https://console.firebase.google.com.

- Clique em "Adicionar Projeto".

- Dê um nome ao projeto (ex: meu_app_flutter).

- Desative ou ative o Google Analytics (opcional).

- Clique em "Criar projeto" e aguarde.

## 📱 Passo 3: Registrar o App no Firebase

## Android

- Clique em "Adicionar App" > Android.

- Preencha:

    - Nome do pacote (ex: com.exemplo.meuapp)

    - Apelido (opcional)

    - SHA-1 (pode ser adicionado depois)

- Baixe o arquivo google-services.json e coloque em:
```bash
android/app/google-services.json
```

## IOS

- Clique em "Adicionar App" > iOS.

- Preencha:

    - Bundle ID (ex: com.exemplo.meuapp)

- Baixe o arquivo GoogleService-Info.plist e coloque em:
```bash
ios/Runner/GoogleService-Info.plist
```
