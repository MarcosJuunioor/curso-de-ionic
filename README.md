# curso-de-ionic
Neste repositório, será feito um resumo do curso de IONIC da udemy.

## Introdução
O Ionic é, basicamente, um framework usado para o desenvolvimento de aplicativos por meio de tecnologias web (JS, HTML, CSS). 

## Requisitos
- NodeJS
- Ionic 
- Cordova
- npm (gerenciador de pacotes do Node) <br>

Para se ter certeza que esses recursos estão instalados, basta usar os comandos: node -v, ionic -v, cordova -v e npm -v. <br>

Caso não estejam, podem ser obtidos da seguinte forma:
- NodeJS: baixar no próprio site e depois instalar normalmente (link:https://nodejs.org/en/). O NodeJS já possui o npm.
- Ionic: executar o comando **npm install -g @ionic/cli**
- Cordova: npm install -g cordova

## Criando um projeto com o Ionic
Comando: **ionic start nome-do-projeto [opção]** <br>
Há três opções de templates para projetos: blank, tabs e sidemenu.

Para testar o aplicativo, deve-se navegar até a pasta do projeto e executar o comando "ionic serve".

## IONIC CLI - Criando uma página
O Ionic cli é a ferramenta usada para criação de aplicativos Ionic. No próprio site do framework, há toda a documentação do cli, com os comandos necessário para se criar diversos recursos (alguns já foram usados aqui como "ionic start" e "ionic serve").

Um dos comandos mais importantes é o **ionic generate**, que é usado para criação de recursos para o framework automaticamente, como **páginas, componentes, diretivas, serviços etc.** A sintaxe do mesmo é a seguinte:

ionic generate <type> <name> [options]
  
Para criação de uma página, por exemplo, usa-se o comando "ionic generate page".

## Adicionando uma página às abas (tabs)
Primeiramente, é necessário colocar a página dentro da aplicação (pode-se dizer que ela ainda não integra o app). O Ionic usa a ideia de "módulos", onde um componente pode ter uma relação de dependência com outro. Um módulo é semelhante a um escopo, isto é, cada componente tem seu próprio escopo e faz parte de algum. No caso da página criada, para que ela faça parte da aplicação, deverá ser colocada dentro do escopo da mesma. Para isso, deve-se acessar o módulo da página e copiar o seu nome (que é semelhante a "export class NOME-DO-MODULO {}). Em seguida, o nome deve ser colado dentro do módulo da aplicação (um arquivo chamado "app.module.ts"), na parte "imports". Pronto, a página foi adicionada ao app. 

A sintaxe do nome do arquivo de módulo de cada componente segue a seguinte estrutura: nome-do-componente.module.ts.

Feito o primeiro passo, basta ir ao arquivo "tabs-routing.module.ts" (na pasta "tabs") e adicionar a página criada às tabs. Para isso, deve ser colocado **dentro do arquivo** um códio semelhante a este:

      {
        path: 'NOME-DA-PAGINA',
        children: [
          {
            path: '',
            loadChildren: () =>
              import('../NOME-DA-PASTA-DA-PAGINA/NOME-DA-PAGINA.module').then(m => m.NomeDaPaginaPageModule)
          }
        ]
      },

Em seguida, é necessário criar o botão da guia correspondente ao componente adicionado. Isso pode ser feito indo ao arquivo "tabs.page.html" e adicionando o seguinte código dentro do elemento "ion-tab-bar":

    <ion-tab-button tab="NOME-DA-PAGINA">
      <ion-icon name="square"></ion-icon>
      <ion-label>Feed</ion-label>
    </ion-tab-button>
    
    
  
