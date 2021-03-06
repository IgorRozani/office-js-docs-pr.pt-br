# <a name="add-in-commands-requirement-sets"></a>Conjuntos de requisitos dos comandos de suplemento

Os conjuntos de requisitos são grupos nomeados de membros da API. Os suplementos do Office usam conjuntos de requisitos especificados no manifesto ou uma verificação em tempo de execução para determinar se um host do Office oferece suporte às APIs necessárias a um suplemento. Para obter mais informações, confira [Versões do Office e conjuntos de requisitos](https://docs.microsoft.com/office/dev/add-ins/develop/office-versions-and-requirement-sets).

Comandos de suplemento são elementos de interface do usuário que estendem a interface do usuário do Office e iniciam ações no suplemento. Você pode usar comandos de suplemento para adicionar um botão à faixa de opções ou um item a um menu de contexto. Para saber mais, confira [Suplementos de comandos para Excel, Word e PowerPoint](https://docs.microsoft.com/office/dev/add-ins/design/add-in-commands) e [Suplementos de comandos para Outlook](https://docs.microsoft.com/outlook/add-ins/add-in-commands-for-outlook).

A versão inicial dos suplementos de comando não tem um conjunto de requisitos correspondente (ou seja, não há um conjunto de requisitos AddInCommands 1.0). A tabela a seguir lista os aplicativos host do Office que oferecem suporte à versão inicial e os números de versão ou de build desses aplicativos.  

| Versão   |  Office 2013 para Windows | Office 2016 para Windows (sem assinatura) | Office 365 para Windows   |  Office 365 para iPad  |  Office 365 para Mac  | Office Online  |  
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
| Suplementos de comandos (versão inicial, nenhum conjunto de requisitos) | N/D | 16.0.4678.1000 *Compatível somente com o Outlook* |Versão 1603 (Build 6769.0000) ou posterior | N/D | 15.33 ou posterior| Janeiro de 2016 | |

O conjunto de requisitos 1.1 de para suplementos de comandos introduz a capacidade de [abrir automaticamente um painel de tarefas com documentos](https://docs.microsoft.com/office/dev/add-ins/develop/automatically-open-a-task-pane-with-a-document).

A tabela a seguir lista os conjuntos de requisitos 1.1 dos suplementos de comandos, os aplicativos host do Office que oferecem suporte a esse conjunto de requisitos e os números de versão ou build dos aplicativos do Office. 

|  Conjunto de requisitos  |  Office 2013 para Windows | Office 2016 para Windows (sem assinatura) | Office 365 para Windows   |  Office 365 para iPad  |  Office 365 para Mac  | Office Online  |  
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
| AddInCommands 1.1  | N/D | 16.0.4678.1000 *Compatível somente com o Outlook*  | Versão 1705 (Build 8121.1000) ou posterior | N/D | 15.34 ou posterior| Maio de 2017 | |

Para saber mais sobre versões, números de build e sobre o Servidor do Office Online, confira:

- [Números de versão e de build de lançamentos do canal de atualizações para clientes do Office 365](https://support.office.com/article/version-and-build-numbers-of-update-channel-releases-ae942449-1fca-4484-898b-a933ea23def7)
- [Qual versão do Office estou usando?](https://support.office.com/article/What-version-of-Office-am-I-using-932788b8-a3ce-44bf-bb09-e334518b8b19)
- [Onde você pode encontrar o número de versão e de build de um aplicativo cliente do Office 365](https://support.office.com/article/version-and-build-numbers-of-update-channel-releases-ae942449-1fca-4484-898b-a933ea23def7)
- [Visão geral sobre o Servidor do Office Online](https://docs.microsoft.com/officeonlineserver/office-online-server-overview)

## <a name="office-common-api-requirement-sets"></a>Conjuntos de requisitos comuns da API do Office

Para saber mais sobre conjuntos de requisitos comuns da API, confira [Conjuntos de requisitos comuns da API do Office](office-add-in-requirement-sets.md).

## <a name="see-also"></a>Confira também

- [Versões do Office e conjuntos de requisitos](https://docs.microsoft.com/office/dev/add-ins/develop/office-versions-and-requirement-sets)
- [Especificar requisitos de API e hosts do Office](https://docs.microsoft.com/office/dev/add-ins/develop/specify-office-hosts-and-api-requirements)
- [Manifesto XML dos Suplementos do Office](https://docs.microsoft.com/office/dev/add-ins/develop/add-in-manifests)
