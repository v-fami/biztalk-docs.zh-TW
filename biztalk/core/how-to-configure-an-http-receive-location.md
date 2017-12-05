---
title: "如何設定 HTTP 接收位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, HTTP adapters
- configuring [HTTP adapters], receive locations
- HTTP adapters, receive locations
ms.assetid: 901adfc8-0361-49d9-b992-c27089dfbd3b
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4448182792cd6f6f5f7e611cd9a9bd54c75a0d05
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-an-http-receive-location"></a>如何設定 HTTP 接收位置
您可以用程式設計方式，或使用 BizTalk Server 管理主控台，來設定 HTTP 接收位置配接器變數。 若未在接收位置設定屬性，則會使用在 [BizTalk Server 管理] 主控台中設定的預設接收處理常式值。  
  
> [!NOTE]
>  完成下列程序之前，您必須已經新增接收埠。 如需詳細資訊，請參閱[如何建立接收埠](../core/how-to-create-a-receive-port.md)。  
  
 **如何設定 HTTP 接收位置以程式設計的方式**  
  
 HTTP 配接器會將其組態資訊儲存在「BizTalk 管理」資料庫中 (也稱為「組態」資料庫)。 組態是儲存於自訂 XML 屬性包中。  
  
 「 BizTalk 總管物件模型公開**IReceiveLocation**組態介面，其具有**TransportTypeData**讀/寫屬性。 此屬性會接受名稱-值組 XML 字串中的 HTTP 接收位置組態屬性包。  
  
 設定**TransportTypeData**屬性**IReceiveLocation**並非必要。 若未設定，就會使用 HTTP 接收位置組態的預設值。 下表會列出預設值，以及您可以在「BizTalk 總管」物件模型中設定之 HTTP 接收位置的組態屬性。  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|**ResponseContentType**|string|HTTP 配接器會從此接收位置傳送回用戶端之 HTTP 回應訊息的內容類型。 此屬性只適用於要求-回應接收埠，而且單向接收埠會忽略它。|字串<br /><br /> **最小長度：** 0<br /><br /> **最大長度：** 256|預設值： Text/XML|  
|**回送**|布林|指定對於在此位置接收到的要求訊息，將會路由至傳送埠或傳回此接收位置，以作為回應傳送。 此屬性只適用於要求-回應接收埠。 單向接收埠會忽略它。|無|**預設值：** False|  
|**ReturnCorrelationHandle**|布林|指定若提交成功，HTTP 配接器會傳送 HTTP 回應上已提交之訊息的相互關聯 Token 給用戶端。 此屬性只適用於單向接收埠，而且要求-回應接收埠會忽略它。|無|**預設值：** ，則為 True|  
|**SuspendFailedRequests**|布林|指定是否要擱置失敗的 HTTP 要求。 True 值表示擱置失敗的要求，並將「已接受」狀態碼 (202) 傳送給單向接收埠的用戶端，或是將「錯誤」狀態碼 (500) 傳送給雙向接收埠的用戶端。|無|**預設值：** False|  
|**UseSSO**|布林|指定 HTTP 配接器是否會將 SSO 票證發給到達此接收位置的訊息。|無|**預設值：** False|  
  
 設定這些屬性的 XML 字串格式如下：  
  
```  
<CustomProps>  
   <UseSSO vt="11">-1</UseSSO>  
   <SuspendFailedRequests vt="11">-1</SuspendFailedRequests>  
   <ReturnCorrelationHandle vt="11">-1</ReturnCorrelationHandle>  
   <ResponseContentType vt="8">text/xml</ResponseContentType>  
   <LoopBack vt="11">-1</LoopBack>  
</CustomProps>  
  
```  
  
 **如何設定 HTTP 接收位置與 BizTalk Server 管理主控台**  
  
 若要使用 [BizTalk Server 管理] 主控台設定接收位置，請使用下列程序。  
  
### <a name="to-configure-variables-for-an-http-receive-location"></a>設定 HTTP 接收位置的變數  
  
1.  設定 Internet Information Services (IIS) 以使用 HTTP 接收位置。 如需設定 IIS 的指示，請參閱[如何設定 HTTP 接收位置的 IIS](../core/how-to-configure-iis-for-an-http-receive-location.md)。  
  
2.  在 BizTalk Server 管理主控台中，展開  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開您要建立接收位置的應用程式。  
  
3.  在左窗格中，按一下 **接收埠**節點。 然後在右窗格中，使用滑鼠右鍵按一下與現有接收位置關聯的接收埠，或是您要與新接收位置關聯的接收埠，然後按一下 **[屬性]**。  
  
4.  在**接收埠屬性**對話方塊的左窗格中，選取**接收位置**，並在右窗格中，按兩下現有接收位置或按一下**新增**若要建立新接收位置。  
  
5.  在**接收位置屬性**對話方塊中，於**傳輸**區段旁邊**類型**，選取**HTTP**從下拉式清單然後按一下 **設定**。  
  
6.  在**HTTP 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**虛擬目錄加 ISAPI 延伸模組**|指定用來公佈 HTTP/HTTPS 接收位置所接收到之訊息的虛擬目錄名稱。 虛擬目錄包含接收位置 DLL 名稱和選擇性查詢字串。 虛擬目錄名稱的範例如：<br /><br /> /\<虛擬目錄\>/BTSHTTPReceive.dll<br /><br /> /\<虛擬目錄\>/BTSHTTPReceive.dll 嗎？購買 %20order<br /><br /> 此位置 (包括所有子資料夾) 最多只能包含一個 BTSHTTPReceive.dll ISAPI 延伸模組。<br /><br /> **類型：**字串<br /><br /> **最大長度：** 256**附註：** URI 傳送埠或接收位置不能超過 256 個字元。|  
    |**公用位址**|指定此接收位置的完整格式 URI。 此屬性的值是由伺服器名稱與虛擬目錄所組成。 BizTalk 傳訊引擎會對外部夥伴公開此位址。 指定的 URI 應指派當訊息傳送至 BizTalk Server 時，所要連接的交易夥伴的公用網站 URL。<br /><br /> 此資訊是選擇性的，BizTalk Server 不會使用。 此參數可用來允許管理員記載接收位置所連結的公用 URL。<br /><br /> **類型：**字串<br /><br /> **最小長度：** 0<br /><br /> **最大長度：** 256|  
    |**傳回內容類型**|指定接收位置傳回給用戶端的 HTTP 回應訊息內容類型。 此屬性只適用於要求-回應接收位置。<br /><br /> **預設值：** text/xml<br /><br /> **類型：**字串<br /><br /> **最小長度：** 0<br /><br /> **最大長度：** 256|  
    |**回送**|定義對於在此位置接收到的要求訊息，是要設定路由至傳送埠或傳回此接收位置，以當做回應傳送。 此屬性只適用於要求-回應接收位置。<br /><br /> **預設值：** False<br /><br /> **類型：**布林|  
    |**成功 （只有單向連接埠） 時傳回相互關聯控制代碼**|定義若成功，接收位置將傳送 HTTP 回應上已提交之訊息的相互關聯 Token 給用戶端。 此屬性只適用於單向接收位置。<br /><br /> **預設值：** ，則為 True<br /><br /> **類型：**布林|  
    |**使用單一登入**|指示使用「企業單一登入」。<br /><br /> **預設值：** False<br /><br /> **類型：**布林**附註：**如果啟用此選項，則您也必須啟用的選項**允許票證**在**SSO 系統**層級。 **允許票證**選項是可在**選項** 索引標籤**SSO 系統屬性**對話方塊可以在**SSO 管理**MMC 介面。 如果已啟用此選項和**允許票證**選項**SSO 系統**未啟用層級，然後由此接收任何訊息接收位置會遭擱置。|  
    |**擱置失敗的要求**|指出是否要擱置輸入處理失敗的 HTTP 要求。<br /><br /> False 值表示要捨棄失敗的要求，並將錯誤狀態碼 (401 或 500) 傳送至用戶端。<br /><br /> 如果為 true 值表示擱置失敗的要求，並將 「 已接受 」 狀態碼 (200) 傳送至用戶端進行單向接收埠或用戶端將 「 錯誤 」 狀態碼 (500) 雙向接收埠。<br /><br /> **預設值：** False<br /><br /> **類型：**布林|  
  
7.  按一下**確定**儲存設定。  
  
8.  在 **[接收位置屬性]** 對話方塊中輸入適當的值，以完成接收位置的組態，然後按一下 **[確定]** 儲存設定值。 如需有關資訊**接收位置屬性**對話方塊中，請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。  
  
 HTTP 用戶端呼叫「HTTP 位置」時，HTTP 配接器會使用匿名、基本、摘要或 Windows 整合式驗證來驗證 HTTP 用戶端。 若未驗證使用者，使用者內容會傳送至接收處理常式。  
  
> [!NOTE]
>  任何導致 SOAP 與 HTTP 共用相同程序的 IIS 組態都無效。 每個程序只能有一個隔離的接收器。