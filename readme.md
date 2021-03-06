
#Testes Mobile Uolet

Utilizei para a criação do Script de testes do aplicativo [ UOLET ](https://uolet.com/) a IDE Eclipse utilizando a linguagem Java.

Para gerar os vários casos de testes é possivel utilizar o JUnit ou o [ TestNG ](http://testng.org/doc/index.html), optei pelo TestNG.

Para acessar as funcionalidades do **APP mobile** utilizei o Framework [ Appium ](http://appium.io/), enviando comandos do selenium com o java.

O teste emgloba vários testes de comportamento e de aceitação visando a qualidade e garantindo que todas as funcionalidades estão se comportando corretamente.

#####Atenção
Necessário para que o teste funcione ter o SDK Android para usar a tools **ADB Devices** e o **Appium** instalado.

No linux necessário adicionar as variaveis do ADB e do APPIUM no $PATH global.

No windown a instalação é feita apartir de .exe e o PATH e adicionado automaticamente. 

Qualquer duvida ler documentação [ Appium - Documentação ](http://appium.io/documentation.html?lang=pt) .


# Guia pratico para executar os testes

1- Altere o nome do device onde quer que o appium rode seus códigos.

```java
/*Setando meu device - Android Uolet*/
cap.setCapability(MobileCapabilityType.DEVICE_NAME, "LGH342c0e8e752"); 
```

Para saber como descobrir qual o nome do seu device execute o comando **ADB DEVICES** no terminal.

```terminal
$ adb devices
List of devices attached
LGH342c0e8e752	no permissions;
```


**Obs:** Caso o Android não apareça na lista, lembre-se que deve estar com o modo **DESENVOLVEDOR ATIVADO** e deburação liberada para o computador.


2- Inicie o Appium utilizando o comando **appium** no terminal.


```terminal
$ appium
[Appium] Welcome to Appium v1.6.3 (REV 40e40975ebd3593d08c3f83de2546258f9ddf11d)
[Appium] Appium REST http interface listener started on 0.0.0.0:4723

```


3- Vá no case teste ou no xml de teste do testNG e selecione **Run As > Run TestNG Test**


4- Aguarde o fim do teste para obter relatório sobre sucesso e falhas.

======



# Organização dos Testes aplicativo Uolet
======

Os testes vão ser organizados em test cases com a IDE Eclipse, que serão executados pelo TestNG em uma ordem pré determinada.

###### Obs: Em todos os casos de testes o driver **AndroidDriver** vai ter suas **SetCapability** configuradas no inicio da sua execução antes do **TestCase** iniciar e finalizado após os **TestCase** ter sido *completamente* executado.
======

## Suite de teste
======

#### TestCase 1 (finalizado)

Abrindo aplicativo pela primeira vez

* Aguardando aplicativo ser carregado
* Passando 3 paginas de tutorial e indo para tela home
* Clica em carteira na pagina home sem ter feito cadastro e deve ser redirecionado para tela login
* Efetua login no contexto UOLET (via email)
* Volta a tela home agora estando logado
* Clica no botão QrCode, verifica se ele foi carregado e volta a tela home.
* Clica no botão Mapa, verifica se ele foi carregado e volta a tela home.
* Clica no botão Carteira, agora logado, verifica se foi carregada a tela Carteira Uolet e volta a tela home.

###### Obs²: Testes de Leitura de QrCode e Testes de GeoLocalização serão feitos manualmente, pois são funcionalidades nativas do android e não são contempladas via Appium.


#### TestCase 2 (finalizado)

Verifica Itens do Menu

* Aguardando aplicativo ser carregado
* Clicando no Menu
* Verifica se **Convidar Amigos** abre as redes sociais do celular
* Verifica se **Ver tutorial** abre o tutorial
* Verifica se **Fale conosco** abre as configurações do Email do usuario
* Verifica se **Termos de Uso** abre os termos de uso do aplicativo Uolet
* Verifica se **Política de privacidade** abre os termos de uso do aplicativo Uolet
* Verifica se **Limpar Cache** funcionalidade cancelar funciona
* Verifica se **Limpar Cache** funcionalidade excluir funciona
* Verifica se quando deslogado o **Minha Uolet** vai para a tela login
* Verifica se quando deslogado o **Criar Conta** vai para a tela login
* Verifica se quando deslogado o **Meus Interesses** vai para a tela login
* Logando Uolet
* Verifica se quando logado **Minha Uolet** vai para a tela carteira Uolet
* Verifica se quando logado **Meus Interesses** vai para a tela meus interesses e se é possivel selecionar um e voltar a tela inicial
* Verifica se o nome do usuário Logado está sendo apresentado no menu.
* Verifica se quando logado **Minha Conta** abre a tela de alteração de dados do usuário
* Verifica se o usuário realmente não pode alterar as informações se deixar o nome em branco
* Verifica se o usuário realmente não pode alterar as informações se deixar o email em branco
* Verifica se o usuário realmente tem as informações alteradas se tudo estiver preenchido corretamente
* Botão Sair efetua o Logout do sistema



#### TestCase 3 (em produção)

Verifica Tela Campanha

* Aguarda aplicativo ser carregado e logando com login Uolet
* Arrasta campanha para a direita e esquerda para testar a funcionalidad de *Visualização da campanha*
* Clica em uma campanha
* Arrasta os itens para direita e esquerda para testar a funcionalidade de *Visualização da campanha*
* Verifica a ordem dos itens
* Verifica as informações dos itens e fotos dele
* Verifica se o link do item funciona e volta para o item
* Verifica se o video do item funciona e volta para o item
* Verifica se o item é coletado e exibe mensagem de coleta


#### TestCase 4 (em produção)

Verifica Tela Carteira Uolet

* Aguarda aplicativo ser carregado e logando com login Uolet
* Clica na carteira e verificando se ela foi carregada
* Verifica se a carteira tem 3 abas, **Disponível**, **Resgatados** e **Vencidos**
* Verifica se na aba **Disponível** está o item coletado no **TestCase 3**
* Verifica se o item coletado é o mesmo item 
* Verifica se ao arrastar o item para a esquerda é exibido o botão deletar
* Verifica se o botão deletar realmente deleta o item
* Verifica se um cupom pode ser resgatado


#### TestCase 5 (em produção)

Verifica Tela Login

* Aguarda aplicativo a ser carregado e indo para tela login
* Loga via facebook usuário existente
* Loga via facebook usuário inválido
* Loga via google usuário existente
* Loga via google usuário inválido
* Loga via Uolet usuário novo
* Loga via Uolet usuário existente senha correta
* Loga via Uolet usuário existente senha inválida






	