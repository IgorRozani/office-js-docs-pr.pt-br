# <a name="outlook-add-in-api-requirement-set-13"></a>Conjunto de requisitos de API para suplementos do Outlook versão 1.3

O subconjunto de API de suplemento do Outlook da API JavaScript para o Office inclui objetos, métodos, propriedades e eventos que você pode usar em um suplemento do Outlook.

> [!NOTE]
> Esta documentação destina-se a um [conjunto de requisitos](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets) diferente do conjunto de requisitos mais recente. 

## <a name="whats-new-in-13"></a>Novidades na versão 1.3

O conjunto de requisitos 1.3 inclui todos os recursos do [Conjunto de requisitos 1.2](../requirement-set-1.2/outlook-requirement-set-1.2.md). Ele adicionou os seguintes recursos.

- Foi adicionado o suporte para [comandos de suplemento](https://docs.microsoft.com/outlook/add-ins/add-in-commands-for-outlook).
- Foi adicionada a capacidade para salvar ou fechar um item que está sendo redigido.
- O objeto [Body](/javascript/api/outlook_1_3/office.body) foi aprimorado para permitir que os suplementos obtenham ou definam todo o corpo.
- Foram adicionados os métodos de conversão para converter IDs entre os formatos EWS e REST.
- Adicionada capacidade de adicionar mensagens de notificação à barra de informações nos itens.

### <a name="change-log"></a>Log de alterações

- Foi adicionado o [Body.getAsync](/javascript/api/outlook_1_3/office.body#getasync-coerciontype--options--callback-): Retorna o corpo atual em um formato especificado.
- Foi adicionado o [Body.setAsync](/javascript/api/outlook_1_3/office.body#setasync-data--options--callback-): Substitui todo o corpo com o texto especificado.
- Foi adicionado o [Office.context.officeTheme](office.context.md#officetheme-object): Fornece acesso às cores de temas do Office.
- Foi adicionado o objeto [Event](/javascript/api/office/office.addincommands.event): Passado como um parâmetro para funções de comando sem interface de usuário em um suplemento do Outlook. Usado para sinalizar a conclusão do processamento.
- Foi adicionado o [Office.context.mailbox.item.close](office.context.mailbox.item.md#close): Fecha o item atual que está sendo composto.
- Foi adicionado o [Office.context.mailbox.item.saveAsync](office.context.mailbox.item.md#saveasyncoptions-callback): Salva um item de forma assíncrona.
- Foi adicionado o [Office.context.mailbox.item.notificationMessages](office.context.mailbox.item.md#notificationmessages-notificationmessagesjavascriptapioutlook13officenotificationmessages): Obtém as mensagens de notificação de um item.
- Foi adicionado o [Office.context.mailbox.convertToEwsId](office.context.mailbox.md#converttoewsiditemid-restversion--string): Converte uma ID de item formatada para REST em formato EWS.
- Foi adicionado o [Office.context.mailbox.convertToRestId](office.context.mailbox.md#converttorestiditemid-restversion--string): Converte uma ID de item formatada para EWS em formato REST.
- Foi adicionado o [Office.MailboxEnums.ItemNotificationMessageType](/javascript/api/outlook_1_3/office.mailboxenums.itemnotificationmessagetype): Especifica o tipo de mensagem de notificação para um compromisso ou uma mensagem.
- Foi adicionado o [Office.MailboxEnums.RestVersion](/javascript/api/outlook_1_3/office.mailboxenums.restversion): Especifica a versão da API REST que corresponde a uma ID de item formatado para REST.
- Foi adicionado o objeto [NotificationMessages](/javascript/api/outlook_1_3/office.notificationmessages) : Fornece métodos para acessar as mensagens de notificação em um suplemento do Outlook.
- Foi adicionado o tipo [NotificationMessageDetails](/javascript/api/outlook_1_3/office.notificationmessagedetails) : Retornado pelo método `NotificationMessages.getAllAsync`.

## <a name="see-also"></a>Confira também

- [Suplementos do Outlook](https://docs.microsoft.com/outlook/add-ins/)
- [Exemplos de código de suplementos do Outlook](https://developer.microsoft.com/outlook/gallery/?filterBy=Outlook,Samples,Add-ins)
- [Introdução](https://docs.microsoft.com/outlook/add-ins/quick-start)