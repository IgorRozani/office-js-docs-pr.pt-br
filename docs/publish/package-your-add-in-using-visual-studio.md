---
title: Empacote seu suplemento usando o Visual Studio para preparar a publicação | Microsoft Docs
description: Este artigo descreve como implantar seu projeto Web e empacotar seu suplemento usando o Visual Studio 2015.
ms.date: 01/25/2018
ms.openlocfilehash: d74ead03b8ac5b7652c7c98851e7e082f4b31ba8
ms.sourcegitcommit: eb74e94d3e1bc1930a9c6582a0a99355d0da34f2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "25004914"
---
# <a name="package-your-add-in-using-visual-studio-to-prepare-for-publishing"></a>Empacote seu suplemento usando o Visual Studio para preparar a publicação

Seu pacote de Suplemento do Office contém um [arquivo de manifesto XML](../develop/add-in-manifests.md) que deve ser usado para publicar o suplemento. Você terá que publicar os arquivos do aplicativo Web do seu projeto separadamente. Este artigo descreve como implantar seu projeto Web e empacotar seu suplemento usando o Visual Studio 2015

## <a name="to-deploy-your-web-project-using-visual-studio-2015"></a>Para implantar seu projeto Web usando o Visual Studio 2015

Conclua as etapas a seguir para implantar seu projeto Web usando o Visual Studio 2015.

1. No **Gerenciador de Soluções**, abra o menu de atalho do projeto do suplemento e escolha **Publicar**.
    
    A página **Publicar seu suplemento** é exibida.
    
2. Na lista suspensa **Perfil atual**, selecione um perfil ou escolha **Novo...** para criar um novo perfil.
    
    > [!NOTE]
    > Um perfil de publicação especifica o servidor que você está implantando, as credenciais necessárias para fazer logon no servidor, os bancos de dados para implantar e outras opções de implantação.

    Se você escolher **Novo...**, o assistente Criar perfil de publicação será exibido. Use esse assistente para importar um perfil de publicação de um site de hospedagem, como o Microsoft Azure, ou criar um novo perfil e adicionar seu servidor, as credenciais e outras configurações no procedimento seguinte.
    
    Para mais informações sobre como importar perfis de publicação ou criar novos perfis de publicação, confira [Criar um Perfil de Publicação](https://msdn.microsoft.com/library/dd465337.aspx#creating_a_profile).
    
3. Na página **Publicar seu suplemento**, escolha o link **Implantar seu projeto Web**.
    
    A caixa de diálogo  **Publicar Web** aparece. Para mais informações sobre a utilização do desse assistente, veja [Instruções: Implantar um Projeto da Web usando o On-Click Publishing no Visual Studio](https://msdn.microsoft.com/library/dd465337.aspx).
    

## <a name="to-package-your-add-in-using-visual-studio-2015"></a>Para empacotar seu suplemento usando o Visual Studio 2015

Conclua as etapas a seguir para empacotar seu suplemento usando o Visual Studio 2015.

1. Na página **Publicar seu suplemento**, escolha o link **Empacotar o suplemento**.
    
    O assistente Publicar Suplementos do Office e SharePoint é exibido.
    
2. Na lista suspensa **Onde seu site está hospedado?**, escolha ou digite a URL do site que hospedará os arquivos de conteúdo do seu suplemento e escolha **Concluir**. 
    
    Você deve especificar uma URL que comece com o prefixo HTTPS para concluir este assistente. Se você quiser usar um ponto de extremidade HTTP para o site, abra o arquivo de manifesto XML em um editor de texto após criar o pacote e substitua o prefixo HTTPS do site por um prefixo HTTP. 

    > [!IMPORTANT]
    > [!include[HTTPS guidance](../includes/https-guidance.md)] Os sites do Azure fornecem automaticamente um ponto de extremidade HTTPS.

    O Visual Studio gera os arquivos que você precisa para publicar seu suplemento e, em seguida, abre a pasta de saída da publicação. 
    
Se você planeja enviar seu suplemento ao AppSource, pode escolher o link **Executar uma verificação de validação** para identificar problemas que possam impedir a aceitação de seu suplemento. Resolva todos os problemas antes de enviar seu suplemento para a loja.

Agora é possível carregar seu manifesto XML no local apropriado para [publicar seu suplemento](../publish/publish.md). É possível encontrar o manifesto XML em `OfficeAppManifests` na pasta `app.publish`. Por exemplo:

 `%UserProfile%\Documents\Visual Studio 2015\Projects\MyApp\bin\Debug\app.publish\OfficeAppManifests`


## <a name="see-also"></a>Veja também

- [Publicar seu Suplemento do Office](../publish/publish.md)
- [Disponibilizar suas soluções no AppSource e no Office](https://docs.microsoft.com/office/dev/store/submit-to-the-office-store)
    
