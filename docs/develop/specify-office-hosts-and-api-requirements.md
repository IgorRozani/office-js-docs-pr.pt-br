---
title: Especificar requisitos de API e hosts do Office
description: ''
ms.date: 12/04/2017
ms.openlocfilehash: ff6c0e4b4b2f8a517a62932722c34142ffdab609
ms.sourcegitcommit: c53f05bbd4abdfe1ee2e42fdd4f82b318b363ad7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "25505976"
---
# <a name="specify-office-hosts-and-api-requirements"></a>Especificar requisitos de API e hosts do Office

Seu suplemento do Office pode depender de um host específico do Office, um conjunto de requisitos, um membro de API ou uma versão da API para funcionar conforme o esperado. Por exemplo, o suplemento pode:

- Executar em um único aplicativo do Office (Word ou Excel) ou em diversos aplicativos.
    
- Usar as APIs JavaScript que estão disponíveis apenas em algumas versões do Office. Por exemplo, você pode usar as APIs JavaScript do Excel em um suplemento executado no Excel 2016. 
    
- Executar apenas nas versões do Office que deem suporte a membros da API que seu suplemento usa.
    
Este artigo ajuda você a entender quais opções você deve escolher para garantir que seu suplemento funcione conforme o esperado e atinja o público mais amplo possível.

> [!NOTE]
> Para uma visão de alto nível dos locais em que os suplementos do Office possuem compatibilidade, veja a página [Disponibilidade de host e de plataforma de suplementos do Office](../overview/office-add-in-availability.md). 

A tabela a seguir lista os principais conceitos discutidos neste artigo.

|**Conceito**|**Descrição**|
|:-----|:-----|
|Aplicativo do Office, aplicativo host do Office, host do Office ou host|O aplicativo do Office usado para executar seu suplemento. Por exemplo, Word, Word Online, Excel, entre outros.|
|Plataforma|Onde o host do Office é executado, por exemplo, no Office Online ou no Office para iPad.|
|Conjunto de requisitos|Um grupo nomeado de membros relacionados da API. Os suplementos usam conjuntos de requisitos para determinar se o host do Office dá suporte a membros da API usados por seu suplemento. É mais fácil testar a compatibilidade com um conjunto de requisitos do que com membros individuais da API. A compatibilidade para um conjunto de requisitos varia de acordo com o host do Office e a versão do host do Office. <br >Conjuntos de requisitos são especificados no arquivo de manifesto. Ao especificar conjuntos de requisitos no manifesto, você estabelece o nível mínimo de suporte à API que o host do Office deve fornecer a fim de executar seu suplemento. Os hosts do Office que não dão suporte aos conjuntos de requisitos especificados no manifesto não podem executar o suplemento, e seu suplemento não aparecerá em <span class="ui">Meus Suplementos</span>. Isso restringe onde seu suplemento é disponibilizado. Isso é definido no código usando verificações no tempo de execução. Para obter uma lista completa de conjuntos de requisitos, confira [Conjuntos de requisitos de Suplemento do Office](https://docs.microsoft.com/office/dev/add-ins/reference/requirement-sets/office-add-in-requirement-sets?view=office-js).|
|Verificação em tempo de execução|Um teste é executado em tempo de execução para determinar se o host do Office que está executando seu suplemento oferece suporte aos conjuntos de requisitos ou métodos usados por seu suplemento. Para executar uma verificação em tempo de execução, use uma instrução **if** com o método **isSetSupported**, os conjuntos de requisito ou os nomes de método que não fazem parte de um conjunto de requisitos. Use as verificações em tempo de execução para garantir que seu suplemento alcance o maior número de clientes. Ao contrário dos conjuntos de requisitos, as verificações em tempo de execução não especificam o nível mínimo de suporte à API exigido do host do Office para que seu suplemento possa ser executado. Em vez disso, use a instrução **if** para determinar se há compatibilidade com um membro da API. Se houver, você poderá oferecer mais funcionalidades em seu suplemento. Seu suplemento sempre aparecerá em **Meus Suplementos** ao usar verificações em tempo de execução.|

## <a name="before-you-begin"></a>Antes de começar

O suplemento deve usar a versão mais recente do esquema de manifesto de suplemento. Se você usar as verificações em tempo de execução em seu suplemento, use a biblioteca mais recente da API JavaScript para Office (office.js).

### <a name="specify-the-latest-add-in-manifest-schema"></a>Especifique o esquema de manifesto de suplemento mais recente

Seu manifesto de suplemento deve usar a versão 1.1 do esquema de manifesto de suplemento. Defina o elemento **OfficeApp** no manifesto do seu suplemento da seguinte maneira.

```XML
<OfficeApp xmlns="http://schemas.microsoft.com/office/appforoffice/1.1" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:type="TaskPaneApp">
```

### <a name="specify-the-latest-javascript-api-for-office-library"></a>Especifique a biblioteca mais recente de API JavaScript para Office

Se você usar as verificações em tempo de execução, faça referência à versão mais recente da biblioteca de API JavaScript para Office na CDN (rede de distribuição de conteúdo). Para tanto, adicione a seguinte marca `script` ao código HTML. O uso de `/1/` na URL da CDN garante a referência à versão mais recente do Office.js.

```HTML
<script src="https://appsforoffice.microsoft.com/lib/1/hosted/Office.js" type="text/javascript"></script>
```

## <a name="options-to-specify-office-hosts-or-api-requirements"></a>Opções para especificar os hosts do Office ou requisitos de API

Ao especificar os hosts do Office ou os requisitos de API, há vários fatores a serem considerados. O diagrama a seguir mostra como decidir sobre qual técnica usar em seu suplemento.

![Escolha a melhor opção para o seu suplemento ao especificar os hosts do Office ou os requisitos de API](../images/options-for-office-hosts.png)

- Se o seu suplemento for executado em um host do Office, defina o elemento **Hosts** no manifesto. Para saber mais, confira [Definir o elemento Hosts](#set-the-hosts-element).
    
- Para definir o conjunto de requisitos mínimos ou os membros da API que devem receber suporte de um host do Office para que seu suplemento seja executado, defina o elemento **Requirements** no manifesto. Para saber mais, confira [Definir o elemento Requirements no manifesto](#set-the-requirements-element-in-the-manifest).
    
- Se você quiser fornecer outras funcionalidades caso conjuntos de requisitos ou membros da API específicos estejam disponíveis no host do Office, execute uma verificação em tempo de execução no código JavaScript do seu suplemento. Por exemplo, se o seu suplemento for executado no Excel 2016, use os membros da nova API JavaScript para Excel a fim de fornecer outras funcionalidades. Para saber mais, confira [Usar verificações de tempo de execução em seu código JavaScript](#use-runtime-checks-in-your-javascript-code).
    
## <a name="set-the-hosts-element"></a>Definir o elemento Hosts

Para fazer seu suplemento ser executado em um aplicativo host do Office, use os elementos  **Hosts** e **Host** no manifesto. Se você não especificar o elemento **Hosts**, o suplemento será executado em todos os hosts.

Por exemplo, a declaração de **Hosts** e **Host** a seguir especifica que o suplemento funcionará com qualquer versão do Excel, o que inclui o Excel para Windows, o Excel Online e o Excel para iPad.

```xml
<Hosts>
  <Host Name="Workbook" />
</Hosts>
```

O elemento **Hosts** pode conter um ou mais elementos **Host**. O elemento **Host** especifica o host do Office exigido por seu suplemento. O atributo **Name** é obrigatório e pode ser definido com um dos valores a seguir.

| Nome          | Aplicativos host do Office                      |
|:--------------|:----------------------------------------------|
| Database      | Aplicativos Web do Access                               |
| Document      | Word para Windows, Mac, iPad e Online        |
| Mailbox       | Outlook para Windows, Mac, Web e Outlook.com | 
| Presentation  | PowerPoint para Windows, Mac, iPad e Online  |
| Project       | Project                                       |
| Pasta de trabalho      | Excel para Windows, Mac, iPad e Online           |

> [!NOTE]
> O atributo `Name` especifica o aplicativo host do Office que pode executar seu suplemento. Há compatibilidade com hosts do Office em várias plataformas, que são executados em computadores, navegadores da Web, tablets e dispositivos móveis. Você não pode especificar qual plataforma pode ser usada para executar seu suplemento. Por exemplo, se você especificar `Mailbox`, o Outlook e o Outlook Web App podem ser usados para executar o suplemento. 


## <a name="set-the-requirements-element-in-the-manifest"></a>Definir o elemento Requirements no manifesto

O elemento **Requirements** especifica os conjuntos de requisitos mínimos ou os membros da API que devem receber suporte de um host do Office para que seu suplemento seja executado. O elemento **Requirements** pode especificar tanto conjuntos de requisitos quanto métodos individuais usados em seu suplemento. Na versão 1.1 do esquema de manifesto de suplemento, o elemento **Requirements** é opcional para todos os suplementos, exceto para os suplementos do Outlook.

> [!WARNING]
> Use o elemento **Requirements** apenas para especificar conjuntos de requisitos ou membros de API cruciais ao seu suplemento. Se o host do Office ou a plataforma não der suporte ao conjunto de requisitos ou membros da API especificados no elemento **Requirements**, o suplemento não será executado no host ou na plataforma e não será exibido em **Meus Suplementos**. Em vez disso, recomendamos que você disponibilize seu suplemento em todas as plataformas de um host do Office, como o Excel para Windows, o Excel Online e o Excel para iPad. Para disponibilizar seu suplemento em _todos_ os hosts e plataformas do Office, use verificações em tempo de execução em vez do elemento **Requirements**.

O exemplo de código a seguir mostra um suplemento que carrega em todos os aplicativos host do Office que dão suporte ao seguinte:

-  O conjunto de requisitos **TableBindings**, que tem uma versão mínima de 1.1.
    
-  O conjunto de requisitos **OOXML**, que tem uma versão mínima de 1.1.
    
-  O método **Document.getSelectedDataAsync**.

```XML
<Requirements>
   <Sets DefaultMinVersion="1.1">
      <Set Name="TableBindings" MinVersion="1.1"/>
      <Set Name="OOXML" MinVersion="1.1"/>
   </Sets>
   <Methods>
      <Method Name="Document.getSelectedDataAsync"/>
   </Methods>
</Requirements>
```

- O elemento **Requirements** contém os elementos filhos **Sets** e **Methods**.
    
- O elemento **Sets** pode conter um ou mais elementos **Set**. **DefaultMinVersion** especifica o valor padrão de **MinVersion** para todos os elementos filhos de **Set**.
    
- O elemento **Set** especifica os conjuntos de requisitos que devem receber suporte do host do Office para que o suplemento seja executado. O atributo **Name** especifica o nome do conjunto de requisitos. **MinVersion** especifica a versão mínima do conjunto de requisitos. **MinVersion** substitui o valor de **DefaultMinVersion**. Para saber mais sobre os conjuntos de requisito e sobre as versões de conjuntos de requisitos aos quais membros de sua API pertencem, confira [Conjuntos de requisitos de suplementos do Office](https://docs.microsoft.com/office/dev/add-ins/reference/requirement-sets/office-add-in-requirement-sets?view=office-js).
    
- O elemento **Methods** pode conter um ou mais elementos **Method**. Você não pode usar o elemento **Methods** com suplementos do Outlook.
    
- O elemento **Methods** especifica um método individual que deve receber suporte no host do Office em que o suplemento é executado. O atributo **Name** é obrigatório e especifica o nome do método qualificado com seu objeto pai.
    

## <a name="use-runtime-checks-in-your-javascript-code"></a>Usar verificações em tempo de execução em seu código JavaScript


Se certos conjuntos de requisitos são compatíveis no host do Office, você pode oferecer funcionalidades adicionais em seu suplemento. Por exemplo, você pode usar a nova API JavaScript para Word em seu suplemento existente se o seu suplemento for executado no Word 2016. Para fazer isso, use o método **isSetSupported** com o nome do conjunto de requisitos. **isSetSupported** determina, em tempo de execução, se o host do Office que está executando o suplemento dá suporte ao conjunto de requisitos. Se houver suporte para o conjunto de requisitos, **isSetSupported** retorna **true** e executa o código adicional que usa os membros da API desse conjunto de requisitos. Se o host do Office não dá suporte ao conjunto de requisitos, **isSetSupported** retorna **false** e o código adicional não é executado. O código a seguir mostra a sintaxe a ser usada com **isSetSupported**.


```js
if (Office.context.requirements.isSetSupported(RequirementSetName , VersionNumber))
{
   // Code that uses API members from RequirementSetName.
}

```


-  _RequirementSetName_ (obrigatório) é uma sequência de caracteres que representa o nome do conjunto de requisitos. Para saber mais sobre os conjuntos de requisitos disponíveis, confira [Conjuntos de requisitos de Suplemento do Office](https://docs.microsoft.com/office/dev/add-ins/reference/requirement-sets/office-add-in-requirement-sets?view=office-js).
    
-  _VersionNumber_ (opcional) é a versão do conjunto de requisitos.
    
No Excel 2016 ou no Word 2016, use **isSetSupported** com os conjuntos de requisitos **ExcelAPI** ou **WordAPI**. O método **isSetSupported** e os conjuntos de requisitos **ExcelAPI** e **WordAPI** estão disponíveis no arquivo Office.js mais recente disponível na CDN. Se você não usa o Office.js da CDN, seu suplemento pode gerar exceções, pois **isSetSupported** fica indefinido. Para saber mais, confira [Especificar a biblioteca mais recente de API JavaScript para Office](#specify-the-latest-javascript-api-for-office-library). 


> [!NOTE]
> **isSetSupported** não funciona no Outlook ou no Outlook Web App. Para usar uma verificação em tempo de execução no Outlook ou no Outlook Web App, use a técnica descrita em [Verificações em tempo de execução usando métodos que não fazem parte de um conjunto de requisitos](#runtime-checks-using-methods-not-in-a-requirement-set).

O exemplo de código a seguir mostra como um suplemento pode fornecer outras funcionalidades para hosts do Office diferentes que podem dar suporte a conjuntos de requisitos ou membros de API diferentes.




```js
if (Office.context.requirements.isSetSupported('WordApi', 1.1))
{
    // Run code that provides additional functionality using the JavaScript API for Word when the add-in runs in Word 2016.
}
else if (Office.context.requirements.isSetSupported('CustomXmlParts'))
{
      // Run code that uses API members from the CustomXmlParts requirement set.
}
else 
{
    // Run additional code when the Office host is not Word 2016, and when the Office host does not support the CustomXmlParts requirement set.
}

```


## <a name="runtime-checks-using-methods-not-in-a-requirement-set"></a>Verificações em tempo de execução usando métodos que não fazem parte de um conjunto de requisitos


Alguns membros de API não pertencem a conjuntos de requisitos. Isso aplica-se apenas a membros da API que fazem parte do namespace [API JavaScript para Office](https://docs.microsoft.com/office/dev/add-ins/reference/javascript-api-for-office?view=office-js) (tudo sob o Office.), não a membros de API que pertencem a namespaces da API JavaScript para Word (qualquer coisa no Word.) ou da [Referência sobre a API JavaScript para suplementos do Excel](https://docs.microsoft.com/office/dev/add-ins/reference/overview/excel-add-ins-reference-overview?view=office-js) (qualquer coisa no Excel.). Quando seu suplemento depende de um método que não faz parte de um conjunto de requisitos, é possível usar a verificação no tempo de execução para determinar se o método tem suporte no host do Office, conforme mostra o exemplo de código a seguir. Para obter uma lista completa dos métodos que não pertencem a um conjunto de requisitos, confira [Conjuntos de requisitos de Suplemento do Office](https://docs.microsoft.com/office/dev/add-ins/reference/requirement-sets/office-add-in-requirement-sets?view=office-js).


> [!NOTE]
> Recomendamos limitar o uso desse tipo de verificação em tempo de execução no código de seu suplemento.

O exemplo de código a seguir verifica se o host oferece suporte a **document.setSelectedDataAsync**.




```js
if (Office.context.document.setSelectedDataAsync)
{
    // Run code that uses document.setSelectedDataAsync.
}
```


## <a name="see-also"></a>Confira também

- [Manifesto XML dos suplementos do Office](add-in-manifests.md)
- [Conjuntos de requisitos em Suplementos do Office](https://docs.microsoft.com/office/dev/add-ins/reference/requirement-sets/office-add-in-requirement-sets?view=office-js)
- [Word-Add-in-Get-Set-EditOpen-XML](https://github.com/OfficeDev/Word-Add-in-Get-Set-EditOpen-XML)