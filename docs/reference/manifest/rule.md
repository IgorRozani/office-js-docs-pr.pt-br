# <a name="rule-element"></a>Elemento Rule

Especifica a(s) regra(s) de ativação que deve(m) ser avaliada(s) para este suplemento contextual de email.

**Tipo de suplemento:** Suplemento contextual de email

## <a name="contained-in"></a>Contido em

- [OfficeApp](officeapp.md)
- [ExtensionPoint](extensionpoint.md)

## <a name="attributes"></a>Atributos

| Atributo | Obrigatório | Descrição |
|:-----|:-----|:-----|
| **xsi:type** | Sim | O tipo de regra que está sendo definida. |

O tipo de regra pode ser um dos seguintes:

- [ItemIs](#itemis-rule)
- [ItemHasAttachment](#itemhasattachment-rule)
- [ItemHasKnownEntity](#itemhasknownentity-rule)
- [ItemHasRegularExpressionMatch](#itemhasregularexpressionmatch-rule)
- [RuleCollection](#rulecollection)

## <a name="itemis-rule"></a>Regra ItemIs

Define uma regra que é avaliada como verdadeira se o item selecionado for do tipo especificado.

### <a name="attributes"></a>Atributos

| Atributo | Obrigatório | Descrição |
|:-----|:-----|:-----|
| **ItemType** | Sim | Especifica o tipo de item para fazer a correspondência. Pode ser `Message` ou `Appointment`. O tipo de item `Message` inclui email, solicitações de reunião, respostas de reunião e cancelamentos de reunião. |
| **FormType** | Não (dentro de [ExtensionPoint](extensionpoint.md)), Sim (dentro de [OfficeApp](officeapp.md)) | Especifica se o aplicativo deve aparecer no formulário de leitura ou edição do item. Pode ser um dos seguintes: `Read`, `Edit`, `ReadOrEdit`. Se não for especificado em um `Rule` dentro de um `ExtensionPoint`, esse valor DEVERÁ ser `Read`. |
| **itemClass** | Não | Especifica a classe personalizada de mensagens para fazer a correspondência. Para saber mais, confira o artigo [Ativar um suplemento de email no Outlook para uma classe de mensagens específica](https://docs.microsoft.com/outlook/add-ins/activation-rules). |
| **IncludeSubClasses** | Não | Especifica se a regra deve ser avaliada como true se o item pertencer a uma subclasse da classe de mensagens especificada. O padrão é `false`. |

### <a name="example"></a>Exemplo

```XML
<Rule xsi:type="ItemIs" ItemType= "Message" />
```

## <a name="itemhasattachment-rule"></a>Regra ItemHasAttachment

Define uma regra que é avaliada como verdadeira se o item contiver um anexo.

### <a name="example"></a>Exemplo

```XML
<Rule xsi:type="ItemHasAttachment" />
```

## <a name="itemhasknownentity-rule"></a>Regra ItemHasKnownEntity

Define uma regra que é avaliada como true se o item contiver texto do tipo de entidade especificada em seu assunto ou corpo.

### <a name="attributes"></a>Atributos

| Atributo | Obrigatório | Descrição |
|:-----|:-----|:-----|
| **EntityType** | Sim | Especifica o tipo de entidade que deve ser encontrado para a regra para que ela seja avaliada como verdadeira. Pode ser um dos seguintes: `MeetingSuggestion`, `TaskSuggestion`, `Address`, `Url`, `PhoneNumber`, `EmailAddress` ou `Contact`. |
| **RegExFilter** | Não | Especifica uma expressão regular para ativação desta entidade. |
| **FilterName** | Não | Especifica o nome do filtro de expressões regulares para que seja possível consultá-lo posteriormente no código do seu suplemento. |
| **IgnoreCase** | Não | Especifica ignorar maiúsculas e minúsculas ao executar a expressão regular especificada pelo atributo **RegExFilter**. |
| **Marcação** | Não | **Observação:** isso se aplica somente aos elementos **Rule** dentro dos elementos **ExtensionPoint**. Especifica como o cliente deve destacar entidades correspondentes. Pode ser um dos seguintes: `all` ou `none`. Se não for especificado, o valor padrão será `all`. |

### <a name="example"></a>Exemplo

```XML
<Rule xsi:type="ItemHasKnownEntity" EntityType="EmailAddress" />
```

## <a name="itemhasregularexpressionmatch-rule"></a>Regra ItemHasRegularExpressionMatch

Define uma regra que é avaliada como verdadeira se uma correspondência para a expressão regular especificada puder ser encontrada na propriedade especificada do item.

### <a name="attributes"></a>Atributos

| Atributo | Obrigatório | Descrição |
|:-----|:-----|:-----|
| **RegExName** | Sim | Especifica o nome da expressão regular para que você possa fazer referência à expressão no código de seu suplemento. |
| **RegExValue** | Sim | Especifica a expressão regular que será avaliada para determinar se o suplemento de email deve ser mostrado. |
| **PropertyName** | Sim | Especifica o nome da propriedade em relação a qual a expressão regular será avaliada. Pode ser um dos seguintes: `Subject`, `BodyAsPlaintext`, `BodyAsHtml` ou `SenderSTMPAddress`. |
| **IgnoreCase** | Não | Especifica que as maiúsculas e minúsculas devem ser ignoradas ao executar a expressão regular. |
| **Destaque** | Não | **Observação:** isso se aplica somente aos elementos **Rule** dentro dos elementos **ExtensionPoint**. Especifica como o cliente deve destacar texto correspondente. Pode ser um dos seguintes: `all` ou `none`. Se não for especificado, o valor padrão será `all`. |

### <a name="example"></a>Exemplo

```XML
<Rule xsi:type="ItemHasRegularExpressionMatch" RegExName="SupportArticleNumber" RegExValue="(\W|^)kb\d{6}(\W|$)" PropertyName="BodyAsHtml" IgnoreCase="true" />
```

## <a name="rulecollection"></a>RuleCollection

Define uma coleção de regras e o operador lógico a ser usado ao avaliá-las.

### <a name="attributes"></a>Atributos

| Atributo | Obrigatório | Descrição |
|:-----|:-----|:-----|
| **Modo** | Sim | Especifica o operador lógico a usar quando avaliar essa coleção de regras. Pode ser: `And` ou `Or` . |

### <a name="example"></a>Exemplo

```XML
<Rule xsi:type="RuleCollection" Mode="And">
  <Rule xsi:type="ItemIs" ItemType="Message" />
  <Rule xsi:type="ItemHasKnownEntity" EntityType="MeetingSuggestion" />
  <Rule xsi:type="ItemHasKnownEntity" EntityType="Address" Highlight="none" />
</Rule>
```

## <a name="see-also"></a>Confira também

- [Regras de ativação para suplementos do Outlook](https://docs.microsoft.com/outlook/add-ins/activation-rules)
- [Corresponder sequências de caracteres em um item do Outlook como entidades conhecidas](https://docs.microsoft.com/outlook/add-ins/match-strings-in-an-item-as-well-known-entities)    
- [Usar regras de ativação de expressões regulares para mostrar um suplemento do Outlook](https://docs.microsoft.com/outlook/add-ins/use-regular-expressions-to-show-an-outlook-add-in)