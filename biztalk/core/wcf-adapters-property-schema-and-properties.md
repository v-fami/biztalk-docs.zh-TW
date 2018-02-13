---
title: "WCF 配接器屬性結構描述和屬性 |Microsoft 文件"
ms.custom: 
ms.date: 02/09/2018
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2093745e-86c0-4276-a7cc-a0187391ca4a
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04bb48f54347eabeb886d91fa245bae18c34de55
ms.sourcegitcommit: 50798e04fdcaf5dce5288aa18608e2a981b162fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2018
---
# <a name="wcf-adapters-property-schema-and-properties"></a>WCF 配接器屬性結構描述和屬性
閱讀有關 WCF 配接器屬性結構描述中的升級屬性。 WCF 配接器會為您可以在應用程式中使用的屬性指派值。 WCF 配接器也提供了一種將自訂屬性寫入但不升級至 BizTalk 訊息內容的機制，以及一種將自訂屬性升級至 BizTalk 訊息內容的機制。 如需詳細資訊，請參閱[SOAP 標頭與已發佈 WCF 服務](../core/soap-headers-with-published-wcf-services.md)。  

## <a name="promoted-properties"></a>升級屬性  
**命名空間︰** http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties  

#### <a name="action"></a>動作
指定 **SOAPAction** 外寄訊息的標頭欄位。 您可以將這個值指定兩個不同的方式︰ 單一動作格式和動作對應格式。 如果您在單一動作格式中設定這個屬性 — 例如，http://contoso.com/Svc/Op1 — **SOAPAction**標頭外寄訊息一定會設定這個屬性中指定的值。

如果您設定此屬性以動作對應格式傳出 **SOAPAction** 標頭由 **BTS。作業** 內容屬性。 例如，如果此屬性設定為下列 XML 格式和**BTS。作業**屬性設定為 Op1，WCF 傳送配接器會使用`http://contoso.com/Svc/Op1`針對外寄**SOAPAction**標頭。

```
<BtsActionMapping>
<Operation Name="Op1" Action="http://contoso.com/Svc/Op1">
<Operation Name="Op2" Action="http://contoso.com/Svc/Op2">
</BtsActionMapping>
```

協調流程執行個體如果外寄訊息是來自協調流程連接埠，以動態方式設定 **BTS。作業** 與連接埠的作業名稱的屬性。 如果外寄訊息會路由傳送，以內容為基礎的路由，您可以設定 **BTS。作業** 管線元件中的屬性。
這個屬性會以單一動作格式自動從內送訊息升級。

유형: 문자열  
預設值： 空字串  
適用於： 所有 WCF 都傳送配接器

#### <a name="affiliateapplicationname"></a>AffiliateApplicationName
指定要針對企業單一登入 (SSO) 使用的分支機構應用程式。 如果這個屬性，則需要 **UseSSO** 屬性設定為 **True**。 

유형: 문자열  
預設值： 空字串  
適用於： 所有 WCF 都傳送配接器*除了*Wcf-netnamedpipe 配接器

#### <a name="algorithmsuite"></a>AlgorithmSuite
指定訊息加密和 Key Wrap 演算法。 這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。

如需有關適用值**AlgorithmSuite**屬性，請參閱**演算法套件**屬性**Wcf-nettcp 傳輸屬性對話方塊、 傳送、安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。

유형: 문자열  
預設值︰ **Basic256**  
適用於： 

- WCF-BasicHttp 配接器
- WCF-NetMsmq 配接器
- WCF-NetTcp 配接器
- WCF-WSHttp 配接器

#### <a name="bindingconfiguration"></a>BindingConfiguration
指定的 XML 字串**\<繫結\>**項目來設定不同類型的預先定義 Windows Communication Foundation (WCF) 所提供的繫結。 如需有關系統提供之繫結與自訂繫結的詳細資訊，請參考「請參閱」一節中的適當主題。

範例：

```
<binding name="wsHttpBinding" transactionFlow="true">
<security><message clientCredentialType="UserName"></security>
</binding>
```

유형: 문자열  
預設值： 空字串  
適用於： Wcf-custom 配接器，Wcf-customisolated 配接器

#### <a name="bindingtype"></a>BindingType
指定要用於端點的繫結類型。 如需有關適用值**BindingType**屬性，請參閱**繫結的型別**屬性**Wcf-custom 傳輸屬性對話方塊、 傳送、 繫結**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。

유형: 문자열  
預設值： 空字串  
適用於： Wcf-custom 配接器，Wcf-customisolated 配接器

#### <a name="clientcertificate"></a>ClientCertificate
指定 X.509 憑證的憑證指紋，以便向服務驗證此傳送埠。 如果這個屬性，則需要 **ClientCredentialsType** 屬性設定為 **憑證**。 要用於此屬性的憑證必須安裝到 **我** 存放 **目前使用者** 位置。

유형: 문자열  
預設值： 空字串  
適用於： 

- WCF-BasicHttp 傳送配接器
- WCF-WSHttp 傳送配接器
- WCF-NetTcp 傳送配接器
- WCF-NetMsmq 傳送配接器

#### <a name="closetimeout"></a>CloseTimeout
指定時間值，表示可供完成通道關閉作業的時間間隔。

유형: 문자열  
預設值：00:01:00  
適用於： 所有 WCF 配接器*除了*Wcf-custom 和 Wcf-customisolated

#### <a name="customdeadletterqueue"></a>CustomDeadLetterQueue
指定完整格式的 URI，連同 **net.msmq** 配置位置的每個應用程式寄不出信件佇列，已過期、 無法傳輸或傳遞的郵件放置的位置。 例如，net.msmq://localhost/deadLetterQueueName。 無法寄出的信件佇列是傳送端應用程式之佇列管理員上的佇列，適用於傳遞失敗的過期訊息。 如果這個屬性，則需要 **DeadLetterQueue** 屬性設定為 **自訂**。

유형: 문자열  
預設值： 空字串  
適用於： Wcf-netmsmq 傳送配接器

#### <a name="deadletterqueue"></a>DeadLetterQueue
指定無法傳遞到應用程式的訊息將會傳輸到的無效信件佇列。 如需有關訊息傳遞至寄不出信件佇列的詳細資訊，請參閱**Wcf-netmsmq 傳輸屬性對話方塊、 傳送、 繫結** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。

유형: 문자열  
預設值︰ **系統**  
適用於： Wcf-netmsmq 傳送配接器

#### <a name="disablelocationonfailure"></a>DisableLocationOnFailure
指定是否停用由於接收管線失敗或路由失敗造成輸入處理失敗的接收位置。 您可能想要將此屬性設定為 **True** 當接收位置可以停用和拒絕服務 (DoS) 不是問題。

例如：  
- Wcf-custom 配接器： 當**BindingType**屬性設定為**netMsmqBinding**。
- Wcf-custom 配接器： 當**BindingType**屬性設定為**customBinding**，而**BindingConfiguration**屬性設定為使用依賴的自訂通道在已佇列之 MSMQ 等傳輸。
- Wcf-customisolated 配接器： 當**BindingType**屬性設定為**customBinding**，而**BindingConfiguration**屬性設定為使用自訂的通道依賴例如 MSMQ 佇列傳輸
- WCF-NetMsmq 配接器

類型：Boolean  
預設值︰ **False**  
適用於：  
- WCF-NetMsmq 接收配接器
- WCF-Custom 接收配接器
- WCF-CustomIsolated 接收配接器

#### <a name="enabletransaction"></a>EnableTransaction
這個屬性的效果會隨著 WCF 配接器而改變。 如需此屬性的詳細資訊，請參閱 < how to 主題中的每個 WCF 配接器[WCF 配接器](../core/wcf-adapters.md)。

類型：Boolean  
適用於： 

- WCF-WSHttp 配接器
- WCF-NetTcp 配接器
- WCF-NetNamedPipe 配接器
- WCF-NetMsmq 配接器

#### <a name="endpointbehaviorconfiguration"></a>EndpointBehaviorConfiguration
指定的 XML 字串**\<行為\>**元素 **\<endpointBehaviors\>** 項目來設定的行為設定WCF 端點。 如需有關 **\<endpointBehaviors\>** 項目，請參閱 < 另請參閱中的適當主題。

範例： 
```
<behavior name="sampleBehavior"><callbackTimeouts/></behavior>
```

유형: 문자열  
預設值： 空字串  
適用於： Wcf-custom 傳送配接器

#### <a name="establishsecuritycontext"></a>EstablishSecurityContext
指定此安全性通道是否會建立安全的工作階段。 安全的工作階段會在交換應用程式訊息之前，先建立安全性內容語彙基元 (SCT)。

類型：Boolean  
預設值：True  
套用至： Wcf-wshttp 配接器

#### <a name="fromaddress"></a>FromAddress
指定用來傳送內送 WCF 訊息的來源端點位址。 此屬性會自動從內送訊息升級。

유형: 문자열  
適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 傳送配接器
  
#### <a name="headers"></a>標頭
指定用來提供 URI 之外其他定址資訊的端點參考。 使用這個屬性時，這個屬性必須具有\<**標頭**\>元素是根項目。 所有位址標頭必須置於\<**標頭**\>項目。 內送訊息的這個屬性會自動升級。

範例：
```
<headers>
<Region xmlns="Uri">"String"</Region>
<Member xmlns="Uri">"String"</Member> 
</headers>
```

유형: 문자열  
適用於： 所有 WCF 配接器
  
#### <a name="identity"></a>識別
指定接收位置或傳送埠所預期之服務的識別。 您可以指定的值 **識別** 屬性，則根據安全性組態而有所不同。 這些設定可讓用戶端驗證服務。 在用戶端與服務之間的交握程序中，Windows Communication Foundation (WCF) 基礎結構可確保服務的識別能夠與用戶端的值相符。

範例：
```
<identity>
<userPrincipalName value="username@contoso.com"/>
</identity>
```

유형: 문자열  
預設值： 空字串  
適用於： 所有 WCF 配接器

#### <a name="inboundbodylocation"></a>InboundBodyLocation
指定資料選取範圍 soap **主體** 內送 WCF 訊息的項目。 如需有關如何使用**InboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。

유형: 문자열  
預設值： UseBodyElement  

    Applicable values are:  
        - UseBodyElement: Use the content of the SOAP **Body** element of an incoming message to create the BizTalk message body part. If the **Body** element has more than one child element, only the first element becomes the BizTalk message body part.
        - UseEnvelope: Create the BizTalk message body part from the entire SOAP **Envelope** of an incoming message.
        - UseBodyPath: Use the body path expression in the **InboundBodyPathExpression** property to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP **Body** element of an incoming message. This property is valid only for solicit-response ports.  

適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 傳送  

#### <a name="inboundbodypathexpression"></a>InboundBodyPathExpression
指定內文路徑運算式來識別用於建立 BizTalk 訊息內文部分之內送訊息的特定部分。 此內文路徑運算式評估的 soap 的直系子項目 **主體** 內送訊息的節點。 如果此內文路徑運算式傳回一個以上的節點，則只會為 BizTalk 訊息內文部分選擇第一個節點。 如果這個屬性，則需要 **InboundBodyLocation** 屬性設定為 **UseBodyPath**。 如需有關如何使用**InboundBodyPathExpression**屬性，請參閱[WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)。

유형: 문자열  
預設值： 空字串  
適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 傳送配接器

#### <a name="inboundheaders"></a>InboundHeaders
使用 **InboundHeaders** 屬性來存取內送 WCF 訊息的 SOAP 標頭。 WCF 配接器會將內送訊息中的所有 SOAP 標頭值複製到這個屬性，包括 WCF 基礎結構用於WS-Addressing、WS-Security 和 WS-AtomicTransaction 等的自訂 SOAP 標頭和標準 SOAP 標頭。 內容屬性中所包含的值是包含 XML 資料字串\<**標頭**\>根項目，並傳入的 SOAP 標頭複製成為子項目的\< **標頭**\>項目。 使用 WCF 配接器如何存取 SOAP 標頭的相關資訊，請參閱 SDK 範例中，使用自訂 SOAP 標頭使用 WCF 配接器，從 [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960)。

유형: 문자열  
適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 傳送配接器

#### <a name="inboundnodeencoding"></a>InboundNodeEncoding
指定的編碼的 WCF 接收配接器，用來解碼中指定的內文路徑運算式所識別的節點類型 **InboundBodyPathExpression**。 如果這個屬性，則需要 **InboundBodyLocation** 屬性設定為 **UseBodyPath**。

유형: 문자열  
預設值： XML  

    Applicable values are:  
        - Base64: Base64 encoding
        - Hex: Hexadecimal encoding
        - String: Text encoding - UTF-8
        - XML: The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in **InboundBodyPathExpression**.  

適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 傳送配接器

#### <a name="isfault"></a>IsFault
指出是否收到 SOAP 錯誤訊息。 此屬性會自動從內送訊息升級。 

**附註**  
**IsFault**屬性不能用來檢查所接收的訊息傳輸錯誤，例如 HTTP 404 （檔案或目錄找不到） 錯誤。

類型：Boolean  
適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 傳送配接器

#### <a name="leasetimeout"></a>LeaseTimeout
指定作用中之集區連線的最大存留期間。 在指定的時間過去後，目前的要求獲得服務之後，連線隨即會關閉。

Wcf-nettcp 配接器會利用 [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087) 類別與端點進行通訊。 當使用 [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087) 在負載平衡案例中，請考慮減少預設租用逾時。如需詳細資訊時使用之負載平衡[NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087)，請參閱 < 另請參閱中的適當主題。

유형: 문자열  
預設值︰ 00:05:00  
適用於： Wcf-nettcp 接收配接器  

#### <a name="maxconcurrentcalls"></a>MaxConcurrentCalls
指定對單一服務執行個體的並行呼叫數目。 超出上限的呼叫將排入佇列。 將這個值設定為 0 的效果與設定為 **Int32.MaxValue**相同。 

**附註**  
您無法使用追蹤設定檔在 BAM 主要匯入資料庫中追蹤這個屬性。 

類型： 整數  
預設值：200  
適用於： 所有 WCF 都接收配接器*除了*Wcf-custom 和 Wcf-customisolated 配接器

#### <a name="maxconnections"></a>MaxConnections
指定待命程式最多可以擁有等待應用程式接受的連線數目。 超過此配額值時，則會捨棄新的傳入連線，而非等待接受連線。 

**附註**  
因為這是配接器處理常式屬性，所以無法在管線元件和協調流程中設定。 

**附註**  
您無法使用追蹤設定檔在 BAM 主要匯入資料庫中追蹤這個屬性。 

類型： 整數  
預設值︰ 10  
適用於： Wcf-netnamedpipe 配接器，Wcf-nettcp 配接器  

#### <a name="maxreceivedmessagesize"></a>MaxReceivedMessageSize
指定大小上限，以位元組為單位，在網路上可以接收的訊息 （包括標頭）。 訊息的大小受限於配置給每個訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。

類型： 整數  
預設值：65536  
適用於： 
- WCF-BasicHttp 配接器
- WCF-WSHttp 配接器
- WCF-NetTcp 配接器
- WCF-NetNamedPipe 配接器
- WCF-NetMsmq 接收配接器

#### <a name="messageclientcredentialtype"></a>MessageClientCredentialType
指定當使用以訊息為基礎的安全性來執行用戶端驗證時，所要使用的認證類型。

每個 WCF 配接器適用的值都不一樣。 如需有關**MessageClientCredentialType**屬性，請參閱使用說明主題中的每個 WCF 配接器[WCF 配接器](../core/wcf-adapters.md)。

유형: 문자열  
適用於： 
- WCF-BasicHttp 配接器
- WCF-WSHttp 配接器
- WCF-NetTcp 配接器
- WCF-NetNamedPipe 配接器

#### <a name="messageencoding"></a>MessageEncoding
指定用來為 SOAP 訊息編碼的編碼器。

유형: 문자열  
預設值︰ 文字  

    Applicable values: 
        - Text: Use a text message encoder
        - Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder  

適用於： Wcf-basichttp 配接器、 Wcf-wshttp 配接器


#### <a name="msmqauthenticationmode"></a>MsmqAuthenticationMode
指定訊息如何由 MSMQ 傳輸進行驗證。

유형: 문자열  
預設值︰ **WindowsDomain**  
    如需有關適用值**MsmqAuthenticationMode**屬性，請參閱**MSMQ 驗證模式**屬性**Wcf-netmsmq 傳輸屬性對話方塊方塊中，傳送、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
適用於： Wcf-netmsmq 配接器  

#### <a name="msmqencryptionalgorithm"></a>MsmqEncryptionAlgorithm
指定在訊息佇列管理員之間傳輸訊息時，要在連線上使用之訊息加密的演算法。 這個屬性只有當 **MsmqProtectionLevel** 屬性設定為 **EncryptAndSign**。

유형: 문자열  
預設值︰ **RC4Stream**  

    Applicable values are: RC4Stream, AES

適用於： Wcf-netmsmq 配接器  

#### <a name="msmqprotectionlevel"></a>MsmqProtectionLevel
指定在 MSMQ 傳輸層維持訊息安全的方式。

유형: 문자열  
預設值︰ **符號**  

    Applicable values are:
        - None: No protection
        - Sign: Messages are signed
        - EncryptAndSign: Messages are encrypted and signed. To use this protection level, you must enable **Active Directory Integration** for **MSMQ**  

適用於： Wcf-netmsmq 配接器  

#### <a name="msmqsecurehashalgorithm"></a>MsmqSecureHashAlgorithm
指定用來計算雜湊的雜湊演算法。 這個屬性不會使用如果 **MsmqProtectionLevel** 屬性設定為 **無**。

유형: 문자열  
預設值︰ **SHA1**  

    Applicable values are: MD5, SHA1, SHA25, SHA512  

適用於： Wcf-netmsmq 配接器  

#### <a name="negotiateservicecredential"></a>NegotiateServiceCredential
指定是否會在超出範圍的用戶端提供此服務認證，或是透過交涉程序從此服務取得服務認證給用戶端。 這類交涉是一般訊息交換的先驅。

如果 **MessageClientCredentialType** 屬性等於 **無**, ，**Username**, ，或 **憑證**, ，此屬性設定為 **False** 意指服務憑證可超出用戶端，且用戶端必須指定服務憑證。 這個模式可以與 SOAP 堆疊交互運作 (SOAP 堆疊會實作 WS-Trust 和 WS-SecureConversation)。

如果 **MessageClientCredentialType** 屬性設定為 **Windows**, ，此屬性設定為 **False** 指定 Kerberos 驗證。 這表示，用戶端和服務都必須是相同 Kerberos 網域的一部分。 這個模式可以與 SOAP 堆疊交互運作，SOAP 堆疊會實作 Kerberos Token 設定檔 (如 OASIS WSS TC 上所定義) 以及 WS-Trust 和 WS-SecureConversation。

當這個屬性是 **True**, ，會造成透過 SOAP 訊息傳送 SPNego 交換的.NET SOAP 交涉。

類型：Boolean  
預設值：True  
適用於： Wcf-wshttp 配接器  

#### <a name="opentimeout"></a>OpenTimeout
指定時間值，表示可供完成通道開啟作業的時間間隔。 

**附註**  
您無法使用追蹤設定檔在 BAM 主要匯入資料庫中追蹤這個屬性。 

유형: 문자열  
預設值：00:01:00  
適用於： 所有 WCF 配接器*除了*Wcf-custom 和 Wcf-customisolated 配接器

#### <a name="orderedprocessing"></a>OrderedProcessing
指定是否連續處理訊息。 選取此屬性時，此接收位置所能容納已排序的訊息傳遞的 BizTalk 傳訊 」 或 「 協調流程傳送埠搭配使用時 **排序的傳遞** 選項設為 `True`。 如需詳細資訊 **排序的傳遞** 選項，請參閱 < 另請參閱中的適當主題。

這個屬性適用於下列情況：
- Wcf-custom 配接器： 當**BindingType**屬性設定為**netMsmqBinding**
- Wcf-custom 配接器： 當**BindingType**屬性設定為**customBinding**，而**BindingConfiguration**屬性設定為使用依賴的自訂通道在支援排序的傳遞，例如 MSMQ 傳輸。
- Wcf-customisolated 配接器： 當**BindingType**屬性設定為**customBinding**，而**BindingConfiguration**屬性設定為使用自訂的通道依賴支援排序的傳遞的傳輸。
- WCF-NetMsmq 配接器

유형: 문자열  
預設值︰ **False**  
適用於： 
- WCF-NetMsmq 接收配接器
- WCF-Custom 接收配接器
- WCF-CustomIsolated 接收配接器

#### <a name="outboundbodylocation"></a>OutboundBodyLocation
指定資料選取範圍 soap **主體** 外寄 WCF 訊息的項目。 如需有關如何使用**OutboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。

유형: 문자열  
預設值： UseBodyElement  

    Applicable values are:
        - UseBodyElement: Use the BizTalk message body part to create the content of the SOAP **Body** element for an outgoing message
        - **UseTem****plate**: Use the template supplied in the OutboundXMLTemplate property to create the content of the SOAP **Body** element for an outgoing message

適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 接收配接器

#### <a name="outboundcustomheaders"></a>OutboundCustomHeaders
指定外寄訊息的自訂 SOAP 標頭。 使用這個屬性時，屬性必須有\<**標頭**\>元素是根項目。 所有自訂 SOAP 標頭必須置於\<**標頭**\>項目。 如果自訂 SOAP 標頭值為空字串，您必須指派\<**標頭**\>\</**標頭**\>或\<**標頭**\>給這個屬性。 如需如何使用 WCF 配接器使用 SOAP 標頭的詳細資訊，請參閱 SDK 範例，使用自訂 SOAP 標頭使用 WCF 配接器從 [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960)。

유형: 문자열  
適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 接收配接器

#### <a name="outboundxmltemplate"></a>OutboundXmlTemplate
指定 XML 格式的範本內容的 SOAP **主體** 外寄訊息的項目。 如果這個屬性，則需要 **OutboundBodyLocation** 屬性設定為 **UseTemplate**。 如需有關如何使用**OutboundXMLTemplate**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。

유형: 문자열  
預設值： 空字串  
適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 接收配接器

#### <a name="password"></a>密碼
指定要用於驗證目的地伺服器的密碼時 **UseSSO** 屬性設定為 **False**。

유형: 문자열  
預設值： 空字串  
適用於： 所有 WCF 都傳送配接器*除了*Wcf-netnamedpipe 配接器  

#### <a name="propagatefaultmessage"></a>PropagateFaultMessage
指定要傳送或擱置在輸出處理中失敗的訊息。 此屬性只對請求-回應連接埠有效。 

**附註**  
您無法使用追蹤設定檔在 BAM 主要匯入資料庫中追蹤這個屬性。

類型：Boolean  
預設值︰ **，則為 True**  

    Applicable values are:  
        - True: Route the message that fails outbound processing to a subscribing application (such as another receive port or orchestration schedule)
        - False: Suspend failed messages and generate a negative acknowledgment (NACK)

適用於： 所有 WCF 都傳送配接器*除了*Wcf-netmsmq 配接器
  
#### <a name="proxyaddress"></a>ProxyAddress
指定 Proxy 伺服器的位址。 使用 **https** 或 **http** 根據安全性組態的配置。 這個位址後面可以加上冒號和連接埠編號， 如果需要此屬性， **ProxyToUse**屬性設定為**UserSpecified** (例如 http://127.0.0.1:8080)

유형: 문자열  
預設值： 空字串  
適用於： Wcf-basichttp 傳送配接器、 Wcf-wshttp 傳送配接器  

#### <a name="proxypassword"></a>ProxyPassword
指定要用於指定 proxy 伺服器密碼 **ProxyAddress** 屬性。

유형: 문자열  
預設值： 空字串  
適用於： Wcf-basichttp 傳送配接器、 Wcf-wshttp 傳送配接器

#### <a name="proxytouse"></a>ProxyToUse
指定要針對外寄 HTTP 流量使用哪一個 Proxy 伺服器。

유형: 문자열  
預設值︰ **無**  

    Applicable values are:  
        - None: Do not use a proxy server for this send port
        - Default: Use the proxy settings in the send handler hosting this send port
        - UserSpecified: Use the proxy server specified in the **ProxyAddress** property

適用於： Wcf-basichttp 傳送配接器、 Wcf-wshttp 傳送配接器  

#### <a name="proxyusername"></a>ProxyUserName
指定要用於指定 proxy 伺服器的使用者名稱 **ProxyAddress** 屬性。 此屬性為必要的如果 **ProxyToUse** 屬性設定為 **UserSpecified**。

如需有關這個屬性的詳細資訊，請參閱[如何設定 Wcf-wshttp 傳送埠](../core/how-to-configure-a-wcf-wshttp-send-port.md)和[如何設定 Wcf-basichttp 傳送埠](http://msdn.microsoft.com/library/acdb50fa-57fe-4657-9561-b6b2f4919c7f)。

유형: 문자열  
適用於： Wcf-basichttp 傳送配接器、 Wcf-wshttp 傳送配接器

#### <a name="replytoaddress"></a>ReplyToAddress
指出外寄 WCF 訊息的回應端點位址，這些訊息對應於透過要求-回應接收位置接收的內送訊息。 此屬性會自動從內送訊息升級。

유형: 문자열  
預設值： 空字串  
適用於： 所有 WCF 配接器*除了*Wcf-netmsmq 配接器

#### <a name="securitymode"></a>SecurityMode
指定使用的安全性類型。 每個 WCF 配接器適用的值都不一樣。 如需有關**SecurityMode**屬性，請參閱使用說明主題中的每個 WCF 配接器[WCF 配接器](../core/wcf-adapters.md)。 

**附註**  
您無法使用追蹤設定檔在 BAM 主要匯入資料庫中追蹤這個屬性。

유형: 문자열  
適用於： 所有 WCF 配接器*除了*Wcf-custom 和 Wcf-customisolated 配接器

#### <a name="sendtimeout"></a>SendTimeout
指定時間值，表示可供完成傳送作業的時間間隔。 這個值會指定完成整個互動的時間長度，即使對應方傳送很大的訊息也是如此。

유형: 문자열  
預設值：00:01:00  
適用於： 所有 WCF 配接器*除了*Wcf-custom 和 Wcf-customisolated 配接器

#### <a name="servicebehaviorconfiguration"></a>ServiceBehaviorConfiguration
指定的 XML 字串**\<行為\>**元素 **\<serviceBehaviors\>** 設定 WCF 行為設定的項目服務。 如需有關 **\<serviceBehaviors\>** 項目，請參閱 < 另請參閱中的適當主題。

範例：

```
<behavior name="SampleServiceBehavior">
<serviceAuthorization principalPermissionMode="UseAspNetRoles"/>
<serviceCredentials>
<serviceCertificate findValue="539d9ab3089bb6dc187fa7dbb382cf01f8d78f5f" storeLocation="CurrentUser" x509FindType="FindByThumbprint"/>
</serviceCredentials>
<serviceMetadata httpGetEnabled="true"/>
</behavior>
```

유형: 문자열  
預設值： 空字串  
適用於： Wcf-custom 接收配接器，Wcf-customisolated 配接器

#### <a name="servicecertificate"></a>ServiceCertificate
如果將這個屬性用於接收位置，請針對用戶端驗證服務時所使用的接收位置，指定 X.509 憑證的指紋。 要用於此屬性的憑證必須安裝到 **我** 存放 **目前使用者** 位置。

如果將這個屬性用於傳送埠，請指定 X.509 憑證的指紋，以驗證此傳送埠傳送訊息的目標服務。 要用於此屬性的憑證必須安裝到 **其他人** 存放 **本機** 位置。

유형: 문자열  
預設值： 空字串  
適用於： 
- WCF-BasicHttp 配接器
- WCF-NetMsmq 配接器
- WCF-WSHttp 配接器
- WCF-NetTcp 接收配接器

#### <a name="suspendmessageonfailure"></a>SuspendMessageOnFailure
指定是否擱置因接收管線失敗或路由失敗而造成輸入處理失敗的要求訊息。

類型：Boolean  
預設值：True  
適用於： 所有 WCF 都接收配接器  

#### <a name="textencoding"></a>TextEncoding
指定字元集的編碼方式來繫結上發出訊息時 **MessageEncoding** 屬性設定為 **文字**。 

**附註**  
您無法使用追蹤設定檔在 BAM 主要匯入資料庫中追蹤這個屬性。 

유형: 문자열  
預設值： utf-8  

    Applicable values are:  
        - unicodeFFF: Unicode BigEndian encoding
        - utf-16: 16-bit encoding
        - utf-8: 8-bit encoding

適用於： Wcf-basichttp 配接器、 Wcf-wshttp 配接器
  
#### <a name="timetolive"></a>TimeToLive
指定訊息在過期並置入無效信件佇列之前的有效時間有多長。 設定這個屬性可確保講求時效的訊息，在經過傳送埠處理之後才會變成過時訊息。 在佇列中的訊息，若是沒有在指定的時間間隔內由此傳送埠耗用，便會被視為過期。 過期的訊息會傳送到特殊的佇列，稱為無法寄出的信件佇列。 寄不出信件佇列的位置會設定與 **DeadLetterQueue** 屬性。

유형: 문자열  
預設值︰ 1.00:00:00  
適用於： Wcf-netmsmq 傳送配接器

#### <a name="to"></a>若要
指定 WCF 傳送埠傳送之外寄 WCF 訊息的目的端點位址。

유형: 문자열  
預設值： 空字串  
適用於： 所有 WCF 都傳送配接器  

#### <a name="transactionprotocol"></a>TransactionProtocol
指定要搭配此繫結使用的交易通訊協定。 如果這個屬性，則需要 **EnableTransaction** 屬性設定為 **True**。

유형: 문자열  
預設值： OleTransaction  

    Applicable values are: OleTransaction, WS-AtomicTransaction

適用於： Wcf-netnamedpipe 配接器，Wcf-nettcp 配接器  

#### <a name="transportclientcredentialtype"></a>TransportClientCredentialType
指定在執行傳送埠驗證時，所要使用的認證類型。 每個 WCF 配接器適用的值都不一樣。 如需有關**TransportClientCredentialType**屬性，請參閱使用說明主題中的每個 WCF 配接器[WCF 配接器](../core/wcf-adapters.md)。

유형: 문자열  
適用於： Wcf-basic 配接器、 Wcf-nettcp 配接器、 Wcf-wshttp 配接器  

#### <a name="transportprotectionlevel"></a>TransportProtectionLevel
指定在 TCP 傳輸層的安全性。 簽署訊息可以降低訊息在傳輸時遭到第三者竄改的風險。 加密可在傳輸時提供資料等級的隱私權。

유형: 문자열  
預設值︰ **EncryptAndSign**  

    Applicable values are:  
        - None: No protection
        - Sign: Messages are signed
        - EncryptAndSign: Messages are encrypted and signed

適用於： Wcf-nettcp 配接器，Wcf-netnamedpipe 配接器  

#### <a name="username"></a>UserName
指定要用於目的地伺服器驗證的使用者名稱時 **UseSSO** 屬性設定為 **False**。 您不需要對此屬性使用 domain\user 格式。

유형: 문자열  
預設值： 空字串  
適用於： 所有 WCF 都傳送配接器*除了*Wcf-netnamedpipe 配接器

#### <a name="usesourcejournal"></a>UseSourceJournal
指定由此傳送埠處理的訊息複本是否應該存放在來源日誌佇列中。

類型：Boolean  
預設值：False  
適用於： Wcf-netmsmq 傳送配接器  

#### <a name="usesso"></a>UseSSO
대상 서버 인증을 위한 클라이언트 자격 증명을 검색하는 데 Single Sign-On을 사용할지 여부를 지정합니다. 

**附註**  
您無法使用追蹤設定檔在 BAM 主要匯入資料庫中追蹤這個屬性。 

類型：Boolean  
預設值：False  
適用於： 所有 WCF 都傳送配接器*除了*Wcf-netnamedpipe 配接器

#### <a name="referencedbindings"></a>ReferencedBindings
指定所參考的繫結組態**bindingConfiguration**屬性**\<簽發者\>**元素**wsFederationHttpBinding**和**customBinding**，表示安全性權杖服務 (STS) 發行安全性權杖。 如需詳細資訊**\<簽發者\>**項目，請參閱主題 <"\<簽發者\>」 在[http://go.microsoft.com/fwlink/?LinkId=83476](http://go.microsoft.com/fwlink/?LinkId=83476)。

繫結資訊，包括**\<簽發者\>**元素**wsFederationHttpBinding**和**customBinding**可以是透過設定**BindingConfiguration** Wcf-custom 和 Wcf-customisolated 配接器的屬性。 所有參考繫結組態，這個屬性必須放置在表單的[\<繫結\>](http://go.microsoft.com/fwlink/?LinkID=80878)項目。 

**附註**  
**BindingConfiguration**屬性**\<簽發者\>**元素必須參考這個屬性中的有效繫結名稱。 

**附註**  
**\<簽發者\>**中參考繫結組態項目也可以使用參照到不同的繫結中設定這個屬性如果這個參考鏈結不會循環相依性。 

範例： 

```
WCF.BindingConfiguration = @"<wsFederationHttpBinding>
<binding name=""sampleBinding"">
<security mode=""Message"">
<message issuedKeyType=""AsymmetricKey"">
<issuer address=""http://www.contoso.com/samplests"" binding=""wsFederationHttpBinding"" bindingConfiguration=""**contosoSTSBinding**""/>
</message>
</security>
</binding>
</wsFederationHttpBinding>";
WCF.ReferencedBinding =@"<bindings>
<wsFederationHttpBinding>
<binding name=""**contosoSTSBinding**"">
<security mode=""Message"">
<message negotiateServiceCredential=""false"">
<issuer address=""http://northwind.com/samplests"" bindingConfiguration=""**northwindBinding**"" binding=""wsHttpBinding"">
</issuer>
</message>
</security>
</binding>
</wsFederationHttpBinding>
<wsHttpBinding>
<binding name=""**northwindBinding**"">
<security mode=""Message"">
<message clientCredentialType=""Certificate""/>
</security>
</binding>
</wsHttpBinding>
</bindings>" 
``` 

**附註**  
**ReferencedBinding**屬性不能包含中使用的繫結組態**BindingConfiguration**屬性。

유형: 문자열  
預設值： 空字串  
適用於： Wcf-custom 配接器，Wcf-customisolated 配接器
  
## <a name="see-also"></a>另請參閱  
 [WCF 配接器](../core/wcf-adapters.md)   
 [\<行為\>的\<endpointBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=80879)   
 [\<bindings\>](http://go.microsoft.com/fwlink/?LinkId=80878)   
 [\<behavior\> of \<serviceBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=81095)   
 [依序傳遞訊息](../core/ordered-delivery-of-messages.md)   
 [負載平衡](http://go.microsoft.com/fwlink/?LinkId=81089)
