# 📱 Instalação e Configuração do Android Studio no Linux

Este guia documenta o processo completo de download, instalação e configuração inicial do **Android Studio** em distribuições Linux (Ubuntu 20.04+), incluindo variáveis de ambiente e Java.

---

## ✅ Requisitos do Sistema

- **Sistema Operacional**: Ubuntu 20.04 ou superior
- **Memória RAM**: 8 GB (mínimo recomendado)
- **Espaço em Disco**: 4 GB para o IDE + espaço adicional para SDKs/emuladores
- **Java JDK**: OpenJDK 17
- **Permissões**: Acesso de administrador (sudo)

---

## ☕ Etapa 0: Instalação do Java (OpenJDK 17)
Instale a versão do java que o app de coletas utiliza.

### 0.1 Instalar OpenJDK 17

```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
```

### 0.2 Verificar a instalação

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

## 📦 Etapa 1: Download do Android Studio

1. Acesse o site oficial: [https://developer.android.com/studio](https://developer.android.com/studio)
2. Clique em **Download Android Studio**
3. Aceite os termos de uso
4. Baixe o arquivo `.tar.gz` (ex: `android-studio-2024.1.1.21-linux.tar.gz`)

---

## 📂 Etapa 2: Instalação

### 2.1 Extraia o arquivo

```bash
cd ~/Downloads
tar -xvzf android-studio-*.tar.gz
```

### 2.2 Mova para `/opt`

```bash
sudo mv android-studio /opt/
```

### 2.3 Execute o instalador

```bash
/opt/android-studio/bin/studio.sh
```

---

## ⚙️ Etapa 3: Configuração Inicial

1. Aceite os termos
2. Escolha o modo **Standard**
3. O Android Studio baixará automaticamente:
   - SDKs
   - Build Tools
   - Emuladores
   - NDK (opcional)

---

## 🧰 Etapa 4: Configurações Recomendadas

### 4.1 SDK Manager

Menu: `Tools > SDK Manager`

Instale ou verifique:
- Android SDK Platform (versões mais usadas)
- Android SDK Command-line Tools
- Google USB Driver (caso use dispositivo físico)

---

## 🧪 Etapa 5: Criar e Rodar um Projeto

1. Clique em **"New Project"**
2. Escolha um template (ex: Empty Activity)
3. Defina nome, linguagem (Kotlin/Java) e versão do Android
4. Aguarde o Gradle sincronizar
5. Clique em ▶️ para rodar no emulador ou dispositivo

---

## 📱 Etapa 6: Configurar Emulador (AVD)

Menu: `Tools > Device Manager`

1. Clique em **"Create Device"**
2. Escolha um modelo (Pixel 5, por exemplo)
3. Selecione uma imagem do sistema Android
4. Finalize e clique em **▶️** para iniciar

---

## 🖥️ Etapa 7: Criar Atalho no Menu (opcional)

### 7.1 Criar `.desktop`

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

Salvar com `Ctrl + O`, `Enter` e sair com `Ctrl + X`.

---

## 🌍 Etapa 8: Variáveis de Ambiente

### 8.1 Adicionar JAVA_HOME e ANDROID_HOME

Abra o arquivo `.bashrc` (ou `.zshrc` se usar ZSH):

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

Salve e aplique:

```bash
source ~/.bashrc
```

> ⚠️ Ajuste os caminhos conforme seu sistema. Para descobrir o SDK real instalado:
> - No Android Studio: `File > Settings > Appearance & Behavior > System Settings > Android SDK`

---

## 🔌 Etapa 9: Rodar em Dispositivo Físico

1. Ative o **modo desenvolvedor** no celular
2. Habilite a **depuração USB**
3. Conecte via USB
4. Confirme a chave RSA na tela do celular
5. Execute o app via Android Studio (ícone ▶️)

---

## ❗ Problemas Comuns e Soluções

| Erro | Causa Provável | Solução |
|------|----------------|---------|
| `SDK not found` | SDK não configurado corretamente | Verifique o caminho nas configurações |
| Emulador lento/travando | Virtualização desativada | Ative VT-x ou AMD-V na BIOS |
| Gradle muito lento | Conexão ruim ou proxy ativo | Ative "Offline Mode" em `File > Settings > Build > Gradle` |
| `java: source release 17 requires target release 17` | Versão incompatível no Gradle | Use OpenJDK 17 e configure corretamente no `build.gradle` |

---

## 🧼 Desinstalação

```bash
sudo rm -rf /opt/android-studio
sudo rm /usr/share/applications/android-studio.desktop
```

Remover SDK:

```bash
rm -rf ~/Android/Sdk
```

---

## 📚 Links Úteis

- [Android Studio](https://developer.android.com/studio)
- [Documentação Android](https://developer.android.com/docs)
- [Kotlin](https://kotlinlang.org/)
- [Jetpack Compose](https://developer.android.com/jetpack/compose)
- [Design Material](https://m3.material.io/)

---

## 👨‍💻 Autor

**Matheus Viana**  
Contribuições e sugestões são bem-vindas!

---
