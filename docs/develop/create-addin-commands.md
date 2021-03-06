---
title: Criar comandos de suplemento no manifesto para Excel, Word e PowerPoint
description: Use VersionOverrides em seu manifesto para definir comandos de suplemento para o Excel, Word e PowerPoint. Use comandos de suplemento para criar elementos de interface do usuário, adicionar botões ou listas e executar ações.
ms.date: 12/04/2017
ms.openlocfilehash: 652add3eeadcbeefc20db1bf65a3255e4175332a
ms.sourcegitcommit: c53f05bbd4abdfe1ee2e42fdd4f82b318b363ad7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "25506312"
---
# <a name="create-add-in-commands-in-your-manifest-for-excel-word-and-powerpoint"></a>Criar comandos de suplemento no manifesto para Excel, Word e PowerPoint


Use **[VersionOverrides](https://docs.microsoft.com/office/dev/add-ins/reference/manifest/versionoverrides?view=office-js)** em seu manifesto para definir comandos de suplemento do Excel, Word e PowerPoint. Os comandos de suplemento fornecem uma maneira fácil de personalizar a interface de usuário do Office padrão (UI) com elementos de interface do usuário especificados que executam ações. Você pode usar comandos de suplemento para:
- Criar elementos de interface do usuário ou pontos de entrada que facilitam o uso da funcionalidade de suplementos.  
  
- Adicionar botões ou uma lista suspensa de botões à faixa de opções.    
  
- Adicionar itens de menu individuais — cada um contendo submenus opcionais — aos menus de contexto específicos (atalho).    
  
- Executar ações quando seu comando de suplemento é escolhido. É possível:
    
  - Mostrar um ou mais suplementos do painel de tarefas para interação dos usuários. Dentro do seu suplemento do painel de tarefas, você pode exibir o HTML que usa o Office UI Fabric para criar uma interface do usuário personalizada.
    
     *ou* 
      
  - Executar um código JavaScript, que normalmente é executado sem exibir qualquer interface do usuário.
      
Este artigo descreve como editar seu manifesto para definir comandos de suplemento. O diagrama a seguir mostra a hierarquia de elementos usados para definir comandos de suplemento. Esses elementos são descritos em mais detalhes neste artigo. 
      
A imagem a seguir é uma visão geral dos elementos dos comandos de suplementos no manifesto. ![Visão geral de elementos de comandos de suplementos no manifesto](../images/version-overrides.png)
 
## <a name="step-1-start-from-a-sample"></a>Etapa 1: iniciar usando uma amostra

É altamente recomendável que você comece a partir de um dos exemplos que fornecemos em [Exemplos de comandos de suplementos do Office](https://github.com/OfficeDev/Office-Add-in-Command-Sample). Opcionalmente, você pode criar seu próprio manifesto seguindo as etapas deste guia. Você pode validar seu manifesto usando o arquivo XSD no site de exemplos de comandos de suplemento do Office. Certifique-se de ter lido [Comandos de suplemento para o Excel, Word e PowerPoint](../design/add-in-commands.md) antes de usar os comandos de suplemento.

## <a name="step-2-create-a-task-pane-add-in"></a>Etapa 2: criar um suplemento de painel de tarefas

Para começar a usar comandos de suplemento, você deve primeiro criar um suplemento do painel de tarefas e modificar o manifesto do suplemento conforme descrito neste artigo. Você não pode usar comandos de suplemento com suplementos de conteúdo. Se você estiver atualizando um manifesto existente, deverá adicionar os  **namespaces XML** apropriados, bem como adicionar o elemento **VersionOverrides** ao manifesto conforme descrito em [Etapa 3: adicionar o elemento VersionOverrides](#step-3-add-versionoverrides-element).
   
O exemplo a seguir mostra um manifesto do suplemento do Office 2013. Não há comandos de complemento neste manifesto porque não há um elemento **VersionOverrides**. O Office 2013 não suporta comandos suplementares, mas ao adicionar **VersionOverrides** a este manifesto, o seu suplemento será executado no Office 2013 e no Office 2016. No Office 2013, o seu suplemento não exibirá comandos adicionais e usará o valor de **SourceLocation** para executar o suplemento como um único suplemento do painel de tarefas. No Office 2016, se nenhum elemento **VersionOverrides** estiver incluído, **SourceLocation** será usado para executar seu complemento. Se você incluir **VersionOverrides**, no entanto, seu suplemento exibirá apenas os comandos de suplemento e não exibirá seu suplemento como um único suplemento do painel de tarefas.
  
```xml
<OfficeApp xmlns="http://schemas.microsoft.com/office/appforoffice/1.1" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xmlns:bt="http://schemas.microsoft.com/office/officeappbasictypes/1.0" xmlns:ov="http://schemas.microsoft.com/office/taskpaneappversionoverrides" xsi:type="TaskPaneApp">
  <Id>657a32a9-ab8a-4579-ac9f-df1a11a64e52</Id>
  <Version>1.0.0.0</Version>
  <ProviderName>Contoso</ProviderName>
  <DefaultLocale>en-US</DefaultLocale>
  <DisplayName DefaultValue="Contoso Add-in Commands" />
  <Description DefaultValue="Contoso Add-in Commands"/>
  <IconUrl DefaultValue="~remoteAppUrl/Images/Icon_32.png" />
 
  <AppDomains>
    <AppDomain>AppDomain1</AppDomain>
    <AppDomain>AppDomain2</AppDomain>
    <AppDomain>AppDomain3</AppDomain>
  </AppDomains>
  <Hosts>
    <Host Name="Workbook" />
  </Hosts>
  <DefaultSettings>
    <SourceLocation DefaultValue="https://www.contoso.com/Pages/Home.aspx" />
  </DefaultSettings>
  <Permissions>ReadWriteDocument</Permissions>

 <!-- The VersionOverrides element is inserted at this location in the manifest. -->

</OfficeApp>
```

## <a name="step-3-add-versionoverrides-element"></a>Etapa 3: adicionar o elemento VersionOverrides
O elemento **VersionOverrides** é o elemento raiz que contém a definição do comando de suplemento. **VersionOverrides** é um elemento filho do elemento **OfficeApp** no manifesto. A tabela a seguir lista os atributos do elemento **VersionOverrides**.

|**Atributo**|**Descrição**|
|:-----|:-----|
|**xmlns** <br/> | Obrigatório. O local do esquema, que deve ser "http://schemas.microsoft.com/office/taskpaneappversionoverrides". <br/> |
|**xsi:type** <br/> |Obrigatório. A versão do esquema. A versão descrita neste artigo é "VersionOverridesV1_0".  <br/> |
   
A tabela a seguir identifica os elementos filho de **VersionOverrides**.
  
|**Elemento**|**Descrição**|
|:-----|:-----|
|**Descrição** <br/> |Opcional. Descreve o suplemento. Esse elemento filho **Description** substitui um elemento **Description** anterior na parte pai do manifesto. O atributo **resid** para esse elemento **Description** é definido como a **id** de um elemento **String**. O elemento **String** contém o texto para **Description**. <br/> |
|**Requirements** <br/> |Opcional. Especifica o conjunto de requisitos mínimos e a versão do Office.js exigida pelo suplemento. Esse elemento filho **Requirements** substitui o elemento **Requirements** na parte pai do manifesto. Para saber mais, confira [Especificar requisitos de API e hosts do Office](../develop/specify-office-hosts-and-api-requirements.md).  <br/> |
|**Hosts** <br/> |Obrigatório. Especifica um conjunto de hosts do Office. O elemento filho **Hosts** substitui o elemento **Hosts** na parte pai do manifesto. Você deve incluir um conjunto de atributos **xsi:type** como "Pasta de trabalho" ou "Documento". <br/> |
|**Resources** <br/> |Define um conjunto de recursos (cadeias de caracteres, URLs e imagens) referenciado por outros elementos de manifesto. Por exemplo, o valor do elemento **Description** refere-se a um elemento filho em **Resources**. O elemento **Resources** é descrito na [Etapa 7: adicionar o elemento Resources](#step-7-add-the-resources-element) mais adiante neste artigo. <br/> |
   
O exemplo a seguir mostra como usar o elemento **VersionOverrides** e seus elementos filho.

```xml
<OfficeApp>
...
  <VersionOverrides xmlns="http://schemas.microsoft.com/office/taskpaneappversionoverrides" xsi:type="VersionOverridesV1_0">
    <Description resid="residDescription" />
    <Requirements>
      <!-- add information about requirement sets -->
    </Requirements>
    <Hosts>
      <Host xsi:type="Workbook">
        <!-- add information about form factors -->
      </Host>
      <Host xsi:type="Document">
        <!-- add information about form factors -->
      </Host>
    </Hosts>
    <Resources> 
      <!-- add information about resources -->
    </Resources>
  </VersionOverrides>
...
</OfficeApp>
```

## <a name="step-4-add-hosts-host-and-desktopformfactor-elements"></a>Etapa 4: adicionar os elementos Hosts, Host e DesktopFormFactor

O elemento **Hosts** contém um ou mais elementos **Host**. Um elemento **Host** especifica um determinado host do Office. O elemento **Host** contém elementos filho que especificam os comandos de suplemento que serão exibidos após a instalação do suplemento nesse host do Office. Para mostrar os mesmos comandos de suplemento em dois ou mais hosts do Office diferentes, você deve duplicar os elementos filho em cada **Host**.
       
O elemento **DesktopFormFactor** especifica as configurações para um suplemento que é executado no Office, na área de trabalho do Windows e no Office Online (no navegador).
      
Veja a seguir um exemplo dos elementos **Hosts**, **Host** e **DesktopFormFactor**.

```xml
<OfficeApp>
...
  <VersionOverrides xmlns="http://schemas.microsoft.com/office/taskpaneappversionoverrides" xsi:type="VersionOverridesV1_0">
  ...
    <Hosts>
      <Host xsi:type="Workbook">
        <DesktopFormFactor>

              <!-- information about FunctionFile and ExtensionPoint -->

        </DesktopFormFactor>
      </Host>
    </Hosts>
  ...
  </VersionOverrides>
...
</OfficeApp>
```

## <a name="step-5-add-the-functionfile-element"></a>Etapa 5: adicionar o elemento FunctionFile

O elemento **FunctionFile** especifica um arquivo que contém o código JavaScript a ser executado quando um comando de suplemento usa a ação **ExecuteFunction** (confira [Controles de botão](https://docs.microsoft.com/office/dev/add-ins/reference/manifest/control?view=office-js#Button-control) para obter uma descrição). O atributo **resid** do elemento **FunctionFile** é definido como um arquivo HTML que inclui todos os arquivos JavaScript exigidos por seus comandos de suplemento. Você não pode criar um vínculo diretamente com um arquivo JavaScript, somente com um arquivo HTML. O nome do arquivo é especificado como um elemento **Url** no elemento **Resources**.
        
Veja a seguir um exemplo do elemento **FunctionFile**.
  
```xml
<DesktopFormFactor>
    <FunctionFile resid="residDesktopFuncUrl" />
    <ExtensionPoint xsi:type="PrimaryCommandSurface">
      <!-- information about this extension point -->
    </ExtensionPoint> 

    <!-- You can define more than one ExtensionPoint element as needed -->
</DesktopFormFactor>
```

> [!IMPORTANT]
> Verifique se seu código JavaScript chama `Office.initialize`. 
   
O JavaScript no arquivo HTML referenciado pelo elemento **FunctionFile** deve chamar `Office.initialize`. O elemento **FunctionName** (confira [Controles de botão](https://docs.microsoft.com/office/dev/add-ins/reference/manifest/control?view=office-js#Button-control) para obter uma descrição) usa as funções em **FunctionFile**.
     
O código a seguir mostra como implementar a função usada por **FunctionName**.

```javascript

<script>
    // The initialize function must be run each time a new page is loaded.
    (function () {
        Office.initialize = function (reason) {
            // If you need to initialize something you can do so here. 
        };
    })();

    // Your function must be in the global namespace.
    function writeText(event) {

        // Implement your custom code here. The following code is a simple example.  
        Office.context.document.setSelectedDataAsync("ExecuteFunction works. Button ID=" + event.source.id,
            function (asyncResult) {
                var error = asyncResult.error;
                if (asyncResult.status === Office.AsyncResultStatus.Failed) {
                    // Show error message. 
                }
                else {
                    // Show success message.
                }
            });
        
        // Calling event.completed is required. event.completed lets the platform know that processing has completed. 
        event.completed();
    }
</script>
```

> [!IMPORTANT]
> A chamada para **event.completed** sinaliza que o evento foi manipulado. Quando uma função é chamada várias vezes, por exemplo, com vários cliques no mesmo comando de suplemento, todos os eventos são enfileirados automaticamente. O primeiro evento é executado automaticamente, enquanto os outros eventos permanecem na fila. Quando sua função chama **event.completed**, a próxima chamada em fila para essa função é executada. Você deve implementar **event.completed**; caso contrário, sua função não será executada.
 
## <a name="step-6-add-extensionpoint-elements"></a>Etapa 6: adicionar elementos do ExtensionPoint

O elemento **ExtensionPoint** define onde os comandos de suplemento devem aparecer na interface do usuário do Office. Você pode definir os elementos **ExtensionPoint** com estes valores de **xsi:type**:
   
- **PrimaryCommandSurface**, que se refere à faixa de opções no Office.
     
- **ContextMenu**, que é o menu de atalho exibido quando você clica com o botão direito na interface do usuário do Office.
    
Os exemplos a seguir mostram como usar o elemento **ExtensionPoint** com os valores de atributo **PrimaryCommandSurface** e **ContextMenu** e os elementos filho que devem ser usados com cada um.
    
> [!IMPORTANT]
> Para os elementos que contêm um atributo ID, forneça uma ID exclusiva. Recomendamos usar o nome da sua empresa com a ID. Por exemplo, use o seguinte formato: `<CustomTab id="mycompanyname.mygroupname">`. 
  
```xml
<ExtensionPoint xsi:type="PrimaryCommandSurface">
  <CustomTab id="Contoso Tab">
  <!-- If you want to use a default tab that comes with Office, remove the above CustomTab element, and then uncomment the following OfficeTab element -->
  <!-- <OfficeTab id="TabData"> -->
    <Label resid="residLabel4" />
    <Group id="Group1Id12">
      <Label resid="residLabel4" />
      <Icon>
        <bt:Image size="16" resid="icon1_32x32" />
        <bt:Image size="32" resid="icon1_32x32" />
        <bt:Image size="80" resid="icon1_32x32" />
      </Icon>
      <Tooltip resid="residToolTip" />
      <Control xsi:type="Button" id="Button1Id1">
        
        <!-- information about the control -->
      </Control>   
      <!-- other controls, as needed -->                                    
    </Group>
  </CustomTab>
</ExtensionPoint>
<ExtensionPoint xsi:type="ContextMenu">
  <OfficeMenu id="ContextMenuCell">
    <Control xsi:type="Menu" id="ContextMenu2">
            <!-- information about the control -->
    </Control>   
    <!-- other controls, as needed -->         
  </OfficeMenu>
</ExtensionPoint>
```

|**Elemento**|**Descrição**|
|:-----|:-----|
|**CustomTab** <br/> |Obrigatório se você quiser adicionar uma guia personalizada à faixa de opções (usando **PrimaryCommandSurface**). Se você usar o elemento **CustomTab**, o elemento **OfficeTab** não poderá ser usado. O atributo **id** é obrigatório. <br/> |
|**OfficeTab** <br/> |Obrigatório se você quiser estender uma guia de faixa de opções padrão do Office (usando **PrimaryCommandSurface**). Se você usar o elemento **OfficeTab**, o elemento **CustomTab** não poderá ser usado. <br/> Para obter mais valores de guia a serem usados com o atributo **id**, confira [Valores de guia para guias de faixa de opções padrão do Office](https://docs.microsoft.com/office/dev/add-ins/reference/manifest/officetab?view=office-js).  <br/> |
|**OfficeMenu** <br/> | Obrigatório se você estiver adicionando comandos de suplemento a um menu de contexto padrão (usando **ContextMenu**). O atributo **id** deve ser definido como: <br/> **ContextMenuText** para Excel ou Word. Exibe o item no menu de contexto quando o texto é selecionado e o usuário clica com o botão direito do mouse no texto selecionado. <br/> **ContextMenuCell** para Excel. Exibe o item no menu de contexto quando o usuário clica com o botão direito do mouse em uma célula na planilha. <br/> |
|**Grupo** <br/> |Um grupo de pontos de extensão de interface do usuário em uma guia. Um grupo pode ter até seis controles. O atributo **id** é obrigatório. É uma cadeia de caracteres com, no máximo, 125 caracteres. <br/> |
|**Label** <br/> |Obrigatório. O rótulo do grupo. O atributo **resid** deve ser definido como o valor do atributo **id** de um elemento **String**. O elemento **String** é um elemento filho do elemento **ShortStrings**, que é elemento filho do elemento **Resources**. <br/> |
|**Icon** <br/> |Obrigatório. Especifica o ícone do grupo a ser usado em dispositivos de fator forma pequeno ou quando muitos botões são exibidos. O atributo **resid** deve ser definido como o valor do atributo **id** de um elemento **Image**. O elemento **Image** é um elemento filho do elemento **Images**, que é um elemento filho do elemento **Resources**. O atributo **size** fornece o tamanho da imagem em pixels. Três tamanhos de imagem são obrigatórios: 16, 32 e 80 pixels. Também há suporte para cinco tamanhos opcionais: 20, 24, 40, 48 e 64 pixels. <br/> |
|**Tooltip** <br/> |Opcional. A dica de ferramenta do grupo. O atributo **resid** deve ser definido como o valor do atributo **id** de um elemento **String**. O elemento **String** é um elemento filho do elemento **LongStrings**, que é um elemento filho do elemento **Resources**. <br/> |
|**Controle** <br/> |Cada grupo exige pelo menos um controle. Um elemento **Control** pode ser um **Button** ou um **Menu**. Use **Menu** para especificar uma lista suspensa de controles de botão. Atualmente, há suporte apenas para botões e menus. Confira as seguintes seções [Controles de botão](https://docs.microsoft.com/office/dev/add-ins/reference/manifest/control?view=office-js#Button-control) e [Controles de menu](https://docs.microsoft.com/office/dev/add-ins/reference/manifest/control?view=office-js#menu-dropdown-button-controls) para saber mais. <br/>**Observação:** para facilitar a solução de problemas, recomendamos adicionar um elemento **Control** e os elementos filho **Resources** relacionados, um de cada vez.          |
   

### <a name="button-controls"></a>Controles de botão
Um botão executa uma única ação quando o usuário o seleciona. Pode ser a execução de uma função JavaScript ou a exibição de um painel de tarefas. O exemplo a seguir mostra como definir dois botões. O primeiro botão executa uma função JavaScript sem mostrar uma interface do usuário e o segundo botão mostra um painel de tarefas. No elemento **Control**:        

- O atributo **type** é obrigatório e deve ser definido como **Button**.
    
- O atributo **id** do elemento **Control** é uma cadeia de caracteres com, no máximo, 125 caracteres.
    
```xml
<!-- Define a control that calls a JavaScript function. -->
<Control xsi:type="Button" id="Button1Id1">
  <Label resid="residLabel" />
  <Tooltip resid="residToolTip" />
  <Supertip>
    <Title resid="residLabel" />
    <Description resid="residToolTip" />
  </Supertip>
  <Icon>
    <bt:Image size="16" resid="icon1_32x32" />
    <bt:Image size="32" resid="icon1_32x32" />
    <bt:Image size="80" resid="icon1_32x32" />
  </Icon>
  <Action xsi:type="ExecuteFunction">
    <FunctionName>getData</FunctionName>
  </Action>
</Control>

<!-- Define a control that shows a task pane. -->
<Control xsi:type="Button" id="Button2Id1">
  <Label resid="residLabel2" />
  <Tooltip resid="residToolTip" />
  <Supertip>
    <Title resid="residLabel" />
    <Description resid="residToolTip" />
  </Supertip>
  <Icon>
    <bt:Image size="16" resid="icon2_32x32" />
    <bt:Image size="32" resid="icon2_32x32" />
    <bt:Image size="80" resid="icon2_32x32" />
  </Icon>
  <Action xsi:type="ShowTaskpane">
    <SourceLocation resid="residUnitConverterUrl" />
  </Action>
</Control>
```

|**Elementos**|**Descrição**|
|:-----|:-----|
|**Label** <br/> |Obrigatório. O texto do botão. O atributo **resid** deve ser definido como o valor do atributo **id** de um elemento **String**. O elemento **String** é um elemento filho do elemento **ShortStrings**, que é elemento filho do elemento **Resources**. <br/> |
|**Tooltip** <br/> |Opcional. A dica de ferramenta do botão. O atributo **resid** deve ser definido como o valor do atributo **id** de um elemento **String**. O elemento **String** é um elemento filho do elemento **LongStrings**, que é um elemento filho do elemento **Resources**. <br/> |
|**Dica detalhada** <br/> | Obrigatório. A superdica para esse botão, que é definida pelos seguintes itens: <br/> **Title** <br/>  Obrigatório. O texto da superdica. O atributo **resid** deve ser definido como o valor do atributo **id** de um elemento **String**. O elemento **String** é um elemento filho do elemento **ShortStrings**, que é elemento filho do elemento **Resources**. <br/> **Descrição** <br/>  Obrigatório. A descrição da superdica. O atributo **resid** deve ser definido como o valor do atributo **id** de um elemento **String**. O elemento **String** é um elemento filho do elemento **LongStrings**, que é um elemento filho do elemento **Resources**. <br/> |
|**Icon** <br/> | Necessário. Contém os elementos **Image** do botão. Arquivos de imagem devem ser no formato .png. <br/> **Image** <br/>  Define uma imagem a ser exibida no botão. O atributo **resid** deve ser definido como o valor do atributo **id** de um elemento **Image**. O elemento **Image** é um elemento filho do elemento **Images**, que é um elemento filho do elemento **Resources**. O atributo **size** indica o tamanho em pixels da imagem. Três tamanhos de imagem são obrigatórios: 16, 32 e 80 pixels. Também há suporte para cinco tamanhos opcionais: 20, 24, 40, 48 e 64 pixels. <br/> |
|**Action** <br/> | Necessário. Especifica a ação a ser executada quando o usuário seleciona o botão. Você pode especificar um dos seguintes valores para o atributo **xsi:type**: <br/> **ExecuteFunction**, que executa uma função de JavaScript localizada no arquivo referenciado pelo **FunctionFile**. **ExecuteFunction** não exibe uma interface do usuário. O elemento filho **FunctionFile** especifica o nome da função a ser executada. <br/> **ShowTaskPane**, que mostra um suplemento de painel de tarefas. O elemento filho **SourceLocation** especifica o local do arquivo de origem do suplemento de painel de tarefas a ser exibido. O atributo **resid** deve ser definido como o valor do atributo **id** de um elemento **Url** no elemento **Urls** do elemento **Resources**. <br/> |
   

### <a name="menu-controls"></a>Controles de menu
Um controle **Menu** pode ser usado com **PrimaryCommandSurface** ou **ContextMenu** e define:
  
- Um item de menu no nível raiz.
   
- Uma lista de itens de submenu.
 
Quando usado com **PrimaryCommandSurface**, o item de menu raiz é exibido como um botão na faixa de opções. Quando o botão é selecionado, o submenu é exibido como uma lista suspensa. Quando usado com **ContextMenu**, um item de menu com um submenu é inserido no menu de contexto. Em ambos os casos, cada item de submenu pode executar uma função JavaScript ou mostrar um painel de tarefas. Somente um nível de submenus é compatível no momento.
       
O exemplo a seguir mostra como definir um item de menu com dois itens de submenu. O primeiro item do submenu mostra um painel de tarefas e o segundo item do submenu executa uma função JavaScript. No elemento **Control**:
    
- O atributo **xsi:type** é obrigatório e deve ser definido como **Menu**.
  
- O atributo **id** é uma cadeia de caracteres com, no máximo, 125 caracteres.
    
```xml

<Control xsi:type="Menu" id="TestMenu2">
  <Label resid="residLabel3" />
  <Tooltip resid="residToolTip" />
  <Supertip>
    <Title resid="residLabel" />
    <Description resid="residToolTip" />
  </Supertip>
  <Icon>
    <bt:Image size="16" resid="icon1_32x32" />
    <bt:Image size="32" resid="icon1_32x32" />
    <bt:Image size="80" resid="icon1_32x32" />
  </Icon>
  <Items>
    <Item id="showGallery2">
      <Label resid="residLabel3"/>
      <Supertip>
        <Title resid="residLabel" />
        <Description resid="residToolTip" />
      </Supertip>
      <Icon>
        <bt:Image size="16" resid="icon1_32x32" />
        <bt:Image size="32" resid="icon1_32x32" />
        <bt:Image size="80" resid="icon1_32x32" />
      </Icon>
      <Action xsi:type="ShowTaskpane">
        <TaskpaneId>MyTaskPaneID1</TaskpaneId>
        <SourceLocation resid="residUnitConverterUrl" />
      </Action>
    </Item>
    <Item id="showGallery3">
      <Label resid="residLabel5"/>
      <Supertip>
        <Title resid="residLabel" />
        <Description resid="residToolTip" />
      </Supertip>
      <Icon>
        <bt:Image size="16" resid="icon4_32x32" />
        <bt:Image size="32" resid="icon4_32x32" />
        <bt:Image size="80" resid="icon4_32x32" />
      </Icon>
      <Action xsi:type="ExecuteFunction">
        <FunctionName>getButton</FunctionName>
      </Action>
    </Item>
  </Items>
</Control>
```

|**Elementos**|**Descrição**|
|:-----|:-----|
|**Label** <br/> |Obrigatório. O texto do item de menu raiz. O atributo **resid** deve ser definido como o valor do atributo **id** de um elemento **String**. O elemento **String** é um elemento filho do elemento **ShortStrings**, que é elemento filho do elemento **Resources**. <br/> |
|**Tooltip** <br/> |Opcional. A dica de ferramenta do menu. O atributo **resid** deve ser definido como o valor do atributo **id** de um elemento **String**. O elemento **String** é um elemento filho do elemento **LongStrings**, que é um elemento filho do elemento **Resources**. <br/> |
|**Dica detalhada** <br/> | Obrigatório. A superdica para o menu, que é definida pelos seguintes itens: <br/> **Title** <br/>  Obrigatório. O texto da superdica. O atributo **resid** deve ser definido como o valor do atributo **id** de um elemento **String**. O elemento **String** é um elemento filho do elemento **ShortStrings**, que é elemento filho do elemento **Resources**. <br/> **Descrição** <br/>  Obrigatório. A descrição da superdica. O atributo **resid** deve ser definido como o valor do atributo **id** de um elemento **String**. O elemento **String** é um elemento filho do elemento **LongStrings**, que é um elemento filho do elemento **Resources**. <br/> |
|**Icon** <br/> | Necessário. Contém os elementos **Image** do botão. Arquivos de imagem devem ser no formato .png. <br/> **Image** <br/>  Uma imagem para o menu. O atributo **resid** deve ser definido como o valor do atributo **id** de um elemento **Image**. O elemento **Image** é um elemento filho do elemento **Images**, que é um elemento filho do elemento **Resources**. O atributo **size** indica o tamanho em pixels da imagem. Três tamanhos de imagem, em pixels, são obrigatórios: 16, 32 e 80 pixels. Cinco tamanhos opcionais, em pixels, também têm suporte: 20, 24, 40, 48 e 64 pixels. <br/> |
|**Items** <br/> |Obrigatório. Contém os elementos **Item** para cada item do submenu. Cada elemento **Item** contém os mesmos elementos filho que [Controles de botão](https://docs.microsoft.com/office/dev/add-ins/reference/manifest/control?view=office-js#Button-control).  <br/> |
   
## <a name="step-7-add-the-resources-element"></a>Etapa 7: adicionar o elemento Resources

O elemento **Resources** contém recursos usados pelos diferentes elementos filho do elemento **VersionOverrides**. Resources inclui ícones, cadeias de caracteres e URLs. Um elemento no manifesto pode usar um recurso fazendo referência a **id** do recurso. O uso da **id** ajuda a organizar o manifesto, especialmente quando há versões diferentes do recurso para localidades diferentes. Uma **id** tem no máximo 32 caracteres.
  
    
    
Veja a seguir um exemplo de como usar o elemento **Resources**. Cada recurso pode ter um ou mais elementos filho **Override** para definir um recurso diferente para uma localidade específica.


```xml
<Resources>
  <bt:Images>
    <bt:Image id="icon1_16x16" DefaultValue="https://www.contoso.com/Images/icon_default.png">
      <bt:Override Locale="ja-jp" Value="https://www.contoso.com/Images/ja-jp16-icon_default.png" />
    </bt:Image>
    <bt:Image id="icon1_32x32" DefaultValue="https://www.contoso.com/Images/icon_default.png">
      <bt:Override Locale="ja-jp" Value="https://www.contoso.com/Images/ja-jp32-icon_default.png" />
    </bt:Image>
    <bt:Image id="icon1_80x80" DefaultValue="https://www.contoso.com/Images/icon_default.png">
      <bt:Override Locale="ja-jp" Value="https://www.contoso.com/Images/ja-jp80-icon_default.png" />
    </bt:Image>        
  </bt:Images>
  <bt:Urls>
    <bt:Url id="residDesktopFuncUrl" DefaultValue="https://www.contoso.com/Pages/Home.aspx">
      <bt:Override Locale="ja-jp" Value="https://www.contoso.com/Pages/Home.aspx" />
    </bt:Url>        
  </bt:Urls>
  <bt:ShortStrings>
    <bt:String id="residLabel" DefaultValue="GetData">
      <bt:Override Locale="ja-jp" Value="JA-JP-GetData" />
    </bt:String>      
  </bt:ShortStrings>
  <bt:LongStrings>
    <bt:String id="residToolTip" DefaultValue="Get data for your document.">
      <bt:Override Locale="ja-jp" Value="JA-JP - Get data for your document." />
    </bt:String>
  </bt:LongStrings>
</Resources>
```

|**Recurso**|**Descrição**|
|:-----|:-----|
|**Imagens**/ **Imagem** <br/> | Fornece a URL HTTPS para um arquivo de imagem. Cada imagem precisa definir os três tamanhos de imagem necessários: <br/>  16×16 <br/>  32×32 <br/>  80×80 <br/>  Os seguintes tamanhos de imagem também têm suporte, mas não são obrigatórios: <br/>  20×20 <br/>  24×24 <br/>  40×40 <br/>  48×48 <br/>  64×64 <br/> |
|**Urls**/ **Url** <br/> |Fornece um local para a URL HTTPS. Uma URL pode ter no máximo 2048 caracteres.  <br/> |
|**Sequências de caracteres curtas**/ **Sequência de caracteres** <br/> |O texto para os elementos **Label** e **Title**. Cada **String** contém no máximo 125 caracteres. <br/> |
|**Sequências de caracteres longas**/ **Sequência de caracteres** <br/> |O texto para os elementos **Tooltip** e **Description**. Cada **String** contém no máximo 250 caracteres. <br/> |
   
> [!NOTE] 
> Use o protocolo SSL (Secure Sockets Layer) para todas as URLs nos elementos **Image** e **Url**.

### <a name="tab-values-for-default-office-ribbon-tabs"></a>Valores para as guias de faixa de opções padrão do Office
No Excel e no Word, é possível adicionar seus comandos de suplemento na faixa de opções usando as guias padrão da interface de usuário do Office. A tabela a seguir lista os valores que podem ser usados para o atributo **id** do elemento **OfficeTab**. Os valores da guia diferenciam maiúsculas de minúsculas.

|**Aplicativo host do Office**|**Valores de guia**|
|:-----|:-----|
|Excel  <br/> |**TabHome**         **TabInsert**         **TabPageLayoutExcel**         **TabFormulas**         **TabData**         **TabReview**         **TabView**         **TabDeveloper**         **TabAddIns**         **TabPrintPreview**         **TabBackgroundRemoval** <br/> |
|Word  <br/> |**TabHome**         **TabInsert**         **TabWordDesign**         **TabPageLayoutWord**         **TabReferences**         **TabMailings**         **TabReviewWord**         **TabView**         **TabDeveloper**         **TabAddIns**         **TabBlogPost**         **TabBlogInsert**         **TabPrintPreview**         **TabOutlining**         **TabConflicts**         **TabBackgroundRemoval**         **TabBroadcastPresentation** <br/> |
|PowerPoint  <br/> |**TabHome**         **TabInsert**         **TabDesign**         **TabTransitions**         **TabAnimations**         **TabSlideShow**         **TabReview**         **TabView**         **TabDeveloper**         **TabAddIns**         **TabPrintPreview**         **TabMerge**         **TabGrayscale**         **TabBlackAndWhite**         **TabBroadcastPresentation**         **TabSlideMaster**         **TabHandoutMaster**         **TabNotesMaster**         **TabBackgroundRemoval**         **TabSlideMasterHome**          <br/> |
   
## <a name="see-also"></a>Confira também

-  [Comandos de suplemento para Excel, Word e PowerPoint](../design/add-in-commands.md)      
