---
title: 如何設定 HTTP 傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send ports, HTTP adapters
- HTTP adapters, send ports
- configuring [HTTP adapters], send ports
ms.assetid: 29c6868c-4570-4375-9494-08c07220eeb3
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dd46ced62441c9a61c3813d0bcff5e4f2f34629
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22251302"
---
# <a name="how-to-configure-an-http-send-port"></a>如何設定 HTTP 傳送埠
您可以使用程式設計的方式，或使用 BizTalk Server 管理主控台，來設定 HTTP 傳送埠。  
  
## <a name="configure-an-http-send-port-programmatically"></a>以程式設計方式設定 HTTP 傳送埠
  
 HTTP 配接器會將其組態資訊儲存在「BizTalk 管理」資料庫中 (也稱為「組態」資料庫)。 您可以將組態資訊儲存在自訂 XML 屬性包中。 在 HTTP 配接器初始化期間及其執行階段，伺服器會傳遞組態至配接器，如下：  
  
-   HTTP 傳送處理常式組態資訊傳遞至配接器藉由呼叫**負載**方法**IPersistPropertyBag**介面。  
  
-   如為 HTTP 傳送埠，則將組態資訊視為訊息內文中的一組屬性，傳遞至配接器。 HTTP 命名空間會將這些屬性群組在一起。  
  
 「BizTalk 總管」物件模型會公開傳送埠的 `ItransportInfo` 配接器組態介面，包括 `TransportTypeData` 讀取/寫入屬性。 此屬性會將 HTTP 傳送埠組態屬性包接受為名稱/值組 XML 字串。 請注意，若要在 「 BizTalk 總管物件模型中設定這個屬性，它必須先設定上`Address`屬性**ITransportInfo**介面。  
  
 設定**TransportTypeData**屬性**ITransportInfo**介面並非必要。 若沒有設定，HTTP 配接器會使用 HTTP 傳送處理常式的預設值。  
  
 若沒有定義複製處理常式之組態的傳送埠組態屬性，則會使用處理常式的組態屬性。 若 HTTP 傳送處理常式沒有組態值，HTTP 傳送配接器會在事件日誌中記錄錯誤，並將訊息移動至備份配接器。  
  
 您可以使用程式設計的方式，在訊息內文上設定組態屬性。 您可以在 BizTalk Server 協調流程排程或自訂管線元件中設定這些屬性。 使用這些屬性時適用下列規則：  
  
-   若在協調流程上或接收管線的自訂管線元件中設定組態屬性，則：  
  
    -   若訊息傳送至靜態傳送埠，屬性值會以該傳送埠設定的值覆寫。  
  
    -   若訊息傳送至動態傳送埠，則不會覆寫屬性值。  
  
-   若在傳送管線的自訂管線元件中設定組態屬性，則：  
  
    -   無論訊息是傳送至靜態或動態傳送埠，都不會覆寫值。  
  
 下表列出您可以在「BizTalk 總管」物件模型中設定之 HTTP 傳送位置的組態屬性。  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|**RequestTimeout**|xs:int|等待伺服器回應的逾時期間。 若設定為零 (0)，則系統會根據要求訊息的大小來計算逾時。|**最小值：** 0<br /><br /> **最大值：** MAX_LONG|**預設值：** 0|  
|**ContentType**|xs:string|要求訊息的內容類型|**最小長度：** 0<br /><br /> **最大長度：** 256|**預設值：** Text/XML|  
|**MaxRedirects**|xs:int|HTTP 配接器重新導向要求的次數上限。|**最小值：** 0<br /><br /> **最大值：** 10|**預設值：** 5|  
|**UseHandlerProxySettings**|xs:boolean|指定 HTTP 傳送埠是否要對傳送處理常式使用 Proxy 組態。|無|**預設值：** ，則為 True<br /><br /> 若為 True，傳送埠將會使用在處理常式層級指定的 Proxy 設定。 若為 False，傳送配接器將使用在傳送埠指定的 Proxy 資訊。|  
|**UseProxy**|xs:boolean|指定 HTTP 配接器是否要使用 Proxy 伺服器。 Proxy 伺服器可由所有 HTTP 傳送埠共用。|無|**預設值：** False<br /><br /> 如果這個屬性就會忽略**UseHandlerProxySettings**是**True**。|  
|**ProxyName**|xs:string|指定 Proxy 伺服器名稱。|**最小長度：** 0<br /><br /> **最大長度：** 256|**預設值：** 空白<br /><br /> HTTP 傳送配接器會忽略此屬性，如果**UseHandlerProxySettings**屬性設定為**True**。 否則，HTTP 傳送配接器使用這個屬性只有當**UseProxy**是**True**。 如果這個屬性，則需要**UseProxy**是**True**。|  
|**ProxyPort**|xs:int|指定 Proxy 伺服器連接埠。|**最小值：** 0<br /><br /> **最大值：** 65535|**預設值：** 80<br /><br /> HTTP 傳送配接器會忽略此屬性，如果**UseHandlerProxySettings**是**True**。 否則，HTTP 傳送配接器使用這個屬性只有當**UseProxy**是**True**。 如果這個屬性，則需要**UseProxy**是**True**。|  
|**ProxyUsername**|xs:string|指定要用於 Proxy 伺服器驗證的使用者名稱。|**最小長度：** 0<br /><br /> **最大長度：** 256|**預設值：** 空白<br /><br /> HTTP 傳送配接器會忽略此屬性，如果**UseHandlerProxySettings**是**True**。 否則，HTTP 傳送配接器使用這個屬性只有當**UseProxy**是**True**。|  
|**ProxyPassword**|xs:string|指定要用於 Proxy 伺服器驗證的使用者密碼。|**最小長度：** 0<br /><br /> **最大長度：** 256|**預設值：** 空白<br /><br /> HTTP 傳送配接器會忽略此屬性，如果**UseHandlerProxySettings**是**True**。 否則，HTTP 傳送配接器使用這個屬性只有當**UseProxy**是**True**。|  
|**AuthenticationScheme**|xs:string|與目的地伺服器搭配使用的驗證類型。|無|**有效值：**<br /><br /> -   **匿名 （預設值）**<br />-   **基本**<br />-   **摘要**<br />-   **Kerberos**|  
|**使用者名稱**|xs:string|要提供給伺服器驗證的使用者名稱。|**最小長度：** 0<br /><br /> **最大長度：** 256|**預設值：** 空白<br /><br /> 如果您選取，則需要此值**基本**或**摘要**驗證。 HTTP 配接器會忽略這個屬性的值，如果**UseSSO**是**True**。|  
|**密碼**|xs:string|要提供給伺服器驗證的使用者密碼。|**最小長度：** 0<br /><br /> **最大長度：** 256|**預設值：** 空白<br /><br /> 如果您選取，則需要此值**基本**或**摘要**驗證。 如果這個屬性的值就會忽略**UseSSO**是**True**。|  
|**EnableChunkedEncoding**|xs:boolean|指定 HTTP 配接器是否會使用區塊編碼|無|**預設值：**<br /><br /> True|  
|**[MSSQLSERVER 的通訊協定內容]**|xs:string|用戶端 SSL 憑證的指紋。|**最小長度：** 0<br /><br /> **最大長度：** 59|**預設值：** 空白|  
|**UseSSO**|xs:boolean|指定是否要針對傳送埠使用 SSO。|無|**預設值：** False|  
|**AffiliateApplicationName**|xs:string|SSO 使用之分支機構應用程式的名稱。|**最小長度：** 0<br /><br /> **最大長度：** 256|**預設值：** 空白<br /><br /> 若**UseSSO**是**True**。|  
  
 下列程式碼會顯示用來設定這些屬性的 XML 字串：  
  
```  
<CustomProps>  
   <ContentType vt="8">text/xml</ContentType>  
   <RequestTimeout vt="3">0</RequestTimeout>  
   <MaxRedirects vt="3">5</MaxRedirects>  
   <UseHandlerProxySettings vt="8">-1</UseHandlerProxySettings>  
   <UseProxy vt="8">-1</UseProxy>  
   <ProxyName vt="8">sdfsd</ProxyName>  
   <ProxyPort vt="3">80</ProxyPort>  
   <ProxyUsername vt="8">Somename</ProxyUsername>  
   <ProxyPassword vt="8">Somepassword</ProxyPassword>  
   <AuthenticationScheme vt="8">Basic</AuthenticationScheme>  
   <Username vt="8">Somename</Username>  
   <Password vt="8">Somepassword</Password>  
   <EnableChunkedEncoding vt="11">1</EnableChunkedEncoding>  
   <Certificate vt="8">AAAA BBBB CCCC DDDD</Certificate>  
   <UseSSO vt="11">0</UseSSO>  
   <AffiliateApplicationName vt="8">Name</AffiliateApplicationName>  
</CustomProps>  
```  
  
## <a name="configure-an-http-send-port-with-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台設定 HTTP 傳送埠
  
 您可以在 [BizTalk Server 管理] 主控台中設定 HTTP 傳送埠配接器變數。 若未設定傳送埠的屬性，則使用 [BizTalk Server 管理] 主控台中所設定的預設傳送處理常式值。  
  
> [!NOTE]
>  本主題中所述的組態屬性是單向和要求-回應 HTTP 傳送埠所常用的。  
  
1.  在 BizTalk Server 管理主控台中，建立新的傳送埠，或按兩下現有的傳送埠進行修改。 請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)如需詳細資訊。 設定所有傳送埠選項，並指定**HTTP**如**類型**選項**傳輸**區段**一般** 索引標籤。  
  
2.  在**一般**索引標籤的**傳輸**區段中，按一下**設定**旁邊**類型**。  
  
3.  在**HTTP 傳輸屬性**對話方塊**一般**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**目的地 URL**|必要。 指定傳送 HTTP 要求的位址。 包括附加於基底 URL 的查詢字串。<br /><br /> **類型：** 字串<br /><br /> **最大長度：** 256<br /><br /> 如需詳細資訊，請參閱[目的地 URL 屬性的限制](../core/restrictions-on-the-destination-url-property.md)。 **注意：** URI 傳送埠或接收位置不能超過 256 個字元。|  
    |**啟用區塊編碼**|指定使用區塊編碼。 若啟用此選項，HTTP 配接器將會使用其最大區塊大小為 8 KB 的 HTTP 區段編碼。 如果 HTTP 傳送處理常式設定為區塊編碼會隱含停**使用 proxy**。<br /><br /> **類型：** 布林<br /><br /> **預設值：** ，則為 True|  
    |**要求逾時 （秒）**|指定 HTTP/HTTPS 傳輸逾時 (以秒為單位)。 若 HTTP 配接器在此時間內未接收到回應，則服務會記錄錯誤，並根據重試基礎結構重新提交訊息。<br /><br /> 若設定為零 (0)，則 BizTalk 傳訊引擎會根據要求訊息的大小來計算逾時。 若未提供任何值，則會使用處理常式的值。<br /><br /> **類型：** 長<br /><br /> **最小值：** 0<br /><br /> **最大值：** MAX_LONG|  
    |**重新導向上限**|指定允許訊息傳送的重新導向上限。<br /><br /> **預設值：** 5<br /><br /> **類型：** Int<br /><br /> **最小值：** 0<br /><br /> **最大值：** 10|  
    |**內容類型**|指定要求訊息的內容類型。<br /><br /> 若未設定此值，則使用處理常式的值。<br /><br /> **類型：** 字串<br /><br /> **最小長度：** 0<br /><br /> **最大長度：** 256|  
  
4.  在**HTTP 傳輸屬性**對話方塊**Proxy （處理常式覆寫）** 索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**使用處理常式的預設 proxy 設定**|指定傳送埠組態必須使用為 HTTP 傳送處理常式所指定的 Proxy 設定。<br /><br /> 這是預設值。|  
    |**不使用 proxy**|指定 HTTP 傳送處理常式是否要使用 Proxy 伺服器。<br /><br /> 若選取，則此傳送埠的 HTTP 傳送處理常式不會使用 Proxy 伺服器。|  
    |**使用 Proxy**|指定 HTTP 傳送處理常式是否要使用 Proxy 伺服器。<br /><br /> 若選取，則 HTTP 傳送處理常式會使用 Proxy 伺服器。|  
    |**Server**|指定此傳送埠的 Proxy 伺服器位址。<br /><br /> 這個屬性只需要一個值，如果**使用 proxy**已選取。<br /><br /> **類型：** 字串<br /><br /> **最小長度：** 0<br /><br /> **最大長度：** 256|  
    |**[通訊埠]**|指定此傳送埠的 Proxy 伺服器連接埠。<br /><br /> 這個屬性只需要一個值，如果**使用 proxy**已選取。<br /><br /> **預設值：** 80<br /><br /> **類型：** 長<br /><br /> **最小值：** 0<br /><br /> **最大值：** 65535|  
    |**使用者名稱**|指定要用於 Proxy 伺服器驗證的使用者名稱。<br /><br /> 這個屬性只需要一個值，如果**使用 proxy**已選取。<br /><br /> **類型：** 字串<br /><br /> **最小長度：** 0<br /><br /> **最大長度：** 256|  
    |**密碼**|指定要用於 Proxy 伺服器驗證的使用者密碼。<br /><br /> 這個屬性只需要一個值，如果**使用 proxy**已選取。<br /><br /> **類型：** 字串<br /><br /> **最小長度：** 0<br /><br /> **最大長度：** 256|  
  
5.  在**HTTP 傳輸屬性**對話方塊**驗證**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**驗證類型**|指定要提供給目的地伺服器的驗證類型。<br /><br /> 有效的選項包括：<br /><br /> -   **匿名**<br />-   **基本**<br />-   **摘要**<br />-   **Kerberos**<br /><br /> **預設值：** 匿名|  
    |**認證**|指定要使用的認證類型。<br /><br /> 僅適用於當**驗證類型**是**基本**或**摘要**。<br /><br /> 有效的選項包括：<br /><br /> -   **請勿使用單一登入**<br />     **使用者名稱：**<br />     要提供給目的地伺服器驗證的使用者名稱。 如果**驗證類型**屬性是**匿名**或**Kerberos**，此選項會停用。 此屬性需要一個值，如果**基本**或**摘要**選取時，不是使用企業單一登入。<br />     **最小長度：** 0<br />     **最大長度：** 256<br />     **密碼：**<br />     要提供給目的地伺服器驗證的密碼。 如果**驗證類型**屬性是**匿名**或**Kerberos**，此選項會停用。 此屬性需要一個值，如果**基本**或**摘要**選取時，不是使用單一登入。<br />     **最小長度：** 0<br />     **最大長度：** 256<br />-   **使用單一登入**<br />     指定是否要使用「單一登入」來擷取用戶端認證，以供目的地伺服器驗證。<br />     **分支機構應用程式**<br />     指定要用於「單一登入」的分支機構應用程式。<br />     選擇要包括在「單一登入」中的應用程式。<br />     **最小長度：** 0<br />     **最大長度：** 256|  
    |**SSL 用戶端憑證指紋**|指定用來建立「安全通訊端層」(SSL) 連線的用戶端憑證指紋。<br /><br /> **最小長度：** 0<br /><br /> **最大長度：** 59|  
  
6.  按一下**確定**和**確定**以儲存設定。  
  
## <a name="see-also"></a>另請參閱  
 [設定 HTTP 傳送埠](../core/configuring-an-http-send-port.md)