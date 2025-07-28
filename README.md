
# 📱 Como Instalar o Android Studio no Linux (Ubuntu 20.04+)

Passo a passo para instalar o Android Studio, configurar o Java, SDK, rodar um app e criar atalhos.

---

## ✅ 1. Requisitos

- 🖥️ **Ubuntu 20.04 ou superior**  
- 🧠 **8 GB de RAM** (mínimo recomendado)  
- 💽 **4 GB de espaço + SDK/emuladores**  
- ☕ **Java JDK 17 (OpenJDK)**  
- 🔐 **Acesso root (sudo)**

---

## ☕ 2. Instalar o Java (OpenJDK 17)

### 2.1 Atualize o sistema e instale o Java

```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
```

### 2.2 Verifique a instalação

```bash
java --version
```

Saída esperada:
```
openjdk 17.0.x ...
```

---

## 📦 3. Baixar o Android Studio

1. Vá para: [developer.android.com/studio](https://developer.android.com/studio)  
2. Baixe o arquivo `.tar.gz` (ex: `android-studio-2024.1.1.21-linux.tar.gz`)

---

## 📂 4. Instalar o Android Studio

### 4.1 Extraia o arquivo

```bash
cd ~/Downloads
tar -xvzf android-studio-*.tar.gz
```

### 4.2 Mova para a pasta /opt

```bash
sudo mv android-studio /opt/
```

### 4.3 Execute o Android Studio

```bash
/opt/android-studio/bin/studio.sh
```

---

## ⚙️ 5. Configuração Inicial

- Aceite os termos de uso  
- Escolha o modo **Standard**  
- O Android Studio baixará automaticamente:
  - Android SDK
  - Build Tools
  - Emuladores  
  - (Opcional) NDK

---

## 🧰 6. Ajustes no SDK

### 6.1 Acesse o SDK Manager

Menu: `Tools > SDK Manager`

### 6.2 Certifique-se que os seguintes estão instalados:

- Android SDK Platform (versões comuns)  
- Command-line Tools  
- Google USB Driver (para celular físico)

---

## 📱 7. Criar Emulador (AVD)

### 7.1 Acesse o Device Manager

Menu: `Tools > Device Manager`

1. Clique em **Create Device**  
2. Escolha um modelo (ex: Pixel 5)  
3. Baixe a imagem do sistema Android  
4. Clique em ▶️ para iniciar o emulador

---

## 🧪 8. Rodar o App de Coletas

### 8.1 Clone o projeto

```bash
git clone https://github.com/ultralims/app-coletas
cd app-coletas
```

### 8.2 Instale dependências e rode

```bash
npm install
npm start
```

---

## 🖥️ 9. Criar Atalho no Menu (opcional)

### 9.1 Crie o arquivo `.desktop`

```bash
sudo nano /usr/share/applications/android-studio.desktop
```

Cole o conteúdo abaixo:

```ini
[Desktop Entry]
Version=1.0
Type=Application
Name=Android Studio
Exec=/opt/android-studio/bin/studio.sh
Icon=/opt/android-studio/bin/studio.png
Categories=Development;IDE;
Terminal=false
```

Salve com `Ctrl + O`, `Enter` e saia com `Ctrl + X`.

---

## 🌍 10. Variáveis de Ambiente

### 10.1 Edite o arquivo `.bashrc` ou `.zshrc`

```bash
nano ~/.bashrc
```

Adicione no final do arquivo:

```bash
# Java
export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
export PATH=$PATH:$JAVA_HOME/bin

# Android SDK
export ANDROID_HOME=$HOME/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
export PATH=$PATH:$ANDROID_HOME/platform-tools
```

### 10.2 Atualize as variáveis

```bash
source ~/.bashrc
```

> ⚠️ Ajuste os caminhos conforme necessário.

---

## 🔌 11. Executar no Celular (USB)

1. Ative o **modo desenvolvedor** no celular  
2. Habilite a **depuração USB**  
3. Conecte o celular com cabo USB  
4. Aceite a chave RSA no celular  
5. Clique em ▶️ no Android Studio

---

## 🐞 12. Diagnóstico com React Native Doctor

Se `npm start` falhar, use:

```bash
npx react-native doctor
```

Esse comando mostra se o ambiente está corretamente configurado.

---
