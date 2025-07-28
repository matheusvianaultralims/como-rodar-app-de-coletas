# 📱 Instalação e Configuração do Android Studio no Linux

Este guia cobre todo o processo de instalação e configuração do **Android Studio** em distribuições Linux (Ubuntu 20.04+), incluindo Java, SDK, variáveis de ambiente e execução de um app.

---

## ✅ Requisitos do Sistema

- 🖥️ **Sistema Operacional**: Ubuntu 20.04 ou superior  
- 🧠 **Memória RAM**: 8 GB (mínimo recomendado)  
- 💽 **Espaço em Disco**: 4 GB para o IDE + espaço adicional para SDKs/emuladores  
- ☕ **Java JDK**: OpenJDK 17  
- 🔐 **Permissões**: Acesso de administrador (sudo)  

---

## ☕ Etapa 0: Instalar o Java (OpenJDK 17)

### 📌 0.1 Instale o Java

```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
```

### ✅ 0.2 Verifique a instalação

```bash
java --version
```

**Saída esperada:**

```
openjdk 17.0.15 2025-04-15
OpenJDK Runtime Environment (build 17.0.15+0-adhoc...)
OpenJDK 64-Bit Server VM (build 17.0.15+0-adhoc..., mixed mode)
```

---

## 📦 Etapa 1: Baixar o Android Studio

1. Acesse: [developer.android.com/studio](https://developer.android.com/studio)  
2. Clique em **Download Android Studio**  
3. Aceite os termos  
4. Baixe o `.tar.gz` (ex: `android-studio-2024.1.1.21-linux.tar.gz`)  

---

## 📂 Etapa 2: Instalação

### 📥 2.1 Extraia o arquivo

```bash
cd ~/Downloads
tar -xvzf android-studio-*.tar.gz
```

### 🚚 2.2 Mova para `/opt`

```bash
sudo mv android-studio /opt/
```

### ▶️ 2.3 Execute o Android Studio

```bash
/opt/android-studio/bin/studio.sh
```

---

## ⚙️ Etapa 3: Configuração Inicial

1. Aceite os termos de uso  
2. Selecione o modo **Standard**  
3. O Android Studio fará o download automático de:  
   - Android SDK  
   - Build Tools  
   - Emuladores  
   - (Opcional) NDK  

---

## 🧰 Etapa 4: Ajustes no SDK Manager

### 📍 Acesse:

`Tools > SDK Manager`

### ✔️ Certifique-se que os seguintes componentes estão instalados:

- Android SDK Platform (versões mais usadas)  
- Android SDK Command-line Tools  
- Google USB Driver (para dispositivos físicos)  

---

## 📱 Etapa 5: Criar Emulador (AVD)

### 🛠️ Acesse:

`Tools > Device Manager`

1. Clique em **Create Device**  
2. Selecione um modelo (ex: Pixel 5)  
3. Escolha uma imagem do sistema Android  
4. Finalize e clique em **▶️** para iniciar o emulador  

---

## 🧪 Etapa 6: Rodar o App de Coletas

### 🧾 Clone o repositório

```bash
git clone https://github.com/ultralims/app-coletas
```

### 📂 Acesse o projeto e instale as dependências

```bash
cd app-coletas
npm install
```

### ▶️ Inicie o app

```bash
npm start
```

---

## 🖥️ Etapa 7: Criar Atalho no Menu (opcional)

### 📄 7.1 Crie um arquivo `.desktop`

```bash
sudo nano /usr/share/applications/android-studio.desktop
```

Conteúdo:

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

## 🌍 Etapa 8: Variáveis de Ambiente

### ✏️ Edite o `.bashrc` ou `.zshrc`

```bash
nano ~/.bashrc
```

Adicione ao final do arquivo:

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

### ✅ Aplique as mudanças

```bash
source ~/.bashrc
```

> ⚠️ Ajuste os caminhos conforme seu sistema.  
> No Android Studio: `File > Settings > Appearance & Behavior > System Settings > Android SDK`

---

## 🔌 Etapa 9: Executar em um Dispositivo Físico

1. Ative o **modo desenvolvedor** no celular  
2. Habilite a **depuração USB**  
3. Conecte o cabo USB  
4. Aceite a chave RSA no celular  
5. Execute pelo Android Studio (botão ▶️)  

---

## 🐞 Etapa 10: Debug com React Native Doctor

Se o comando `npm start` falhar, use:

```bash
npx react-native doctor
```

Esse comando verifica se o ambiente está corretamente configurado e sugere correções automáticas.

---
