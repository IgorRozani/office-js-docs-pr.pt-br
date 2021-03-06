---
title: Desenvolver suplementos do Office para o Angular
description: ''
ms.date: 12/04/2017
ms.openlocfilehash: 65b2a229e0379106b63b0f1abaaa8b66d7cdf367
ms.sourcegitcommit: eb74e94d3e1bc1930a9c6582a0a99355d0da34f2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "25004970"
---
# <a name="develop-office-add-ins-with-angular"></a>Desenvolver suplementos do Office para o Angular

Este artigo fornece orientações sobre como usar o Angular 2+ para criar um Suplemento do Office como um aplicativo de página única.

> [!NOTE]
> Você tem alguma contribuição a fazer com base na sua experiência de uso do Angular para criar Suplementos do Office? É possível contribuir com este artigo no [GitHub](https://github.com/OfficeDev/office-js-docs) ou enviando seus comentários por meio de uma [questão](https://github.com/OfficeDev/office-js-docs-pr/issues) no repositório. 

Para ver um exemplo de Suplementos do Office criado utilizando a estrutura do Angular, confira o [Suplemento de Verificação de Estilo do Word Criado no Angular](https://github.com/OfficeDev/Word-Add-in-Angular2-StyleChecker).

## <a name="install-the-typescript-type-definitions"></a>Instalar as definições de tipo TypeScript
Abra uma janela de nodejs e insira o seguinte na linha de comando: 

```bash
npm install --save-dev @types/office-js
```

## <a name="bootstrapping-must-be-inside-officeinitialize"></a>A inicialização deve ocorrer no Office.initialize

Em qualquer página que chame as APIs do JavaScript do Office, do Word ou do Excel, seu código deve atribuir primeiro um método para a propriedade `Office.initialize`. (Se você não tiver nenhum código de inicialização, o corpo do método poderá ser apenas símbolos "`{}`" vazios, mas você não deve deixar a propriedade `Office.initialize` indefinida. Para mais detalhes, confira [Iniciar o suplemento](understanding-the-javascript-api-for-office.md#initializing-your-add-in).) O Office chama esse método imediatamente depois que ele inicializa as bibliotecas JavaScript do Office.

**O seu código de inicialização do Angular deve ser chamado dentro do método atribuído a `Office.initialize`** para garantir que as bibliotecas JavaScript do Office inicializem primeiro. O exemplo a seguir mostra como fazer isso. Este código deve estar no arquivo main.ts do projeto.

```js
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
import { AppModule } from './app.module';

Office.initialize = function () {
  const platform = platformBrowserDynamic();
  platform.bootstrapModule(AppModule);
};
```

## <a name="use-the-hash-location-strategy-in-the-angular-application"></a>Use a estratégia de localização de hash no aplicativo Angular

A navegação entre rotas no aplicativo pode não funcionar se você não especificar a estratégia de localização de hash. Você pode fazer isso de duas maneiras. Primeiro, você pode especificar um provedor para a estratégia de localização no módulo do seu aplicativo, conforme mostrado no exemplo a seguir. Ele fica no arquivo app.module.ts.

```js
import { LocationStrategy, HashLocationStrategy } from '@angular/common';
// Other imports suppressed for brevity

@NgModule({
  providers: [
    { provide: LocationStrategy, useClass: HashLocationStrategy },
    // Other providers suppressed
  ],
  // Other module properties suppressed
})
export class AppModule { }
``` 

Se você definir suas rotas em um módulo de roteamento distinto, há uma forma alternativa para especificar a estratégia de localização de hash. No seu arquivo .ts do módulo de roteamento, transmita um objeto de configuração para a função `forRoot` que especifica a estratégia. O código a seguir é um exemplo. 

```js
import { RouterModule, Routes } from '@angular/router';
// Other imports suppressed for brevity

const routes: Routes = // route definitions go here

@NgModule({
  imports: [RouterModule.forRoot(routes, { useHash: true })],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```   


## <a name="consider-wrapping-fabric-components-with-angular-components"></a>Considere a possibilidade de dispor componentes do Fabric com componentes do Angular

Recomendamos usar o uso do estilo [Office UI Fabric](https://developer.microsoft.com/fabric#/fabric-js) no seu suplemento. O Fabric contém componentes que vêm com em várias versões, incluindo uma versão [baseada no TypeScript](https://github.com/OfficeDev/office-ui-fabric-js). Considere o uso de componentes do Fabric no seu suplemento dispondo-os em componentes do Angular. Para ver um exemplo de como fazer isso, consulte [Suplemento de verificação de estilo do Word criado no Angular](https://github.com/OfficeDev/Word-Add-in-Angular2-StyleChecker). Observe, por exemplo, como o componente do Angular definido em [fabric.textfield.wrapper](https://github.com/OfficeDev/Word-Add-in-Angular2-StyleChecker/blob/master/app/shared/office-fabric-component-wrappers/fabric.textfield.wrapper.component.ts) importa o arquivo do Fabric TextField.ts, onde o componente do Fabric é definido. 


## <a name="using-the-office-dialog-api-with-angular"></a>Usar a API de diálogo do Office com o Angular

A API de Diálogo do Suplemento do Office permite que seu suplemento abra uma página em uma caixa de diálogo semi-modal que pode trocar informações com a página principal, que costuma ficar no painel de tarefas. 

O método [displayDialogAsync](https://docs.microsoft.com/javascript/api/office/office.ui?view=office-js) usa um parâmetro que especifica a URL da página que deve ser aberta na caixa de diálogo. Seu suplemento pode ter uma página HTML distinta (diferente da página de base) para transmitir esse parâmetro ou você pode transmitir a URL de uma rota em um aplicativo do Angular. 

É importante lembrar, se você transmitir uma rota, que a caixa de diálogo cria uma nova janela com seu próprio contexto de execução. Sua página de base e todos os códigos de inicialização são executados novamente nesse novo contexto e todas as variáveis são definidas para seus valores iniciais na caixa de diálogo. Então essa técnica lança uma segunda instância do seu aplicativo com uma única página na caixa de diálogo. O código que altera as variáveis na caixa de diálogo não altera a versão do painel tarefas das mesmas variáveis. Da mesma forma, a caixa de diálogo tem seu próprio armazenamento de sessão, que não pode ser acessado a partir do código no painel de tarefas.  


## <a name="trigger-the-ui-update"></a>Acionar a atualização da interface do usuário

Em um aplicativo do Angular, às vezes, a interface do usuário não é atualizada. Isso ocorre porque essa parte do código fica sem a zona do Angular. A solução é colocar o código na região, conforme mostrado no exemplo a seguir.

```js
import { NgZone } from '@angular/core';

export class MyComponent {
  constructor(private zone: NgZone) { }

  myFunction() {
    this.zone.run(() => {
      // the codes that need update the UI
    });
  }
}
``` 

## <a name="using-observable"></a>Usando o Observable

O Angular usa o RxJS (Expansões Reativas para JavaScript) e o RxJS introduz os objetos `Observable` e `Observer` para implementar o processamento assíncrono. Esta seção fornece uma breve introdução ao uso de `Observables`; para saber mais informações, consulte a documentação de [RxJS](http://reactivex.io/rxjs/) oficial.

Um `Observable` é como um objeto `Promise` em certos aspectos. Ele é retornado diretamente de uma chamada assíncrona, mas poderá só ser resolvido algum tempo depois. Contudo, embora `Promise` seja um único valor (que pode ser um objeto de matriz), um `Observable` é uma matriz de objetos (possivelmente com apenas um único membro). Isso permite que o código chame [métodos de matriz](https://www.w3schools.com/jsref/jsref_obj_array.asp), como `concat`, `map` e `filter`, em objetos `Observable`. 

### <a name="pushing-instead-of-pulling"></a>Obter em vez de enviar

Seu código "obtém" objetos `Promise` atribuindo-os a variáveis, mas objetos `Observable` "enviam" seus valores para objetos que se *inscrevem* no `Observable`. Os assinantes são objetos `Observer`. O benefício da arquitetura push é que novos membros podem ser adicionados à matriz `Observable` ao longo do tempo. Quando um novo membro é adicionado, todos os objetos `Observer` que assinam o `Observable` recebem uma notificação. 

O `Observer` é configurado para processar cada novo objeto (chamado o "próximo" objeto) com uma função. (Ele também é configurado para responder a um erro e a uma notificação de conclusão. Consulte a próxima seção para obter um exemplo.) Por esse motivo, os objetos `Observable` podem ser usados em uma maior variedade de cenários do que os objetos `Promise`. Por exemplo, além de retornarem um `Observable` de uma chamada AJAX, a maneira como você pode retornar um `Promise`, um `Observable` pode ser retornado de um manipulador de eventos, como o manipulador de eventos "modificado" de uma caixa de texto. Cada vez que um usuário insere texto na caixa, todos os objetos `Observer` inscritos reagem imediatamente usando o texto mais recente e/ou o estado atual do aplicativo como entrada. 


### <a name="waiting-until-all-asynchronous-calls-have-completed"></a>Aguardando a conclusão de todas as chamadas assíncronas

Quando quiser garantir que um retorno de chamada só seja executado quando todos os membros de um conjunto de objetos `Promise` forem resolvidos, use o método `Promise.all()`.

```js
myPromise.all([x, y, z]).then(
  // TODO: Callback logic goes here
)
``` 

Para fazer o mesmo com um objeto `Observable`, use o método [Observable.forkJoin()](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/forkjoin.md).  

```js
const source = Observable.forkJoin([x, y, z]);

const subscription = source.subscribe(
  x => {
    // TODO: Callback logic goes here
  },
  err => console.log('Error: ' + err),
  () => console.log('Completed')
);
``` 

