---
title: 如何設定 Wcf-custom 接收位置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e2092cd4-6612-4ac3-81f3-dd25438837ae
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9c46434f22fe94ce046b7e7caf855d7f7a3eed4
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "25975788"
---
# <a name="how-to-configure-a-wcf-custom-receive-location"></a>如何設定 WCF-Custom 接收位置
您可以用程式設計方式或使用 BizTalk 管理主控台來設定 WCF-Custom 接收位置。  
  
## <a name="configuration-properties"></a>組態屬性
  
 「BizTalk 總管物件模型」可讓您以程式設計的方式建立和設定接收位置。 BizTalk 總管物件模型會公開**IReceiveLocation** 接收位置組態介面具有 **TransportTypeData** 讀/寫屬性。 這個屬性會以 XML 字串之成對的名稱-數值格式接受 WCF-Custom 接收位置組態屬性包。 若要設定這個屬性在 BizTalk 總管物件模型，您必須設定 **InboundTransportLocation** 屬性 **IReceiveLocation** 介面。  
  
 **TransportTypeData** 屬性 **IReceiveLocation** 介面並沒有設定。 若沒有設定此屬性，WCF-Custom 配接器就會針對 WCF-Custom 接收位置組態使用預設值，如下表所示。  
  
 下表列出您可在「BizTalk 總管物件模型」中，針對 WCF-Custom 接收位置設定的組態屬性。  
  
|屬性名稱|유형|Description|  
|-------------------|----------|-----------------|  
|**身分識別**|XML BLOB<br /><br /> 範例：<br /><br /> &lt;身分識別&gt;<br /><br /> &lt;userPrincipalName value="username@contoso.com" /&gt;<br /><br /> &lt;/identity&gt;|指定此接收位置所提供服務的識別。 您可以指定的值 **識別** 屬性，則根據安全性組態而有所不同。 這些設定可讓用戶端驗證此接收位置。 在用戶端與服務之間的交握程序中，Windows Communication Foundation (WCF) 基礎結構可確保預期之服務的識別能夠與這個項目的值相符。<br /><br /> 預設為空字串。|  
|**BindingType**|Enum<br /><br /> -   **basicHttpBinding**<br />-   **customBinding**<br />-   **mexHttpBinding**<br />-   **mexHttpsBinding**<br />-   **mexNamedPipeBinding**<br />-   **mexTcpBinding**<br />-   **netMsmqBinding**<br />-   **netNamedPipeBinding**<br />-   **netPeerTcpBinding**<br />-   **netTcpBinding**<br />-   **wsDualHttpBinding**<br />-   **wsFederationHttpBinding**<br />-   **wsHttpBinding**|指定此接收位置所用之端點要使用的繫結類型。 **注意︰**  如果您使用自訂繫結， **BindingType** 屬性可以使用自訂繫結來設定。 如需如何使用自訂繫結的詳細資訊，請參閱[如何啟用 WCF 擴充性點，WCF 配接器](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md)。 <br /><br /> 預設為空字串。|  
|**BindingConfiguration**|XML BLOB<br /><br /> 範例：<br /><br /> &lt;繫結名稱 ="p"&gt;&lt;安全性模式 ="None"/&gt;&lt;繫結&gt;|指定的 XML 字串**\<繫結\>** 項目來設定不同類型的預先定義 Windows Communication Foundation (WCF) 所提供的繫結。 如需有關系統提供之繫結與自訂繫結的詳細資訊，請參考「請參閱」一節中的適當主題。 **注意︰**  BizTalk Server 不支援所有類型的繫結延伸項目，您可以使用設定 **BindingConfiguration** 屬性。 <br /><br /> 預設為空字串。|  
|**ServiceBehaviorConfiguration**|XML BLOB<br /><br /> 範例：<br /><br /> &lt;行為名稱 ="SampleServiceBehavior"&gt;&lt;serviceMetadata httpGetEnabled ="true"httpGetUrl ="http://mycomputer:9995/SampleMex"/&gt;&lt;serviceCredentials /&gt;&lt;/behavior&gt;|指定的 XML 字串**\<行為\>** 元素**\<serviceBehaviors\>** 設定 WCF 行為設定的項目服務。 如需有關**\<serviceBehaviors\>** 項目，請參閱 < 另請參閱中的適當主題。<br /><br /> 預設為空字串。|  
|**EndpointBehaviorConfiguration**|XML BLOB<br /><br /> 範例：<br /><br /> &lt;行為名稱 ="sampleBehavior"&gt;&lt;callbackTimeouts /&gt;&lt;/behavior&gt;|指定的 XML 字串**\<行為\>** 元素**\<endpointBehaviors\>** 項目來設定的行為設定WCF 端點。 如需有關**\<endpointBehaviors\>** 項目，請參閱 < 另請參閱中的適當主題。 **注意︰**  BizTalk Server 不支援所有類型的行為延伸模組項目，您可以使用設定 **EndpointBehaviorConfiguration** 屬性。 <br /><br /> 預設為空字串。|  
|**CredentialType**|Enum<br /><br /> -   **無**： 不要的使用任何認證，當這個接收位置傳送請求訊息以輪詢外部服務，或這個接收位置不需要輪詢任何外部服務。<br />-   **IssueTicket**︰ 使用企業單一登入 (SSO) 來擷取用戶端認證，以發出 SSO 票證。 這個選項需要使用安全性模式，以允許這個接收位置模擬使用者帳戶來發出 SSO 票證。<br />-   **UserAccount**︰ 使用中指定的認證 **Username** 和 **密碼** 屬性時，這個接收位置傳送請求訊息以輪詢外部服務。<br />-   **GetCredentials**︰ 使用 SSO 分支機構應用程式中指定 **AffiliateApplicationName** 屬性時，此接收位置傳送請求訊息以輪詢外部服務。|指定接收位置在輪詢外部服務時要使用的認證類型。<br /><br /> 預設值︰ **無**|  
|**使用者名稱**|字串|指定在輪詢外部服務以擷取回應訊息時，要針對這個接收位置所使用的使用者名稱。 這個屬性時，需要 **CredentialType** 屬性設定為 **UserAccount**。<br /><br /> 預設為空字串。|  
|**密碼**|字串|指定在輪詢外部服務以擷取回應訊息時，要針對這個接收位置所使用的密碼。 這個屬性時，需要 **CredentialType** 屬性設定為 **UserAccount**。<br /><br /> 預設為空字串。|  
|**AffiliateApplicationName**|字串|當這個接收位置傳送請求訊息以輪詢外部服務時，指定 SSO 分支機構應用程式以傳回要使用的外部認證。 指定的 SSO 分支機構應用程式在其下執行這個接收位置的 Windows 帳戶以及外部服務的帳戶之間，必須具有對應。 這個屬性時，需要 **CredentialType** 屬性設定為 **GetCredentials**。<br /><br /> 預設為空字串。|  
|**OrderedProcessing**|Boolean|指定在處理訊息 (配合 NetMsmq 繫結使用) 時，是否保存訊息順序。<br /><br /> 預設值︰ **False**|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -使用內容的 SOAP**主體**內送訊息建立 BizTalk 訊息內文部分的項目。 如果 **Body** 元素有一個以上的子元素，則只有第一個元素會成為 BizTalk 訊息內文部分。<br />-   **UseEnvelope** -從整個 SOAP 建立 BizTalk 訊息內文部分 **信封** 內送訊息。<br />-   **UseBodyPath** -使用中的內文路徑運算式 **InboundBodyPathExpression** 屬性來建立 BizTalk 訊息內文部分。 內文路徑運算式會依照內送訊息 SOAP **Body** 元素的直系子元素來進行評估。 此屬性只對請求-回應連接埠有效。<br /><br /> 如需有關如何使用**InboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定資料選取範圍 soap **主體** 內送 WCF 訊息的項目。<br /><br /> 預設值︰ **UseBodyElement**|  
|**InboundBodyPathExpression**|字串<br /><br /> 如需有關如何使用**InboundBodyPathExpression**屬性，請參閱[WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)。|指定內文路徑運算式來識別用於建立 BizTalk 訊息內文部分之內送訊息的特定部分。 此內文路徑運算式評估的 soap 的直系子項目 **主體** 內送訊息的節點。 如果此內文路徑運算式傳回一個以上的節點，則只會為 BizTalk 訊息內文部分選擇第一個節點。 如果這個屬性，則需要 **InboundBodyLocation** 屬性設定為 **UseBodyPath**。<br /><br /> 預設為空字串。|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** -Base64 編碼方式。<br />-   **Hex** ︰ 十六進位編碼方式。<br />-   **字串** ︰ 文字編碼-utf-8。<br />-   **XML** -WCF 配接器建立 BizTalk 訊息內文中的內文路徑運算式所選取之節點外部 xml **InboundBodyPathExpression**。|指定的編碼，則 WCF 自訂接收配接器，用來解碼中指定的內文路徑運算式所識別的節點類型 **InboundBodyPathExpression**。 如果這個屬性，則需要 **InboundBodyLocation** 屬性設定為 **UseBodyPath**。<br /><br /> 預設值︰ **XML**|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -使用 BizTalk 訊息內文部分建立的 soap 內容**主體**外寄回應訊息的項目。<br />-   **UseTemplate** -使用中提供的範本 **OutboundXMLTemplate** 屬性來建立的內容的 soap **主體** 外寄回應訊息的項目。<br /><br /> 如需有關如何使用**OutboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定資料選取範圍 soap **主體** 外寄 WCF 訊息的項目。 此屬性只適用於要求-回應接收位置。<br /><br /> 預設值︰ **UseBodyElement**|  
|**OutboundXMLTemplate**|字串<br /><br /> 如需有關如何使用**OutboundXMLTemplate**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定 XML 格式的範本內容的 SOAP **主體** 外寄回應訊息的項目。 如果這個屬性，則需要 **OutboundBodyLocation** 屬性設定為 **UseTemplate**。 此屬性只適用於要求-回應接收位置。<br /><br /> 預設為空字串。|  
|**DisableLocationOnFailure**|Boolean|指定是否停用由於接收管線失敗或路由失敗造成輸入處理失敗的接收位置。<br /><br /> 預設值︰ **False**|  
|**SuspendMessageOnFailure**|Boolean|指定是否擱置因接收管線失敗或路由失敗而造成輸入處理失敗的要求訊息。<br /><br /> 預設值︰ **，則為 True**|  
|**IncludeExceptionDetailInFaults**|Boolean|指定基於偵錯目的傳回用戶端的 SOAP 錯誤詳細資料中，是否包括 Managed 例外狀況資訊。<br /><br /> 預設值︰ **False**|  
|**ReferencedBindings**|XML BLOB<br /><br /> 範例：<br /><br /> \<**BindingConfiguration** vt="8"\><br /><br /> &lt;wsFederationHttpBinding&gt;<br /><br /> &lt;繫結名稱 ="sampleBinding"&gt;<br /><br /> &lt;安全性模式 = [訊息]&gt;<br /><br /> &lt;訊息 issuedKeyType ="AsymmetricKey"&gt;<br /><br /> &lt;issuer address="http://www.contoso.com/samplests" binding="wsFederationHttpBinding" bindingConfiguration="**contosoSTSBinding**"/&gt;<br /><br /> &lt;/message&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/ 繫結&gt;<br /><br /> &lt;/wsFederationHttpBinding&gt;<br /><br /> \</**BindingConfiguration**\><br /><br /> \<**ReferencedBindings** vt="8"\><br /><br /> &lt;繫結&gt;<br /><br /> &lt;wsFederationHttpBinding&gt;<br /><br /> &lt;繫結名稱 ="**contosoSTSBinding**」&gt;<br /><br /> &lt;安全性模式 = [訊息]&gt;<br /><br /> &lt;訊息 negotiateServiceCredential ="false"&gt;<br /><br /> &lt;issuer address="http://northwind.com/samplests" bindingConfiguration="**northwindBinding**" binding="wsHttpBinding"&gt;<br /><br /> &lt;/issuer&gt;<br /><br /> &lt;/message&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/ 繫結&gt;<br /><br /> &lt;/wsFederationHttpBinding&gt;<br /><br /> &lt;wsHttpBinding&gt;<br /><br /> &lt;繫結名稱 ="**northwindBinding**」&gt;<br /><br /> &lt;安全性模式 = [訊息]&gt;<br /><br /> &lt;訊息 clientCredentialType ="Certificate"/&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/ 繫結&gt;<br /><br /> &lt;/wsHttpBinding&gt;<br /><br /> &lt;/bindings&gt;<br /><br /> \</**ReferencedBindings** \> **附註：** **ReferencedBinding**屬性不能包含中使用的繫結組態**BindingConfiguration**屬性。|指定所參考的繫結組態**bindingConfiguration**屬性**\<簽發者\>** 元素**wsFederationHttpBinding**和**customBinding**，表示安全性權杖服務 (STS) 發行安全性權杖。 如需詳細資訊**\<簽發者\>** 項目，請參閱主題 <"\<簽發者\>」 在[ http://go.microsoft.com/fwlink/?LinkId=83476 ](http://go.microsoft.com/fwlink/?LinkId=83476)。<br /><br /> 繫結資訊，包括**\<簽發者\>** 元素**wsFederationHttpBinding**和**customBinding**可以是透過設定**BindingConfiguration** Wcf-custom 和 Wcf-customisolated 配接器的屬性。 所有參考繫結組態，這個屬性必須放置在表單的[\<繫結\>](http://go.microsoft.com/fwlink/?LinkID=80878)項目。 **注意︰**  無法設定此屬性 **繫結** 傳輸屬性 對話方塊中的索引標籤。 您可以匯入和匯出此屬性透過 **匯入/匯出** Wcf-custom 和 Wcf-customisolated 配接器傳輸屬性對話方塊中的索引標籤。 **注意：** **bindingConfiguration**屬性**\<簽發者\>** 元素必須參考這個屬性中的有效繫結名稱。 **注意：** **\<簽發者\>** 中參考繫結組態項目也可以參考不同的繫結組態中使用該屬性如果這個參考鏈結不會產生循環相依性。 <br /><br /> 預設為空字串。|  
  
## <a name="configure-a-wcf-custom-receive-location-with-the-biztalk-administration-console"></a>設定 WCF 自訂接收位置使用 BizTalk 管理主控台
  
 您可以在 [BizTalk Server 管理] 主控台中設定 WCF-Custom 接收位置配接器變數。 若接收位置並未設定屬性，系統就會使用 [BizTalk 管理主控台] 中的預設接收處理常式值。  
  
> [!NOTE]
>  完成下列程序之前，您必須已經新增接收埠。 如需詳細資訊，請參閱[如何建立接收埠](../core/how-to-create-a-receive-port.md)。  
  
## <a name="configure-variables-for-a-wcf-custom-receive-location"></a>設定 Wcf-custom 接收位置的變數  
  
1.  如果設定 WCF-Custom 配接器時，您打算使用自訂繫結元素、自訂行為項目和自訂通道元件這類 WCF 擴充性點，必須將實作擴充性點和所有相依組件的組件，同時加入至 BizTalk 處理電腦 (執行階段電腦) 和管理電腦上的全域組件快取。 此外，您必須在 machine.config 檔案註冊延伸模組元件。 如需如何搭配 WCF 自訂配接器使用 WCF 擴充性點的詳細資訊，請參閱[如何啟用 WCF 擴充性點，WCF 配接器](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md)。  
  
2.  在 BizTalk 管理主控台中，展開  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開您要建立接收位置的應用程式。  
  
3.  在 [BizTalk 管理主控台] 的左窗格中，按一下 **[接收埠]** 節點。 然後在右窗格中，使用滑鼠右鍵按一下與現有接收位置關聯的接收埠，或是您要與新接收位置關聯的接收埠，然後按一下 **[屬性]**。  
  
4.  在 **接收埠屬性** 對話方塊的左窗格中，選取 **接收位置**, ，然後在右窗格中，按兩下現有接收位置或按一下 **新增**來建立新的接收位置。  
  
5.  在 **接收位置屬性** 對話方塊中，於 **傳輸** 區段旁邊 **類型**, ，請選取 **WCF 自訂** 從下拉式清單，然後按一下  **設定**。  
  
6.  在 **Wcf-custom 傳輸屬性** 對話方塊的 [ **一般** ] 索引標籤上，設定端點位址和服務識別的 WCF 自訂接收位置。 如需有關**一般**索引標籤中**Wcf-custom 傳輸屬性**對話方塊中，請參閱**Wcf-custom 傳輸屬性對話方塊、 接收、 一般** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
7.  在 **Wcf-custom 傳輸屬性** 對話方塊的  **繫結** 索引標籤上，設定不同類型的 WCF 預先定義或自訂繫結。 如需有關**繫結**索引標籤中**Wcf-custom 傳輸屬性**對話方塊中，請參閱**Wcf-custom 傳輸屬性對話方塊、 接收、 繫結** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
8.  在 **Wcf-custom 傳輸屬性** 對話方塊的 [ **行為** ] 索引標籤上，設定端點和服務行為，這個接收位置。 結束點行為是一組行為延伸模組項目，可修改或延伸服務或是用戶端功能。 如需有關**行為**索引標籤中**Wcf-custom 傳輸屬性**對話方塊中，請參閱**Wcf-custom 傳輸屬性對話方塊、 接收、 行為** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
9. 在 **Wcf-custom 傳輸屬性** 對話方塊的  **其他** 索引標籤上，此接收位置時輪詢外部服務，要使用與此接收位置是否保存訊息順序處理訊息時設定的認證。 如需有關**其他**索引標籤中**Wcf-custom 傳輸屬性**對話方塊中，請參閱**Wcf-custom 傳輸屬性對話方塊、 接收、 其他**索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
10. 在 **Wcf-custom 傳輸屬性** 對話方塊的  **訊息** 索引標籤上，指定資料選取範圍 soap **主體** 項目。 如需有關**訊息**索引標籤中**Wcf-custom 傳輸屬性**對話方塊中，請參閱**Wcf-custom 傳輸屬性對話方塊、 接收、 訊息** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
11. 在 **Wcf-custom 傳輸屬性** 對話方塊的  **匯入/匯出**  索引標籤上，匯入和匯出 **位址 (URI)** 和 **端點身分識別** 屬性 **一般**  索引標籤上的繫結資訊 **繫結**  索引標籤，以及端點行為 **行為**  索引標籤，此接收位置。 如需有關**匯入/匯出**索引標籤中**Wcf-custom 傳輸屬性**對話方塊中，請參閱**Wcf-custom 傳輸屬性對話方塊、 接收、 匯入匯出**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  

## <a name="configure-a-wcf-custom-receive-location-programmatically"></a>以程式設計方式設定 Wcf-custom 接收位置
  
 您可以使用下列格式來設定屬性：  
  
```  
<CustomProps>  
  <InboundBodyPathExpression vt="8" />  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <BindingConfiguration vt="8"><binding name="netNamedPipeBinding"><security mode="None" /></binding></BindingConfiguration>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <CredentialType vt="8">GetCredentials</CredentialType>  
  <Identity vt="8" />  
  <ServiceBehaviorConfiguration vt="8"><behavior name="SampleServiceBehavior"><serviceMetadata httpGetEnabled="true" httpGetUrl="http://mycomputer:9995/SampleService/Mex" /><serviceCredentials /></behavior></ServiceBehaviorConfiguration>  
  <Password vt="1" />  
  <OrderedProcessing vt="11">-1</OrderedProcessing>  
  <IncludeExceptionDetailInFaults vt="11">0</IncludeExceptionDetailInFaults>  
  <AffiliateApplicationName vt="8">SampleAffiliateApplication</AffiliateApplicationName>  
  <DisableLocationOnFailure vt="11">0</DisableLocationOnFailure>  
  <SuspendMessageOnFailure vt="11">0</SuspendMessageOnFailure>  
  <BindingType vt="8">netNamedPipeBinding</BindingType>  
  <UserName vt="8">Hello</UserName>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <EndpointBehaviorConfiguration vt="8"><behavior name="EndpointBehavior" /></EndpointBehaviorConfiguration>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```  
  
 下列程式碼片段會示範如何建立 WCF-Custom 接收位置：  
  
```  
// Use BizTalk Explorer object model to create new WCF-Custom receive location   
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
string transportConfigData = @"<CustomProps>  
  <BindingConfiguration vt=""8""><binding name=""netNamedPipeBinding""><security mode=""None"" /></binding></BindingConfiguration>  
  <BindingType vt=""8"">netNamedPipeBinding</BindingType>  
</CustomProps>";  
//requires project reference to \Program Files\Microsoft BizTalk Server 2009\Developer Tools\Microsoft.BizTalk.ExplorerOM.dll  
BtsCatalogExplorer explorer = new Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer();  
explorer.ConnectionString = connectionString;  
// Add a new BizTalk application  
Application application = explorer.AddNewApplication();  
application.Name = "SampleBizTalkApplication";  
// Save  
explorer.SaveChanges();  
  
// Add a new one-way receive port  
IReceivePort receivePort = application.AddNewReceivePort(false);  
receivePort.Name = "SampleReceivePort";  
// Add a new one-way receive location  
IReceiveLocation recieveLocation = receivePort.AddNewReceiveLocation();  
recieveLocation.Name = "SampleReceiveLocation";  
// Find a receive handler for WCF-Custom   
int i = 0;  
for(i=0; i < explorer.ReceiveHandlers.Count; ++i)   
{  
    if("WCF-Custom" == explorer.ReceiveHandlers[i].TransportType.Name)  
        break;  
}  
recieveLocation.ReceiveHandler = explorer.ReceiveHandlers[i];  
recieveLocation.Address = "net.pipe://mycomputer/samplePipeName";  
recieveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];  
recieveLocation.TransportType = explorer.ProtocolTypes["WCF-Custom"];  
recieveLocation.TransportTypeData = transportConfigData;  
// Save  
explorer.SaveChanges();   
```  
  
## <a name="see-also"></a>另請參閱  
 [發行服務中繼資料之 wcf 接收配接器](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)   
 [管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)   
 [如何變更服務帳戶和密碼](../core/how-to-change-service-accounts-and-passwords.md)   
 [WCF 配接器安裝憑證](../core/installing-certificates-for-the-wcf-adapters.md)   
 [指定訊息本文為 WCF 配接器](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [設定 WCF 自訂配接器](../core/configuring-the-wcf-custom-adapter.md)   
 [如何建立分支機構應用程式](../core/how-to-create-an-affiliate-application.md)   
 [\<行為\>的\<endpointBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=80879)   
 [\<bindings\>](http://go.microsoft.com/fwlink/?LinkId=80878)   
 [\<行為\>的\<serviceBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=81095)