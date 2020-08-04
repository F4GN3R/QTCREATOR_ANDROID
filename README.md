# QTCREATOR_ANDROID

Manual de configuração do qtcreator para compilação android

### Configuração do Java

1. Atualize os repositórios:

```Shell
sudo apt-get update
```

2. Instale o OpenJDK 8:

```Shell
sudo apt-get install openjdk-8-jdk
```

3. Verifique a versão do JDK:

```Shell
java -version
```

```
openjdk version "1.8.0_242"
OpenJDK Runtime Environment (build 1.8.0_242-b09)
OpenJDK 64-Bit Server VM (build 25.242-b09, mixed mode)
```

4. Se a versão correta do Java não estiver sendo usada, use o comando alternative para alterná-lo:

```Shell
sudo update-alternatives --set java /usr/lib/jvm/jdk1.8.0_**version**/bin/java
```

5. Verifique novamente a versão do JDK:

```Shell
java -version
```

```
openjdk version "1.8.0_242"
OpenJDK Runtime Environment (build 1.8.0_242-b09)
OpenJDK 64-Bit Server VM (build 25.242-b09, mixed mode)
```

6. Adicionar o diretório do *jdk* na variável de ambiente PATH para tornar o executável disponível globalmente. Adicione no fim do arquivo ~/.bashrc ou ~/.profile para torná-lo permanente:

```Shell
nano ~/.bashrc
```

```
# JAVA
export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-amd64
export PATH=$JAVA_HOME/bin:$PATH
```

7. Adicionar o caminho do JDK nas configurações do QT Creator:

> Tools - Options... - Devices - Android - Java Settings - JDK location: /usr/lib/jvm/java-1.8.0-openjdk-amd64

### Configuração do Android

1. Baixar o Android NDK, para o tutorial foi utilizado a versão estável mais recente (*r21b*).

https://developer.android.com/ndk/downloads

2. Baixar o *sdkmanager* para não precisar instalar o Android Studio:

```Shell
wget https://dl.google.com/android/repository/sdk-tools-linux-3859397.zip
```

3. Adicione o diretório do *sdkmanager* na variável de ambiente PATH para tornar o executável disponível globalmente. Adicione no fim do arquivo ~/.bashrc ou ~/.profile para torná-lo permanente:

```Shell
nano ~/.bashrc
```

```
#ANDROID
export PATH=home/Android/sdk-tools-linux-3859397/tools:/home/Android/sdk-tools-linux-3859397/tools/bin:$PATH
```

4. Recarregue o arquivo ~/.bashrc ou ~/.profile:

```Shell
source ~/.bashrc
```

6. Adicionar o caminho do JDK nas configurações do QT Creator:

> Tools - Options... - Devices - Android - Android Settings - Android SDK location: /home/Android/sdk-tools-linux-3859397
> Tools - Options... - Devices - Android - Android Settings - Android NDK list: /home/Android/android-ndk-r21b-linux-x86_64/android-ndk-r21b

## Compilando...

Se tudo ocorreu bem até aqui o Qt Creator deve detectar todas as configurações e solicitar uma confirmação para baixar os pacotes essenciais como o "build-tools" e o "platform-tools", após a instalação desses pacotes basta ir em *SDK Manager* e instalar os pacotes que for usar, no meu caso usei esses:

- Android 7.0
- [x] SDK Platform
- [x] ARM 64 v8a System Image
- [x] ARM 64 v7a System Image