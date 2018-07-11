---
title: Realizar sideload de suplementos do Office para teste
description: ''
ms.date: 01/25/2018
---

# <a name="sideload-office-add-ins-for-testing"></a>Realizar sideload de suplementos do Office para teste

Você pode instalar um suplemento do Office para testá-lo em um cliente do Office em execução no Windows usando um catálogo de pasta compartilhada para publicar o manifesto em um compartilhamento de arquivos de rede. 

Se não estiver testando um suplemento do Word, do Excel ou do PowerPoint no Windows, confira um dos tópicos a seguir para fazer sideload do suplemento:

- [Sideload de suplementos do Office para teste no Office Online](sideload-office-add-ins-for-testing.md)
- [Sideload dos suplementos do Office para teste em um iPad ou Mac](sideload-an-office-add-in-on-ipad-and-mac.md)

O vídeo a seguir oferece orientações para o processo de sideload do seu suplemento no Office para área de trabalho ou no Office Online.  


> [!VIDEO https://www.youtube.com/embed/XXsAw2UUiQo]


## <a name="share-a-folder"></a>Compartilhar uma pasta

1. No computador do Windows, onde você deseja hospedar seu suplemento, acesse a pasta pai ou letra da unidade da pasta que você deseja usar como seu catálogo de pasta compartilhada.

2. Abra o menu de contexto para a pasta (com o botão direito) e escolha **Propriedades**.

3. Abra a guia **Compartilhamento**.

4. Na página **Escolher pessoas...**, adicione a si mesmo e qualquer pessoa com quem você deseja compartilhar seu suplemento. Se todos eles forem membros de um grupo de segurança, você poderá adicionar o grupo. Você precisará de pelo menos permissão de **leitura/gravação** para a pasta. 

5. Escolha **Compartilhar** > **Concluído** > **Fechar**.


## <a name="specify-the-shared-folder-as-a-trusted-catalog"></a>Especificar a pasta compartilhada como um catálogo confiável
      
1. Abra um novo documento no Excel, no Word ou no PowerPoint.
    
2. Escolha a guia **Arquivo** e escolha **Opções**.
    
3. Escolha **Central de Confiabilidade**, e escolha o botão **Configurações da Central de Confiabilidade**.
    
4. Escolha **Catálogos de Suplemento Confiáveis**.
    
5. Na caixa  **URL de Catálogo**, digite o caminho de rede completo para o catálogo da pasta compartilhada e escolha **Adicionar Catálogo**.
    
6. Selecione a caixa de seleção **Mostrar no Menu** e, em seguida, escolha **OK**.

7. Feche o aplicativo do Office para que as alterações tenham efeito.
    

## <a name="sideload-your-add-in"></a>Realizar o sideload do seu suplemento

1. Coloque o arquivo de manifesto de qualquer suplemento que você está testando no catálogo de pasta compartilhada. Observe que você implanta o próprio aplicativo Web em um servidor Web. Não deixe de especificar a URL no elemento **SourceLocation** do arquivo de manifesto.

    > [!IMPORTANT]
    > [!include[HTTPS guidance](../includes/https-guidance.md)]

2. No Excel, Word ou PowerPoint, selecione **Meus Suplementos** na guia **Inserir** da faixa de opções.

3. Escolha **PASTA COMPARTILHADA** na parte superior da caixa de diálogo **Suplementos do Office**.

4. Selecione o nome do suplemento e escolha **OK** para inseri-lo.


## <a name="see-also"></a>Veja também

- [Validar e solucionar problemas com seu manifesto](troubleshoot-manifest.md)
- [Publicar seu Suplemento do Office](../publish/publish.md)
    