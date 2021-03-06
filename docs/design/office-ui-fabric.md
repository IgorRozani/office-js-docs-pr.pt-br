---
title: Office UI Fabric em suplementos do Office
description: ''
ms.date: 12/04/2017
ms.openlocfilehash: 7b1e4a9c377c9a60195a51115d7f275603f1ca5a
ms.sourcegitcommit: 30435939ab8b8504c3dbfc62fd29ec6b0f1a7d22
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "23944031"
---
# <a name="office-ui-fabric-in-office-add-ins"></a>Office UI Fabric em suplementos do Office 

O Office UI Fabric é uma estrutura de front-end JavaScript destinada à criação de experiências de usuário para Office e Office 365. O Fabric fornece componentes com foco em efeitos visuais que você pode estender, reformular e usar no suplemento do Office. Como o Fabric usa a linguagem de design da Microsoft, os componentes da experiência de usuário do Fabric são semelhantes a uma extensão natural do Office. 

Se estiver criando um suplemento, recomendamos usar o Office UI Fabric para criar a experiência de usuário. O uso do Office UI Fabric é opcional.

As seções a seguir explicam como começar a usar o Fabric para atender às suas necessidades. 

## <a name="use-fabric-core-icons-fonts-colors"></a>Uso do Fabric Core: ícones, fontes, cores
O Fabric Core contém os elementos principais da linguagem de design, como ícones, cores, tipo e grade. O Fabric Core é independente de estrutura. Tanto o Fabric JS como o Fabric React usam o Fabric Core.

Para começar a usar o Fabric Core:

1. Adicione a referência da CDN ao HTML da sua página.  

    ```html
    <link rel="stylesheet" href="https://static2.sharepointonline.com/files/fabric/office-ui-fabric-js/1.4.0/css/fabric.min.css">
    ```   
    
2. Use ícones e fontes do Fabric. 

    Para usar um ícone do Fabric, inclua o elemento "i" na sua página e, em seguida, faça referência às classes apropriadas. Para controlar o tamanho do ícone, você pode alterar o tamanho da fonte. Por exemplo, o código a seguir mostra como criar um ícone de tabela muito grande que usa a cor themePrimary (#0078d7). 
   
    ```html
    <i class="ms-Icon ms-font-xl ms-Icon--Table ms-fontColor-themePrimary"></i>
    ```

    Para localizar mais ícones disponíveis no Office UI Fabric, use o recurso de pesquisa na página [Ícones](https://developer.microsoft.com/fabric#/styles/icons). Quando encontrar um ícone para usar no suplemento, não deixe de adicionar um prefixo ao nome do ícone com `ms-Icon--`. 

    Para saber mais sobre os tamanhos de fonte e as cores disponíveis no Office UI Fabric, confira [Tipografia](https://developer.microsoft.com/fabric#/styles/typography) e [Cores](https://developer.microsoft.com/fabric#/styles/colors).
 
## <a name="use-fabric-components"></a>Uso dos componentes do Fabric 
O Fabric oferece uma variedade de componentes da experiência do usuário que você pode usar para criar o suplemento. Alguns desses componentes incluem:

- Componentes de entrada – por exemplo, botão, caixa de seleção e alternância
- Componentes de navegação – por exemplo, Pivot e Breadcrumb
- Componentes de notificação – por exemplo, MessageBar e balão  

Nem todos os componentes do Fabric são recomendados para uso em suplementos. Aqui está uma lista de componentes do Fabric React UX que recomendamos para suplementos:

- [Breadcrumb](https://developer.microsoft.com/fabric#/components/breadcrumb)
- [Botão](https://developer.microsoft.com/fabric#/components/button)
- [Caixa de seleção](https://developer.microsoft.com/fabric#/components/checkbox)
- [ChoiceGroup](https://developer.microsoft.com/fabric#/components/choicegroup)
- [Lista suspensa](https://developer.microsoft.com/fabric#/components/dropdown)
- [Rótulo](https://developer.microsoft.com/fabric#/components/label)
- [Lista](https://developer.microsoft.com/fabric#/components/list)
- [Tabela dinâmica](https://developer.microsoft.com/fabric#/components/pivot)
- [TextField](https://developer.microsoft.com/fabric#/components/textfield)
- [Alternância](https://developer.microsoft.com/fabric#/components/toggle)

Você pode usar diferentes estruturas do JavaScript, como Angular ou React, para criar o suplemento. Para começar a usar componentes do Fabric com sua estrutura, confira os recursos a seguir.

|**Estrutura**|**Exemplo**|
|:------------|:----------|
|**Reagir**|[Uso do Office UI Fabric React em suplementos do Office](using-office-ui-fabric-react.md )|
|**Angular**| Confira [ngOfficeUIFabric](http://ngofficeuifabric.com/), que é um projeto comunitário com diretivas do Angular 1.5, e [Considere a possibilidade de dispor componentes do Fabric com componentes do Angular 2](../develop/add-ins-with-angular2.md#consider-wrapping-fabric-components-with-angular-components)|
