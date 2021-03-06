---
title: Abrir automaticamente um painel de tarefas com um documento
description: ''
ms.date: 05/02/2018
ms.openlocfilehash: 2ebce1ce8bd95ee7802b5509d375f1986bb2877e
ms.sourcegitcommit: c53f05bbd4abdfe1ee2e42fdd4f82b318b363ad7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "25505913"
---
# <a name="automatically-open-a-task-pane-with-a-document"></a>Abrir automaticamente um painel de tarefas com um documento

Você pode usar comandos de suplemento no seu suplemento do Office para estender a interface do usuário do Office adicionando botões à faixa de opções do Office. Quando os usuários clicam no botão de comando, ocorre uma ação, como abrir um painel de tarefas. 

Alguns cenários exigem que um painel de tarefas abra automaticamente quando um documento é aberto, sem a interação explícita do usuário. Você pode usar o recurso autoopen do painel de tarefas, apresentado no conjunto de requisitos AddInCommands 1.1, para abrir automaticamente um painel de tarefas quando necessário. 


## <a name="how-is-the-autoopen-feature-different-from-inserting-a-task-pane"></a>De que forma o recurso autoopen é diferente da inserção de um painel de tarefas? 

Quando um usuário iniciar suplementos que não usam comandos de suplemento - por exemplo, suplementos que são executados no Office 2013 - eles serão inseridos no documento e persistirão nesse documento. Como resultado, quando outros usuários abrem o documento, é solicitado que eles instalem o suplemento e o painel de tarefas abrirá. O desafio com esse modelo é que, em muitos casos, os usuários não querem que o suplemento persista no documento. Por exemplo, um aluno que usa um suplemento de dicionário em um documento do Word pode não querer que seus colegas ou professores sejam avisados para instalar esse suplemento quando abrirem o documento.  

Com o recurso autoopen, você pode explicitamente definir, ou permitir que o usuário defina, se um suplemento do painel de tarefas irá persistir em um documento específico. 

## <a name="support-and-availability"></a>Suporte e disponibilidade
O recurso autoopen atualmente tem suporte do <!-- in **developer preview** and it is only --> nos seguintes produtos e plataformas.

|**Produtos**|**Plataformas**|
|:-----------|:------------|
|<ul><li>Word</li><li>Excel</li><li>PowerPoint</li></ul>|Plataformas suportadas para todos os produtos:<ul><li>Office para Windows Desktop. Build 16.0.8121.1000+</li><li>Office para Mac. Build 15.34.17051500+</li><li>Office Online</li></ul>|


## <a name="best-practices"></a>Práticas recomendadas

Aplique as seguintes práticas recomendadas ao usar o recurso autoopen:

- Use o recurso autoopen quando ele auxiliar a eficiência dos usuários do seu suplemento, como:
    - Quando o documento precisa do suplemento para funcionar corretamente. Por exemplo, uma planilha que inclui valores de ações que são atualizados periodicamente por um suplemento. O suplemento deverá abrir automaticamente quando a planilha for aberta para manter os valores atualizados. 
    - Quando o usuário provavelmente sempre usará o suplemento com um documento específico. Por exemplo, um suplemento que ajuda os usuários a preencher ou alterar dados em um documento, obtendo informações de um sistema back-end. 
- Permita que os usuários ativem ou desativem o recurso autoopen. Inclua uma opção em sua interface de usuário para que eles possam escolher quando não querem mais que o suplemento abra automaticamente no painel de tarefas.  
- Use a detecção do conjunto de requisitos para determinar se o recurso autoopen está disponível e forneça um comportamento de fallback, se não estiver.
- Não use o recurso autoopen para aumentar artificialmente o uso do seu suplemento. Se não faz sentido seu suplemento abrir automaticamente em determinados documentos, esse recurso pode incomodar os usuários. 

    > [!NOTE]
    > Se a Microsoft detectar abuso do recurso autoopen, seu suplemento poderá ser rejeitado no AppSource. 

- Não use esse recurso para fixar vários painéis de tarefas. Você só pode definir um painel do suplemento para abrir automaticamente com um documento.  

## <a name="implementation"></a>Implementação
Para implementar o recurso autoopen:

- Especifique o painel de tarefas a ser aberto automaticamente.
- Marque o documento para abrir o painel de tarefas automaticamente.

> [!IMPORTANT]
> O painel que você designar para abrir automaticamente só será aberto se o suplemento já estiver instalado no dispositivo do usuário. Se o usuário não tiver o suplemento instalado quando abrir um documento, o recurso autoopen não funcionará e a configuração será ignorada. Se você também exigir que o suplemento seja distribuído com o documento, será preciso definir a propriedade de visibilidade como 1. Isso só pode ser feito usando OpenXML. Um exemplo será fornecido posteriormente neste artigo. 

### <a name="step-1-specify-the-task-pane-to-open"></a>Etapa 1: especificar o painel de tarefas que será aberto
Para especificar o painel de tarefas que será aberto automaticamente, defina o valor [TaskpaneId](https://docs.microsoft.com/office/dev/add-ins/reference/manifest/action?view=office-js#taskpaneid) para **Office.AutoShowTaskpaneWithDocument**. Você só pode definir esse valor em um painel de tarefas. Se você definir esse valor em vários painéis de tarefas, a primeira ocorrência do valor será reconhecida e as outras serão ignoradas. 

O exemplo a seguir mostra o valor TaskPaneId configurado para Office.AutoShowTaskpaneWithDocument.
          
```xml
<Action xsi:type="ShowTaskpane">
    <TaskpaneId>Office.AutoShowTaskpaneWithDocument</TaskpaneId>
    <SourceLocation resid="Contoso.Taskpane.Url" />
</Action>
```     

### <a name="step-2-tag-the-document-to-automatically-open-the-task-pane"></a>Etapa 2: marcar o documento para abrir o painel de tarefas automaticamente

Você pode marcar o documento para acionar o recurso autoopen de duas maneiras. Escolha a alternativa que funciona melhor para o seu cenário.  


#### <a name="tag-the-document-on-the-client-side"></a>Marcar o documento no lado do cliente
Use o método [settings.set](https://docs.microsoft.com/javascript/api/office/office.settings?view=office-js) do Office.js para configurar o **Office.AutoShowTaskpaneWithDocument** para **true**, conforme mostrado no exemplo a seguir.   

```js
Office.context.document.settings.set("Office.AutoShowTaskpaneWithDocument", true);
Office.context.document.settings.saveAsync();
```

Use esse método se você precisar marcar o documento como parte da interação com o suplemento (por exemplo, assim que o usuário criar uma ligação ou escolher uma opção para indicar que deseja que o painel abra automaticamente).

#### <a name="use-open-xml-to-tag-the-document"></a>Usar o Open XML para marcar o documento
Você pode usar o Open XML para criar ou modificar um documento e adicionar a marcação XML do Open Office apropriada para acionar o recurso autoopen. Veja um exemplo de como fazer isso em [Office-OOXML-EmbedAddin](https://github.com/OfficeDev/Office-OOXML-EmbedAddin). 

Adicione duas partes do Open XML no documento:

- Uma parte webextension
- Uma parte do painel de tarefas

O exemplo a seguir mostra como adicionar a parte webextension.

```xml
<we:webextension xmlns:we="http://schemas.microsoft.com/office/webextensions/webextension/2010/11" id="[ADD-IN ID PER MANIFEST]">
  <we:reference id="[GUID or AppSource asset ID]" version="[your add-in version]" store="[Pointer to store or catalog]" storeType="[Store or catalog type]"/>
  <we:alternateReferences/>
  <we:properties>
    <we:property name="Office.AutoShowTaskpaneWithDocument" value="true"/>
  </we:properties>
  <we:bindings/>
  <we:snapshot xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"/>
</we:webextension>
```

A parte webextension inclui um conjunto de propriedades e uma propriedade chamada **Office.AutoShowTaskpaneWithDocument** que deve ser definida para `true`.

A parte webextension também inclui uma referência para a loja ou o catálogo com atributos para `id`, `storeType`, `store` e `version`. Dos valores `storeType`, somente quatro são relevantes para o recurso autoopen. Os valores dos outros três atributos dependem do valor de `storeType`, conforme mostrado na tabela a seguir. 

| **`storeType` valor** | **`id` valor**    |**`store` valor** | **`version` valor**|
|:---------------|:---------------|:---------------|:---------------|
|OMEX (AppSource)|A ID do ativo do suplemento no AppSource (confira a observação)|A localidade do AppSource, por exemplo, "pt-br".|A versão no catálogo do AppSource (confira a observação)|
|FileSystem (um compartilhamento de rede)|A GUID do suplemento no manifesto do suplemento.|O caminho do compartilhamento de rede. Por exemplo, "\\\\Meu Computador\\Minha Pasta Compartilhada".|A versão no manifesto do suplemento.|
|EXCatalog (implantação por meio do servidor Exchange) |A GUID do suplemento no manifesto do suplemento.|A linha EXCatalog é a linha a ser usada com suplementos que usam a Implantação Centralizada no Centro de administração do Office 365.|A versão no manifesto do suplemento.
|Registro (registro de sistema)|A GUID do suplemento no manifesto do suplemento.|"desenvolvedor"|A versão no manifesto do suplemento.|

> [!NOTE]
> Para localizar a ID de ativos e a versão de um suplemento no AppSource, vá para a página inicial do suplemento no AppSource. A ID de ativo aparece na barra de endereços no navegador. A versão aparece na seção **Detalhes** da página.

Confira mais informações sobre a marcação webextension em [[MS-OWEXML] 2.2.5. WebExtensionReference](https://msdn.microsoft.com/library/hh695383(v=office.12).aspx).

O exemplo a seguir mostra como adicionar a parte do painel de tarefas.

```xml
<wetp:taskpane dockstate="right" visibility="0" width="350" row="4" xmlns:wetp="http://schemas.microsoft.com/office/webextensions/taskpanes/2010/11">
  <wetp:webextensionref xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships" r:id="rId1" />
</wetp:taskpane>
```

Observe que neste exemplo, o atributo `visibility` está definido como "0". Isso significa que após serem adicionadas as partes webextension e painel de tarefas, a primeira vez que o documento for aberto, o usuário deverá instalar o suplemento clicando no botão **Suplemento** na faixa de opções. Depois disso, o painel de tarefas do suplemento abrirá automaticamente quando o arquivo for aberto. Além disso, ao definir `visibility` como "0", é possível usar o Office.js para permitir que os usuários ativem ou desativem o recurso autoopen. Especificamente, seu script define a configuração de documento **Office.AutoShowTaskpaneWithDocument** para `true` ou `false`. Confira mais detalhes em [Marcar o documento no lado do cliente](#tag-the-document-on-the-client-side). 

Se o elemento `visibility` é definido como "1", o painel de tarefas abrirá automaticamente na primeira vez em que o documento for aberto. O usuário é solicitado a confiar no suplemento e, quando a confiança é concedida, o suplemento é aberto. Depois disso, o painel de tarefas do suplemento abrirá automaticamente quando o arquivo for aberto. Entretanto, ao definir `visibility` como "1", não é possível usar o Office.js para permitir que os usuários ativem ou desativem o recurso autoopen. 

Definir `visibility` como "1" é uma boa opção quando o complemento e o modelo ou o conteúdo do documento são tão integrados que o usuário não pode desativar o recurso autoopen. 

> [!NOTE]
> Se quiser distribuir seu suplemento com o documento, para que os usuários sejam solicitados a instalá-lo, você deverá definir a propriedade de visibilidade como 1. Isso só pode ser feito pelo Open XML.

Uma maneira fácil de escrever o XML é primeiro executar seu suplemento e [marcar o documento no lado do cliente](#tag-the-document-on-the-client-side) para escrever o valor e, em seguida, salvar o documento e inspecionar o XML que é gerado. O Office detectará e fornecerá os valores de atributo apropriados. Você também pode usar a [Ferramenta de Produtividade Open XML SDK 2.5](https://www.microsoft.com/download/details.aspx?id=30425) para gerar o código C# para adicionar programaticamente a marcação com base no XML gerado.

## <a name="test-and-verify-opening-taskpanes"></a>Teste e verifique a abertura dos painéis de tarefas
Você pode implantar uma versão de teste do seu suplemento que abrirá automaticamente um painel de tarefas usando a Implantação Centralizada por meio do Centro de administração do Office 365. O exemplo a seguir mostra como os suplementos são inseridos do catálogo de Implantação Centralizada usando a versão da loja EXCatalog.

```xml
<we:webextension xmlns:we="http://schemas.microsoft.com/office/webextensions/webextension/2010/11" id="{52811C31-4593-43B8-A697-EB873422D156}">
    <we:reference id="af8fa5ba-4010-4bcc-9e03-a91ddadf6dd3" version="1.0.0.0" store="EXCatalog" storeType="EXCatalog"/>
    <we:alternateReferences/>
    <we:properties/>
    <we:bindings/>
    <we:snapshot xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"/>
</we:webextension>
```
Para testar o exemplo anterior, considere participar do [Programa de desenvolvedores do Office 365](https://docs.microsoft.com/office/developer-program/office-365-developer-program) e inscrever-se para uma [conta de desenvolvedor do Office 365](https://developer.microsoft.com/office/dev-program) se você ainda não tem uma assinatura do Office 365. Na verdade, você pode testar a unidade Implantação Centralizada e verificar se seu suplemento funciona conforme o esperado.


## <a name="see-also"></a>Confira também

Para obter um exemplo que mostra como usar o recurso autoopen, consulte [Exemplos de comandos de suplementos do Office](https://github.com/OfficeDev/Office-Add-in-Commands-Samples/tree/master/AutoOpenTaskpane). [Ingressar no programa de desenvolvedores do Office 365](https://docs.microsoft.com/office/developer-program/office-365-developer-program). 

