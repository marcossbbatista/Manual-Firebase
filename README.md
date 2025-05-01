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

---

## 📱 Passo 3: Registrar o App no Firebase

## Android

- Clique em "Adicionar App" > Android.

- Preencha:

    - Para encontrar o nome do pacote, acesse o arquivo android/app/build.gradle e verifique o valor do campo applicationId:
```bash
defaultConfig {
        // TODO: Specify your own unique Application ID (https://developer.android.com/studio/build/application-id.html).
        applicationId = "com.example.cineritz"
        // You can update the following values to match your application needs.
        // For more information, see: https://flutter.dev/to/review-gradle-config.
        minSdk = 23
        targetSdk = flutter.targetSdkVersion
        versionCode = flutter.versionCode
        versionName = flutter.versionName
    }
```
    - Apelido (opcional)

    - SHA-1 (pode ser adicionado depois)

- Baixe o arquivo google-services.json e coloque em:
```bash
android/app/google-services.json
```

Adicione o plug-in como dependência no arquivo  android/settings.gradle:

```bash
id("com.google.gms.google-services") version "4.4.2" apply false
```

Em seguida, no arquivo android/app/build.gradle, adicione:

```bash
plugins {
  id("com.android.application")

  // Add the Google services Gradle plugin
  id("com.google.gms.google-services")

  ...
}

dependencies {
  // Import the Firebase BoM
  implementation(platform("com.google.firebase:firebase-bom:33.13.0"))


  // TODO: Add the dependencies for Firebase products you want to use
  // When using the BoM, don't specify versions in Firebase dependencies
  implementation("com.google.firebase:firebase-analytics")


  // Add the dependencies for any other desired Firebase products
  // https://firebase.google.com/docs/android/setup#available-libraries
}
```

## IOS

- Clique em "Adicionar App" > iOS.

- Preencha:

    - Bundle ID (ex: com.exemplo.meuapp)

- Baixe o arquivo GoogleService-Info.plist e coloque em:
```bash
ios/Runner/GoogleService-Info.plist
```

No arquivo ios/Runner/AppDelegate.swift, adicione:

```bash
import FirebaseCore
...
[UIApplicationLaunchOptionsKey: Any]?) -> Bool {
FirebaseApp.configure()
...
```

---

## 📦 Passo 4: Adicionar os Pacotes Firebase ao pubspec.yaml

## Adicione ao seu pubspec.yaml:

```bash
dependencies:
  flutter:
    sdk: flutter
  firebase_core: ^3.0.0
  firebase_auth: ^5.0.0
  cloud_firestore: ^6.0.0

```

Depois, rode:
```bash
flutter pub get
```

---

## 🧠 Passo 5: Inicializar o Firebase no Projeto

No seu main.dart:

```bash
import 'package:flutter/material.dart';
import 'package:firebase_core/firebase_core.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp();
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Meu App Firebase',
      home: Scaffold(
        appBar: AppBar(title: Text('Firebase App')),
        body: Center(child: Text('Firebase Inicializado!')),
      ),
    );
  }
}
```

---

## 🧪 Passo 6: Testar a Conexão

Execute o app:
```bash
flutter run
```

Se tudo estiver certo, o console mostrará algo como:
```bash
[FirebaseCore] Firebase has been successfully initialized.
```

---

## 🔒 Observações de Segurança

- Nunca compartilhe os arquivos google-services.json ou GoogleService-Info.plist em repositórios públicos.

- Use as regras de segurança do Firebase (Firestore/Realtime DB).

- Em produção, ative App Check e use autenticação com verificação de email ou outros métodos seguros.

---

## 📑 Fontes

As informações contidas neste manual foram baseadas nas seguintes fontes:

- [Documentação oficial do Firebase para Flutter](https://firebase.flutter.dev/docs/overview)
- [Documentação oficial do Firebase](https://firebase.google.com/docs)
- [Flutter documentation](https://flutter.dev/docs)
- [YouTube - Flutter Firebase Setup. In 5 minutes - (Android & IOS 2025) ](https://www.youtube.com/watch?v=z-JRQZSqQNc&list=WL&index=1)
