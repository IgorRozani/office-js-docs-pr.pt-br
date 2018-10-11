
# <a name="mailbox"></a><span data-ttu-id="8702b-101">mailbox</span><span class="sxs-lookup"><span data-stu-id="8702b-101">mailbox</span></span>

### <span data-ttu-id="8702b-p101">[Office](Office.md)[.context](Office.context.md). caixa de correio</span><span class="sxs-lookup"><span data-stu-id="8702b-p101">[Office](Office.md)[.context](Office.context.md). mailbox</span></span>

<span data-ttu-id="8702b-104">Fornece acesso ao modelo de objeto do suplemento do Outlook para o Microsoft Outlook e o Microsoft Outlook na Web.</span><span class="sxs-lookup"><span data-stu-id="8702b-104">Provides access to the Outlook Add-in object model for Microsoft Outlook and Microsoft Outlook on the web.</span></span>

##### <a name="requirements"></a><span data-ttu-id="8702b-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8702b-105">Requirements</span></span>

|<span data-ttu-id="8702b-106">Requisito</span><span class="sxs-lookup"><span data-stu-id="8702b-106">Requirement</span></span>| <span data-ttu-id="8702b-107">Valor</span><span class="sxs-lookup"><span data-stu-id="8702b-107">Value</span></span>|
|---|---|
|[<span data-ttu-id="8702b-108">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="8702b-108">Minimum mailbox requirement set version</span></span>](/javascript/office/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="8702b-109">1.0</span><span class="sxs-lookup"><span data-stu-id="8702b-109">1.0</span></span>|
|[<span data-ttu-id="8702b-110">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="8702b-110">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="8702b-111">Restrito</span><span class="sxs-lookup"><span data-stu-id="8702b-111">Restricted</span></span>|
|[<span data-ttu-id="8702b-112">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="8702b-112">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="8702b-113">Redigir ou ler</span><span class="sxs-lookup"><span data-stu-id="8702b-113">Compose or read</span></span>|

### <a name="namespaces"></a><span data-ttu-id="8702b-114">Namespaces</span><span class="sxs-lookup"><span data-stu-id="8702b-114">Namespaces</span></span>

<span data-ttu-id="8702b-115">[diagnostics](Office.context.mailbox.diagnostics.md): Fornece informações de diagnóstico para um suplemento do Outlook.</span><span class="sxs-lookup"><span data-stu-id="8702b-115">[diagnostics](Office.context.mailbox.diagnostics.md): Provides diagnostic information to an Outlook add-in.</span></span>

<span data-ttu-id="8702b-116">[item](Office.context.mailbox.item.md): Fornece métodos e propriedades para acessar uma mensagem ou um compromisso em um suplemento do Outlook.</span><span class="sxs-lookup"><span data-stu-id="8702b-116">[item](Office.context.mailbox.item.md): Provides methods and properties for accessing a message or appointment in an Outlook add-in.</span></span>

<span data-ttu-id="8702b-117">[userProfile](Office.context.mailbox.userProfile.md): Fornece informações sobre o usuário em um suplemento do Outlook.</span><span class="sxs-lookup"><span data-stu-id="8702b-117">[userProfile](Office.context.mailbox.userProfile.md): Provides information about the user in an Outlook add-in.</span></span>

### <a name="members"></a><span data-ttu-id="8702b-118">Membros</span><span class="sxs-lookup"><span data-stu-id="8702b-118">Members</span></span>

#### <a name="ewsurl-string"></a><span data-ttu-id="8702b-119">ewsUrl :String</span><span class="sxs-lookup"><span data-stu-id="8702b-119">ewsUrl :String</span></span>

<span data-ttu-id="8702b-p102">Obtém a URL do ponto de extremidade dos Serviços Web do Exchange (EWS) para esta conta de email. Somente modo de leitura.</span><span class="sxs-lookup"><span data-stu-id="8702b-p102">Gets the URL of the Exchange Web Services (EWS) endpoint for this email account. Read mode only.</span></span>

> [!NOTE]
> <span data-ttu-id="8702b-122">Esse membro não é suportado no Outlook para iOS ou no Outlook para Android.</span><span class="sxs-lookup"><span data-stu-id="8702b-122">Note: This member is not supported in Outlook for iOS or Outlook for Android.</span></span>

<span data-ttu-id="8702b-p103">O valor `ewsUrl` pode ser usado por um serviço remoto para fazer chamadas do EWS à caixa de correio do usuário. Por exemplo, você pode criar um serviço remoto para [obter anexos do item selecionado](https://docs.microsoft.com/outlook/add-ins/get-attachments-of-an-outlook-item).</span><span class="sxs-lookup"><span data-stu-id="8702b-p103">The `ewsUrl` value can be used by a remote service to make EWS calls to the user's mailbox. For example, you can create a remote service to [get attachments from the selected item](https://docs.microsoft.com/outlook/add-ins/get-attachments-of-an-outlook-item).</span></span>

##### <a name="type"></a><span data-ttu-id="8702b-125">Tipo:</span><span class="sxs-lookup"><span data-stu-id="8702b-125">Type:</span></span>

*   <span data-ttu-id="8702b-126">Sequência de caracteres</span><span class="sxs-lookup"><span data-stu-id="8702b-126">String</span></span>

##### <a name="requirements"></a><span data-ttu-id="8702b-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8702b-127">Requirements</span></span>

|<span data-ttu-id="8702b-128">Requisito</span><span class="sxs-lookup"><span data-stu-id="8702b-128">Requirement</span></span>| <span data-ttu-id="8702b-129">Valor</span><span class="sxs-lookup"><span data-stu-id="8702b-129">Value</span></span>|
|---|---|
|[<span data-ttu-id="8702b-130">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="8702b-130">Minimum mailbox requirement set version</span></span>](/javascript/office/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="8702b-131">1.0</span><span class="sxs-lookup"><span data-stu-id="8702b-131">1.0</span></span>|
|[<span data-ttu-id="8702b-132">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="8702b-132">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="8702b-133">ReadItem</span><span class="sxs-lookup"><span data-stu-id="8702b-133">ReadItem</span></span>|
|[<span data-ttu-id="8702b-134">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="8702b-134">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="8702b-135">Leitura</span><span class="sxs-lookup"><span data-stu-id="8702b-135">Read</span></span>|

### <a name="methods"></a><span data-ttu-id="8702b-136">Métodos</span><span class="sxs-lookup"><span data-stu-id="8702b-136">Methods</span></span>

####  <a name="converttolocalclienttimetimevalue--localclienttimejavascriptapioutlook11officelocalclienttime"></a><span data-ttu-id="8702b-137">convertToLocalClientTime(timeValue) → {[LocalClientTime](/javascript/api/outlook_1_1/office.LocalClientTime)}</span><span class="sxs-lookup"><span data-stu-id="8702b-137">convertToLocalClientTime(timeValue) → {[LocalClientTime](/javascript/api/outlook_1_1/office.LocalClientTime)}</span></span>

<span data-ttu-id="8702b-138">Obtém um dicionário contendo informações da hora local do cliente.</span><span class="sxs-lookup"><span data-stu-id="8702b-138">Gets a dictionary containing time information in local client time.</span></span>

<span data-ttu-id="8702b-p104">As datas e horas usadas por um aplicativo de email para Outlook ou pelo aplicativo Web do Outlook podem usar fusos horários diferentes. O Outlook usa o fuso horário do computador cliente; o o aplicativo Web do Outlook usa o fuso horário definido no Centro de administração do Exchange (EAC). Você deve controlar os valores de data e hora para que os valores exibidos na interface do usuário sejam sempre consistentes com o fuso horário que o usuário espera.</span><span class="sxs-lookup"><span data-stu-id="8702b-p104">The dates and times used by a mail app for Outlook or Outlook Web App can use different time zones. Outlook uses the client computer time zone; Outlook Web App uses the time zone set on the Exchange Admin Center (EAC). You should handle date and time values so that the values you display on the user interface are always consistent with the time zone that the user expects.</span></span>

<span data-ttu-id="8702b-p105">Se o aplicativo de email estiver em execução no Outlook, o método `convertToLocalClientTime` retornará um objeto de dicionário com os valores definidos para o fuso horário do computador do cliente. Se o aplicativo de email estiver em execução no aplicativo Web do Outlook, o método `convertToLocalClientTime` retornará um objeto de dicionário com os valores definidos para o fuso horário especificado no EAC.</span><span class="sxs-lookup"><span data-stu-id="8702b-p105">If the mail app is running in Outlook, the `convertToLocalClientTime` method will return a dictionary object with the values set to the client computer time zone. If the mail app is running in Outlook Web App, the `convertToLocalClientTime` method will return a dictionary object with the values set to the time zone specified in the EAC.</span></span>

##### <a name="parameters"></a><span data-ttu-id="8702b-144">Parâmetros:</span><span class="sxs-lookup"><span data-stu-id="8702b-144">Parameters:</span></span>

|<span data-ttu-id="8702b-145">Nome</span><span class="sxs-lookup"><span data-stu-id="8702b-145">Name</span></span>| <span data-ttu-id="8702b-146">Tipo</span><span class="sxs-lookup"><span data-stu-id="8702b-146">Type</span></span>| <span data-ttu-id="8702b-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="8702b-147">Description</span></span>|
|---|---|---|
|`timeValue`| <span data-ttu-id="8702b-148">Data</span><span class="sxs-lookup"><span data-stu-id="8702b-148">Date</span></span>|<span data-ttu-id="8702b-149">Um objeto Date</span><span class="sxs-lookup"><span data-stu-id="8702b-149">A Date object</span></span>|

##### <a name="requirements"></a><span data-ttu-id="8702b-150">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8702b-150">Requirements</span></span>

|<span data-ttu-id="8702b-151">Requisito</span><span class="sxs-lookup"><span data-stu-id="8702b-151">Requirement</span></span>| <span data-ttu-id="8702b-152">Valor</span><span class="sxs-lookup"><span data-stu-id="8702b-152">Value</span></span>|
|---|---|
|[<span data-ttu-id="8702b-153">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="8702b-153">Minimum mailbox requirement set version</span></span>](/javascript/office/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="8702b-154">1.0</span><span class="sxs-lookup"><span data-stu-id="8702b-154">1.0</span></span>|
|[<span data-ttu-id="8702b-155">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="8702b-155">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="8702b-156">ReadItem</span><span class="sxs-lookup"><span data-stu-id="8702b-156">ReadItem</span></span>|
|[<span data-ttu-id="8702b-157">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="8702b-157">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="8702b-158">Redigir ou ler</span><span class="sxs-lookup"><span data-stu-id="8702b-158">Compose or read</span></span>|

##### <a name="returns"></a><span data-ttu-id="8702b-159">Retorna:</span><span class="sxs-lookup"><span data-stu-id="8702b-159">Returns:</span></span>

<span data-ttu-id="8702b-160">Tipo: [LocalClientTime](/javascript/api/outlook_1_1/office.LocalClientTime)</span><span class="sxs-lookup"><span data-stu-id="8702b-160">Type: [LocalClientTime](/javascript/api/outlook_1_1/office.LocalClientTime)</span></span>

####  <a name="converttoutcclienttimeinput--date"></a><span data-ttu-id="8702b-161">convertToUtcClientTime(input) → {Date}</span><span class="sxs-lookup"><span data-stu-id="8702b-161">convertToUtcClientTime(input) → {Date}</span></span>

<span data-ttu-id="8702b-162">Obtém um objeto Date de um dicionário contendo as informações de hora.</span><span class="sxs-lookup"><span data-stu-id="8702b-162">Gets a Date object from a dictionary containing time information.</span></span>

<span data-ttu-id="8702b-163">O método `convertToUtcClientTime` converte um dicionário que contém uma data e hora locais para um objeto Date com os valores corretos para a data e hora locais.</span><span class="sxs-lookup"><span data-stu-id="8702b-163">The `convertToUtcClientTime` method converts a dictionary containing a local date and time to a Date object with the correct values for the local date and time.</span></span>

##### <a name="parameters"></a><span data-ttu-id="8702b-164">Parâmetros:</span><span class="sxs-lookup"><span data-stu-id="8702b-164">Parameters:</span></span>

|<span data-ttu-id="8702b-165">Nome</span><span class="sxs-lookup"><span data-stu-id="8702b-165">Name</span></span>| <span data-ttu-id="8702b-166">Tipo</span><span class="sxs-lookup"><span data-stu-id="8702b-166">Type</span></span>| <span data-ttu-id="8702b-167">Descrição</span><span class="sxs-lookup"><span data-stu-id="8702b-167">Description</span></span>|
|---|---|---|
|`input`| [<span data-ttu-id="8702b-168">LocalClientTime</span><span class="sxs-lookup"><span data-stu-id="8702b-168">LocalClientTime</span></span>](/javascript/api/outlook_1_1/office.LocalClientTime)|<span data-ttu-id="8702b-169">O valor de hora local para converter.</span><span class="sxs-lookup"><span data-stu-id="8702b-169">The local time value to convert.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="8702b-170">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8702b-170">Requirements</span></span>

|<span data-ttu-id="8702b-171">Requisito</span><span class="sxs-lookup"><span data-stu-id="8702b-171">Requirement</span></span>| <span data-ttu-id="8702b-172">Valor</span><span class="sxs-lookup"><span data-stu-id="8702b-172">Value</span></span>|
|---|---|
|[<span data-ttu-id="8702b-173">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="8702b-173">Minimum mailbox requirement set version</span></span>](/javascript/office/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="8702b-174">1.0</span><span class="sxs-lookup"><span data-stu-id="8702b-174">1.0</span></span>|
|[<span data-ttu-id="8702b-175">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="8702b-175">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="8702b-176">ReadItem</span><span class="sxs-lookup"><span data-stu-id="8702b-176">ReadItem</span></span>|
|[<span data-ttu-id="8702b-177">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="8702b-177">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="8702b-178">Redigir ou ler</span><span class="sxs-lookup"><span data-stu-id="8702b-178">Compose or read</span></span>|

##### <a name="returns"></a><span data-ttu-id="8702b-179">Retorna:</span><span class="sxs-lookup"><span data-stu-id="8702b-179">Returns:</span></span>

<span data-ttu-id="8702b-180">Um objeto Date com o horário expresso em UTC.</span><span class="sxs-lookup"><span data-stu-id="8702b-180">A Date object with the time expressed in UTC.</span></span>

<dl class="param-type"><span data-ttu-id="8702b-181">

<dt>Tipo</dt>

</span><span class="sxs-lookup"><span data-stu-id="8702b-181">

<dt>Type</dt>

</span></span><dd><span data-ttu-id="8702b-182">Data</span><span class="sxs-lookup"><span data-stu-id="8702b-182">Date</span></span></dd>

</dl>

####  <a name="displayappointmentformitemid"></a><span data-ttu-id="8702b-183">displayAppointmentForm(itemId)</span><span class="sxs-lookup"><span data-stu-id="8702b-183">displayAppointmentForm(itemId)</span></span>

<span data-ttu-id="8702b-184">Exibe um compromisso de calendário existente.</span><span class="sxs-lookup"><span data-stu-id="8702b-184">Displays an existing calendar appointment.</span></span>

> [!NOTE]
> <span data-ttu-id="8702b-185">Esse método não é suportado no Outlook para iOS ou no Outlook para Android.</span><span class="sxs-lookup"><span data-stu-id="8702b-185">Note: This method is not supported in Outlook for iOS or Outlook for Android.</span></span>

<span data-ttu-id="8702b-186">O método `displayAppointmentForm` abre um compromisso de calendário existente em uma nova janela na área de trabalho ou em uma caixa de diálogo em dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="8702b-186">The `displayAppointmentForm` method opens an existing calendar appointment in a new window on the desktop or in a dialog box on mobile devices.</span></span>

<span data-ttu-id="8702b-p106">No Outlook para Mac, você pode usar esse método para exibir um único compromisso que não faz parte de uma série recorrente, ou o compromisso mestre de uma série recorrente, mas não pode exibir uma instância da série. Isso ocorre porque no Outlook para Mac você não pode acessar as propriedades (incluindo a ID do item) das instâncias de uma série recorrente.</span><span class="sxs-lookup"><span data-stu-id="8702b-p106">In Outlook for Mac, you can use this method to display a single appointment that is not part of a recurring series, or the master appointment of a recurring series, but you cannot display an instance of the series. This is because in Outlook for Mac, you cannot access the properties (including the item ID) of instances of a recurring series.</span></span>

<span data-ttu-id="8702b-189">No Outlook Web App, esse método abre o formulário especificado somente se o corpo do formulário for menor ou igual ao número de caracteres de 32 KB.</span><span class="sxs-lookup"><span data-stu-id="8702b-189">In Outlook Web App, this method opens the specified form only if the body of the form is less than or equal to 32KB number of characters.</span></span>

<span data-ttu-id="8702b-190">Se o identificador de item especificado não identificar um compromisso existente, um painel em branco será aberto no computador ou no dispositivo cliente e nenhuma mensagem de erro será retornada.</span><span class="sxs-lookup"><span data-stu-id="8702b-190">If the specified item identifier does not identify an existing appointment, a blank pane opens on the client computer or device, and no error message will be returned.</span></span>

##### <a name="parameters"></a><span data-ttu-id="8702b-191">Parâmetros:</span><span class="sxs-lookup"><span data-stu-id="8702b-191">Parameters:</span></span>

|<span data-ttu-id="8702b-192">Nome</span><span class="sxs-lookup"><span data-stu-id="8702b-192">Name</span></span>| <span data-ttu-id="8702b-193">Tipo</span><span class="sxs-lookup"><span data-stu-id="8702b-193">Type</span></span>| <span data-ttu-id="8702b-194">Descrição</span><span class="sxs-lookup"><span data-stu-id="8702b-194">Description</span></span>|
|---|---|---|
|`itemId`| <span data-ttu-id="8702b-195">Sequência de caracteres</span><span class="sxs-lookup"><span data-stu-id="8702b-195">String</span></span>|<span data-ttu-id="8702b-196">O identificador de serviços da Web do Exchange (EWS) para um compromisso de calendário existente.</span><span class="sxs-lookup"><span data-stu-id="8702b-196">The Exchange Web Services (EWS) identifier for an existing calendar appointment.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="8702b-197">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8702b-197">Requirements</span></span>

|<span data-ttu-id="8702b-198">Requisito</span><span class="sxs-lookup"><span data-stu-id="8702b-198">Requirement</span></span>| <span data-ttu-id="8702b-199">Valor</span><span class="sxs-lookup"><span data-stu-id="8702b-199">Value</span></span>|
|---|---|
|[<span data-ttu-id="8702b-200">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="8702b-200">Minimum mailbox requirement set version</span></span>](/javascript/office/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="8702b-201">1.0</span><span class="sxs-lookup"><span data-stu-id="8702b-201">1.0</span></span>|
|[<span data-ttu-id="8702b-202">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="8702b-202">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="8702b-203">ReadItem</span><span class="sxs-lookup"><span data-stu-id="8702b-203">ReadItem</span></span>|
|[<span data-ttu-id="8702b-204">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="8702b-204">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="8702b-205">Redigir ou ler</span><span class="sxs-lookup"><span data-stu-id="8702b-205">Compose or read</span></span>|

##### <a name="example"></a><span data-ttu-id="8702b-206">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8702b-206">Example</span></span>

```
Office.context.mailbox.displayAppointmentForm(appointmentId);
```

####  <a name="displaymessageformitemid"></a><span data-ttu-id="8702b-207">displayMessageForm(itemId)</span><span class="sxs-lookup"><span data-stu-id="8702b-207">displayMessageForm(itemId)</span></span>

<span data-ttu-id="8702b-208">Exibe uma mensagem existente.</span><span class="sxs-lookup"><span data-stu-id="8702b-208">Displays an existing message.</span></span>

> [!NOTE]
> <span data-ttu-id="8702b-209">Esse método não é suportado no Outlook para iOS ou no Outlook para Android.</span><span class="sxs-lookup"><span data-stu-id="8702b-209">Note: This method is not supported in Outlook for iOS or Outlook for Android.</span></span>

<span data-ttu-id="8702b-210">O método `displayMessageForm` abre uma mensagem existente em uma nova janela na área de trabalho ou em uma caixa de diálogo em dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="8702b-210">The `displayMessageForm` method opens an existing message in a new window on the desktop or in a dialog box on mobile devices.</span></span>

<span data-ttu-id="8702b-211">No aplicativo Web do Outlook, este método abre o formulário especificado somente se o corpo do formulário for menor que ou igual ao número de caracteres de 32 KB.</span><span class="sxs-lookup"><span data-stu-id="8702b-211">In Outlook Web App, this method opens the specified form only if the body of the form is less than or equal to 32 KB number of characters.</span></span>

<span data-ttu-id="8702b-212">Se o identificador do item especificado não identificar uma mensagem existente, não será exibida mensagem no computador cliente e não será exibida nenhuma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="8702b-212">If the specified item identifier does not identify an existing message, no message will be displayed on the client computer, and no error message will be returned.</span></span>

<span data-ttu-id="8702b-p107">Não use o método `displayMessageForm` com um `itemId` que representa um compromisso. Use o método `displayAppointmentForm` para exibir um compromisso existente e `displayNewAppointmentForm` para exibir um formulário e criar um novo compromisso.</span><span class="sxs-lookup"><span data-stu-id="8702b-p107">Do not use the `displayMessageForm` with an `itemId` that represents an appointment. Use the `displayAppointmentForm` method to display an existing appointment, and `displayNewAppointmentForm` to display a form to create a new appointment.</span></span>

##### <a name="parameters"></a><span data-ttu-id="8702b-215">Parâmetros:</span><span class="sxs-lookup"><span data-stu-id="8702b-215">Parameters:</span></span>

|<span data-ttu-id="8702b-216">Name</span><span class="sxs-lookup"><span data-stu-id="8702b-216">Name</span></span>| <span data-ttu-id="8702b-217">Type</span><span class="sxs-lookup"><span data-stu-id="8702b-217">Type</span></span>| <span data-ttu-id="8702b-218">Description</span><span class="sxs-lookup"><span data-stu-id="8702b-218">Description</span></span>|
|---|---|---|
|`itemId`| <span data-ttu-id="8702b-219">Sequência de caracteres</span><span class="sxs-lookup"><span data-stu-id="8702b-219">String</span></span>|<span data-ttu-id="8702b-220">O identificador dos Serviços Web do Exchange (EWS) para uma mensagem existente.</span><span class="sxs-lookup"><span data-stu-id="8702b-220">The Exchange Web Services (EWS) identifier for an existing message.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="8702b-221">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8702b-221">Requirements</span></span>

|<span data-ttu-id="8702b-222">Requisito</span><span class="sxs-lookup"><span data-stu-id="8702b-222">Requirement</span></span>| <span data-ttu-id="8702b-223">Valor</span><span class="sxs-lookup"><span data-stu-id="8702b-223">Value</span></span>|
|---|---|
|[<span data-ttu-id="8702b-224">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="8702b-224">Minimum mailbox requirement set version</span></span>](/javascript/office/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="8702b-225">1.0</span><span class="sxs-lookup"><span data-stu-id="8702b-225">1.0</span></span>|
|[<span data-ttu-id="8702b-226">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="8702b-226">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="8702b-227">ReadItem</span><span class="sxs-lookup"><span data-stu-id="8702b-227">ReadItem</span></span>|
|[<span data-ttu-id="8702b-228">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="8702b-228">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="8702b-229">Redigir ou ler</span><span class="sxs-lookup"><span data-stu-id="8702b-229">Compose or read</span></span>|

##### <a name="example"></a><span data-ttu-id="8702b-230">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8702b-230">Example</span></span>

```
Office.context.mailbox.displayMessageForm(messageId);
```

#### <a name="displaynewappointmentformparameters"></a><span data-ttu-id="8702b-231">displayNewAppointmentForm(parameters)</span><span class="sxs-lookup"><span data-stu-id="8702b-231">displayNewAppointmentForm(parameters)</span></span>

<span data-ttu-id="8702b-232">Exibe um formulário para criar um novo compromisso no calendário.</span><span class="sxs-lookup"><span data-stu-id="8702b-232">Displays a form for creating a new calendar appointment.</span></span>

> [!NOTE]
> <span data-ttu-id="8702b-233">Esse método não é suportado no Outlook para iOS ou no Outlook para Android.</span><span class="sxs-lookup"><span data-stu-id="8702b-233">Note: This method is not supported in Outlook for iOS or Outlook for Android.</span></span>

<span data-ttu-id="8702b-p108">O método `displayNewAppointmentForm` abre um formulário que permite ao usuário criar um novo compromisso ou reunião. Se os parâmetros forem especificados, os campos de formulário do compromisso serão preenchidos automaticamente com o conteúdo dos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8702b-p108">The `displayNewAppointmentForm` method opens a form that enables the user to create a new appointment or meeting. If parameters are specified, the appointment form fields are automatically populated with the contents of the parameters.</span></span>

<span data-ttu-id="8702b-p109">No aplicativo Web do Outlook e no OWA para Dispositivos, esse método sempre exibe um formulário com um campo de participantes. Se você não especificar nenhum participante como argumento de entrada, o método exibe um formulário com um botão **Salvar**. Se você especificar participantes, o formulário inclui os participantes e um botão **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="8702b-p109">In Outlook Web App and OWA for Devices, this method always displays a form with an attendees field. If you do not specify any attendees as input arguments, the method displays a form with a **Save** button. If you have specified attendees, the form would include the attendees and a **Send** button.</span></span>

<span data-ttu-id="8702b-p110">No cliente avançado do Outlook e no Outlook RT, se você especificar quaisquer participantes ou recursos nos parâmetros `requiredAttendees`, `optionalAttendees` ou `resources`, o método exibirá um formulário de reunião com um botão **Enviar**. Se você não especificar destinatários, o método exibirá um formulário de compromisso com um botão **Salvar & Fechar**.</span><span class="sxs-lookup"><span data-stu-id="8702b-p110">In the Outlook rich client and Outlook RT, if you specify any attendees or resources in the `requiredAttendees`, `optionalAttendees`, or `resources` parameter, this method displays a meeting form with a **Send** button. If you don't specify any recipients, this method displays an appointment form with a **Save & Close** button.</span></span>

<span data-ttu-id="8702b-241">Se algum dos parâmetros exceder os limites de tamanho especificados ou se um nome de parâmetro desconhecido for especificado, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="8702b-241">If any of the parameters exceed the specified size limits, or if an unknown parameter name is specified, an exception is thrown.</span></span>

##### <a name="parameters"></a><span data-ttu-id="8702b-242">Parâmetros:</span><span class="sxs-lookup"><span data-stu-id="8702b-242">Parameters:</span></span>

|<span data-ttu-id="8702b-243">Name</span><span class="sxs-lookup"><span data-stu-id="8702b-243">Name</span></span>| <span data-ttu-id="8702b-244">Type</span><span class="sxs-lookup"><span data-stu-id="8702b-244">Type</span></span>| <span data-ttu-id="8702b-245">Description</span><span class="sxs-lookup"><span data-stu-id="8702b-245">Description</span></span>|
|---|---|---|
| `parameters` | <span data-ttu-id="8702b-246">Objeto</span><span class="sxs-lookup"><span data-stu-id="8702b-246">Object</span></span> | <span data-ttu-id="8702b-247">Um dicionário de parâmetros que descreve o novo compromisso.</span><span class="sxs-lookup"><span data-stu-id="8702b-247">A dictionary of parameters describing the new appointment.</span></span> |
| `parameters.requiredAttendees` | <span data-ttu-id="8702b-248">Array.&lt;String&gt; | Array.&lt;[EmailAddressDetails](/javascript/api/outlook_1_1/office.emailaddressdetails)&gt;</span><span class="sxs-lookup"><span data-stu-id="8702b-248">Array.&lt;String&gt; &#124; Array.&lt;[EmailAddressDetails](/javascript/api/outlook_1_1/office.emailaddressdetails)&gt;</span></span> | <span data-ttu-id="8702b-p111">Uma matriz de sequências de caracteres que contém os endereços de email ou uma matriz contendo um objeto `EmailAddressDetails` para cada um dos participantes obrigatórios do compromisso. A matriz está limitada a um máximo de 100 entradas.</span><span class="sxs-lookup"><span data-stu-id="8702b-p111">An array of strings containing the email addresses or an array containing an `EmailAddressDetails` object for each of the required attendees for the appointment. The array is limited to a maximum of 100 entries.</span></span> |
| `parameters.optionalAttendees` | <span data-ttu-id="8702b-251">Array.&lt;String&gt; | Array.&lt;[EmailAddressDetails](/javascript/api/outlook_1_1/office.emailaddressdetails)&gt;</span><span class="sxs-lookup"><span data-stu-id="8702b-251">Array.&lt;String&gt; &#124; Array.&lt;[EmailAddressDetails](/javascript/api/outlook_1_1/office.emailaddressdetails)&gt;</span></span> | <span data-ttu-id="8702b-p112">Uma matriz de sequências de caracteres que contém os endereços de email ou uma matriz contendo um objeto `EmailAddressDetails` para cada um dos participantes opcionais do compromisso. A matriz está limitada a um máximo de 100 entradas.</span><span class="sxs-lookup"><span data-stu-id="8702b-p112">An array of strings containing the email addresses or an array containing an `EmailAddressDetails` object for each of the optional attendees for the appointment. The array is limited to a maximum of 100 entries.</span></span> |
| `parameters.start` | <span data-ttu-id="8702b-254">Date</span><span class="sxs-lookup"><span data-stu-id="8702b-254">Date</span></span> | <span data-ttu-id="8702b-255">Um objeto `Date` que especifica a data e a hora de início do compromisso.</span><span class="sxs-lookup"><span data-stu-id="8702b-255">A `Date` object specifying the start date and time of the appointment.</span></span> |
| `parameters.end` | <span data-ttu-id="8702b-256">Date</span><span class="sxs-lookup"><span data-stu-id="8702b-256">Date</span></span> | <span data-ttu-id="8702b-257">Um objeto `Date` que especifica a data e a hora de término do compromisso.</span><span class="sxs-lookup"><span data-stu-id="8702b-257">A `Date` object specifying the end date and time of the appointment.</span></span> |
| `parameters.location` | <span data-ttu-id="8702b-258">Sequência de caracteres</span><span class="sxs-lookup"><span data-stu-id="8702b-258">String</span></span> | <span data-ttu-id="8702b-p113">Uma sequência de caracteres que contém o local do compromisso. Está limitada a um máximo de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="8702b-p113">A string containing the location of the appointment. The string is limited to a maximum of 255 characters.</span></span> |
| `parameters.resources` | <span data-ttu-id="8702b-261">Array.&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="8702b-261">Array.&lt;String&gt;</span></span> | <span data-ttu-id="8702b-p114">Uma matriz de sequências de caracteres que contém os recursos necessários para o compromisso. A matriz está limitada a um máximo de 100 entradas.</span><span class="sxs-lookup"><span data-stu-id="8702b-p114">An array of strings containing the resources required for the appointment. The array is limited to a maximum of 100 entries.</span></span> |
| `parameters.subject` | <span data-ttu-id="8702b-264">Sequência de caracteres</span><span class="sxs-lookup"><span data-stu-id="8702b-264">String</span></span> | <span data-ttu-id="8702b-p115">Uma sequência de caracteres que contém o assunto do compromisso. Está limitada a um máximo de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="8702b-p115">A string containing the subject of the appointment. The string is limited to a maximum of 255 characters.</span></span> |
| `parameters.body` | <span data-ttu-id="8702b-267">Sequência de caracteres</span><span class="sxs-lookup"><span data-stu-id="8702b-267">String</span></span> | <span data-ttu-id="8702b-p116">O corpo do compromisso. O conteúdo do corpo está limitado a um tamanho máximo de 32 KB.</span><span class="sxs-lookup"><span data-stu-id="8702b-p116">The body of the appointment. The body content is limited to a maximum size of 32 KB.</span></span> |

##### <a name="requirements"></a><span data-ttu-id="8702b-270">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8702b-270">Requirements</span></span>

|<span data-ttu-id="8702b-271">Requisito</span><span class="sxs-lookup"><span data-stu-id="8702b-271">Requirement</span></span>| <span data-ttu-id="8702b-272">Valor</span><span class="sxs-lookup"><span data-stu-id="8702b-272">Value</span></span>|
|---|---|
|[<span data-ttu-id="8702b-273">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="8702b-273">Minimum mailbox requirement set version</span></span>](/javascript/office/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="8702b-274">1.0</span><span class="sxs-lookup"><span data-stu-id="8702b-274">1.0</span></span>|
|[<span data-ttu-id="8702b-275">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="8702b-275">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="8702b-276">ReadItem</span><span class="sxs-lookup"><span data-stu-id="8702b-276">ReadItem</span></span>|
|[<span data-ttu-id="8702b-277">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="8702b-277">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="8702b-278">Leitura</span><span class="sxs-lookup"><span data-stu-id="8702b-278">Read</span></span>|

##### <a name="example"></a><span data-ttu-id="8702b-279">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8702b-279">Example</span></span>

```
var start = new Date();
var end = new Date();
end.setHours(start.getHours() + 1);

Office.context.mailbox.displayNewAppointmentForm(
  {
    requiredAttendees: ['bob@contoso.com'],
    optionalAttendees: ['sam@contoso.com'],
    start: start,
    end: end,
    location: 'Home',
    resources: ['projector@contoso.com'],
    subject: 'meeting',
    body: 'Hello World!'
  });
```

#### <a name="getcallbacktokenasynccallback-usercontext"></a><span data-ttu-id="8702b-280">getCallbackTokenAsync(callback, [userContext])</span><span class="sxs-lookup"><span data-stu-id="8702b-280">getCallbackTokenAsync(callback, [userContext])</span></span>

<span data-ttu-id="8702b-281">Obtém uma sequência de caracteres que contém um token usado para obter um anexo ou um item de um Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="8702b-281">Gets a string that contains a token used to get an attachment or item from an Exchange Server.</span></span>

<span data-ttu-id="8702b-p117">O método `getCallbackTokenAsync` faz uma chamada assíncrona para obter um token opaco do Exchange Server que hospeda a caixa de correio do usuário. A vida útil do token de retorno de chamada é de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="8702b-p117">The `getCallbackTokenAsync` method makes an asynchronous call to get an opaque token from the Exchange Server that hosts the user's mailbox. The lifetime of the callback token is 5 minutes.</span></span>

<span data-ttu-id="8702b-p118">Você pode passar o token e um identificador de anexo ou um identificador de item a um sistema de terceiros. O sistema de terceiros usa o token como portador da autorização para chamar as operações [GetAttachment](https://docs.microsoft.com/exchange/client-developer/web-service-reference/getattachment-operation) ou [GetItem](https://docs.microsoft.com/exchange/client-developer/web-service-reference/getitem-operation) dos Serviços Web do Exchange (EWS) para retornar um anexo ou item. Por exemplo, você pode criar um serviço remoto para [obter anexos do item selecionado](https://docs.microsoft.com/outlook/add-ins/get-attachments-of-an-outlook-item).</span><span class="sxs-lookup"><span data-stu-id="8702b-p118">You can pass the token and an attachment identifier or item identifier to a third-party system. The third-party system uses the token as a bearer authorization token to call the Exchange Web Services (EWS) [GetAttachment](https://docs.microsoft.com/exchange/client-developer/web-service-reference/getattachment-operation) or [GetItem](https://docs.microsoft.com/exchange/client-developer/web-service-reference/getitem-operation) operation to return an attachment or item. For example, you can create a remote service to [get attachments from the selected item](https://docs.microsoft.com/outlook/add-ins/get-attachments-of-an-outlook-item).</span></span>

<span data-ttu-id="8702b-287">Seu aplicativo deve ter a permissão **ReadItem** especificada em seu manifesto para chamar o método `getCallbackTokenAsync`.</span><span class="sxs-lookup"><span data-stu-id="8702b-287">Your app must have the **ReadItem** permission specified in its manifest to call the `getCallbackTokenAsync` method.</span></span>

##### <a name="parameters"></a><span data-ttu-id="8702b-288">Parâmetros:</span><span class="sxs-lookup"><span data-stu-id="8702b-288">Parameters:</span></span>

|<span data-ttu-id="8702b-289">Name</span><span class="sxs-lookup"><span data-stu-id="8702b-289">Name</span></span>| <span data-ttu-id="8702b-290">Type</span><span class="sxs-lookup"><span data-stu-id="8702b-290">Type</span></span>| <span data-ttu-id="8702b-291">Attributes</span><span class="sxs-lookup"><span data-stu-id="8702b-291">Attributes</span></span>| <span data-ttu-id="8702b-292">Description</span><span class="sxs-lookup"><span data-stu-id="8702b-292">Description</span></span>|
|---|---|---|---|
|`callback`| <span data-ttu-id="8702b-293">função</span><span class="sxs-lookup"><span data-stu-id="8702b-293">function</span></span>||<span data-ttu-id="8702b-294">Quando o método for concluído, a função passada no parâmetro `callback` é chamada com um único parâmetro, `asyncResult`, que é um objeto [`AsyncResult`](/javascript/api/office/office.asyncresult).</span><span class="sxs-lookup"><span data-stu-id="8702b-294">When the method completes, the function passed in the `callback` parameter is called with a single parameter, `asyncResult`, which is an [`AsyncResult`](/javascript/api/office/office.asyncresult) object.</span></span><br/><br/><span data-ttu-id="8702b-295">O token é fornecido como uma sequência de caracteres na propriedade `asyncResult.value`.</span><span class="sxs-lookup"><span data-stu-id="8702b-295">The token is provided as a string in the `asyncResult.value` property.</span></span>|
|`userContext`| <span data-ttu-id="8702b-296">Objeto</span><span class="sxs-lookup"><span data-stu-id="8702b-296">Object</span></span>| <span data-ttu-id="8702b-297">&lt;opcional&gt;</span><span class="sxs-lookup"><span data-stu-id="8702b-297">&lt;optional&gt;</span></span>|<span data-ttu-id="8702b-298">Qualquer dado de estado que é passado para o método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="8702b-298">Any state data that is passed to the asynchronous method.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="8702b-299">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8702b-299">Requirements</span></span>

|<span data-ttu-id="8702b-300">Requisito</span><span class="sxs-lookup"><span data-stu-id="8702b-300">Requirement</span></span>| <span data-ttu-id="8702b-301">Valor</span><span class="sxs-lookup"><span data-stu-id="8702b-301">Value</span></span>|
|---|---|
|[<span data-ttu-id="8702b-302">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="8702b-302">Minimum mailbox requirement set version</span></span>](/javascript/office/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="8702b-303">1.0</span><span class="sxs-lookup"><span data-stu-id="8702b-303">1.0</span></span>|
|[<span data-ttu-id="8702b-304">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="8702b-304">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="8702b-305">ReadItem</span><span class="sxs-lookup"><span data-stu-id="8702b-305">ReadItem</span></span>|
|[<span data-ttu-id="8702b-306">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="8702b-306">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="8702b-307">Leitura</span><span class="sxs-lookup"><span data-stu-id="8702b-307">Read</span></span>|

##### <a name="example"></a><span data-ttu-id="8702b-308">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8702b-308">Example</span></span>

```js
function getCallbackToken() {
  Office.context.mailbox.getCallbackTokenAsync(cb);
}

function cb(asyncResult) {
  var token = asyncResult.value;
}
```

####  <a name="getuseridentitytokenasynccallback-usercontext"></a><span data-ttu-id="8702b-309">getUserIdentityTokenAsync(callback, [userContext])</span><span class="sxs-lookup"><span data-stu-id="8702b-309">getUserIdentityTokenAsync(callback, [userContext])</span></span>

<span data-ttu-id="8702b-310">Obtém um token que identifica o usuário e o suplemento do Office.</span><span class="sxs-lookup"><span data-stu-id="8702b-310">Gets a token identifying the user and the Office Add-in.</span></span>

<span data-ttu-id="8702b-311">O método `getUserIdentityTokenAsync` retorna um token que pode ser utilizado para identificar e [autenticar o suplemento e o usuário com um sistema de terceiros](https://docs.microsoft.com/outlook/add-ins/authentication).</span><span class="sxs-lookup"><span data-stu-id="8702b-311">The `getUserIdentityTokenAsync` method returns a token that you can use to identify and [authenticate the add-in and user with a third-party system](https://docs.microsoft.com/outlook/add-ins/authentication).</span></span>

##### <a name="parameters"></a><span data-ttu-id="8702b-312">Parâmetros:</span><span class="sxs-lookup"><span data-stu-id="8702b-312">Parameters:</span></span>

|<span data-ttu-id="8702b-313">Name</span><span class="sxs-lookup"><span data-stu-id="8702b-313">Name</span></span>| <span data-ttu-id="8702b-314">Type</span><span class="sxs-lookup"><span data-stu-id="8702b-314">Type</span></span>| <span data-ttu-id="8702b-315">Attributes</span><span class="sxs-lookup"><span data-stu-id="8702b-315">Attributes</span></span>| <span data-ttu-id="8702b-316">Description</span><span class="sxs-lookup"><span data-stu-id="8702b-316">Description</span></span>|
|---|---|---|---|
|`callback`| <span data-ttu-id="8702b-317">função</span><span class="sxs-lookup"><span data-stu-id="8702b-317">function</span></span>||<span data-ttu-id="8702b-318">Quando o método for concluído, a função passada no parâmetro `callback` é chamada com um único parâmetro, `asyncResult`, que é um objeto [`AsyncResult`](/javascript/api/office/office.asyncresult).</span><span class="sxs-lookup"><span data-stu-id="8702b-318">When the method completes, the function passed in the `callback` parameter is called with a single parameter, `asyncResult`, which is an [`AsyncResult`](/javascript/api/office/office.asyncresult) object.</span></span><br/><br/><span data-ttu-id="8702b-319">O token é fornecido como uma sequência de caracteres na propriedade `asyncResult.value`.</span><span class="sxs-lookup"><span data-stu-id="8702b-319">The token is provided as a string in the `asyncResult.value` property.</span></span>|
|`userContext`| <span data-ttu-id="8702b-320">Objeto</span><span class="sxs-lookup"><span data-stu-id="8702b-320">Object</span></span>| <span data-ttu-id="8702b-321">&lt;opcional&gt;</span><span class="sxs-lookup"><span data-stu-id="8702b-321">&lt;optional&gt;</span></span>|<span data-ttu-id="8702b-322">Qualquer dado de estado que é passado para o método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="8702b-322">Any state data that is passed to the asynchronous method.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="8702b-323">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8702b-323">Requirements</span></span>

|<span data-ttu-id="8702b-324">Requisito</span><span class="sxs-lookup"><span data-stu-id="8702b-324">Requirement</span></span>| <span data-ttu-id="8702b-325">Valor</span><span class="sxs-lookup"><span data-stu-id="8702b-325">Value</span></span>|
|---|---|
|[<span data-ttu-id="8702b-326">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="8702b-326">Minimum mailbox requirement set version</span></span>](/javascript/office/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="8702b-327">1.0</span><span class="sxs-lookup"><span data-stu-id="8702b-327">1.0</span></span>|
|[<span data-ttu-id="8702b-328">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="8702b-328">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="8702b-329">ReadItem</span><span class="sxs-lookup"><span data-stu-id="8702b-329">ReadItem</span></span>|
|[<span data-ttu-id="8702b-330">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="8702b-330">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="8702b-331">Redigir ou ler</span><span class="sxs-lookup"><span data-stu-id="8702b-331">Compose or read</span></span>|

##### <a name="example"></a><span data-ttu-id="8702b-332">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8702b-332">Example</span></span>

```js
function getIdentityToken() {
  Office.context.mailbox.getUserIdentityTokenAsync(cb);
}

function cb(asyncResult) {
  var token = asyncResult.value;
}
```

####  <a name="makeewsrequestasyncdata-callback-usercontext"></a><span data-ttu-id="8702b-333">makeEwsRequestAsync(data, callback, [userContext])</span><span class="sxs-lookup"><span data-stu-id="8702b-333">makeEwsRequestAsync(data, callback, [userContext])</span></span>

<span data-ttu-id="8702b-334">Faz uma solicitação assíncrona em um serviço dos Serviços Web do Exchange (EWS) no Exchange Server que hospeda a caixa de correio do usuário.</span><span class="sxs-lookup"><span data-stu-id="8702b-334">Makes an asynchronous request to an Exchange Web Services (EWS) service on the Exchange server that hosts the user’s mailbox.</span></span>

> [!NOTE]
> <span data-ttu-id="8702b-335">Esse método não é suportado nos seguintes cenários.</span><span class="sxs-lookup"><span data-stu-id="8702b-335">This method is not supported in the following scenarios.</span></span>
> - <span data-ttu-id="8702b-336">No Outlook para iOS ou no Outlook para Android</span><span class="sxs-lookup"><span data-stu-id="8702b-336">In Outlook for iOS or Outlook for Android</span></span>
> - <span data-ttu-id="8702b-337">Quando o suplemento é carregado em uma caixa de correio do Gmail</span><span class="sxs-lookup"><span data-stu-id="8702b-337">When the add-in is loaded in a Gmail mailbox</span></span>
> 
> <span data-ttu-id="8702b-338">Nesses casos, os suplementos devem [usar APIs REST](https://docs.microsoft.com/outlook/add-ins/use-rest-api) para acessar a caixa de correio do usuário.</span><span class="sxs-lookup"><span data-stu-id="8702b-338">In these cases, add-ins should [use REST APIs](https://docs.microsoft.com/outlook/add-ins/use-rest-api) to access the user's mailbox instead.</span></span>

<span data-ttu-id="8702b-339">O método `makeEwsRequestAsync` envia uma solicitação do EWS em nome do suplemento ao Exchange.</span><span class="sxs-lookup"><span data-stu-id="8702b-339">The `makeEwsRequestAsync` method sends an EWS request on behalf of the add-in to Exchange.</span></span> <span data-ttu-id="8702b-340">Para obter uma lista de operações EWS compatíveis, consulte [Chamar serviços Web de um suplemento do Outlook](https://docs.microsoft.com/outlook/add-ins/web-services#ews-operations-that-add-ins-support) .</span><span class="sxs-lookup"><span data-stu-id="8702b-340">See [Call web services from an Outlook add-in](https://docs.microsoft.com/outlook/add-ins/web-services#ews-operations-that-add-ins-support) for a list of the supported EWS operations.</span></span>

<span data-ttu-id="8702b-341">Não é possível solicitar os itens associados da pasta com o método `makeEwsRequestAsync`.</span><span class="sxs-lookup"><span data-stu-id="8702b-341">You cannot request Folder Associated Items with the `makeEwsRequestAsync` method.</span></span>

<span data-ttu-id="8702b-342">A solicitação XML deve especificar a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="8702b-342">The XML request must specify UTF-8 encoding.</span></span>

```
<?xml version="1.0" encoding="utf-8"?>
```

<span data-ttu-id="8702b-p120">O suplemento deve ter a permissão **ReadWriteMailbox** para usar o método `makeEwsRequestAsync`. Para obter mais informações sobre como usar a permissão **ReadWriteMailbox** e as operações do EWS que você pode chamar com o método `makeEwsRequestAsync`, consulte [Especificar permissões para acesso do suplemento de email na caixa de correio do usuário](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions).</span><span class="sxs-lookup"><span data-stu-id="8702b-p120">Your add-in must have the **ReadWriteMailbox** permission to use the `makeEwsRequestAsync` method. For information about using the **ReadWriteMailbox** permission and the EWS operations that you can call with the `makeEwsRequestAsync` method, see [Specify permissions for mail add-in access to the user's mailbox](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions).</span></span>

> [!NOTE]
> <span data-ttu-id="8702b-345">O administrador do servidor deve definir `OAuthAuthentication` como true no diretório do EWS para o servidor de Acesso para Cliente, para que o método `makeEwsRequestAsync` possa realizar solicitações EWS.</span><span class="sxs-lookup"><span data-stu-id="8702b-345">NOTE: The server administrator must set `OAuthAuthentication` to true on the Client Access Server EWS directory to enable the `makeEwsRequestAsync` method to make EWS requests.</span></span>

##### <a name="version-differences"></a><span data-ttu-id="8702b-346">Diferenças de versão</span><span class="sxs-lookup"><span data-stu-id="8702b-346">Version differences</span></span>

<span data-ttu-id="8702b-347">Ao usar o método `makeEwsRequestAsync` nos aplicativos de email em execução em versões do Outlook anteriores à 15.0.4535.1004, é preciso definir o valor de codificação como `ISO-8859-1`.</span><span class="sxs-lookup"><span data-stu-id="8702b-347">When you use the `makeEwsRequestAsync` method in mail apps running in Outlook versions earlier than version 15.0.4535.1004, you should set the encoding value to `ISO-8859-1`.</span></span>

```
<?xml version="1.0" encoding="iso-8859-1"?>
```

<span data-ttu-id="8702b-p121">Não é necessário definir o valor de codificação quando o aplicativo de email estiver em execução no Outlook na Web. Você pode determinar se o aplicativo de email está em execução no Outlook ou no Outlook na Web usando a propriedade mailbox.diagnostics.hostName. Para determinar qual versão do Outlook está em execução, use a propriedade mailbox.diagnostics.hostVersion.</span><span class="sxs-lookup"><span data-stu-id="8702b-p121">You do not need to set the encoding value when your mail app is running in Outlook on the web. You can determine whether your mail app is running in Outlook or Outlook on the web by using the mailbox.diagnostics.hostName property. You can determine what version of Outlook is running by using the mailbox.diagnostics.hostVersion property.</span></span>

##### <a name="parameters"></a><span data-ttu-id="8702b-351">Parâmetros:</span><span class="sxs-lookup"><span data-stu-id="8702b-351">Parameters:</span></span>

|<span data-ttu-id="8702b-352">Name</span><span class="sxs-lookup"><span data-stu-id="8702b-352">Name</span></span>| <span data-ttu-id="8702b-353">Type</span><span class="sxs-lookup"><span data-stu-id="8702b-353">Type</span></span>| <span data-ttu-id="8702b-354">Attributes</span><span class="sxs-lookup"><span data-stu-id="8702b-354">Attributes</span></span>| <span data-ttu-id="8702b-355">Description</span><span class="sxs-lookup"><span data-stu-id="8702b-355">Description</span></span>|
|---|---|---|---|
|`data`| <span data-ttu-id="8702b-356">Sequência de caracteres</span><span class="sxs-lookup"><span data-stu-id="8702b-356">String</span></span>||<span data-ttu-id="8702b-357">A solicitação do EWS.</span><span class="sxs-lookup"><span data-stu-id="8702b-357">The EWS request.</span></span>|
|`callback`| <span data-ttu-id="8702b-358">função</span><span class="sxs-lookup"><span data-stu-id="8702b-358">function</span></span>||<span data-ttu-id="8702b-359">Quando o método for concluído, a função passada no parâmetro `callback` é chamada com um único parâmetro, `asyncResult`, que é um objeto [`AsyncResult`](/javascript/api/office/office.asyncresult).</span><span class="sxs-lookup"><span data-stu-id="8702b-359">When the method completes, the function passed in the `callback` parameter is called with a single parameter, `asyncResult`, which is an [`AsyncResult`](/javascript/api/office/office.asyncresult) object.</span></span><br/><br/><span data-ttu-id="8702b-360">O resultado XML da chamada do EWS é fornecido como uma sequência de caracteres na propriedade `asyncResult.value`.</span><span class="sxs-lookup"><span data-stu-id="8702b-360">The XML result of the EWS call is provided as a string in the `asyncResult.value` property.</span></span> <span data-ttu-id="8702b-361">Se o resultado exceder 1 MB, será exibida uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="8702b-361">If the result exceeds 1 MB in size, an error message is returned instead.| | Object| optional|Any state data that is passed to the asynchronous method.|</span></span>|
|`userContext`| <span data-ttu-id="8702b-362">Objeto</span><span class="sxs-lookup"><span data-stu-id="8702b-362">Object</span></span>| <span data-ttu-id="8702b-363">&lt;opcional&gt;</span><span class="sxs-lookup"><span data-stu-id="8702b-363">&lt;optional&gt;</span></span>|<span data-ttu-id="8702b-364">Qualquer dado de estado que é passado para o método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="8702b-364">Any state data that is passed to the asynchronous method.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="8702b-365">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8702b-365">Requirements</span></span>

|<span data-ttu-id="8702b-366">Requisito</span><span class="sxs-lookup"><span data-stu-id="8702b-366">Requirement</span></span>| <span data-ttu-id="8702b-367">Valor</span><span class="sxs-lookup"><span data-stu-id="8702b-367">Value</span></span>|
|---|---|
|[<span data-ttu-id="8702b-368">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="8702b-368">Minimum mailbox requirement set version</span></span>](/javascript/office/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="8702b-369">1.0</span><span class="sxs-lookup"><span data-stu-id="8702b-369">1.0</span></span>|
|[<span data-ttu-id="8702b-370">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="8702b-370">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="8702b-371">ReadWriteMailbox</span><span class="sxs-lookup"><span data-stu-id="8702b-371">ReadWriteMailbox</span></span>|
|[<span data-ttu-id="8702b-372">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="8702b-372">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="8702b-373">Redigir ou ler</span><span class="sxs-lookup"><span data-stu-id="8702b-373">Compose or read</span></span>|

##### <a name="example"></a><span data-ttu-id="8702b-374">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8702b-374">Example</span></span>

<span data-ttu-id="8702b-375">O exemplo a seguir chama `makeEwsRequestAsync` para usar a operação `GetItem` para obter o assunto de um item.</span><span class="sxs-lookup"><span data-stu-id="8702b-375">The following example calls `makeEwsRequestAsync` to use the `GetItem` operation to get the subject of an item.</span></span>

```js
function getSubjectRequest(id) {
   // Return a GetItem operation request for the subject of the specified item.
   var request =
    '<?xml version="1.0" encoding="utf-8"?>' +
    '<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"' +
    '               xmlns:xsd="http://www.w3.org/2001/XMLSchema"' +
    '               xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"' +
    '               xmlns:t="http://schemas.microsoft.com/exchange/services/2006/types">' +
    '  <soap:Header>' +
    '    <RequestServerVersion Version="Exchange2013" xmlns="http://schemas.microsoft.com/exchange/services/2006/types" soap:mustUnderstand="0" />' +
    '  </soap:Header>' +
    '  <soap:Body>' +
    '    <GetItem xmlns="http://schemas.microsoft.com/exchange/services/2006/messages">' +
    '      <ItemShape>' +
    '        <t:BaseShape>IdOnly</t:BaseShape>' +
    '        <t:AdditionalProperties>' +
    '            <t:FieldURI FieldURI="item:Subject"/>' +
    '        </t:AdditionalProperties>' +
    '      </ItemShape>' +
    '      <ItemIds><t:ItemId Id="' + id + '"/></ItemIds>' +
    '    </GetItem>' +
    '  </soap:Body>' +
    '</soap:Envelope>';

   return request;
}

function sendRequest() {
   // Create a local variable that contains the mailbox.
   Office.context.mailbox.makeEwsRequestAsync(
    getSubjectRequest(mailbox.item.itemId), callback);
}

function callback(asyncResult)  {
   var result = asyncResult.value;
   var context = asyncResult.asyncContext;

   // Process the returned response here.
}
```