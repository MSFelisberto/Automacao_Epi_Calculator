# Preparar Instância do Appium no Windows
Para começar com testes automatizados usando o Appium, precisamos seguir alguns passos. Primeiro, vamos preparar seu sistema, depois poderemos iniciar nossa jornada com o Appium.

1. [Baixe e instale o JDK](https://www.oracle.com/java/technologies/javase/jdk11-archive-downloads.html)
2. [Baixe e instale o IntelliJ IDEA (versão Community)](https://www.jetbrains.com/idea/download/)
3. [Baixe e instale o Android Studio e o Android SDK pelo Android Studio](https://developer.android.com/studio)
4. [Baixe e instale o Node.js (LTS)](https://nodejs.org/en/download/)
5. [Baixe e instale o Vysor](https://www.vysor.io/download/)
6. Configure as variáveis de ambiente (path): Defina JAVA_HOME e ANDROID_HOME
7. Verifique se o Node.js, npm e Android SDK estão instalados:
    - `node --version`
    - `npm --version`
    - `adb --version`
8. Instale o Appium: veja o processo de instalação do Appium Versão 2 (comandos abaixo)
9. Verifique se o Appium está instalado: `appium -v`
10. Conecte seu dispositivo (ative o modo desenvolvedor e a depuração USB)
    - Localize o “Número da versão” (build number) em Configurações e toque 7 vezes nele.
    - Informe seu padrão, PIN ou senha para ativar o menu “Opções do desenvolvedor”.
    - O menu “Opções do desenvolvedor” agora aparecerá em suas configurações.
    - Ative “Depuração USB” nas “Opções do desenvolvedor”.
11. Identifique o `appPackage` e `appActivityName`
    - Abra o app no seu dispositivo e use o comando: `adb shell "dumpsys activity activities | grep mResumedActivity"`
12. **Instale o plugin “Create TestNG XML”**:
    - Em IntelliJ IDEA, vá em File >> Settings >> Plugins >> Marketplace >> Pesquise por “Create TestNG XML” e instale.

## Comandos do Appium Versão 2
1. Instalar o Appium: `npm i --location=global appium`
2. Desinstalar o Appium: `npm uninstall -g appium`
3. Verificar lista de drivers: `appium driver list`
4. Instalar drivers `uiautomator2` e plugin `execute-driver`:
    - `appium driver install uiautomator2`
    - `appium plugin install execute-driver`
5. Verificar lista de plugins: `appium plugin list`
6. Instalar plugin específico: `appium plugin install nome_do_plugin`
7. Executar com base-path: `appium --base-path /wd/hub`
8. Executar Appium: `appium`
9. Executar Appium com plugin e path: `appium --use-plugins=execute-driver --base-path /wd/hub`

### Recursos Relacionados
* [Appium NPM](https://www.npmjs.com/package/appium)
* [Appium GitHub](https://github.com/appium/appium)

---

## Criar Projeto Java (Gradle) no IntelliJ IDEA para Appium
1. Crie um projeto Java (Gradle) no IntelliJ IDEA
2. Adicione as dependências do Gradle:
    - [Selenium](https://mvnrepository.com/artifact/org.seleniumhq.selenium/selenium-java)
    - [Appium Client](https://mvnrepository.com/artifact/io.appium/java-client)
    - [TestNG](https://mvnrepository.com/artifact/org.testng/testng)

---

## Appium Inspector para Identificar Elementos
1. [Baixe e instale o Appium Inspector](https://github.com/appium/appium-inspector/releases)
2. **Configure o Appium Inspector**
    - Abra o Appium Inspector e informe:
        - Remote host: `localhost`
        - Port: `4723`
        - Path: `/wd/hub`
        - Permitir certificados não autorizados (Allow Unauthorized Certificates)
3. **Defina as DesiredCapabilities**
```java
   capabilities.setCapability("udid", "192.168.56.101:5555");
   capabilities.setCapability("platformVersion", "12");
   capabilities.setCapability("appPackage", "com.bng.calculator");
   capabilities.setCapability("appActivity", "com.bng.calc.MainActivity");
   capabilities.setCapability("platformName", "Android");
   capabilities.setCapability("automationName", "UiAutomator2");
  ```
4. **Desative a “Permission Monitoring”**
    - Vá em “Opções do desenvolvedor”.
    - No final da lista, procure por “Disable Permission Monitoring” e ative-o.

### Executar o Caso de Teste
* **Executar o caso de teste**: vá até a classe Java que contém o teste, clique com o botão direito sobre o teste e selecione “Run”.
* **Executar o arquivo XML**: após criar o arquivo TestNG, clique com o botão direito sobre o arquivo XML e selecione “Run”.

---

### Baixar Emulador Genymotion & Baixar APK do Google Play
* [Baixar Genymotion Emulator](https://www.genymotion.com/download/)
* [Baixar Oracle VM VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* [Baixar APK do Google Play](https://apps.evozi.com/apk-downloader/)

### Recursos Relacionados
* [Comandos Appium](https://dpgraham.github.io/docs/en/commands/status/)
* [Solução de Problemas de Atividades no Android](https://appium.io/docs/en/writing-running-appium/android/activity-startup/)
* [Documentação API do Appium](https://appium.io/docs/en/about-appium/api/)
* [Selenium WebDriver](https://www.selenium.dev/documentation/webdriver/)