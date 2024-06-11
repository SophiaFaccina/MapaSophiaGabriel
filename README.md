# MapaSophiaGabriel

![image](https://github.com/GabrielAngelon/MapaGabrielSophia/assets/149213303/98ac72a0-4cad-41cb-9659-5a53fa66b09c)

- Como e onde adicionar as permissões necessárias para obter a localização pelo GPS;
- Como simular a localização no emulador do Android;
- Trechos de código comentado para adicionar uma marcação em um mapa baseado na localização do GPS;
- Páginas da documentação oficial do MapBox.


## Configurar credenciais.
  
Antes de instalar o SDK, você precisará reunir as credenciais apropriadas. Você não precisa continuar com Configurar seu token, mas copie e salve o token.

- Um token de acesso público:
```
Na página de tokens da sua conta, você pode copiar seu token público padrão ou clicar
no botão Criar um token para criar um novo token público;

Na página de tokens da sua conta, clique no botão Criar um token;

Na página de criação do token, dê um nome ao token e verifique se a caixa ao lado do escopo está marcada;

Clique no botão Criar token na parte inferior da página para criar seu token;

O token que você criou é um token secreto, o que significa que você terá apenas
uma oportunidade de copiá-lo em algum lugar seguro.
```

Como e onde adicionar as dependências e configurações no projeto para utilizar a API;
Depois de ter todas as credenciais necessárias, você pode iniciar o desenvolvimento de aplicativos de demonstração. Conclua as instruções a seguir passo a passo. Dependendo da sua experiência com desenvolvimento Android e ferramentas de desenvolvimento já instaladas, algumas etapas podem ser ignoradas.
Baixe o Android Studio. É preferível escolher a versão estável mais recente disponível do Android Studio. O SDK de Preenchimento Automático de Endereço requer Java 8 ou posterior para ser executado. Novas versões do Android Studio incorporaram o Java 11.
Crie um novo projeto. Selecione na janela como um modelo. Clique no botão.Empty ActivityNew ProjectNext

## Android:
  
Vamos começar a configuração para Android no arquivo android/app/build.gradle , nele desça até perto do final e procure o objeto dependencies, dentro dele terão algumas linhas começando pela palavra compile, dentro desse objeto, adicione o seguinte trecho:

```
implementation project(':mapbox-react-native-mapbox-gl') {
  implementation ('com.squareup.okhttp3:okhttp:3.6.0') {
    force = true
  }
}
```

Abra agora o arquivo android/settings.gradle, e nele adicione no final as linhas:

```
include ':mapbox-react-native-mapbox-gl'
project(':mapbox-react-native-mapbox-gl').projectDir = new File(rootProject.projectDir, '../node_modules/@mapbox/react-native-mapbox-gl/android/rctmgl')
```

E agora pra finalizar vamos fazer algumas modificações no arquivo:

 > android/app/src/main/java/com/<nome_do_projeto>/MainApplication.java

a primeira delas é adicionar a importação do Mapbox logo abaixo da importação do SoLoader, ficando assim:

```
import com.facebook.soloader.SoLoader;
import com.mapbox.rctmgl.RCTMGLPackage;
```

Feito isso falta apenas instanciar a classe do Mapbox e para isso procure o método getPackages, e dentro dele, logo abaixo da linha new MainReactPackage() adicione o seguinte código:

```
new RCTMGLPackage()
```

Obs: Não se esqueça de adicionar uma  vírgula (,) no final da linha do MainReactPackage.
E assim finalizamos a configuração para o Android, agora falta pouco, só configurar para o IOS e partir pro código, mas antes de prosseguir faça o teste de rodar a aplicação no Emulador do Android para verificar se não ocorre nenhum erro na compilação.

[Documentação MapBox para Android](https://docs.mapbox.com/android/maps/guides/)
